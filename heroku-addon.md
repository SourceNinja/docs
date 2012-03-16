---
layout: page
title: SourceNinja Heroku Add-On
---

[SourceNinja](http://www.sourceninja.com) is an easy way to manage the open source software that your application uses. SourceNinja keeps you aware of updates to the open source software you use.

The key benefits of using SourceNinja are:

* Understanding what packages need to be updated.
* Having actionable information to determine whether an update should take place.
* Alerts when updates become available for Open Source packages.

SourceNinja is accessible via an API and currently supports client libraries for Ruby.

## TL;DR 
1. `heroku addons:add sourceninja`
2. add line `gem 'sourceninja'` to your `Gemfile`;
3. `bundle install`
4. Commit your changes.
5. `git push heroku`

## Installing the add-on
To install the SourceNinja add-on, simply run:

    :::term
    $ heroku addons:add sourceninja
    -----> Adding sourceninja to my-awesome-app... done, v18 (free)

Upon installation of the SourceNinja add-on the application is configured, but, requires the installation of the SourceNinja gem to add your Open Source packages.

## Using with Rails 3.x
SourceNinja supports rails with use of the sourceninja gem which pushes all of your gem names and versions to sourceninja.

Ruby on Rails applications will need to add the following entry into their `Gemfile` specifying the SourceNinja client library.

    :::ruby
    gem 'sourceninja'

Update application dependencies with bundler.

    :::term
    $ bundle install
    Fetching source index for https://rubygems.org/
    ...
    Installing sourceninja (0.0.6) 
    ...
    Your bundle is complete! Use `bundle show [gemname]` to see where a bundled gem is installed.
    $

### Development environment
The gem automatically disables the pushing of development and testing data to SourceNinja. This way the data received about gems will only refer to production data. In doing this, SourceNinja always reflects what gems are used in production.

## Dashboard
For more information on the features available within the SourceNinja dashboard please see the docs at [sourceninja.com/docs](http://sourceninja.com/docs).

The SourceNinja dashboard allows you to identify open source projects and third party libraries that have newer versions available. One purpose of this is to make sure that no security issues are in the current versions of the open source packages you have installed.

![SourceNinja Dashboard](http://cl.ly/2t0t0h0m1b041t2E1P0A/Screen%20shot%202012-03-16%20at%2012.38.28%20PM.png "SourceNinja Dashboard")

The dashboard can be accessed via the CLI:

    :::term
    $ heroku addons:open sourceninja
    Opening sourceninja for my-awesome-app...

or by visiting the [Heroku apps web interface](http://heroku.com/myapps) and selecting the application in question. Select SourceNinja from the Add-ons menu.

![SourceNinja Add-ons Dropdown](http://cl.ly/3s3G3r412T1c282Q3Q1F/Screen%20shot%202012-03-12%20at%2011.11.02%20AM.png "SourceNinja Add-ons Dropdown")

## Monitoring & Logging

Stats and the current state of SourceNinja can be displayed via the CLI.

    :::term
    $ heroku sourceninja:command
    example output

SourceNinja activity can be observed within the Heroku log-stream by [[describe add-on logging recognition, if any]].

    :::term
    $ heroku logs -t | grep 'sourceninja pattern'

## Removing the add-on
SourceNinja can be removed via the  CLI.

<div class="warning" markdown="1">This will destroy all associated data and cannot be undone!</div>

    :::term
    $ heroku addons:remove sourceninja
    -----> Removing sourceninja from my-awesome-app... done, v20 (free)

## Support

All SourceNinja support and run-time issues should be logged with Heroku Support at https://support.heroku.com. Any non-support related issues or product feedback is welcome at support at sourceninja.com.

## Configuration Variables
Once SourceNinja has been added, three configuration variables are set.

`SOURCENINJA_EMAIL` is used by SourceNinja for authentication. __Important: This should NOT be modified.__

`SOURCENINJA_PRODUCT_ID` is used by SourceNinja to identify your individual product.

`SOURCENINJA_TOKEN` is the API token for your actual Application. This token should be safe guarded as it is in essence a username/password combination.
 
This can be confirmed using the `heroku config` command.

    :::term
    $ heroku config | grep SOURCENINJA
    SOURCENINJA_EMAIL      => app2884533@heroku.com
    SOURCENINJA_PRODUCT_ID => d4b782e3-c952-4f44-cb14-df55416b0f98
    SOURCENINJA_TOKEN      => 8c472ab4b8f8d10d29f725d30effd3d5

## Debugging
The sourceninja-ruby gem uses DEBUG level... Add with the following:

    heroku config:add LOG_LEVEL=DEBUG

## Additional resources

Additional resources are available at:

* [SourceNinja Docs](http://www.sourceninja.com/docs/)
* [sourceNinja-ruby gem](sourceninja-gem)
