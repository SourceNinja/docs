---
layout: page
title: SourceNinja Heroku Add-On
---

[SourceNinja](http://addons.heroku.com/sourceninja) is an easy way to manage the open source software that your application uses. SourceNinja keeps you aware of updates to the open source software you use.

The key benefits of using SourceNinja are:

* To understand what packages need to be updated.
* To have actionable information to determine whether an update should take place.
* Be alerted to updates to the Open Source packages.

SourceNinja is accessible via an API and currently supports client libraries for Ruby.

## Installing the add-on
To install the SourceNinja add-on, simply run:

    :::term
    $ heroku addons:add sourceninja
    -----> Adding sourceninja to my-awesome-app... done, v18 (free)

After installing SourceNinja the application should be configured to fully integrate with the add-on.

## Using with Rails 3.x
SourceNinja supports rails through the installation of a gem. Once the application is setup, you will need to add the sourceninja gem to your gemfile. This gem pushes all of the gem names and versions to SourceNinja. 

Ruby on Rails applications will need to add the following entry into their `Gemfile` specifying the SourceNinja client library.

    :::ruby
    gem 'sourceninja-ruby', :git => 'https://github.com/SourceNinja/sourceninja-ruby'

Update application dependencies with bundler.

    :::term
    $ bundle install    
    Fetching https://github.com/SourceNinja/sourceninja-ruby
    remote: Counting objects: 30, done.
    remote: Compressing objects: 100% (20/20), done.
    remote: Total 30 (delta 4), reused 28 (delta 2)
    Unpacking objects: 100% (30/30), done.
    ...
    Your bundle is complete! Use `bundle show [gemname]` to see where a bundled gem is installed.
    $

### Development environment

The gem automatically disables the pushing of developement and testing data to SourceNinja. This way the data received about gems will only refer to production data. In doing this, SourceNinja always reflects what gems are used in production.

### Deploy changes

Deploy the SourceNinja configuration to Heroku:

    :::term
    $ git add config/sourceninja.rb
    $ git commit -a -m "Adding sourceninja config"
    $ git push heroku master
    …
    -----> Heroku receiving push
    -----> Launching... done, v3
           http://warm-frost-1289.herokuapp.com deployed to Heroku

    To git@heroku.com:warm-frost-1289.git
     * [new branch]      master -> master

Configuration of the add-on can be confirmed by running:

    :::term
    $ heroku run confirmation command

[[On Heroku, configuration is managed via configuration variables. Please update client libraries to follow this pattern. No configuration files with sensitive information should ever be required within the application source and required config values should be read in from the ENV by supported libraries.]]

### Feature 1

[[Describe how to use/integrate feature 1 from Ruby on Rails]]

### Feature 2

[[Describe how to use/integrate feature 2 from Ruby on Rails]]

## Monitoring & Logging

Stats and the current state of SourceNinja can be displayed via the CLI.

    :::term
    $ heroku sourceninja:command
    example output

SourceNinja activity can be observed within the Heroku log-stream by [[describe add-on logging recognition, if any]].

    :::term
    $ heroku logs -t | grep 'sourceninja pattern'

## Dashboard

For more information on the features available within the SourceNinja dashboard please see the docs at [sourceninja.com/docs](http://sourceninja.com/docs).

The SourceNinja dashboard allows you to identify open source projects and third party libraries that have newer versions available. One purpose of this is to make sure that no security issues are in the current versions of the open source packages you have installed.

![SourceNinja Dashboard](http://cl.ly/1j212T3m443U0c061h3i/Screen%20shot%202012-03-12%20at%2012.33.32%20PM.png "SourceNinja Dashboard")

The dashboard can be accessed via the CLI:

    :::term
    $ heroku addons:open sourceninja
    Opening sourceninja for my-awesome-app...

or by visiting the [Heroku apps web interface](http://heroku.com/myapps) and selecting the application in question. Select SourceNinja from the Add-ons menu.

![SourceNinja Add-ons Dropdown](http://cl.ly/3s3G3r412T1c282Q3Q1F/Screen%20shot%202012-03-12%20at%2011.11.02%20AM.png "SourceNinja Add-ons Dropdown")

## Removing the add-on
SourceNinja can be removed via the  CLI.

<div class="warning" markdown="1">This will destroy all associated data and cannot be undone!</div>

    :::term
    $ heroku addons:remove sourceninja
    -----> Removing sourceninja from my-awesome-app... done, v20 (free)

## Support

All SourceNinja support and runtime issues should be logged with Heroku Support at https://support.heroku.com. Any non-support related issues or product feedback is welcome at support at sourceninja.com.

## Configuration Variables
Once SourceNinja has been added, three configuration variables are set.

`SOURCENINJA_URL` is a canonical URL used to access the SourceNinja service instance.

`SOURCENINJA_EMAIL` is used by sourceninja for authentication. __Note: This should not be modified.__

`SOURCENINJA_TOKEN` is the API token for your actual Application. This token should be safe guarded as it is in essence a uersname/password combination.

`SOURCENINJA_PRODUCT_ID` is used by SourceNinja to identify your individual product.
 
This can be confirmed using the `heroku config` command.

    :::term
    $ heroku config | grep ADDON_CONFIG_NAME
    ADDON_CONFIG_NAME    => http://user:pass@instance.ip/resourceid

## Additional resources

Additional resources are available at:

* [SourceNinja Docs](http://www.sourceninja.com/docs/)
