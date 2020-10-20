## Lv 0 - Get on Rails!

**Rails** or [Ruby on Rails](https://github.com/rails/rails) is a developer-friendly framework built in [Ruby language](https://www.ruby-lang.org/) and designed to create web apps. 

![Rails logo](https://cdn.freebiesupply.com/logos/thumbs/1x/rails-1-logo.png)

_"Optimizing for programmer happiness with Convention over Configuration is how we roll. "_

### The Rails Doctrine

These are the most important pillars of [The Rails Doctrine](https://rubyonrails.org/doctrine/):

1. [Optimize for programmer happiness](https://rubyonrails.org/doctrine/#optimize-for-programmer-happiness)
1. [Convention over Configuration](https://rubyonrails.org/doctrine/#convention-over-configuration)
1. [The menu is omakase](https://rubyonrails.org/doctrine/#omakase)
1. [No one paradigm](https://rubyonrails.org/doctrine/#no-one-paradigm)
1. [Exalt beautiful code](https://rubyonrails.org/doctrine/#beautiful-code)
1. [Provide sharp knives](https://rubyonrails.org/doctrine/#provide-sharp-knives)
1. [Value integrated systems](https://rubyonrails.org/doctrine/#integrated-systems)
1. [Progress over stability](https://rubyonrails.org/doctrine/#progress-over-stability)
1. [Push up a big tent](https://rubyonrails.org/doctrine/#big-tent)

### Ruby and Gems

In Ruby world, libraries or modules used when building our web apps are called **gems**. For example, **Rails** is in fact a Ruby gem.

![Ruby logo](https://image.pngaaa.com/152/769152-small.png)

There is a public hosting service where we can search for available gems, the [RubyGems.org](https://rubygems.org). To install a gem globaly, we can use the [gem command](https://guides.rubygems.org/rubygems-basics/), but first make sure Ruby is installed, since RubyGems comes built-in with Ruby 1.9 and newer.

```
$ ruby -v
ruby 2.6.3p62 (2019-04-16 revision 67580) [universal.x86_64-darwin19]
```

```
$ gem install sass

Ruby Sass has reached end-of-life and should no longer be used.

* If you use Sass as a command-line tool, we recommend using Dart Sass, the new
  primary implementation: https://sass-lang.com/install

* If you use Sass as a plug-in for a Ruby web framework, we recommend using the
  sassc gem: https://github.com/sass/sassc-ruby#readme

* For more details, please refer to the Sass blog:
  https://sass-lang.com/blog/posts/7828841

Successfully installed sass-3.7.4
Parsing documentation for sass-3.7.4
Installing ri documentation for sass-3.7.4
Done installing documentation for sass after 2 seconds
1 gem installed
```

The set of gems that a Ruby project requires used to be listed on the `Gemfile`. 

```ruby
source "https://rubygems.org"

# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem "rails", "~> 5.1.2"
# Use Puma as the app server
gem "puma", "~> 3.7"
# Use SCSS for stylesheets
gem "sass-rails", "~> 5.0"
# Build JSON APIs with ease. Read more: https://github.com/rails/jbuilder
gem "jbuilder", "~> 2.5"
```

### Bundler

We use [Bundler](https://bundler.io/) (which is also a gem) to manage our applications' gems. 

```
$ gem install bundler
```

To install gems from the `Gemfile` we can use the following command:

```
$ bundle install
```

### rbenv

Since it's very common to have different Rails apps running with different versions of Ruby, we need to have different Ruby versions installed in our machines. We can use [rbenv](https://github.com/rbenv/rbenv) to create an individual environment for each Rails app:

```
$ rbenv local 2.5.0
```

This command will install version 2.5.0 and create a `.ruby-version` file in the current directory with the Ruby version name. The local version set will override the global Ruby version in the current directory and subdirectories (we can confirm this by running `ruby -v` in the current dir, subdirs and parent dir). Ruby versions installed by rbenv are under `~/.rbenv/versions/` dir.

Now when we run `bundler install`, our gems from the `Gemfile` will be installed in `~/.rbenv/versions/<ruby-version>/lib/ruby/gems/...`. That means now we can have the same gem installed for different versions of Ruby.

#### rbenv-gemset

And if different Rails apps running in the same Ruby version, depend of the same gem but in different versions? We can create gemsets for each app with [rbenv-gemset](https://github.com/jf/rbenv-gemset), which is an extension for the rbenv.

```
$ rbenv gemset init [gemsetname]
```

This command will set up the default gem set for our project under the current ruby version and create a `.rbenv-gemsets` file in the current directory with the gem set name (which can be the app name for example).

Our app gems will be installed in `~/.rbenv/versions/<ruby-version>/gemsets/[gemsetname]/gems/...`.

Keep `.ruby-version` and `.rbenv-gemsets` files in the app Git repo.

---

_At this point, we are able to understand the difference between Ruby and Rails, what are gems, the Gemfile and why we need the Bundler and rbenv._

---

[Go to Lv 1 - Hello Rails](./level-1.md)
