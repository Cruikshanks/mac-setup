# VS Code

[VS Code](https://code.visualstudio.com/) is a text editor where I generally do any **Node.js** work (I use [Atom](https://atom.io/) for everything else).

## Install

```bash
brew cask install visual-studio-code
```

## Configure

### Add VSCode to PATH

First thing is to add **VSCode** to the path so we can open it from the command line. Enter SHIFT+COMMAND+P and search for "Install 'code' command in PATH" and select it.

## Settings

Open the **settings** via `Preferences -> Settings`

### Commonly used

- Editor: Tab Size = 2
- Editor: Word Wrap = On
- Editor: Rules `"editor.rulers": [80, 120]`
- Minimap: Enabled = false
- Files: Insert Final Newline = true
- Files: Trim Final Newlines = true
- Files Trim Trailing Whitespace = true
- Appearance: Color Theme = Solarized Dark
- Editor Mgmt: Swipe To Navigate = true
- Workbench: Startup Editor  = none

#### Extensions

##### Ruby configuration

- Code Completion = rcodetools
- Format = rubocop
- Intellisense = rubyLocate
- Use Language Server = true

## Extensions

VSCode works best when you have the plugins you need to support your ways of working.

### Cucumber (Gherkin) Full Support

VSCode Cucumber (Gherkin) Language Support + Format + Steps/PageObjects Autocomplete.

https://marketplace.visualstudio.com/items?itemName=alexkrechik.cucumberautocomplete

### Docker

The Docker extension makes it easy to build, manage and deploy containerized applications from Visual Studio Code.

https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker

### Git History

View git log, file history, compare branches or commits

https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory

### GitLens — Git supercharged

Supercharge the Git capabilities built into Visual Studio Code — Visualize code authorship at a glance via Git blame annotations and code lens, seamlessly navigate and explore Git repositories, gain valuable insights via powerful comparison commands, and so much more.

https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens

### Markdownlint

A library of rules to encourage standards and consistency for Markdown files. It is powered by markdownlint for Node.js which is based on markdownlint for Ruby.

https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint

### Material Icon Theme

The Material Icon Theme provides lots of icons based on Material Design for Visual Studio Code.

https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme

### Ruby Solargraph

Solargraph is a language server that provides intellisense, code completion, and inline documentation for Ruby.

https://marketplace.visualstudio.com/items?itemName=castwide.solargraph

I was previously using the Ruby extension from Peng Lv but unfortunately the key thing I needed, rubocop scanning just never seemed to work properly. Finally after doing some digging it looked like it just wouldn't ever play nice when using something like rbenv and bundler. However in one of the comments someone mentioned [Solargraph](https://github.com/castwide/solargraph) and that seemed to do the trick.

#### Setup

Before adding the extension run the following commands

```bash
gem install solargraph
yard gems
solargraph download-core 2.4.2
```

The first command will install the solargraph gem globally for the current version of ruby, which also installs [Yard](https://github.com/lsegal/yard). `yard gems` will generate documentation for all your currently installed gems. The last command will install documentation for standard ruby, for the version you're using.

Back in VSCode open the settings for Solargraph and set Diagnostics to `true`. This will enable rubocop. Then restart VSCode and all should be good.

### SQLTools

Database management done right. Connection explorer, query runner, intellisense, bookmarks, query history. (Mainly got for the SQL intellisense)

https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools

### StandardJS - JavaScript Standard Style

Integrates JavaScript Standard Style into VS Code.

https://marketplace.visualstudio.com/items?itemName=chenxsan.vscode-standardjs

### Systemd Support

Systemd unit file syntax, autocompletion for Visual Studio Code.

https://marketplace.visualstudio.com/items?itemName=hangxingliu.vscode-systemd-support

### Trailing Spaces

Highlight trailing spaces and delete them in a flash!

https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces

### vscode-pdf

Display pdf in VSCode.

https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf

## Keyboard shortcuts

Add the following keyboard shortcuts via `Preferences -> Keyboard shortcuts`

- `workbench.action.terminal.kill` = - alt+cmd+q
