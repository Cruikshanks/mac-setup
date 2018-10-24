# Pyenv

[Pyenv](https://github.com/pyenv/pyenv) is a version manager for Python.

## Mojave

Following the update to Mojave kept getting this error whenever I tried to install a version of Python using Pyenv

> ERROR: The Python zlib extension was not compiled. Missing the zlib?

The [Pyenv documentation](https://github.com/pyenv/pyenv/wiki/Common-build-problems#requirements) itself says

> When running Mojave or higher (10.14+) you will also need to install the additional SDK headers by downloading them from Apple Developers.

I just ran the command it suggests

```bash
sudo installer -pkg /Library/Developer/CommandLineTools/Packages/macOS_SDK_headers_for_macOS_10.14.pkg -target /
```

And from then on I could install python via pyenv with no issues.

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
