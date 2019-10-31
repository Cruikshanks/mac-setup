# .gemrc

The [.gemrc](http://guides.rubygems.org/command-reference/#gem-environment) is a handy way of declaring command line argument defaults and some [RubyGems](https://rubygems.org/) defaults, which are then used whenever you call the `gem` command.

Though it doesn't have the extension, it should be formatted as a YAML file.

## Install

From the terminal

```bash
touch ~/.gemrc
```

## Configure

Open the file and add the following

```yaml
# Automatically adds the args --no-ri --no-rdoc when calling
# gem install
gem: --no-document
```
