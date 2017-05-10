---
layout: post
title: "In simple terms: backend code, frontend code and how they interact"
date:   2017-03-31 10:25:00
categories: web-development frontend backend JavaScript
---

## A look at the shifting boundaries of web development

This was originally posted as an answer on Quora:
[How does a frontend code and a backend code interact with each other?](https://www.quora.com/How-does-a-frontend-code-and-a-backend-code-interact-with-each-other/)

Let’s start with quick definitions:

## Frontend

All things the browser can read, display and/or run. This means HTML, CSS and JavaScript.

HTML (Hypertext Markup Language) tells the browser “what” content is, eg. “heading”, “paragraph”, “list”, “list item”.
CSS (Cascading Style Sheets) tells the browser how to display elements eg. “the first paragraph has a 20px margin after it”, “all text in the ‘body’ element should be dark grey in colour and use Verdana as its font”.

JavaScript tells the browser how to react to some interactions using a lightweight programming language. A lot of websites don’t actually use much JavaScript but if you click on something and content changes without the page flickering to white before showing the new content, that means JavaScript is used somewhere.

## Backend

All things that run on a server ie. “not in the browser” or “on a computer connected to a network (usually the internet) that replies to other computers’ messages” are backend.

For your backend you can use any tool available on your server (which is just a computer that is set up to reply to messages). This means you can use any general purpose programming language, eg. Ruby, PHP, Python, Java, JavaScript/Node, bash. It also means you can use a host of Database Management Systems eg. MySQL, PostgreSQL, MongoDB, Cassandra, Redis, Memcached.

# The state of backend-frontend interaction

There are two main architectures today that define how your backend and frontend interact.

## Server-rendered apps

The first is straight up HTTP requests to a server-rendered app. This is a system whereby the browser sends a HTTP request and the server replies with a HTML page.
Between receiving the request and responding, the server usually queries the database and feeds it into a template (ERB, Blade, EJS, Handlebars).

Once the page is loaded in the browser, HTML defines what things are, CSS how they look and JS any special interactions.

## Communication using AJAX

AJAX stands for Asynchronous JavaScript and XML. This means that the JavaScript loaded in the browser sends a HTTP request (XHR, XML HTTP Request) from within the page and historically got a XML response.

Nowadays, responses are also done in JSON format.

This means that your server needs to have an endpoint which replies JSON/XML to requests. Two examples of protocols for this are REST and SOAP.

## Client-side (single page) applications

AJAX allows you to load data without refreshing the page. This has been pushed to the max with frameworks such as Angular and Ember. These apps are bundled, sent to the browser and any subsequent rendering is done on the client-side (browser).
These frontends communicate with the backend over HTTP using JSON/XML responses.

## Universal/Isomorphic applications

React and Ember (amongst other) libraries and frameworks allow you to render an app on the server (backend) as well as on the client (frontend).
When set up like this, the app uses both AJAX and server-rendered HTML to communicate frontend to backend.

# Beyond frontend and backend

## Standalone frontends

The web applications you’re going to build are going to need a network connection less and less.

Progressive web applications are loaded once and run forever (ish). You can have a database in the browser. For some use cases, your applications literally only needs a backend on first load and then just for syncing/safeguarding of data. This persistence layer means that most of the logic is into the client-side application (frontend).

## Lightweight backends

Backends are becoming more and more lightweight. Technologies like document stores and graph databases mean that there’s a lot less going on in terms of re-aggregation of data by the backend service. The onus is on the client to specify what data it needs (graph databases) or to fetch all the different fragments of data it needs (REST APIs).

I mean we’re now building backend services that don’t even run all the time, just when they’re required, thanks to serverless architectures like AWS Lambda.

## Blurred lines

The complexity is shifting across the frontend/backend boundary. We now have the choice, depending on what sort of application we’re building, to make our client hold the complexity or to keep it on the server.

Each option has its pros and cons. Namely the server is an environment that is more stable and has less unknowns but it’s always a network call away. Certain users have the latest browsers and can profit from a client-side application that does most of the work with a snappy UI but you may be alienating users who don’t run the latest browser on an optic fibre internet connection.

At the end of the day, having all these options is a good thing. As long as we focus on building great experiences and products using the right tool for the job. Hopefully you have gained a bit more understanding of the state of web development today.
Remember to share this post if you liked it. Follow me on twitter or [@hugo__df](https://twitter.com/hugo__df) for more web-dev content :).

[In simple terms: backend code, frontend code and how they interact](https://hackernoon.com/in-simple-terms-backend-code-frontend-code-and-how-they-interact-2485c5a1bbd2) was originally published at [https://medium.com/@hugo__df](https://medium.com/@hugo__df) on 31st March 2017.