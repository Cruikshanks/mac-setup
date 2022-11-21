# Git

Used for source control.

## Install

```bash
brew install git
```

## Configure

### Set username and email address

```bash
git config --global user.name "Alan Cruikshanks"
git config --global user.email "alan.cruikshanks@gmail.com"
```

### Set default editor

```bash
git config --global core.editor "code --wait --disable-extensions"
```

### Color git output

```bash
git config --global color.ui auto
```

### Always use https over ssh

Have found port 22 for SSH can often be blocked, which can cause issues when pulling in dependencies that rely refer directly to a GitHub repo via SSH. This solves the problem.

```bash
git config --global url."https://".insteadOf git://
```

### Default initial branch name

```bash
git config --global init.defaultBranch main
```

### Auto prune when pulling and fetching

```bash
git config --global fetch.prune true
```

### Set pull strategy

```bash
git config --global pull.ff only
```

Git 2.27 adding a warning if doing a git pull when the `git config pull` setting is missing. The full message is

```text
warning: Pulling without specifying how to reconcile divergent branches is
discouraged. You can squelch this message by running one of the following
commands sometime before your next pull:

  git config pull.rebase false  # merge (the default strategy)
  git config pull.rebase true   # rebase
  git config pull.ff only       # fast-forward only

You can replace "git config" with "git config --global" to set a default
preference for all repositories. You can also pass --rebase, --no-rebase,
or --ff-only on the command line to override the configured default per
invocation.
```

I did not realise that a `git pull` is not a harmless operation.

> In its default mode, git pull is shorthand for git fetch followed by git merge FETCH_HEAD.
>
> [How to deal with this git warning?](https://stackoverflow.com/a/62653400/6117745)

The default strategy is `git config pull.rebase false` which could end up creating a merge commit if there is a difference between the branches. With `git pull --ff-only`, Git will update the branch only if it can be "fast-forwarded" without making new commits. If it can't it will just abort with an error message.

This is how I'd prefer it behave. So this is the strategy I have gone with. I can deal with any divergence manually then.

### Set GPG signing

You'll need to have followed the instructions in [GPG](gpg.md) first. It also includes how to find the `key id`.

```bash
git config --global user.signingkey [key ID]
```

Then call the following to sign all commits by default

```bash
git config --global commit.gpgsign true
```

This saves you having to remember to add `-S` to all your `git commit` calls.

Having done this, [GPG](gpg.md) includes instructions on how to **Sign commits automatically**. Follow that to avoid having to input your passphrase everytime.

## Aliases

```bash
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
git config --global alias.lg1 "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(black)%s%C(reset) %C(dim black)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
git config --global alias.lg2 "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(black)%s%C(reset) %C(dim black)- %an%C(reset)' --all"
git config --global alias.lg3 "log --graph --oneline --decorate --date=relative --all"
git config --global alias.lg4 "log --graph --abbrev-commit --decorate --date=relative --all"
```

To use call `git lg1` i.e. `git [alias]`.

## Local settings

### Allow pushing to https urls with invalid certificates

Some places have a habit when setting things up internally of not bothering with certificates. This bypasses the issue, but use with caution, and set at the repo level rather than globally.

```bash
git config http.sslVerify false
```
