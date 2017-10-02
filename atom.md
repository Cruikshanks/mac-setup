# Atom

[Atom](https://atom.io/) is a text editor where I generally do everything but **Node.js** (I use [VS Code](https://code.visualstudio.com/) for that).

## Install

```bash
brew cask install atom
```

## Configure

Open 'Preferences' and then select 'Settings'. Make the following changes

- `Soft wrap` tick the box
- `Tab type` set to soft

## Plugins

Atom works best when you have the plugins you need to support your ways of working.

### File icons

Atom file-specific icons for improved visual grepping <https://atom.io/packages/file-icons>.

```bash
apm install file-icons
```

### Auto update packages

Keep your Atom packages up to date <https://atom.io/packages/auto-update-packages>.

```bash
apm install auto-update-packages
```

### Omni-ruler

Add multiple rulers/wrap guides <https://atom.io/packages/omni-ruler>.

```bash
apm install omni-ruler
```

In its settings page set `Columns` to `80, 120`.

### Atom-beautify

Beautify HTML, CSS, JavaScript, PHP, Python, Ruby, Java, C, C++, C#, Objective-C, CoffeeScript, TypeScript, Coldfusion, SQL, and more in Atom <https://atom.io/packages/atom-beautify>.

```bash
apm install atom-beautify
```

### Language-docker

[Language-docker](https://atom.io/packages/language-docker) adds syntax highlighting for Dockerfiles in Atom.

```bash
apm install language-docker
```

### Linter

Linter is a base linter provider. You still need to install a specific linter for your language. You will find a full list on <https://atomlinter.github.io> <https://atom.io/packages/linter>.

```bash
apm install linter
```

### Linter-rubocop

Plugin for **Linter** provides an interface to [rubocop](https://github.com/bbatsov/rubocop). It will be used with files that have the “Ruby” syntax.

Before using this plugin, you must ensure that rubocop, version 0.37 or greater, is installed. Essentially when adding a new version of ruby you also want to install **rubocop** and [Bundler](http://bundler.io/).

```bash
apm install linter-rubocop
```

You can set the path to **rubocop** in the settings, but because I use **Rbenv** I shouldn't need to.

### Linter-docker

[Linter-docker](https://atom.io/packages/linter-docker) adds linting for Dockerfiles to Atom. It does this based on [Dockerlint](https://github.com/RedCoolBeans/dockerlint).

```bash
apm install linter-docker
```

### Todo Show Package

Finds all the TODOs, FIXMEs, CHANGEDs, etc. in your project <https://atom.io/packages/todo-show>.

```bash
apm install todo-show
```

### Less than-slash

Package for closing open tags when less-than, slash `</` is typed, like in Sublime Text 3 <https://atom.io/packages/less-than-slash>.

```bash
apm install less-than-slash
```

### Cucumber

Cucumber support for atom <https://atom.io/packages/cucumber>.

```bash
apm install cucumber
```

### PlatformIO IDE Terminal

A terminal package for Atom, complete with themes, API and more for PlatformIO IDE. Fork of terminal-plus. <https://atom.io/packages/platformio-ide-terminal>

```bash
apm install platformio-ide-terminal
```

