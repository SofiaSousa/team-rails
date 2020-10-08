## Level 0 - Get on Rails!

**Rails** or [Ruby on Rails](https://github.com/rails/rails) is a framework built in [Ruby language](https://www.ruby-lang.org/) and designed to create web apps. 

![Rails logo](https://rubyonrails.org/images/rails-logo.svg)

### Ruby and Gems

In Ruby world, the libraries or modules that we can install and use when building our web apps are called **gems**. For example, **Rails** is in fact a Ruby gem.

There is a public hosting service where we can search for available gems, the [RubyGems.org](https://rubygems.org). To install a gem we can use the [gem command](https://guides.rubygems.org/rubygems-basics/), but first make sure Ruby is installed.

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

they used to be listed on our project **Gemfile**. 

We use [Bundler](https://bundler.io/) to manage our applications' gems.

```bash
bundle install
```
### The Rails Doctrine

Getting back to Rails, these are the most important pillars of [The Rails Doctrine](https://rubyonrails.org/doctrine/):

1. [Optimize for programmer happiness](https://rubyonrails.org/doctrine/#optimize-for-programmer-happiness)
1. [Convention over Configuration](https://rubyonrails.org/doctrine/#convention-over-configuration)
1. [The menu is omakase](https://rubyonrails.org/doctrine/#omakase)
1. [No one paradigm](https://rubyonrails.org/doctrine/#no-one-paradigm)
1. [Exalt beautiful code](https://rubyonrails.org/doctrine/#beautiful-code)
1. [Provide sharp knives](https://rubyonrails.org/doctrine/#provide-sharp-knives)
1. [Value integrated systems](https://rubyonrails.org/doctrine/#integrated-systems)
1. [Progress over stability](https://rubyonrails.org/doctrine/#progress-over-stability)
1. [Push up a big tent](https://rubyonrails.org/doctrine/#big-tent)

![Rails doctrine](https://rubyonrails.org/images/doctrine.png)


_At this point, we are able to understand the difference between Rails and Ruby, what are gems, the Gemfile and why we need the Bundler._
