# Jenv

[Jenv](http://www.jenv.be/) is a command line tool to help you manage running multiple Java versions in the same environment.

Unlike other version managers however, it doesn't install **Java**, it simply sets the `JAVA_HOME` variable for you. So the first step is to install the versions of Java you want.

## Install Java

Java 8 is currently used by some of the projects I work on so I need to have it installed locally when working with the source code. Previously I'd have just downloaded the Oracle JDK via brew but due to a number of changes in the Java eco-system this is no longer possible. Basically

- Oracle changed the licensing for historic versions, so you now need to [pay a fee](https://java.com/en/download/release_notice.jsp) to use them. Hence homebrew has pulled previous versions
- The release cadence has dramatically sped up from every x years to every 6 months so you have to be able to specify a version

It's all got insanely complex, so if I need a reminder of what's going on refer to this [great stackoverflow answer](https://stackoverflow.com/a/52431765). Simplified, I now need to use Open JDK binaries compiled by someone who is not Oracle. [AdoptOpenJDK](https://github.com/AdoptOpenJDK) is the group that now provides these, and they have a homebrew formulae we can use.

```bash
brew tap AdoptOpenJDK/openjdk
brew cask install adoptopenjdk8
```

See <https://github.com/AdoptOpenJDK/homebrew-openjdk> for more details and what versions are available for install.

## Install

```bash
brew install jenv
```

The output will tell you to add something like `eval "$(jenv init -)"` to your bash profile. This is used to load jenv in your session. As the default shell in OSX is Catalina, I'm using [Oh my zsh](ohmyzsh.md) to manage plugins for it. One plugin is [jenv](https://github.com/robbyrussell/oh-my-zsh/tree/master/plugins/jenv) and it will handle this for you.

Just add the following to your `~/.zshrc` file

```bash
plugins=(... jenv)
```

## Config

Having installed your version of Java, you now need to add it's location to **jenv**.

```bash
jenv add /Library/Java/JavaVirtualMachines/adoptopenjdk-8.jdk/Contents/Home
```

Confirm the versions **jenv** has by running `jenv versions`. You may find a single Java install will generate multiple results from **jenv**.

## Use

In the root of your Java project run `jenv local [version]` with *version* obviously being one of the versions known to **jenv**. It will generate a `.java-version` which will set the version of Java used automatically in the future.
