## Lv n - Update a Rails app

### List outdated gems

Run `bundle outdated --strict --only-explicit` to find out which gems are outdated in your app. The `--strict` option lists only the newer versions allowed by your Gemfile requirements and the `--only-explicit` option lists only gems specified in your Gemfile, not their dependencies. 

The result is a table like the following:

````
Gem          Current  Latest  Requested  Groups
haml         5.2.2    6.0.5   >= 0       default
i18n-js      3.9.2    4.0.1   >= 0       default
sorcery      0.16.3   0.16.4  >= 0       default
twilio-ruby  5.72.0   5.72.1  >= 0       default
````

### Update gems

Before updating a gem, check for possible breaking changes and how to fix them (more often on major version updates). 

You can use the `bundle update` command to update gem by gem:

`$ bundle update twilio-ruby`

### Bundler

Do not forget to keep **bundler** updated too.

`$ gem install bundler -v 2.3.20`

### Test updated app

Make sure updates don't break your app:

`$ bundle exec rspec`
