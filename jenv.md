# Jenv

[Jenv](http://www.jenv.be/) is a command line tool to help you manage running multiple Java versions in the same environment.

Unlike other version managers however, it doesn't install **Java**, it simply sets the `JAVA_HOME` variable for you. So the first step is to install the versions of Java you want.

This is essentially following <http://davidcai.github.io/blog/posts/install-multiple-jdk-on-mac/>. Also checkout <https://stackoverflow.com/a/29195815>.

## Install Java's

```bash
brew cask install java6

# At time of writing this will install Version 8 of the Oracle JDK
brew cask install java
```

For reference Java 7 was moved behind a login hence its no longer available as a 'cask' <https://github.com/caskroom/homebrew-versions/pull/3914>. If you need it you have to install it manually.

## Install

```bash
brew install jenv
```

Then adding the following to `~/.bash_profile`

```bash
# Init jenv (multiple jdk install management)
if which jenv > /dev/null; then
  export PATH="$HOME/.jenv/bin:$PATH"
fi
if which jenv > /dev/null; then
  eval "$(jenv init -)"
fi
```

## Config

Having installed your versions of Java, you now need to add their locations to **jenv**.

```bash
jenv add /Library/Java/JavaVirtualMachines/1.6.0.jdk/Contents/Home/
jenv add /Library/Java/JavaVirtualMachines/jdk1.8.0_131.jdk/Contents/Home/
```

Confirm the versions **jenv** has by running `jenv versions`. You may find a single Java install will generate multiple results from **jenv**.

Then set one as the global default `jenv global oracle64-1.8.0.131`.

## Use

In the root of your Java project run `jenv local [version]` with *version* obviously being one of the versions known to **jenv**. It will generate a `.java-version` which will set the version of Java used automatically in the future.

