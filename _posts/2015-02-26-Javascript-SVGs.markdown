---
layout: post
title: "Javascript SVGs"
date:   2015-02-26 18:28:11
categories: javascript svg frontend
---
CSS3 brought a whole new section of abilities to the frontend engineer. Personally, <code>border-radius</code>, <code>animations</code>, sometimes <code>transform</code> and <code>box-shadow</code>. It means that you can create whole libraries of shapes using only CSS like in [this post on CSS tricks][shapes]. You can even make crazy shapes that are animated without writing a single line of javscript (see this [animated tree][tree]).

So when I was asked to write a triangle-based layout that has image fills in each shape, my first instinct was to go towards CSS. After a bit of hacking and trying things out, I decided to just dump that and go with SVGs (something about using transforms to do two things seemed hard... or something like that). For those who don't know, SVGs are vector graphics (meaning they scale since the shape isn't defined as a pixel map but in terms of relations). To this end, I sourced [SVG.js][svgjs], a library that is lightweight enough and nicely [documented][docs].

Armed with my library, generating triangles was a breeze. I then tried to use these as masks for the images layers, after a bit of a fight, I realised that instead of masking images with triangles, I could fill the triangles with images. After that, I had to worry about how scaled the images would look, which was fixed with some percentage-sizing of the images, as described in the [documentation][docs].

After that I implemented a slideshow for the top section of the images, using [svg.js'][svgjs] animation API, which was quite like you would expect from a javascript/jQuery style animation. On top of this I created some colour overlays which had to be animated in sync with the images. Again, not too much of a problem.

Finally and as always in this line of work, I had to make it responsive. Thankfully, my javascript was modularised enough so I only had to create update functions and run them on resize. The brunt of the work was actually done with image sizing and positioning the polygons on the canvas. Using a new library, it turns out that the hardest part was getting to grips with the simplest elements/functions it provides.

[tree]: http://codepen.io/yukulele/pen/KCvbi/
[svgjs]: http://svgjs.com/
[shapes]: https://css-tricks.com/examples/ShapesOfCSS/
[docs]: http://documentup.com/wout/svg.js