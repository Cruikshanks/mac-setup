# Rbenv

[Rbenv](https://github.com/rbenv/rbenv) is a version manager for Ruby.

## Install

```bash
brew install rbenv
rbenv init
```

`rbenv init` in my case outputted the following in my terminal

```text
# Load rbenv automatically by appending
# the following to ~/.bash_profile:

eval "$(rbenv init -)"
```

I actually add a slightly tweaked version to protect against errors should rbenv not be found

```bash
# To enable shims and autocompletion for rbenv
if which rbenv > /dev/null; then eval "$(rbenv init -)"; fi
```

If you want more details on what `rbenv init` actually does check out [How rbenv hooks into your shell](https://github.com/rbenv/rbenv#how-rbenv-hooks-into-your-shell).

## Use

Grab the latest version of [Ruby](https://www.ruby-lang.org/) by first running `rbenv install -l` which will return a list of all available **Ruby** versions. Select the latest and then run `rbenv install 2.4.1`. Then run `rbenv global 2.4.1` to set it as you global default version, replacing the outdated system one. 

After all installs run the following

```bash
gem install bundler
gem install rubocop
```

All projects will require [Bundler](http://bundler.io/), and if you open **Atom** when the current **Ruby** version doesn't have [Rubocop](https://github.com/bbatsov/rubocop) installed you'll get errors.
 
