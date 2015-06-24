---
layout: post
title: "Puma on OpenShift"
description: ""
category:
tags: [openshift, heroku]
---
{% include JB/setup %}

If you need a free hosting for your dynamic website you have very few choices (especially if you don't use PHP).
You can use the "free tier" of [Heroku](https://www.heroku.com/), but you'll have some problems:

1. Your application will go in *sleep mode* after 1 hour without any connections and then the first connection needs to wait for the restart of the "server".

2. From August 15, 2015 your free application must sleep 6 hours within a 24 hour period or they will shutdown your application for 6 hours.

You can find more details on [Heroku devcenter](https://devcenter.heroku.com/articles/dyno-sleeping).

Since I was using Heroku only for "hobby" and so I don't want to pay $7/month, I looked for an alternative and I found [OpenShift](https://openshift.redhat.com/).

> [OpenShift](https://openshift.redhat.com/) is a [platform as a service](https://en.wikipedia.org/wiki/Platform_as_a_service) product from Red Hat. It is also an Infrastructure as a Service ([IaaS](https://en.wikipedia.org/wiki/Infrastructure_as_a_service#Infrastructure)), comparable to Google Storage and Amazon S3 online storage services. (from Wikipedia)

The free tier of OpenShift does not have the problems of the free tier of Heroku, the only limitation is that you can only have 3 website for each OpenShift account.

Since I develop my website using [Ruby](https://www.ruby-lang.org) I tried to use the official _Ruby 2.0 Cartridge_, but I found that this cartridge includes Apache with old Passenger and Rack versions and this forces you to put
`gem 'rack',  '1.5.2'` to your Gemfile since requiring new versions prevent your application from starting.

They suggest to use a _Do It Yourself_ cartridge and to configure all by yourself. I avoided this suggestion, because the _Ruby 2.0 Cartridge_ is automatically updated for security problems and so I tried to workaround the problem.

My solution is an hack that prevents Apache to be started and it starts the [http://puma.io/](Puma) webserver instead (obviously this hack can be changed to start any other webserver).

If you want to study my hack and/or to use it you can find it on [my Github repository](https://github.com/drizzt/puma-openshift).

To use my hack just create an application with the _Ruby 2.0 Cartridge_, clone my repository and use it as starting point for your application.

Or just replace your default `.openshift` directory with the `.openshift` directory taked from my repository.
