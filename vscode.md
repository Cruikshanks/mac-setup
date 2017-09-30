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

- Change the tab size from 4 to 2 `"editor.tabSize": 2`
- Turn on word wrap `"editor.wordWrap": "on"`
- Add rulers `"editor.rulers": [80, 120]`
- Add a new line at the end of file upon save `"files.insertFinalNewline": true`
- Remove minimap from window `"editor.minimap.enabled": false`

## Keyboard shortcuts

Add the following keyboard shortcuts via `Preferences -> Keyboard shortcuts`

- `workbench.action.terminal.focusNext` = shift+cmd+->
- `workbench.action.terminal.focusPrevious` = shift+cmd+<-
- `workbench.action.terminal.kill` = cmd+k

