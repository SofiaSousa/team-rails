## Deploying with Capistrano

[intro + capistrano files structure] with rbenv and passenger

Add **capistrano**, **capistrano-rails** and **capistrano-rbenv** gems to `Gemfile`:

```ruby
group :development do
  gem "capistrano", require: false
  gem "capistrano-rails", require: false
  gem 'capistrano-rbenv'
  gem 'capistrano-passenger'
end
```

Install them using Bundler:

```
$ bundle install
```

And run the generator to create the basic set of configuration files:

```
$ bundle exec cap install

mkdir -p config/deploy
create config/deploy.rb
create config/deploy/staging.rb
create config/deploy/production.rb
mkdir -p lib/capistrano/tasks
create Capfile
Capified
```

---
Capistrano tasks

Capistrano gems you installed provide a set of tasks that help you on the deployment process. Use the following commad to see the Capistrano list of tasks:

```
$ bundle exec cap -T
```

---

In `Capfile`, you will have to require the sets you need. For example:

```ruby
# Capfile
require "capistrano/rbenv"
require 'capistrano/bundler' # Rails needs Bundler, right?
require 'capistrano/rails/assets'
require 'capistrano/rails/migrations'
require 'capistrano/passenger'
```

Go to `config/deploy.rb` and add general settings for the deployment.

```ruby
set :application, "my_app_name"
set :repo_url, "git@example.com:me/my_repo.git"

# Default value for :linked_files is []
append :linked_files, "config/database.yml"

# Default value for linked_dirs is []
append :linked_dirs, "log", "tmp/pids", "tmp/cache", "tmp/sockets", "public/system"

set :rbenv_type, :user # or :system, or :fullstaq (for Fullstaq Ruby), depends on your rbenv setup
set :rbenv_ruby, '2.4.2'
# in case you want to set ruby version from the file:
# set :rbenv_ruby, File.read('.ruby-version').strip
```

Then, go to `config/deploy/production.rb` to define production settings.

```ruby
set :rails_env, :production
set :stage, :production

set :branch, :master

set :deploy_user, 'username'

set :full_app_name, "#{fetch(:deploy_user)}_#{fetch(:stage)}"

set :tmp_dir, "/tmp/#{fetch(:deploy_user)}"
set :deploy_to, "/home/#{fetch(:deploy_user)}/apps/#{fetch(:full_app_name)}"

# rbenv
set :rbenv_custom_path, "/home/#{fetch(:deploy_user)}/.rbenv"
set :rbenv_prefix, "RBENV_ROOT=#{fetch(:rbenv_path)} RBENV_VERSION=#{fetch(:rbenv_ruby)} #{fetch(:rbenv_path)}/bin/rbenv exec"
set :rbenv_map_bins, %w{rake gem bundle ruby rails}
set :rbenv_roles, :all
```

Check the setup with `deploy:check` task:

```
$ bundle exec cap production deploy:check 
```

If you get a message like "WARN  rbenv: 2.6.3 is not installed or not found ...", go to the app folder in the server and install the ruby required version using rbenv:

```
$ rbenv install 2.6.3
```

If it passes on the `deploy:check` task, you are ready to deploy!

```
$ bundle exec cap production deploy 
```
