[SourceNinja](http://addons.heroku.com/sourceninja) is an easy way to manage the open source software that your application uses.

SourceNinja keeps you aware of updates to the open source software you use. Additionally, SourceNinja creates a hosted attribution page for your application.

SourceNinja is accessible via an API and has supported client libraries for Ruby*.

<div class="callout" markdown="1">
A list of all plans available can be found [here](http://addons.heroku.com/sourceninja).
</div>

## Installing the add-on
To install the free version of SourceNinja add-on, simply run:

    :::term
    $ heroku addons:add sourceninja
    -----> Adding sourceninja to sharp-mountain-4005... done, v18 (free)

Once SourceNinja has been added a `ADDON_CONFIG_NAME` setting will be available in the app configuration and will contain the [[variable purpose, i.e. "canonical URL used to access the newly provisioned SourceNinja service instance."]]. This can be confirmed using the `heroku config` command.

    :::term
    $ heroku config | grep ADDON_CONFIG_NAME
    ADDON_CONFIG_NAME    => http://user:pass@instance.ip/resourceid

After installing SourceNinja the application should be configured to fully integrate with the add-on.

### Local workstation setup

[[If there is a local executable required (like for the memcache add-on) then include installation instructions. If not, omit entire section]]

SourceNinja can be installed for use in a local development  environment.  Typically this entails [[installing the software | creating another version of the service]] and pointing the ADDON_CONFIG_NAME to this [[local | remote]] service.

<table>
  <tr>
    <th>If you have...</th>
    <th>Install with...</th>
  </tr>
  <tr>
    <td>Mac OS X</td>
    <td style="text-align: left"><code>brew install X</code></td>
  </tr>
  <tr>
    <td>Windows</td>
    <td style="text-align: left">Link to some installer</td>
  </tr>
  <tr>
    <td>Ubuntu Linux</td>
    <td style="text-align: left"><code>apt-get install X</code></td>
  </tr>
  <tr>
    <td>Other</td>
    <td style="text-align: left">Link to some raw package</td>
  </tr>
</table>

## Using with Rails 3.x

[[Repeat this ##Rails 3.x sections for all other supported languages/frameworks including Java, Node.js, Python, Scala, Play!, Grails, Clojure. Heroku is a polyglot platform - don't box yourself into supporting a single language]]

Ruby on Rails applications will need to add the following entry into their `Gemfile` specifying the SourceNinja client library.

    :::ruby
    gem 'sourceninja'

Update application dependencies with bundler.

    :::term
    $ bundle install
    sample output

### Development environment

When developing locally it is best to turn off the integration with SourceNinja to minimize dependencies on remote services. [[Describe how to stub/disable add-on integration - or specific steps required for local dev - for your service here.]].

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

<div class="callout" markdown="1">
For more information on the features available within the SourceNinja dashboard please see the docs at [mysite.com/docs](mysite.com/docs).
</div>

The SourceNinja dashboard allows you to [[describe dashboard features]].

![SourceNinja Dashboard](http://i.imgur.com/FkuUw.png "SourceNinja Dashboard")

The dashboard can be accessed via the CLI:

    :::term
    $ heroku addons:open sourceninja
    Opening sourceninja for sharp-mountain-4005…

or by visiting the [Heroku apps web interface](http://heroku.com/myapps) and selecting the application in question. Select SourceNinja from the Add-ons menu.

![SourceNinja Add-ons Dropdown](http://f.cl.ly/items/1B090n1P0d3W0I0R172r/addons.png "SourceNinja Add-ons Dropdown")

## Troubleshooting

If [[feature X]] does not seem to be [[common issue Y]] then 
[[add specific commands to look for symptoms of common issue Y]].

## Migrating between plans

<div class="note" markdown="1">Application owners should carefully manage the migration timing to ensure proper application function during the migration process.</div>

[[Specific migration process or any migration tips 'n tricks]]

Use the `heroku addons:upgrade` command to migrate to a new plan.

    :::term
    $ heroku addons:upgrade sourceninja:newplan
    -----> Upgrading sourceninja:newplan to sharp-mountain-4005... done, v18 ($49/mo)
           Your plan has been updated to: sourceninja:newplan

## Removing the add-on

SourceNinja can be removed via the  CLI.

<div class="warning" markdown="1">This will destroy all associated data and cannot be undone!</div>

    :::term
    $ heroku addons:remove sourceninja
    -----> Removing sourceninja from sharp-mountain-4005... done, v20 (free)

Before removing SourceNinja a data export can be performed by [[describe steps if export is available]].

## Support

All SourceNinja support and runtime issues should be logged with Heroku Support at https://support.heroku.com. Any non-support related issues or product feedback is welcome at [[your channels]].

## Additional resources

Additional resources are available at:

* [Site docs](http://docs.sourceninja.com)
