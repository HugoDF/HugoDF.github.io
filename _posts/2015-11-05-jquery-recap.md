---
layout: post
title: "Coding and Cookies Session 4: jQuery Recap"
date:   2015-11-05 12:00:00
categories: tutorials recap
---

# jQuery: make it fancy
If you want to take the quiz as you read the resources, it's at [quiz.hugodf.xyz](http://quiz.hugodf.xyz).  
For the HTML and CSS tutorials [click here](/tutorials/2015/11/05/recap.html).

So we should know some HTML, CSS. What do we do if we want to make fancier, more complicated interactions?

Things like hiding elements when you click on a button, opening up a modal. Those are all interactions that are done without a page reload/change. So how do we do it?

## Javascript
Javascript allows you to interact with the web page and update content, show/hide things without changing page.

## jQuery: the library
jQuery is a javascript library that those interactions easier. It means you don't have to deal with different browsers supporting different ways of doing things since jQuery handles all that for you.

And the _query_ in **jQuery** means that it's designed to make it easy to talk to the web page.

## Selecting elements
To select elements just use the appropriate CSS selector.

```javascript
$('body');
$('.button');
$('#some-id');
```
All of these work and will select all the matching elements.

## Calling functions on elements
We've got a way to select things, what can we do with them?

Let's hide some stuff:

```javascript
$('body').hide();
```
Let's show some stuff:

```javascript
$('p').show();
```
Simple enough right?

To call a function a jQuery object (`$(some-selector)`) just append `.functionName()`. Which gives `$('.navbar .mobile-menu-toggle').show();`.

Javascript technically requires semicolons but if you miss one or two out it will be ok. On the other hand if you don't put `()` and `{}` in the right place it will spit errors at you.

## Adding event listeners

Let's say we want to do show the menu when a button is clicked. We can't just show the menu right? We have to wait until that button is clicked. This is how we do it:

```javascript
$('.button').on('click',function(){
  $('.menu').show();
});
```

The syntax is: `jQueryObject.on(eventName, actionToDo);`.  
- `eventName`, can be 'click', 'mousein' and many more (full-er list [here](http://api.jquery.com/category/events/))
- `actionToDo` is a function, in the example we use an _anonymous function_, which means it doesn't have a name but it can be another function that's been declared. `ActionToDo` is what we call a **callback**.

## Callbacks

Callbacks are functions that are called on completion of an action. In the case above, when something is clicked the callback `function(){$('.menu').show();}` is called.  
This concept is very important in javascript

## jQuery vs javascript

Here is some jQuery code:

```javascript
$('.button').on('click',helloWorld);
```

Here is the equivalent in javascript:

```javascript
buttons = document.getElementsByClassName('button');
for(var i=0; i<buttons.length;i++){
  buttons[i].addEventListener('click', helloWorld);
}
```

Which is more complex?

jQuery means you write cleaner code because you don't have to worry as much about what the actual end interaction with the document will be. Just select, add listeners, fire off handlers, great!!!

Hacking around in jQuery is cool, use/abuse Google and [the jQuery documentation](http://api.jquery.com).



> Alright that's it for jQuery. Take the quiz at [quiz.hugodf.xyz](http://quiz.hugodf.xyz) to test out your new-found knowledge :).


> For the HTML and CSS tutorials [click here](/tutorials/2015/11/05/recap.html)
