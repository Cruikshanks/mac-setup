# VS Code

[VS Code](https://code.visualstudio.com/) is my main editor for all work. I used to use [Atom](https://atom.io/) for everything bar Node.js but have switched to it being my one for reasons 😁

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

- Editor: Minimap = false
- Editor: Tab Size = 2
- Editor: Word Wrap = On
- Editor: Scroll Beyond Last Line = false
- Editor: Trim Auto Whitespace = true
- Explorer: Confirm Drag And Drop = false
- Explorer: Compact Folders = false
- Explorer: Confirm Delete = false
- Minimap: Enabled = false
- Files: Trim Final Newlines = true
- Files: Trim Trailing Whitespace = true
- Files: Insert Final Newline = true
- Appearance: Color Theme = Solarized Dark
- Workbench: Startup Editor = none

### settings.json

Some things need to be updated in the `settings.json` file

```json
  "editor.rulers": [
      { "column": 80, "color": "#857f85" },
      { "column": 120, "color": "#ff0000a8" }
  ],
  "files.associations": {
      "Vagrantfile": "ruby",
      "Capfile": "ruby",
      "Dockerfile.*": "dockerfile"
  },
  "[csv]": {
        "editor.wordWrap": "off"
```

#### Terminal font

I found I had an issue with missing symbols in the terminal once I'd set up [oh-my-zsh](ohmyzsh.md). To ensure they displayed correctly I needed to set the following setting to match whatever I have set for the font in [iTerm2](iterm2.md).

- Terminal, Integrated: Font Family = 'Liberation Mono for Powerline'

## Extensions

VSCode works best when you have the plugins you need to support your ways of working.

### Cucumber (Gherkin) Full Support

VSCode Cucumber (Gherkin) Language Support + Format + Steps/PageObjects Autocomplete.

<https://marketplace.visualstudio.com/items?itemName=alexkrechik.cucumberautocomplete>

### Docker

The Docker extension makes it easy to build, manage and deploy containerized applications from Visual Studio Code.

<https://marketplace.visualstudio.com/items?itemName=PeterJausovec.vscode-docker>

### Git History

View git log, file history, compare branches or commits

<https://marketplace.visualstudio.com/items?itemName=donjayamanne.githistory>

### GitLens — Git supercharged

Supercharge the Git capabilities built into Visual Studio Code — Visualize code authorship at a glance via Git blame annotations and code lens, seamlessly navigate and explore Git repositories, gain valuable insights via powerful comparison commands, and so much more.

<https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens>

### Markdownlint

A library of rules to encourage standards and consistency for Markdown files. It is powered by markdownlint for Node.js which is based on markdownlint for Ruby.

<https://marketplace.visualstudio.com/items?itemName=DavidAnson.vscode-markdownlint>

### Material Icon Theme

The Material Icon Theme provides lots of icons based on Material Design for Visual Studio Code.

<https://marketplace.visualstudio.com/items?itemName=PKief.material-icon-theme>

### Rainbow CSV

Highlight CSV and TSV files in different colors, Run SQL-like queries

<https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv>

### Ruby Solargraph

Solargraph is a language server that provides intellisense, code completion, and inline documentation for Ruby.

<https://marketplace.visualstudio.com/items?itemName=castwide.solargraph>

I was previously using the Ruby extension from Peng Lv but unfortunately the key thing I needed, rubocop scanning just never seemed to work properly. Finally after doing some digging it looked like it just wouldn't ever play nice when using something like rbenv and bundler. However in one of the comments someone mentioned [Solargraph](https://github.com/castwide/solargraph) and that seemed to do the trick.

#### Setup

Before adding the extension run the following commands

```bash
gem install solargraph
```

Back in VSCode open the settings for Solargraph and set Diagnostics to `true`. This will enable rubocop. Then restart VSCode and all should be good.

### Ruby Test Explorer

Run your Ruby tests in the Sidebar of Visual Studio Code

<https://marketplace.visualstudio.com/items?itemName=connorshea.vscode-ruby-test-adapter>

Didn't spot to begin with, but it will add a new icon in the sidebar that looks like a flask. You can then interact with the test runner from there.

### Settings Sync

Synchronize Settings, Snippets, Themes, File Icons, Launch, Keybindings, Workspaces and Extensions Across Multiple Machines Using GitHub Gist.

<https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync>

## Setup

When first installed it will need a GitHub token that has permissions to manage Gists. On first install it will create the Gist for you. If setting up a new machine it will want the existing Gist ID.

- Sync: Auto Download = true
- Sync: Auto Upload = true
- Sync: Quiet Sync = true

The extension will handle everything on VSCode for you, but can also be used to sync over files. I have added the following custom entries so they can be synced across my machines by the tool.

- ~/.gemrc
- ~/.rspec
- ~/.vimrc
- ~/.zshrc

### Simple Ruby ERB

Provides simple Ruby and ERB language, code snippets and ERB tag helper support for Visual Studio Code without messing with linting or debugging

<https://marketplace.visualstudio.com/items?itemName=vortizhe.simple-ruby-erb>

### SQLTools

Database management done right. Connection explorer, query runner, intellisense, bookmarks, query history. (Mainly got for the SQL intellisense)

<https://marketplace.visualstudio.com/items?itemName=mtxr.sqltools>

### StandardJS - JavaScript Standard Style

Integrates JavaScript Standard Style into VS Code.

<https://marketplace.visualstudio.com/items?itemName=chenxsan.vscode-standardjs>

### Systemd Support

Systemd unit file syntax, autocompletion for Visual Studio Code.

<https://marketplace.visualstudio.com/items?itemName=hangxingliu.vscode-systemd-support>

### Trailing Spaces

Highlight trailing spaces and delete them in a flash!

<https://marketplace.visualstudio.com/items?itemName=shardulm94.trailing-spaces>

### vscode-pdf

Display pdf in VSCode.

<https://marketplace.visualstudio.com/items?itemName=tomoki1207.pdf>

### XML tools

XML Formatting, XQuery, and XPath Tools for Visual Studio Code.

<https://marketplace.visualstudio.com/items?itemName=DotJoshJohnson.xml>
