<h1>Action Mailer in Devise Authentication</h1>

<a name="readme-top"></a>

<!-- TABLE OF CONTENTS -->

# 📗 Table of Contents

- [📖 About the Project](#about-project)
  - [🛠 Built With](#built-with)
    - [Tech Stack](#tech-stack)
    - [Key Features](#key-features)
- [💻 Getting Started](#getting-started)
  - [Setup](#setup)
  - [Prerequisites](#prerequisites)
  - [Install](#install)
  - [Test](#run-test)
- [👥 Authors](#authors)
- [🔭 Future Features](#future-features)
- [🤝 Contributing](#contributing)
- [⭐️ Show your support](#support)
- [🙏 Acknowledgements](#acknowledgements)
- [📝 License](#license)

<!-- PROJECT DESCRIPTION -->

# 📖 Action Mailer in Devise Auth<a name="about-project"></a>

This project is all about authentication using devise and using action mailer to send outbond emails from your Rails application eg, forgot password, email confirmation

## 🛠 Built With <a name="built-with"></a>

### Tech Stack <a name="tech-stack"></a>

- <a href="https://rubyonrails.org/">Ruby on Rails</a>

<!-- Features -->

### Key Features <a name="key-features"></a>

Key features of the application.

- Devise installation
- Creating a devise User
- Adding action mailer in development.rb file
- Generating app name and password
- Encrypting email and password in Rails application credential
- Accessing the email and password in the mailer configuration

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->

## 💻 Getting Started <a name="getting-started"></a>

To get a local copy up and running, follow these steps.

### Prerequisites

To run this project you need:
- Code Editor.
- Ruby On Rails.

### Setup

Clone this repository to your desired folder:

I am using Ruby -v 3.3.4 and Rails -v 7.2.1 

```sh
  cd my-folder
  gh repo clone https://github.com/fatmahussein/rails-auth-skeleton.git
```

### Install
In your gmail account -> manage account -> security -> search 'app password', create an app name, and copy the generated password, you will use it.

### Setting up devise authentication
 Add `gem 'devise', '~> 4.9.2'` 
 
 bundle install

 Run the following code:
 
  `$ rails generate devise:install`, follow instructions provided
  
  `$ rails generate devise User`
  
  uncomment
  ```
      t.string   :confirmation_token`
      t.datetime :confirmed_at
      t.datetime :confirmation_sent_at
      t.string   :unconfirmed_email
 ```
 in the devise_create_user migration file
       
Add 
    `:confirmable`
    to the User model  
    
  `$ rails db:migrate`
<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Adding action mailer to development.rb
In your development.rb file, add the following settings:
```
config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
  address:         'smtp.gmail.com',
  port:            587,
  domain:          'example.com',
  user_name:       'your email',
  password:        'your password',
  authentication:  'plain',
  enable_starttls: true,
  open_timeout:    5,
  read_timeout:    5 }
```
Your Rails application should now be able to send outbound emails.

### Securing your email and password
Run
`$env:EDITOR="code --wait"; rails credentials:edit`
in your code editor, an editor will pop up.

Add 
```
email:
  username: 'your email'
  password: 'your password'
```
to the editor and save.
We will use
`Rails.application.credentials.email[:username]`
to access the encrypted data.

Your action mailer config should now look like this:

```
  config.action_mailer.delivery_method = :smtp
  config.action_mailer.smtp_settings = {
  address:         'smtp.gmail.com',
  port:            587,
  domain:          'example.com',
  user_name:       Rails.application.credentials.email[:username],
  password:        Rails.application.credentials.email[:password],
  authentication:  'plain',
  enable_starttls: true,
  open_timeout:    5,
  read_timeout:    5 }
```

Your data is now encrypted and rails is sending emails successfully :)

Finally, in case it's still not working,

run
`Rails.application.credentials.email[:username]`
in your rails console to confirm if it's displaying `Nil` or your email address.

All the best.

<!-- AUTHORS -->

## 👥 Author <a name="authors"></a>

👤 Fatuma Hussein
- GitHub: [&nbsp; &nbsp; @githubhandle](https://github.com/fatmahussein)

<!-- FUTURE FEATURES -->

## 🔭 Future Features <a name="future-features"></a>

- **Skeleton to kickstart any RoR project**

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CONTRIBUTING -->

## 🤝 Contributing <a name="contributing"></a>

Contributions, issues, and feature requests are welcome!
Feel free to check the <a href="https://github.com/fatmahussein/rails-auth-skeleton/issues">Issues</a>.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- SUPPORT -->

## ⭐️ Show your support <a name="support"></a>

If you like this project, show your support by giving the project a ⭐️.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ACKNOWLEDGEMENTS -->

## 🙏 Acknowledgments <a name="acknowledgements"></a>

I would like to thank Microverse.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->

## 📝 License <a name="license"></a>

This project is [MIT](./LICENSE) licensed.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

* ...
