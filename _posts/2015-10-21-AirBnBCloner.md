---
layout: post
title: "Coding and Cookies Session 2: jQuery and Responsive Design"
date:   2015-10-21 12:25:00
categories: tutorials
---

# The site

You can see what we've done at [hugodf.github.io/codingandcookies2](http://hugodf.github.io/codingandcookies2).  
The GitHub repository is at [https://github.com/HugoDF/codingandcookies2/tree/gh-pages](https://github.com/HugoDF/codingandcookies2/tree/gh-pages).

Before you start, download the skeleton/starter project either by following [this link](http://hugodf.github.io/codingandcookies2/codingandcookies2.zip) or from GitHub [https://github.com/HugoDF/codingandcookies2](https://github.com/HugoDF/codingandcookies2).

## Walkthrough of components

If you open up Sublime Text/Atom/Brackets/Notepad++ or whatever else you're using you should be able to view a tree that's a bit like this:  
![image of tree][image-1]

If you open up all the folders you should see something like this:  
![image of open tree][image-2]

Now in the img folder, we have a bunch of images provided by Pablo, a tool for social media images built by Buffer.  
In the `js` folder, you've got `jquery.js` and `main.js`.
jQuery is a library for javascript that unifies the programming interface with the browser and allows you to "query" the the representation of your page in the browser (this is called the DOM). `main.js` is where we'll write our javascript code.
In the `css` folder, we've again got two files: `default.css` and `main.css`. `default.css` is the base styles that I have written so that we can focus on improving this website and not the menial basic tasks we saw in the previous post. `main.css` is for you to write styles in :).  

## CSS selectors

Just a quick reminder of how CSS selectors work (more on this at [http://hugodf.github.io/tutorials/2015/10/10/tutorial.html](http://hugodf.github.io/tutorials/2015/10/10/tutorial.html)).  
A css selector uses either the element name:

```css
html
body
aside
h1
```  
or the class name or id preceded by `.` and `#` respectively:  

```css
.some-class{}
#some-id{}
```
jQuery will use similar selectors.

## The web is mobile: responsive design concept

In the year 2000, there was no such thing as widespread smartphones. Back then the web was Desktop-only.

Then came the first smartphones and slowly websites started optimising for mobile performance (small screens). We started talking about the mobile web, the web was still desktop-first but there was progress.

Today, one cannot launch a generic website for desktop-only and expect no issues from mobile users.  
Today, the web is mobile, and then there's the desktop-web.

Responsive design is design that reacts to factors such as screen width (and/or device from which said design is viewed from).

On a simple level, it's doing things like collapsing the navbar items on mobile, making a grid of images full-width and having less columns. Those are responsive design practices.

If you just resize your browser to the minimum width you can, you will get an idea of how it looks on mobile, right now, it looks quite bad.

## Media Queries

To implement responsive designs, we need a mechanism to check device width at the very least. This is where media queries come in.

A media query allows us to apply styles for a certaing type of device, this is what they can look like:

```css
@media screen and (max-width: 720px){
	//some rules
}
```
What this media query is saying is: if the media is `screen` and its width is less than `720px`, apply these rules. In other words, this rule is applied to medias that are `screen` and whose `max-width` is `720px`. When using media queries, be very careful about spaces and `()`.  
For example:

```css
@media screen and (max-width: 720 px){}
```
This won't work because of the space between `720` and `px`. Get used to copyig very carefully, it will stand you in good stead for the javascript parts later on.

Add this to your `main.css`:

```css
@media screen and (max-width: 720px){
  .logo{
    display: none;
  }
  .title{
    font-size: 20px;
  }
}
```
This will make the emoji disappear and bump the font-size down so that it looks nicer on mobile.

## Style the Navbar for mobile

We're going to style the navbar on mobile. Add the following in your `index.html` after `<div class="title">AIRBNB C(L)ONER</div>`:

```html
<div class="mobile-menu-toggle">MENU</div>
```

Next, resize your browser to a width under 720px and add this to the top of your `main.css`:

```css
.mobile-menu-toggle{
  cursor: pointer;
  padding-top: 10px;
  padding-bottom: 15px;
  float:right;
}
```
This is just to make our `MENU` button look nicer.

Add this to your `main.css` inside the `@media` query:

```css
// insert after this:
//.title{
//	font-size: 20px;
//}
.nav-right{
	float: left;
}
.nav-list{
	display: none;
}
.nav-list.open{
	display: block;
}
.nav-list.open li{
	display: block;
	text-align: center;
}
```
Let's explain what this code does:

- `.nav-right` rules say, float the `.nav-right` element to the left when `@media` rule is met
- `.nav-list` rules say, do not display (hide) the `.nav-list` when `@media` rule is met
- `.nav-list.open` and `.nav-list.open li` express the display of the `.nav-list` element and its `li` children _when_ it has class `.open`.

If you open this in your browser, the menu doesn't open. That's because we have nothing adding the `open` class to `.nav-list` on mobile. We can fix that with jQuery.

## console.log and jQuery selectors

Type this:

```javascript
$(document).ready(function(){
	console.log($('.mobile-menu-toggle'));
});
```

Reload your page and open up the console (Right Click on page > Inspect Element > Console Tab). It should come up with something like this:

```
jQuery [<div class="mobile-menu-toggle">]
```

Let's explain the javascript code:

- `$(document).ready(function(){})` means when `$(document)` is `ready` do the content of `function` (body is the stuff inside `{}`). `ready` is what we call an **event**.
- `console.log` just prints whatever is in `()` to the developer console.
- `$('.mobile-menu-toggle')` selects the element `.mobile-menu-toggle` using jQuery `$()`.

Now, let's make this thing (mobile nav) work. Change up the above code to this:

```javascript
$(document).ready(function(){
	$('.mobile-menu-toggle').on('click',function(){
		$(this).toggleClass('open');
	});
});
```
What we're doing inside the outer `function(){}` is we **bind** (attach an action if you will) to the `.mobile-menu-toggle` element. The **event** we're **listening** (waiting) for is `click`. When this event fires (ie. when `.mobile-menu-toggle` is clicked), we `toggleClass('open')` (we toggle the `open` class) on `$(this)` element (which in this context is `.mobile-menu-toggle`).

So that means if you click `.mobile-menu-toggle`, it adds `open` class if it isn't present and removes it if it is.

Try it, it works!!!

If you want to make this `MENU` button not appear on desktop, just write this in `main.css`:

```css
@media screen and (min-width: 720px){
  .mobile-menu-toggle{
    display: none;
  }
}
```
Notice that we're using `screen and (min-width:...)` which means `all screens that are bigger than ...`.

## The tiles: CSS-only

Next up, let's style the tiles :).

### The tiles: style it

They're a bit big and distorted on desktop. Let's hide the description and make them `32%` width. The tiles are wrapped in the `listing` class so the following code should do the trick:

```css
.listing{
  display: inline-block;
  width: 32%;
}
.listing .description{
  display: none;
}
```

You should understand most of the rules above, if you don't know what `display: inline-block` stands for, here's an explanation: `block` takes up the full width of the screen, `inline` has no width (it takes up as much width/height as its contents are wide/high, `inline-block` does a bit of both, its height/width default to the height/width of its content, you can set the width/height _and_ it doesn't take up a whole row... Pretty nifty.

Now we need some more styling with `@media` queries to display nicely on mobile and tablet widths:

```css
@media screen and (max-width: 1024px){
  .listing{
    width: 49%;
  }
}
@media screen and (max-width: 572px){
  .listing{
    width: 100%;
  }
}
```
Those two rules say: on a `screen that is less that 1024px wide` `.listing` should have `width: 49%` and on a `screen that is less that 572px wide` `.listing` should have `width: 100%`.

### The tiles: transition it

Ok now we've hidden the description and displayed the tiles in a nicer way, how do we display the description?

First off I'll show you how to do it with CSS only.

Add this to the end of `main.css`

```css
.listing:hover img{
	width: 50%;
	float: left;
}

.listing:hover .description{
	display: inline-block;
	width: 50%;
	float: left;
}
```
These rules says when `listing` is `hover`-ed, `img` has `width 50%` and `floats left` and `.description` has `width 50%` `displays as inline-block` and `floats left`.

It's really jittery and all but you know, that's without even using javascript. Add this to make the transitions a bit slower and more manageable:

```css
.listing{
  transition: all .25s linear;
}
```
Still too jittery so let's bind it to click with jQuery.

## The tiles: jQuery it :)

We're going to use a very similar snippet of javascript/jQuery as for the mobile menu

So we just swap out `.listing:hover` for `.listing.open` which gives us:

```css
.listing{
  transition: all .25s linear;
}
.listing.open{
  width: 100%;
}
.listing.open img{
  width: 50%;
  float:left;
}
.listing.open .description{
  display: inline-block;
  float:left;
  width: 50%;
}
```

And add this to your `main.js`:

```javascript
$('.listing').on('click', function(){
	$('.listing').removeClass('open');
	$(this).addClass('open');
});
```

So the whole file looks like this:

```javascript
$(document).ready(function(){
	$('.mobile-menu-toggle').on('click', function(){
   		$('.nav-list').toggleClass('open');
   	});
  	$('.listing').on('click', function(){
  		$('.listing').removeClass('open');
   		$(this).addClass('open');
  	});
});
```
Here's what the code does:

- `$('.listing').removeClass('open');` resets all the `listing`s to not having class `open`.
- `$(this).addClass('open');` adds the open class to the listing that was clicked.

## Extra: Scroll-it

Your homework :)

Have a look at `$('.mobile-menu-toggle').offset().top` and `$('body,html').scrollTo(100)` to figure out how to make the page scroll on a certain element's click.

We're doing a Rails blog next week so come back!!!

You can also [follow me on twitter @hugo__df](http://twitter.com/intent/follow?user_id=2603804084).


[image-1]: /img/tutorials/2-screen-1.jpg
[image-2]: /img/tutorials/2-screen-2.jpg
