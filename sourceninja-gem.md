---
layout: page
title: sourceninja-ruby gem
---

Note
----
* This gem is currently alpha. __You need to be invited to [SourceNinja Alpha](http://www.sourceninja.com/sign-up.html) in order to use this gem__.
* If you are using Heroku, please refer to the [Heroku Documentation](heroku-addon) and please ignore this documentation.

What is SourceNinja
-------------------
SourceNinja is an awesome service that allows you to stay informed of updates to the open source packages that your application uses. When a newer version of a package is released, SourceNinja gives you actionable information to help you determine whether you should upgrade to the newer package.

Visit [SourceNinja](http://sourceninja.com) to learn more.

What is the sourceninja gem
------------------------
sourceninja is a gem that can be included in your rails application to allow seamless integration with SourceNinja. The sourceninja gem will send all of your gem files and versions to SourceNinja to begin managing your open source libraries.

Getting Started
---------------
First of all, you'll need the gem. It's at `http://github.com/SourceNinja/sourceninja-ruby`. If you're using Bundler, just add the following to your `Gemfile`.
    
	gem 'sourceninja', :git => 'https://github.com/SourceNinja/sourceninja-ruby'

Of course, as always, when you edit your Gemfile:
	bundle install

Before you can do anything with the sourceninja gem, you'll need to create your very own SourceNinja account (please read the notice above). Go ahead and do so at [http://sourceninja.com](http://sourceninja.com). Once created, you will need to create a product. This is the application you want SourceNinja to track. 

Once your create a product, you will be directed to a page asking what language your application is running. Select `Rails` from the menu on the left side. You will be presented with two keys that you will need for the rest of the installation.

You will then need to setup two environement variables in production, `ENV["SOURCENINJA_TOKEN"]` and `ENV["SOURCENINJA_PRODUCT_ID"]`. You could set these up in a configuration file that is only used in production, however, that is not suggested. You should setup the enviornement variables according to your hosting documentation.

Updated Magically in Production
-----------------
Now each time you push to production the sourceninja gem will be run and data will be populated back to SourceNinja. If you visit your SourceNinja page you will be given a list of outdated gems.

The sourceninja data is populated whenever the app is initilized.

Testing Locally
---------------
If you would like to test if SourceNinja is getting pushed your gems locally, you will want to create an initializer script to set the variables.

### Contents of `config/initializers/sourceninja.rb`
	ENV["SOURCENINJA_TOKEN"]      ||= "2cea0be98caf02e830ac2aadbe44e4ee"
	ENV["SOURCENINJA_PRODUCT_ID"] ||= "fb89e066-b48c-40c3-81b4-a34a5b60a654"

Upon doing this, each time you start the rails server locally the data will be pushed. If you want to have two SourceNinja apps, one for production and one for developement, this is a good way to do it.

Support
-------
Feel free to email us at support at sourceninja dot com if you have any questions or issues.

![sourceninja-ruby](assets/images/splinter.jpg)





### SourceNinja configuration script

Create a file for the configuration variables for the sourceninja gem. The examples use `/config/initializers/sourceninja.rb`

Contents of `config/initializers/sourceninja.rb`
    ENV["SOURCENINJA_TOKEN"]      ||= "07b86556dbac8cb5977ab304a5dad1ce"
    ENV["SOURCENINJA_PRODUCT_ID"] ||= "3a331b4f-5503-437f-829a-5c1a4715d3e7"

Deploy the SourceNinja configuration to Heroku:

    :::term
    $ git add config/initializers/sourceninja.rb
    $ git commit -a -m "Adding sourceninja config"
    $ git push heroku master
    …
    -----> Heroku receiving push
    -----> Launching... done, v3
           http://my-awesome-app.herokuapp.com deployed to Heroku

    To git@heroku.com:my-awesome-app.git
     * [new branch]      master -> master

Configuration of the add-on can be confirmed by running:

    :::term
    $ heroku run confirmation command
    
[[On Heroku, configuration is managed via configuration variables. Please update client libraries to follow this pattern. No configuration files with sensitive information should ever be required within the application source and required config values should be read in from the ENV by supported libraries.]]

Feature 1

[[Describe how to use/integrate feature 1 from Ruby on Rails]]

Feature 2

[[Describe how to use/integrate feature 2 from Ruby on Rails]]




