# NVM

**NVM** or [Node Version Manager](https://github.com/creationix/nvm) is a tool that allows you to manage multiple active node.js versions.

## Install

```bash
brew install nvm
```

Then add the following to `~/.bash_profile`

```text
# NVM support when installed via home brew
if [ -f "$(brew --prefix)/opt/nvm/nvm.sh" ]; then
  export NVM_DIR="$HOME/.nvm"
  . "$(brew --prefix)/opt/nvm/nvm.sh"
fi
```

## Use

After installing **NVM** get the latest version of [Node.js](https://nodejs.org/) by simply running `nvm install node`. To install a specific version use `nvm install v5.1.0`.

