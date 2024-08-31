# README

This project is all about authentication using devise and using action mailer to send outbond emails from your Rails application eg, forgot password, email confirmation

* Ruby version
I am using Ruby -v 3.3.4 and Rails -v 7.2.1 

* Setting up devise authentication
  Add `gem 'devise', '~> 4.9.2'` then bundle install
  `$ rails generate devise:install`, follow instructions provided
  `$ rails generate devise User`
  uncomment
   `  t.string   :confirmation_token`
      ` t.datetime :confirmed_at`
       `t.datetime :confirmation_sent_at`
       `t.string   :unconfirmed_email` in the devise_create_user migration file
    Add `:confirmable` to the User model  
  `$ rails db:migrate`

* Configuration
In your gmail account -> manage account -> security -> search 'app password', create an app name, and copy the generated password, you will use it.

* Adding action mailer to development.rb

Add 
```config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
  address:         'smtp.gmail.com',
  port:            587,
  domain:          'example.com',
  user_name:       Rails.application.credentials.email[:username],
  password:        Rails.application.credentials.email[:password],
  authentication:  'plain',
  enable_starttls: true,
  open_timeout:    5,
  read_timeout:    5 }```

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
