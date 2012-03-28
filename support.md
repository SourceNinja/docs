---
layout: page
title: Support
---

Hello there, welcome to SourceNinja support. The ninjas are here to help you.

If you would like to contact us directly for support please use the form on the [contact page.](https://app.sourceninja.com/contact)

##Getting started with SourceNinja
Currently, you need to be part of our [alpha](http://www.sourceninja.com/sign-up.html) to use SourceNinja.

Integrating your projects with SourceNinja is as easy as telling us your product name and the open source package versions that product is using. That is probably a lot of information to enter manually so we are working hard on developing new methods to make this process easy for you regardless of what technologies you are using.

###Heroku
_Heroku Add-on instructions [**here**](heroku-addon)_

###Ruby
_gem installation instructions [**here**](sourceninja-gem)_

###CSV Import
If one of the above methods does not support your needs, SourceNinja also suppots .csv file import.

####.csv example
      vim,7.2.303
      vixie-cron,4.1
1. Log into SourceNinja and create a product
2. Click import on the left side of the product page(or the big get started now button)
3. Select CSV on the left and then upload your .csv file
4. When the import is finished, you will see an alert at the top of the page:
![SourceNinja-Import](assets/images/import_alert.png)
5. Click on the alert and you will see the list of open source packages SourceNinja matched in your .csv
6. Click import to add those packages to your product or remove to discard the import