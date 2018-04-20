# iTerm2

[iTerm2](https://www.iterm2.com/) is a replacement for Terminal and the successor to iTerm. It has additional features over the default Terminal that comes with OSX, including the ability to easily split the screen.

## Install

```bash
brew cask install iterm2
```

## Configure

iTerm will pick up whatever I set in my `~/.bash_profile` in the same way as the [Terminal](terminal.md). So check that guide for **Bash completion** and **Bash Git prompt**.

Specific to iTerm you need to open preferences and then

- General - Untick *Adjust window when changing the font size*
- General - Tick *Quit when all windows are closed*

Finally in the iTerm2 menu click *Make iTerm2 Default Term*.

### Profiles

Much like [Terminal](terminal.md) I like to default to using [Solarized](http://ethanschoonover.com/solarized). In iTerm this is much simpler to implement however. Open profiles using either the menu or CMD+o, then click *Edit profiles*.

Click the + button at the bottom to add a new profile. Name it **Default (solarized dark)**, then make the following changes

- Colors - Select *Color Presets* and select **Solarized dark**
- Colors - Click *Selection* and then set the color to **Snow** (there is an icon that looks like a document in the centre of the initial color selection screen which if clicked will display another color screen from which you can select **Snow**)
- Text - Click *Change Font* and set size to 14

Finally with it selected select *Set as default* from the *Other Actions...* menu.

Repeat the process again, adding a new profile only this time call it **Solarized light**, and selecting **Solarized light** as the color preset.
