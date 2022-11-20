# SSH

There are no tools to install for this one. This is more a guide to how I have [SSH](https://en.wikipedia.org/wiki/Secure_Shell) configured on my machine.

I'm required to connect to lots of different environments, which at least are all linux based. As such what I cover below has so far given me the most hassle free and simplest to use setup.

Finally, I'm clearly a Mac user so I'm rocking [OpenSSH](https://www.openssh.com/) which comes built into the OS.

## Confirm your ssh version

For this to work you'll need to be using OpenSSH 7.3p1 or greater. You can check with

```bash
ssh -V
```

## Setup folders

You'll need to have the folder `~/.ssh` created. Nearly all guides and tools assume you have this. But don't be surprised if it doesn't exist when you go looking. If that's the case create it followed by another we'll use called `config.d`.

```bash
mkdir ~/.ssh
cd ~/.ssh
mkdir config.d
```

`config.d` is where we'll be adding our 'host' setup but more on that later.

> Why `config.d`? When I first went looking for how to store hosts info outside of the main config file `config.d` was the name used in the examples I followed. So 🤷‍♂️

## Create base config

Within `~/.ssh` create a file called `config` (`touch config`). This definately is the standard for OpenSSH. Add the following to it

```bash
# To better manage the various services each has their own file containing the
# host config. Since ssh version 7.3p1 it has been possible to include
# other configuration files using the `Include` keyword.
#
# You can specify them individually e.g.
#
# Include config.d/wex
#
# Or do as we do and keep all our hosts config in the ~/.ssh/config.d folder
# and include them all.
#
# See https://superuser.com/a/1142813 for details
Include config.d/*

# On macOS Sierra 10.12.2 or newer keys can be automatically loaded into ssh-agent
# and passphrases stored in the keychain.
Host *
  # Do not use this option. It adds unncessary keys to ssh-agent, which in turn
  # leads to the `Too many authentication failures for user` error when trying
  # to connect to a Jenkins slave once connected to a bastion server
  AddKeysToAgent yes
  UseKeychain yes
  # If you use an ssh-agent, ssh will automatically try to use the keys in the
  # agent, even if you have not specified them with in ssh_config's IdentityFile
  # (or -i) option. This is a common reason you might get the
  # `Too many authentication failures for user` error. Using the
  # `IdentitiesOnly yes` option will disable this behavior.
  # See http://superuser.com/a/436015 for more details
  # It should be noted however this only applies when connecting to the bastion
  # server. In order to connect to an environment's Jenkins slave we need to
  # forward the [ENV_SERVICE]KP.pem file. We do this by adding it to the
  # ssh-agent via ssh-add and specifying `ForwardAgent yes`. When on the
  # bastion server this flag no longer applies. So if `ssh-add -L` returns more
  # than 5 entries, you may be at risk of getting a
  # `Too many authentication failures for user` error. The only solution found
  # so far is to clear them out using `ssh-add -D` then re-add the key for the
  # env you are interested in
  IdentitiesOnly yes
  IdentityFile ~/.ssh/id_rsa
  # Added to support connecting to AWS instances on macOS Ventura. RSA and SHA1
  # are known to be vulnerable so many ssh clients are now disabling them by
  # default. When moving to the new Mac Pro M1's running Ventura we found we
  # were getting `Sign_and_send_pubkey: no mutual signature supported`.
  # Thanks to https://stackoverflow.com/a/74258486/6117745 we figured out adding
  # these 2 entries resolved the issue.
  PubkeyAcceptedKeyTypes=+ssh-rsa
  HostKeyAlgorithms=+ssh-rsa

```

The comments in the code explain whats going on. My notes around `PubkeyAcceptedKeyTypes` are recent so should be accurate. The rest have been copied and pasted from build to build over the last 5 years. Stuff still seems to work! But be warned, they may now be out of date or not the best way to go about things.

## Add your first 'service'

By service I mean all environments related to a 'thing'. For example, the Defra Digital Service [Waste Exemptions (WEX)](https://www.gov.uk/guidance/register-your-waste-exemptions-environmental-permits) is a 'thing' I work on. Like a lot of things behind the scenes it has multiple environments, each of which I may need to connect to.

> I'm going to use WEX as my example service throughout. So, where you see WEX feel free to choose a different name.

### ssh keys

First step, create another folder in `~/.ssh`

```bash
cd ~/.ssh
mkdir wex
```

Into this drop the keys you'll need to connect. Typically this is 2 per environment; one to allow connection to the [bastion host](https://en.wikipedia.org/wiki/Bastion_host), another to allow connection to the servers from the bastion host.

> As it's likely I didn't create the keys I can't trust they will have a consistent naming convention. However, you are fine to rename them to something more meaningful. Name of the file does not matter when it comes to keys.

Then create a file in `~/.ssh` e.g. `wex.sh` and add the following content

```bash
#!/bin/bash

# Ensure the permissions are correct on the keys. If they are to permissive ssh
# won't allow you to connect with them
chmod a-rwx ~/.ssh/wex/*.pem
chmod u+rwx ~/.ssh/wex/*.pem

# Clear all existing keys to avoid `Too many authentication failures for user`
# error
ssh-add -D

# Add the keys to ssh agent. Note, you do not add any bastion keys. Ssh agent
# is the mechanism by which when we connect to the bastion, we also have the
# key loaded into the session that then allows us to access our servers from it.
/usr/bin/ssh-add -K ~/.ssh/wex/wex_dev.pem
/usr/bin/ssh-add -K ~/.ssh/wex/wex_tst.pem
/usr/bin/ssh-add -K ~/.ssh/wex/wex_pre.pem

echo "WEX keys added"

```

> You can call this manually when needed. But I prefer to setup an alias in my ~/.zshrc for example, `alias wex='. ~/.ssh/wex.sh'`

### Host file

Next create a file in `~/.ssh/config.d` called `wex`. Add the following content

```bash
### WEX ########################################################################
# Development Bastion server
# Private key for WEX wex_dev.pem
# Equivalent in a 1 liner
# ssh -A -o IdentitiesOnly=yes \
#   -i ~/.ssh/wex/wex_dev_bas.pem \
#   letmein@10.20.30.40
Host wex-dv
  HostName 10.20.30.40
  Port 22
  User letmein
  IdentitiesOnly yes
  IdentityFile ~/.ssh/wex/wex_dev_bas.pem
  ForwardAgent yes
  ServerAliveInterval 30

# Test Bastion server
# Private key for WEX wex_txt.pem
# Equivalent in a 1 liner
# ssh -A -o IdentitiesOnly=yes \
#   -i ~/.ssh/wex/wex_tst_bas.pem \
#   letmein@10.20.30.50
Host wex-qa
  HostName 10.20.30.50
  Port 22
  User letmein
  IdentitiesOnly yes
  IdentityFile ~/.ssh/wex/wex_tst_bas.pem
  ForwardAgent yes
  ServerAliveInterval 30

# Pre-prod Bastion server
# Private key for WEX wex_pre.pem
# Equivalent in a 1 liner
# ssh -A -o IdentitiesOnly=yes \
#   -i ~/.ssh/wex/wex_pre_bas.pem \
#   letmein@10.20.30.60
Host wex-pp
  HostName 10.20.30.60
  Port 22
  User letmein
  IdentitiesOnly yes
  IdentityFile ~/.ssh/wex/wex_pre_bas.pem
  ForwardAgent yes
  ServerAliveInterval 30

```

You'll need to update the following items to their real values

- `User`
- `HostName`
- `IdentifyFile`

You are free to set the `Host`, for example, `wex-dv` to whatever makes sense to you.

That's it. Probably best to kill the terminal to ensure everything is sourced correctly before you try and use this.

### Connect

You should now be ready to connect

```bash
. ~/.ssh/wex.sh # Or just `wex` if you have created the alias
ssh wex-dv
```

If everything is setup correctly you should fine yourself on the bastion host. To then connect to a server you'll need to use `username@servername`, for example, `letmein@WEXBES01`. You can normally find servernames by looking at the local `hosts` file, for example, `cat /etc/hosts`.
