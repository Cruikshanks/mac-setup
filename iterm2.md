# iTerm2

[iTerm2](https://www.iterm2.com/) is a replacement for Terminal and the successor to iTerm. It has additional features over the default Terminal that comes with OSX, including the ability to easily split the screen.

## Install

```bash
brew cask install iterm2
```

## Configure

Open preferences and then

- General - Untick *Adjust window when changing the font size*
- General - Tick *Quit when all windows are closed*
- Apperance/General - For status bar location select *Bottom*
- Apperance/Panes - Select *Separate status bars per pane*

Finally in the iTerm2 menu click *Make iTerm2 Default Term*.

### Profiles

I like to default to using the [Solarized dark](http://ethanschoonover.com/solarized) theme. Select 'Profiles'.

Click the + button at the bottom to add a new profile. Name it **Solarized dark**, then make the following changes

- Colors - Select *Color Presets* and select **Solarized dark**
- Text - Select *Droid Sans Mono for Powerline*
- Session - Tick *Status bar enabled* (see note below for how to configure it)

Finally with it selected select *Set as default* from the *Other Actions...* menu.

Repeat the process again, adding a new profile only this time call it **Solarized light**, and selecting **Solarized light** as the color preset (useful when working in poor light).

#### Status bar configuration

I like to configure my status bar to show

- current directory
- current branch
- date and time

Also click *Auto-Rainbow* to give them some colour.
