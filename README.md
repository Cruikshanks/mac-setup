# Mac setup

This repo simply serves as repository for how I setup various things on a Mac, in case of the time when I either change it or it blows up!

General and base stuff will go here. App or tool specific stuff will have their own files.

- [Git](git.md)
- [GPG](gpg.md)
- [iTerm2](iterm2.md)
- [NVM](nvm.md)
- [Oh my zsh](ohmyzsh.md)
- [OpenVPN](openvpn.md)
- [Pyenv](pyenv.md)
- [Rbenv](rbenv.md)
- [S3cmd tools](s3cmdtools.md)
- [SSH](ssh.md)
- [Terminal](terminal.md)
- [Vim](vim.md)
- [VSCode](vscode.md)

## System Settings

Changes I make to the Mac in settings to get it how I like it.

### Sound

- Untick `Play sound on startup`

### General > Software Update > Automatic updates

- Tick `Install application updates from the App store`

### General > AirDrop & Handoff

- Change `AirDrop` to `Everyone`

### Appearance

- Set `Appearance` to `Dark`
- Set `Show scroll bars` to `Always`
- Set `Click in the scroll bar to` to `Jump to the spot that's clicked`

### Siri & Spotlight

- Untick `Ask Siri`

### Desktop & Dock

- Set `Position on screen` to `Left`

### Desktop & Dock > Mission Control

- Untick `Automatically rearrange Spaces based on most recent use`. This will stop my full screen apps from moving position.
- Untick `Group windows by application`. Should be able to more easily move between the windows of an app.

### Displays > Night shift

- Set `Schedule` to `Sunset to Sunrise`

### Wallpaper

- Use black color

### Battery

- Set `Low Power Mode` to `Never`

### Keyboard

- Set `Turn backlight keyboard off after inactivity` to `After 5 minutes`

### Trackpad

- Untick `Force Click and haptic feedback`
- Untick `Look up & data detectors`

## Base installations

Core stuff I install which also supports getting other things loaded and/or setup. To save time when doing these all in one go you can skip the `brew update` that happens with each `brew install`.

Just call `export HOMEBREW_NO_AUTO_UPDATE=1` in the terminal session you are using to run all your installs.

- [Homebrew](https://brew.sh/) `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`
- [Avast antivirus](https://www.avast.com/en-gb/index#mac) `brew install --cask avast-security`
- [Google Chrome](https://www.google.com/chrome/index.html) `brew install --cask google-chrome`
- [DBeaver](https://dbeaver.io/) `brew install --cask dbeaver-community`
- [Docker Desktop](https://www.docker.com/products/docker-desktop/) `brew install --cask docker`
- [Slack](https://slack.com/downloads/osx) `brew install --cask slack`
- [InTune](https://learn.microsoft.com/en-us/mem/intune/user-help/enroll-your-device-in-intune-macos-cp) `brew install --cask intune-company-portal`
- [Trailer](https://github.com/ptsochantaris/trailer) `brew install --cask trailer`
- [Postman](https://www.postman.com/) `brew install --cask postman`
- [Keka](https://www.keka.io/en/) `brew install --cask keka`
- [Tokei](https://github.com/XAMPPRocky/tokei/) `brew install tokei`
- [The Silver searcher (ag)](https://github.com/ggreer/the_silver_searcher) `brew install the_silver_searcher`
- [Licecap](https://www.cockos.com/licecap/) `brew install --cask licecap`
- [Stats](https://github.com/exelban/stats) `brew install --cask stats`
- [Jitsi](https://jitsi.org/) `brew install --cask jitsi-meet`

## Contributing

If you think I'm doing something wrong or have a better way create an issue or better yet raise a pull request and show me.

## License

This information is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

> If you don't add a license it's neither free or open!
