# Homebrew

[Homebrew](https://brew.sh/) describes itself as the "Missing Package Manager for macOS".

Rather than install apps directly, either through downloads from the web or via the app store, it is more common on 'dev' machines to install and manage apps using a package manager like **brew** (think [Chocolatey](https://chocolatey.org/) for Windows).

## Install

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

## Usage

In the main, just Google `brew app-I-want-to-install` and you'll find the [formulae](https://formulae.brew.sh/) to use.

In the main, the apps I install using this are what Homebrew terms [casks](https://docs.brew.sh/Manpage#terminology) (macOS native applications).

```bash
brew install --cask docker`
```

The rest are typically downloading shell scripts and running them, for example [pyenv](/pyenv.md). These are what Homebrew term **formula**.

```bash
brew install pyenv
```

To list what Homebrew has installed use `brew list`.

## Skip update for new machines

Whenever you run `brew install` it will run `brew update` automatically to ensure that Homebrew is on the latest version before attempting the install.

When I come to setup a new machine, I'll be running `brew install` many times, so this step can slow things down considerably. You can skip it though by calling `export HOMEBREW_NO_AUTO_UPDATE=1` first, in the terminal session you are using to run all your installs.

## Auto-update

Some apps I install with have inbuilt auto-update functions. For the rest, and Homebrew itself it is on you to update it.

In order to automate this I use [Homebrew Autoupdate](https://github.com/DomT4/homebrew-autoupdate).

### Install

```bash
brew tap domt4/autoupdate
```

> a **tap** is a directory (and usually Git repository) of **formulae** and **casks**

Then to enable auto-update call `brew autoupdate start 604800 --upgrade --cleanup`.

- `604800` the number of seconds between updates. This represents a week
- `--upgrade` also upgrade **casks** as well as Homebrew
- `cleanup` clean Homebrew's cache and logs
