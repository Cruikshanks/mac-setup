# Rbenv

[Rbenv](https://github.com/rbenv/rbenv) is a version manager for Ruby.

## Install

```bash
brew install rbenv
```

The output will tell you to add something like `eval "$(rbenv init -)"a` to your bash profile. This is used to load rbenv in your session. As the default shell in OSX is Catalina, I'm using [Oh my zsh](ohmyzsh.md) to manage plugins for it. One plugin is [rbenv](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/rbenv) and it will handle this for you.

Just add the following to your `~/.zshrc` file

```bash
plugins=(... rbenv)
```

## Use

Grab the latest version of [Ruby](https://www.ruby-lang.org/) by first running `rbenv install -l` which will return a list of all available **Ruby** versions. Select the latest and then run `rbenv install 2.4.2`. Then run `rbenv global 2.4.2` to set it as you global default version, replacing the outdated system one.

After all installs run the following

```bash
gem install bundler
gem install rubocop
```

All projects will require [Bundler](http://bundler.io/), and my [VSCode](vscode.md) setup requires [Rubocop](https://github.com/bbatsov/rubocop) to be installed.

### Errors

I commonly get 2 errors when trying to build ruby versions

#### Avira antivirus

If realtime scanning is enabled it seems to stop rbenv from compiling ruby versions. Disable it before attempting any `rbenv install`.

#### Pre 2.4 ruby versions

There is an issue with pre 2.4 versions of ruby being built. They appear to need to use openssl 1.0 however since 2019-10-02 it appears the homebrew version of ruby build now uses openssl 1.1 (see <https://github.com/rbenv/ruby-build/issues/1353#issue-501787062>)

To build older versions do the following once

```bash
brew install openssl
```

Then each time you need to build an old version use

```bash
RUBY_CONFIGURE_OPTS="--with-openssl-dir=/usr/local/opt/openssl" rbenv install 2.3.1
```
