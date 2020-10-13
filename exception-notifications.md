## Lvl X - Exception Notification :warning:

It's very important to be aware and get noticed when an error or an exception occurs in our Rails apps. 

The [Exception Notification](https://github.com/smartinez87/exception_notification) gem provides a set of notifiers for sending notifications via **email**, **Slack**, **custom WebHooks** and [others](https://github.com/smartinez87/exception_notification#notifiers).

[image]

It's quite simple to setup **Exception notificattions**. Start by adding the gem to Gemfile:

```ruby
gem 'exception_notification'
```

Then you can choose what kind of notifications you want to get.

### Email notifications :email:

Add the following configuration to `config/environments/production.rb`, for production env:

```ruby
Rails.application.config.middleware.use ExceptionNotification::Rack,
  email: {
    email_prefix: '[PROD] ',
    sender_address: %{"notifier" <notifier@example.com>},
    exception_recipients: %w{sofia@frontkom.com}
  }
```

### Slack notifications :computer:

For Slack notifications slack-notifier gem is also required. Add the gem to Gemfile:

```ruby
gem 'slack-notifier'
```

And to configure it, you need to set at least the `webhook_url` option, like this:

```ruby
Rails.application.config.middleware.use ExceptionNotification::Rack,
  slack: {
    webhook_url: '[Your webhook url]',
    channel: '#proj-name-status',
  }
```

---

For more details about the configuration, check [Exception Notification Docs](https://github.com/smartinez87/exception_notification/blob/master/README.md)
