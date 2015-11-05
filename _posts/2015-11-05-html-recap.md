---
layout: post
title: "Coding and Cookies Session 4: HTML Recap"
date:   2015-11-05 11:00:00
categories: tutorials recap
---
#HTML: make it readable
If you want to take the quiz as you read the resources, it's at [quiz.hugodf.xyz](http://quiz.hugodf.xyz)  
For the CSS and jQuery tutorials [click here](/tutorials/2015/11/05/recap.html)

HTML stands for Hypertext Markup Language. `Hypertext` means it's cooler than text and `markup language` means it describes its own content.  
That's what it does: when you hit a URL like [http://quiz.hugodf.xyz](http://quiz.hugodf.xyz). A server (computer somewhere that has all the things for that URL) sends a response in HTML format. Your browser then has to **parse** the HTML to show it to you as it was designed by the website's owner (me in this instance ;) ).  
All we're going to do is talk to a browser in a way that it understands.
##Declaring HTML
The first tags you need to know are `html`, `head` and `body`. A HTML document usually looks like this:

```html
<!DOCTYPE html>
<html>
	<head>
	</head>
	<body>
	</body>
</html>
```
Things contained in `head` are not displayed inside the HTML element, they give you info such as the name the tab/window (`title` tag), what needs to be loaded before the page is rendered (css/javascript files). Things like analytics libraries and what favicon to display also go in there.

##Tags and Elements
Tag and element are used interchangeably, depending on the context. So we can say the `body` element and the `body` tag(s).  

If we're more strict:  
- The **tags** correspond to this `<body></body>`, the opening tag corresponds to this `<body>` and the closing tag corresponds to this `</body>`.  
- The **element** is `body`

Some tags self-close eg. `img`, `meta`; this usually means that they are elements that don't contain any text or other elements (an image is an image, it doesn't contain anything else, especially not text).

##Attributes
Here's another HTML document:

```html
<!DOCTYPE html>
<html>
	<head>
		<meta charset="utf-8">
		<title>Title of the page</title>
		<meta description="Some page, this description appears when you link to this page from google/twitter/facebook">
	</head>
	<body>
	</body>
</html>
```

Let's look at these tags:

```html
<meta charset="utf-8">
<meta description="Some page, this description appears when you link to this page from google/twitter/facebook">
```

We say that `charset` and `description` are **attributes** of the respective `meta` elements (meta elements attach extra information to the page). We'll see more of them later but here are a couple of important ones:  
- `src`: is an attribute of the `img` tag it tells the browser the **source** of the image (where it is located)
- `style`: allows you to define **inline-styles** (don't do this if you can help it) on most elements that are displayed
- `class`, `id`: allow you to set a **class** or **id** on most elements,  
**Note: don't ever use id's**  
- `data-some-attribute`: allows you to set an arbitrary data attribute (this will be useful for jQuery).  
- `type`: allows you to set the **type** of the `input` element (example options are checkbox, radio button, text field, email field, password field, hidden field...).

##"Semantic" Tags (HTML5)
HTML allows you to describe what you're writing. Here's a sort of introduction/reference:

```html
<h1>This is a heading</h1>
<h2>This is a smaller heading</h2>
<p>Paragraph of text</p>

<ul>
	Unordered list (will render as bullet points)
	<li>list item</li>
</ul>
<ol>
	Ordered list (will render as 1., 2., ...)
	<li>list item</li>
</ol>
<header>
	A header
</header>
<nav>
	Fancy element
</nav>
A video: 
<video></video>
An image:
<img>
<article>
	Very descriptive tag, basically some text
</article>

<section>
	Section of some sort
</section>

<aside>
	Something that is supposed to go to the side
</aside>
<table>
	A table
	<tr>
		a table row
		<th>Table heading</th>
	</tr>
	<tr>
		another row
		<td>Table division (column kinda thing)</td>
	</tr>
</table>
```

Try them out, get to know them and so on.

##Generic Tags (div/span)
It's all nice and cool to user _semantic_ blablabla, but sometimes you either need something that are not accurately represented by semantic tags or you're just not bothered to write out semantic things. Some of the more semantic tags are also not supported on older browsers.

That's where generic tags come in: `div` and `span`.

- `div`, division: a block of something
- `span`, span: an inline of something

These usually have a `class` attribute that will tell you what they are used for and to style these ugly elements :).

##Anchor tricks
Final element of the day: `a`, also known as **anchor** or for the less tech-inclined: a **link**.

Now there is another element called `link` so we will make sure to call it `a` or **anchor** (`link` is something you put in your `head` element to get extra files that aren't in the page).

`a` has an **attribute** called `href` with which you tell it what it points to.

Eg.
```html
<a href="http://google.com">GOOOGLE</a>
```
Links to `http://google.com` and the text displayed is `GOOOGLE`.

We can do some funky stuff like force the link to open in a new window/tab using the `target` attribute:
```html
<a href="/" target="_blank">Link to root of the thing :o</a>
```

There's another cool thing to explain in the example above: relative vs absolute paths. When you're navigating between pages on your own website, you can just us `/blabla` instead of typing out `http://mysite/blabla` which is quite cool and which means you can have your site in multiple places and each one of them works :).

##Display type
This is more of a CSS thing (I think I will reiterate it there).

There are a couple of display types:  
- `block`: takes up the whole width of the screen unless a `float` rule is applied to it
- `inline-block`: is only as wide as its contents or the `width` rule applied to it, automatically floats
- `inline`: has no width, even if you try to set one to it.

> Alright that's it for HTML. Go to [quiz.hugodf.xyz](http://quiz.hugodf.xyz) to test out your new-found knowledge :).

>For the CSS and jQuery tutorials [click here](/tutorials/2015/11/05/recap.html)