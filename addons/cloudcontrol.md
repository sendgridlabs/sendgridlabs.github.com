## Introduction

[loader io](http://addons.heroku.com/loaderio) is a free [add-on](http://addons.heroku.com) to perform cloud-based load testing against your apps/apis with thousands of concurrent connections. Use our lightweight, simple web-interface or well-documented API to run consistent and reliable load tests against your app.

![Example: loader io test report](https://s3.amazonaws.com/partner.static.loader.io/heroku/loaderio-intro-image1.png)

## Installing the loader io add-on

loader io is easy to install for any of your Heroku applications using the CLI:

    :::term
    $ heroku addons:add loaderio:standard
    -----> Adding loaderio to sharp-mountain-4005... done, v18 (free)

Once loader io has been added an account will be automatically created for you on loader.io and we'll send you an email welcoming you to loader io.

After installing loader io your application will be configured to use with the add-on.

## Using the loader io web-ui

Running load tests with loader io is easy and can be done by selecting loader io from the Add-ons menu in your [Heroku apps web interface](http://heroku.com/myapps)

Or, you can launch the loader io web-ui from the CLI:

	:::term
	$ heroku addons:open loaderio
	Opening loaderio for myapp.heroku.com

## App verification

In order for loader io to run load tests against your application you must first verify ownership of your application.  You can do this in one of two ways.

### URL verification

With URL verification you're provided with an app verification code. This code must make a page accessible by our verification service and insure the content on the page has only the app verification code we provide.

![](https://s3.amazonaws.com/partner.static.loader.io/heroku/loaderio-verify-html-image1.png)

### DNS verification

With this method, you're provided with a app verification code which must be used in a txt record created on the DNS for the domain of the app you are trying to verify.

![](https://s3.amazonaws.com/partner.static.loader.io/heroku/loaderio-verify-dns-image1.png)

## Using loader io in Ruby

Once you've verified your app/domain all you need is your API key to programmatically submit load tests.  You can find your API key one of two ways.

### API key

You can find your API key via the CLI:

	:::term
	$ heroku config:get LOADERIO_API_KEY
	your_api_key_here

Or, you can find your API key by accessing the loader io add-on through your [Heroku apps web interface](http://heroku.com/myapps) and there you'll see the API key you need to start running tests.

![Example: loader io API key](https://s3.amazonaws.com/partner.static.loader.io/heroku/loaderio-api-image1.png)

### Install the loader io gem

Install the `loaderio` gem locally (or specify it in your `Gemfile`).

	:::term
	$ gem install loaderio

and use an interactive console to configure and create a new load test.

	:::term
	$ irb
	> require "loaderio"
	> Loaderio::Configuration.api_key = ENV['LOADERIO_API_KEY'] || "your_api_key_here"
	> Loaderio::Test.create(url: "http://example.com", load: "0-250-60")

<p class="warning" markdown="1">
Make sure you use the exact domain when creating a load test that you specified when verifying the app (including the subdomain). `www.example.com` and `example.com` are treated as two separate apps and must be verified individually.
</p>

Further details about using the API can be found in the [loader io API docs](http://api.loader.io/docs).

## Removing the add-on

loader io can be removed via the CLI.

<div class="warning" markdown="1">This will destroy all associated data and cannot be undone!</div>

    :::term
    $ heroku addons:remove loaderio
    -----> Removing loaderio from sharp-mountain-4005... done, v20 (free)

## Support

All loader io support and runtime issues should be submitted via on of the [Heroku Support channels](support-channels). Any non-support related issues or product feedback is welcome via email: feedback@loader.io or via [twitter @loaderio](http://twitter.com/loaderio).

## Additional information

You can find more information and help resources for loader io at:

[loader io support website](http://feedback.labs.sendgrid.com)