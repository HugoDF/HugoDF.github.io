---
layout: post
title: "UCLU Energy website"
date:   2015-03-06 15:28:11
categories: javascript keystone full-stack CMS
---
With all this talk of [Keystone.js][keystone] I thought I may as well showcase what it can do. I've recently completed work on the UCLU Energy Society's new [website][uclenergy].

It's running a pretty standard Express/Node.js stack. [Keystone.js][keysone] runs on top of Express.js and gives you out of the box (out of the <code>yo keystone</code>) Cloudinary image hosting, Mandrill integration, Mongoose schemas and auto-generated admin UI which is customisable through an object passed to <code>keystone.start(...)</code>.

For this project, one of the main ideas was to make sure they didn't need a developer when they wanted to update content. So all the images are editable throught the CMS, all the sections are editable and reorderable through the CMS. You can check the code out on my [GitHub][proj].

The views are rendered using handlebars and I'm using sass bootstrap as well as custom sass. Everything gets minimised/uglified using grunt (I wrote both development and build tasks) and that's pretty much it.

[keystone]: http://keystonejs.com
[uclenergy]: http://www.uclenergy.com
[proj]: https://github.com/HugoDF/energy-society