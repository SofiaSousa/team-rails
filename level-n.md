## Lv n - Update a Rails app

### Updating

#### List outdated gems

Run `bundle outdated --strict --only-explicit` to find out which gems are outdated in your app. The `--strict` option lists only the newer versions allowed by your Gemfile requirements and the `--only-explicit` option lists only gems specified in your Gemfile, not their dependencies. 

The result is a table like the following:

````
Gem          Current  Latest  Requested  Groups
haml         5.2.2    6.0.5   >= 0       default
i18n-js      3.9.2    4.0.1   >= 0       default
sorcery      0.16.3   0.16.4  >= 0       default
twilio-ruby  5.72.0   5.72.1  >= 0       default
````

#### Update gems

Before updating a gem, check for possible breaking changes and how to fix them (more often on major version updates). 

You can use the `bundle update` command to update gem by gem:

`$ bundle update twilio-ruby`

#### Bundler

Do not forget to keep **bundler** updated too.

`$ gem install bundler -v 2.3.20`

And update hte `Gemfile.lock`:

`$ bundle update --bundler`

#### Test updated app

Make sure updates don't break your app:

`$ bundle exec rspec`

### Deploying 🚀

#### Backups 📦

Before deploying, it's a good practice to keep a backup of the database (and of the uploads folder if relevant).

If your app has a MySQL database, you can use the `mysqldump` command, but if you app has a PG database, you might wanna use the `pg_dump` command

````
$ mysqldump database -u root -p > dump`date +%d-%m-%Y"_"%H_%M_%S`.sql

$ pg_dump -U root database > dump`date +%d-%m-%Y"_"%H_%M_%S`.sql
````

#### Passenger and Apache (optional)

If `passenger` gem was updated, probably you'll have to update it manually on the server `$ gem install passenger` and re-install the Apache module `$ passenger-install-apache2-module`.

Now it's a good time to run the deploy script (`bundle exec cap production deploy`). Remember the app could be down after this step because of the current passenger config on the server is not updated. 

You'll have to update passenger config file too (ex: `/etc/httpd/conf.modules.d/10-passenger.conf` with `root` user and `sudo su -` mode):

````
LoadModule passenger_module /home/deploy/.rbenv/versions/3.1.2/lib/ruby/gems/3.1.0/gems/passenger-6.0.14/buildout/apache2/mod_passenger.so
<IfModule mod_passenger.c>
  PassengerRoot /home/deploy/.rbenv/versions/3.1.2/lib/ruby/gems/3.1.0/gems/passenger-6.0.14
  PassengerDefaultRuby /home/deploy/.rbenv/versions/3.1.2/bin/ruby
  PassengerRuby /home/deploy/.rbenv/shims/ruby
</IfModule>
````

Pay atention to the `ruby` version and on the `passenger` version.

Finally, restart Apache (with `root` user and `sudo su -` mode):

`$ sudo service httpd restart`

And the app should be up again.

#### Deploy with Capistrano

If you didn't run the deploy script yet, run the `bundle exec cap production deploy` command from your local machine to start the deploy script.
