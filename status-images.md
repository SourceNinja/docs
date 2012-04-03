---
layout: page
title: Dependency Status Images
---

## What This Guide Covers
This guide covers build status images feature of SourceNinja. Status images are part of the HTTP API that render dependency information (up-to-date or newer versions avaiailbale) as a PNG image. Developers are encouraged to add them to project sites, README files and so on both to link to demonstrate their commitment to optimization and good security practices.

To get started you will need a [SourceNinja account](http://www.sourceninja.com/sign-up.html), and integrate your application with SourceNinja.

## Status Image URLs

After adding your project to SourceNinja and integrating the SourceNinja gem, you can use the dependency status buttons to show the current dependency status of your projects in your README file on Github or your project website.

	https://app.sourceninja.com/status/[YOUR_PRODUCT_ID].png

HTTPS is used so that GitHub does not cache the image.

## Adding Status Images to README Files

### Textile
Add the following to your README:

	"!https://app.sourceninja.com/status/[YOUR_PRODUCT_ID].png!":https://app.sourceninja.com/products/[YOUR_PRODUCT_ID]

#### Markdown Syntax

	[![Dependency Status](https://app.sourceninja.com/status/[YOUR_PRODUCT_ID].png)](https://app.sourceninja.com/products/[YOUR_PRODUCT_ID])

### RDoc
	{<img src="https://app.sourceninja.com/status/[YOUR_PRODUCT_ID].png" />}[https://app.sourceninja.com/products/[YOUR_PRODUCT_ID]]