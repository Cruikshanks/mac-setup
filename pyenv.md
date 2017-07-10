# Pyenv

[Pyenv](https://github.com/pyenv/pyenv) is a version manager for Python.

## Install

```bash
brew install pyenv
pyenv init
```

`pyenv init` in my case outputted the following in my terminal

```text
# Load pyenv automatically by appending
# the following to ~/.bash_profile:

eval "$(pyenv init -)"
```

I actually add a slightly tweaked version to protect against errors should **pyenv** not be found

```bash
# To enable shims and autocompletion for pyenv
if which pyenv > /dev/null; then eval "$(pyenv init -)"; fi
```

If you want more details on what `pyenv init` actually does check out [Advanced Configuration](https://github.com/pyenv/pyenv#advanced-configuration).

## Use

Grab the latest version of [Python](https://www.python.org/) by first running `pyenv install -l` which will return a list of all available **Python** versions. Select the latest version 3 branch and then run `pyenv install 3.6.1`. Then run `pyenv global 3.6.1` to set it as you global default version, replacing the outdated system one.
