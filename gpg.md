# GPG

> This guide is based on [Sign git commits on GitHub with GPG in macOS](https://samuelsson.dev/sign-git-commits-on-github-with-gpg-in-macos/). It's previous version was based on [Signing commits with gpg](https://help.github.com/articles/signing-commits-with-gpg/)

[GnuPG](https://www.gnupg.org/index.html) (also known as GPG) is a complete and free implementation of the OpenPGP standard as defined by RFC4880 (also known as PGP). It is a command line tool with features for easy integration with other applications. It is used to encrypt and sign data, and features a key management system.

The first step is to install it.

## Install

```bash
brew install gnupg
```

To support git signing of commits you normally would also add `export GPG_TTY=$(tty)` to your bash profile. As I'm using [Oh my zsh](ohmyzsh.md) one plugin is [gpg-agent](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/gpg-agent) and it will handle this for you.

[ohmyzsh](/ohmyzsh.md) covers adding it to the plugins list.

## Generating a key

I have a generated key for use when signing my git commits. However, should I ever need to generate another one you just call `gpg --full-generate-key` and complete the options.

## Exporting existing keys

> How to [back up your pgp keys with gpg](https://msol.io/blog/tech/back-up-your-pgp-keys-with-gpg/) was what provided the commands below. They are also covered in [Sign git commits on GitHub with GPG in macOS](https://samuelsson.dev/sign-git-commits-on-github-with-gpg-in-macos/).

I export my keys from the old Mac to the new one. To export my existing keys I run the following

```bash
gpg --armor --export > pgp-public-keys.asc
gpg --armor --export-secret-keys > pgp-private-keys.asc
gpg --export-ownertrust > pgp-ownertrust.asc
```

Having created these files I then securely transfer them to the new machine ready for importing.

## Importing

To import the files we saved earlier and run the following

```bash
gpg --import pgp-public-keys.asc
gpg --import pgp-private-keys.asc
gpg --import-ownertrust pgp-ownertrust.asc
```

That's it!

## Viewing keys

When setting Git and GitHub up to use your key you'll often be asked to get the key ID.

```bash
gpg --list-secret-keys --keyid-format LONG
```

Running this will return something like this

```bash
$ gpg --list-secret-keys --keyid-format LONG
/Users/hubot/.gnupg/secring.gpg
------------------------------------
sec   4096R/3AA5C34371567BD2 2016-03-10 [expires: 2017-03-10]
uid                          Hubot
ssb   4096R/42B317FD4BA89E7A 2016-03-10
```

They key ID in this example is **3AA5C34371567BD2**.

## Signing commits

Having done all this you can then tell git about the gpg key. [Git](git.md) covers how to do this.

## Sign commits automatically

In [Git](git.md) we also set the config item that tells git to _always_ sign our commits. If you leave it at that, you'll be asked for your GPG passphrase on each commit.

To avoid this do the following. First install [PINEntry](https://github.com/GPGTools/pinentry)

```bash
brew install pinentry-mac
```

Then create the following file `~/.gnupg/gpg-agent.conf` and add the following

```bash
pinentry-program /opt/homebrew/bin/pinentry-mac
```

> Note - The location for pinentry-mac might be different. But when you run the brew command it will detail these instructions including the exact content to add to `gpg-agent.conf`.

In order to save the passphrase to **macOS Keychain** (which is where pinentry will grab it from on subsequent commits) you need to kill `gpg-agent` before you next make a commit.

```bash
gpgconf --kill gpg-agent
```

When you make the commit a dialog will appear and ask for the passphrase. That should be it from then on.
