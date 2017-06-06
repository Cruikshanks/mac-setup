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
git config --global core.editor "vim"
```

### Always use https over ssh

Have found port 22 for SSH can often be blocked, which can cause issues when pulling in dependencies that rely refer directly to a GitHub repo via SSH. This solves the problem.

```bash
git config --global url."https://".insteadOf git://
```

### Stop git asking for GitHub username

```bash
git config --global url."https://Cruikshanks@github.com".insteadOf "https://github.com"
```

### Cache passwords

This will cache a password for a day, so only requires you to enter it the once. The first command enables the cache. The second sets the timeout to 8 hours.

```bash
git config --global credential.helper cache
git config --global credential.helper 'cache --timeout=28800'
```

### Use 'simple' for push default

If you just do a git push from the command line you’ll get a message about the default behaviour of push changing. This message will keep appearing until you explicitly tell git what behaviour you wish to use. Simple means it will push only the current branch, and only if their is a matching one in origin.

```bash
git config --global push.default simple
```

### Allow pushing to https urls with invalid certificates

Some places have a habit when setting things up internally of not bothering with certificates. This bypasses the issue, but use with caution.

```bash
git config --global push.default simple
```

### Auto prune when pulling and fetching

```bash
git config --global fetch.prune true
```

## Aliases

```bash
git config --global alias.lg1 "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(black)%s%C(reset) %C(dim black)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
git config --global alias.lg2 "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(black)%s%C(reset) %C(dim black)- %an%C(reset)' --all"
git config --global alias.lg3 "log --graph --oneline --decorate --date=relative --all"
git config --global alias.lg4 "log --graph --abbrev-commit --decorate --date=relative --all"
```

To use call `git lg1` i.e. `git [alias]`.

