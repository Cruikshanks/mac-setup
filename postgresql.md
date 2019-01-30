# Postgresql

To actually install Postgresql on a host machine I would just use homebrew. However as I normally connect to a postgresql instance running in a vagrant box I don't normally have it installed locally.

This can prove a problem for projects that include the [pg](https://bitbucket.org/ged/ruby-pg/wiki/Home) gem as it will fail to build without it. There is a workaround however.

## libpq

libpq is the C application programmer’s interface to PostgreSQL. libpq is a set of library functions that allow client programs to pass queries to the backend server and to receive the results of these queries.

```bash
brew install libpq
```

With that installed you can tell the **pg** gem to use it when installing.

```bash
gem install pg -v '0.18.4' -- --with-opt-dir="/usr/local/opt/libpq"
```

N.B. Obviously change the version to match what you are trying to install.

## Bundler config

You can also tell Bundler to use libpq every time you install the pg gem in a repo in future.

```bash
bundle config --local build.pg --with-opt-dir="/usr/local/opt/libpq"
bundle install
```

With this done, you should be able to execute or run tests in projects locally that would typically depend on an instance of Postgresql being installed.

## References

[How to install ruby pg gem without PostgreSQL locally](https://michaelrigart.be/install-pg-ruby-gem-without-postgresql/)
[Install pg gem without installing postgres macOS](https://stackoverflow.com/a/46784625)
