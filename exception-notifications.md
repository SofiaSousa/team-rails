## Lvl X - Exception Notification

It's very important to be aware and get noticed when an error or an exception occurs in our Rails apps. 

The [Exception Notification](https://github.com/smartinez87/exception_notification) gem provides a set of notifiers for sending notifications via **email**, **Slack**, **custom WebHooks** and [others](https://github.com/smartinez87/exception_notification#notifiers).

[image]

It's quite simple to setup **Exception notificattions**. Start by adding the gem to Gemfile:

```ruby
gem 'exception_notification'
```

And  installing with Bundler:

```bash
$ bundle install
```

### Email notifications

Add the following configuration to `config/environments/production.rb`, for production env:

```ruby
Rails.application.config.middleware.use ExceptionNotification::Rack,
  email: {
    email_prefix: '[PROD] ',
    sender_address: %{"notifier" <notifier@example.com>},
    exception_recipients: %w{sofia@frontkom.com}
  }
```

### Slack notifications



For more details about the configuration, check [Exception Notification Docs](https://github.com/smartinez87/exception_notification/blob/master/README.md)
