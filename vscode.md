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

### Ruby

Provides Ruby language and debugging support for Visual Studio Code

https://marketplace.visualstudio.com/items?itemName=rebornix.Ruby

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
