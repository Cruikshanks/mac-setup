# Pyenv

[pyenv](https://github.com/pyenv/pyenv) is a tool that allows you to manage multiple active python versions.

## Install

```bash
brew install pyenv
```

Before we can install python, we need to ensure the [build dependencies it relies on are installed](https://github.com/pyenv/pyenv/wiki#suggested-build-environment). pyenv does not download pre-built binaries. Instead, it builds python directly on the host to ensure dependent binaries are correct for the OS & hardware.

```bash
brew install openssl readline sqlite3 xz zlib tcl-tk@8
```

> When I did this, only a couple were not already installed and brew handles it.

## Configure

Add the following to the `~/.zshrc` file _before_ the `plugins=(..)` declaration.

```bash
# Needed to support pyenv and the pyenv plugin
# See https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/pyenv
export PYENV_ROOT="$HOME/.pyenv"
export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init --path)"
```

Then add `pyenv` to the `plugins(..)` declaration.

```bash
plugins=(git gpg-agent pyenv rbenv zsh-nvm)
```

## Add the current version of python

Run `pyenv install -l` to get the list of available versions. Assuming python v3 is still the current major release, pick which ever is the latest non-dev release, then set it as the global version.

```bash
pyenv install 3.13.1
pyenv global 3.13.1
```

## pyenv-virtualenv Plugin

pyenv supports [plugins](https://github.com/pyenv/pyenv/wiki/Plugins) though I only add [pyenv-virtualenv](https://github.com/pyenv/pyenv-virtualenv).

As far as I can tell, python adopts an approach similar to [rvm](https://rvm.io/). Python is like ruby in that it installs its packages to a central place. When using pyenv (or rbenv in the case of ruby), these would go under the version of python currently being used. So, the same package might be installed twice, if you have 2 different versions. But if you had 5 different projects using that package, and all on the same version, when you install them you _wouldn't_ end up with 5 copies. You would just have 1.

Or you would in ruby if you just stuck with rbenv. rvm was the original tool in ruby-land to manage multiple ruby versions (what it refers to as interpreters). You are then expected to create an environment specific to your project. That way you keep your projects dependencies separate. In our example above, you _would_ end up with 5 copies of the same package.

That was how I started with ruby, but things got a lot better with how gems are handled, hence the move to rbenv and dropping the need to create project environments.

Back in python-land, creating an environment still seems to be the norm. So, this tool, along with the VSCode extension [Python Environment Manager (PEM)](https://marketplace.visualstudio.com/items?itemName=donjayamanne.python-environment-manager&ssr=false) was what I ended up using to do this: pyenv-virtualenv to create the virtual env and PEM to select it in VSCode when working with a python project.

### Install

```bash
brew install pyenv-virtualenv
```

### Usage

To create an environment for a specific version of python installed

```bash
pyenv virtualenv 3.13.1 my-awesome-project-3.13.1
```

Or let it work out the current version for you.

```bash
pyenv virtualenv my-awesome-project
```

To list the current virtualenvs use `pyenv virtualenvs`.

You can manually activate a virtualenv on the command line using `pyenv activate my-awesome-project`. The plugin supports automatically activating a virtualenv using a `.python-version` file that contains the name of a valid virtual environment as shown in the output of `pyenv virtualenvs`.

It then tells you to add `eval "$(pyenv virtualenv-init -)"` to your shell. However, I can skip this step because the [oh-my-zsh](/ohmyzsh.md) plugin handles this for me.
