# Terminal

How I like to setup the default terminal on a Mac.

## Settings

Open the **Terminal** preferences then select `Shell` for the profile being used (I stick with 'Basic'). Then set

- When the shell exits: `Close if the shell exited cleanly`

## Configure

### Bash completion

Add support for bash completion e.g. when working with **Git** bash completion means having entered a few characters you can then hit tab to auto-complete commands and branch names.

```bash
brew install bash-completion
```

Original source for this was [Bash completion on OS X with Brew](http://davidalger.com/development/bash-completion-on-os-x-with-brew/). However its a little outdated now as you don't need to bother with the `brew tap homebrew/completions` step (they've been moved into core **Homebrew**).

Then add the following to `~/.bash_profile`

```text
# Add support for bash completions e.g. git
if [ -f $(brew --prefix)/etc/bash_completion ]; then
  . $(brew --prefix)/etc/bash_completion
fi
```

### Bash Git Prompt

Add IMHO a better prompt to the terminal using [Bash-git-prompt](https://github.com/magicmonty/bash-git-prompt). If I'm in a git repo its gives me an indication of the current state, plus when you hit return it displays the current path and the repo status on one line, but then drops you onto a fresh line with just `$` giving you more space for your command.

Install with `brew install bash-git-prompt` and then add the following to `~/.bash_profile`

```text
if [ -f "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh" ]; then
  __GIT_PROMPT_DIR=$(brew --prefix)/opt/bash-git-prompt/share
  source "$(brew --prefix)/opt/bash-git-prompt/share/gitprompt.sh"
fi
```

### Profiles

I default to using the [Solarized](http://ethanschoonover.com/solarized) profile for terminal, and like to have both the dark (my default) and the light available (the light for when working in bright light or with a dim screen). To achieve this download solarized from <http://ethanschoonover.com/solarized>, and then uncompress the zip file which comes down.

In the uncompressed files should be the folder `[where ever the zip has been uncompressed to]/solarized/osx-terminal.app-colors-solarized/xterm-256color`. In there will be 2 files

- `Solarized Dark xterm-256color.terminal`
- `Solarized Light xterm-256color.terminal`

Open **Terminal** and go to **Preferences->Profiles**. At the bottom should be a button that looks like a cog which if clicked will display a menu that includes the option **Import**. Click that and then simply `Solarized Dark xterm-256color.terminal` from the files found. The profile **Solarized Dark** will have been added. Select it and make the following changes

- Text - Untick *Use bright colors for bold text*
- Text - Click *Change...* button for Font and set size to 14
- Text - Click the color button next to *Selection* and then set colour to **Snow** (I have difficulty using the default selection color)
- Shell - Select **Close if shell exited cleanly** from *When the shell exits*

Repeat the process for **Solarized Light**.
