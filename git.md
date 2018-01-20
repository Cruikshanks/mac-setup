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

### Auto prune when pulling and fetching

```bash
git config --global fetch.prune true
```

### Set GPG signing

```bash
git config --global user.signingkey [key ID]
```

See [GPG](gpg.md) and the 'Viewing keys' section on how to find the key ID.

You must then add this to `.bash_profile`

```bash
# Needed to support signing of my git commits
export GPG_TTY=$(tty)
```

Finally call the following to sign all commits by default

```bash
git config --global commit.gpgsign true
```

This saves you having to remember to add `-S` to all your `git commit` calls.

## Aliases

```bash
git config --global alias.lg1 "log --graph --abbrev-commit --decorate --date=relative --format=format:'%C(bold blue)%h%C(reset) - %C(bold green)(%ar)%C(reset) %C(black)%s%C(reset) %C(dim black)- %an%C(reset)%C(bold yellow)%d%C(reset)' --all"
git config --global alias.lg2 "log --graph --abbrev-commit --decorate --format=format:'%C(bold blue)%h%C(reset) - %C(bold cyan)%aD%C(reset) %C(bold green)(%ar)%C(reset)%C(bold yellow)%d%C(reset)%n''          %C(black)%s%C(reset) %C(dim black)- %an%C(reset)' --all"
git config --global alias.lg3 "log --graph --oneline --decorate --date=relative --all"
git config --global alias.lg4 "log --graph --abbrev-commit --decorate --date=relative --all"
```

To use call `git lg1` i.e. `git [alias]`.

### Terminal aliases

Add the following to `/.bash_profile` in order to enable quick commands that can be used in the terminal

```bash
# Alias for git status. -s means display output using the short format
alias gst='git status -s'
# Alias for git branch. -a means show all branches, both local and remote
alias gb='git branch -a'
```

## Local settings

### Allow pushing to https urls with invalid certificates

Some places have a habit when setting things up internally of not bothering with certificates. This bypasses the issue, but use with caution, and set at the repo level rather than globally.

```bash
git config http.sslVerify false
```

### Sign commits by default

To manually sign a commit you call `git commit -S`. You can also set this as the default on a global or local level. I choose to go with local due to not all source code hosts supporting GPG signed commits.

```bash
git config commit.gpgsign true
```

You will be required to enter your key's passphrase after every commit, but the [GPG suite](https://gpgtools.org/) has tools that let you store your passphrase in the Mac OS keychain which removes this requirement. At this time I'm happy to just keep entering it.
