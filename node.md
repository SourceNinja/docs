---
layout: page
title: sourceninja node module
---

[![Dependency Status](https://app.sourceninja.com/status/a78ca9a5-0a4a-4764-8639-87cc5a41948e.png)](https://app.sourceninja.com/products/a78ca9a5-0a4a-4764-8639-87cc5a41948e)

What This Guide Covers
-------------------------
This guide will help you integrate SourceNinja into your node application. This only needs to be done once.

What is the sourceninja module
---------------------------
The sourceninja node module can be included in your node application to allow seamless integration with SourceNinja. The sourceninja module will send all of your modules and versions to SourceNinja to begin managing your open source libraries.

Getting Started
---------------
1. Create a [SourceNinja](http://sourceninja.com) account.

2. Log into SourceNinja and create a product. The product you create will be paired with your application.

3. After you create a product, you will be directed to a page asking what language your application is running. Select `Node.js` from the menu on the left side. 

4. You will be presented with two values, you'll need these two values later.

		Example:

		SOURCENINJA_TOKEN="50a336d92da8ddea1ae0a6c0d06a172"
		SOURCENINJA_PRODUCT_ID="477fcfa7-765a-4b91-b6a5-2ebe4c4f9d58"

5. Install the [sourceninja module](https://github.com/SourceNinja/sourceninja-node). You can do this by adding the following line to your `packages.json` under dependencies.
    
		"sourceninja": "*"

6. Run `npm install`.

7. Set the environment variables ```SOURCENINJA_TOKEN``` and ```SOURCENINJA_PRODUCT_ID``` using the values from step 4. On Heroku, you can use the command `heroku config:add SOURCENINJA_TOKEN=XXX SOURCENINJA_PRODUCT_ID=XXX`

8. Add the following code above your main function.


		var sourceninja = require('sourceninja');
		sourceninja.core.kapow();


Updated Magically in Production
-----------------
Now each time you push to production the sourceninja module will report your node modules and versions back to SourceNinja. If you visit your SourceNinja product page you will be given a list of outdated modules.

The SourceNinja data is populated whenever the app is initialized.

Testing Locally
---------------
If you would like to test sourceninja node module locally, you can call the environement variables before launching your app locally.

	SOURCENINJA_TOKEN=XXX SOURCENINJA_PRODUCT_ID=XXX node

Upon doing this, each time you start the node server locally the data will be pushed. You could also use these steps if you want to manage a production instance and a development instance by using a different product_id.

Support
-------
Feel free to email us at support at sourceninja dot com if you have any questions or issues.