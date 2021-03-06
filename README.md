# Mac setup

This repo simply serves as repository for how I setup various things on a Mac, in case of the time when I either change it or it blows up!

General and base stuff will go here. App or tool specific stuff will have their own files.

- [Gemrc](gemrc.md)
- [Git](git.md)
- [GPG](gpg.md)
- [iTerm2](iterm2.md)
- [Jenv](jenv.md)
- [NVM](nvm.md)
- [Oh my zsh](ohmyzsh.md)
- [OpenVPN](openvpn.md)
- [PostgreSQL](postgresql.md)
- [Rbenv](rbenv.md)
- [S3cmd tools](s3cmdtools.md)
- [SSH](ssh.md)
- [Terminal](terminal.md)
- [Vim](vim.md)
- [VSCode](vscode.md)

## General

Changes I make to the Mac in settings to get it how I like it.

### System Preferences > Mission Control

- Untick `Automatically rearrange Spaces based on most recent use`. This will stop my full screen apps from moving position.
- Untick `Group windows by application`. Should be able to more easily move between the windows of an app.

### System Preferences > Energy Saver

- Power adapter > Untick `Put hard disks to sleep when possible` and `Wake up for Wi-Fi network access`

### System Preferences > General

- Select `Dark` appearance
- Click in the scroll bar to `Jump to the spot that's clicked`

## Base installations

Core stuff I install which also supports getting other things loaded and/or setup. To save time when doing these all in one go you can skip the `brew update` that happens with each `brew install`.

Just call `export HOMEBREW_NO_AUTO_UPDATE=1` in the terminal session you are using to run all your installs.

- [Homebrew](https://brew.sh/) `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
- [Avira antivirus](https://www.avira.com/) `brew cask install avira-antivirus`
- [Google Chrome](https://www.google.com/chrome/index.html) `brew cask install google-chrome`
- [Firefox](https://www.mozilla.org/en-GB/firefox/new/) `brew cask install firefox`
- [Evernote](https://evernote.com/) `brew cask install evernote`
- [VirtualBox](https://www.virtualbox.org/) `brew cask install virtualbox`
  - [VirtualBox extension pack](https://www.virtualbox.org/wiki/Downloads) `brew cask install virtualbox-extension-pack`
- [Vagrant](https://www.vagrantup.com/) `brew cask install vagrant`
- [Gimp](https://www.gimp.org/) `brew cask install gimp`
- [pgAdmin4](https://www.pgadmin.org/) `brew cask install pgadmin4`
- [Docker Community Edition for Mac](https://store.docker.com/editions/community/docker-ce-desktop-mac) *go to the site and download manually*
- [Slack](https://slack.com/downloads/osx) *go to the site and download manually*
- [Trailer](https://github.com/ptsochantaris/trailer) `brew cask install trailer`
- [Robo 3T](https://robomongo.org/) `brew cask install robo-3t`
- [Cheat](https://github.com/chrisallenlane/cheat) `brew install cheat`
- [tldr](https://github.com/tldr-pages/tldr) `brew install tldr`
- [Keka](https://www.keka.io/en/) `brew cask install keka`
- [Tokei](https://github.com/XAMPPRocky/tokei/) `brew install tokei`
- [IntelliJ IDEA CE](https://www.jetbrains.com/idea/) `brew cask install intellij-idea-ce`

## Contributing

If you think I'm doing something wrong or have a better way create an issue or better yet raise a pull request and show me.

## License

This information is available as open source under the terms of the [MIT License](http://opensource.org/licenses/MIT).

> If you don't add a license it's neither free or open!
