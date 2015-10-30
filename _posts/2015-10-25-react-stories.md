---
layout: post
title: "Cross-platform React stories"
date:   2015-10-25 10:25:00
categories: react
---
>The tale of a BrumHack and 3 platforms. 

React brought us a new way to think about the client-side and UIs in general. So that was exciting.

For React to be effective we start to think of UI as a function of state, which is great since for the most part, it is. Think of a button, its state: active, disabled, clicked etc… has a direct mapping to how it displays.

React Native brings the same paradigm to the native mobile environments. One of its great strengths beyond being React is that we can leverage the mass of npm packages and Node development techniques.

At BrumHack 3.0 I used React to deliver a truly cross-platform experience. I have the native apps on [http://github.com/HugoDF/beercalculatorapp/](http://github.com/HugoDF/beercalculatorapp/) and the web version on [http://hugodf.github.io/beercalculator](http://hugodf.github.io/beercalculator).

#The setup

Coming from webdev, the build pipeline actually felt quite slow for React Gulp/Browserify since I’m used to Gulp just compiling my SCSS to CSS, and running a livereload server. Here I was running a nice big bundling task instead. It turns out the Chrome devtools for React are quite nice and easy to use, they track state and all that, which is awesome because it means you’ve almost got a development environment (as opposed to abusing “console.log”). It’s not Eclipse, but it’s nice and the errors are pretty solid when compared to what the rest of the javascript world is doing, the likes of “undefined is not a function”, React telling you “check Component’s render method” is a breath of fresh air.

Onto the native environments. The iOS environment is a lot easier to set up and find my way around. That could just be that the guides don’t involve the main Android IDE: AndroidStudio whereas for iOS, we’re using Xcode, mostly because there’s no choice. I had done a tutorial in iOS React-Native before and my app was simple enough so I started off with iOS, then straight ported it to Android and it worked for the most part. I didn’t go through and fix up all the issues on Android, so I don’t know if I would have been able to but the iOS app feels at least as good as the webapp and with a couple more months I’m pretty confident the Android app would be too.

#The things I would change 

##1. Use JSX styles 

As it happened, the closer I got to low-level rendering components, the more I had to chop and change. The main thing I would do differently is definitely _not_ using CSS for the webapp since I basically had to throw away all the infrastructure I set up for that by means ditching className attributes.That was costly just in terms of raw time, it didn’t affect my efficiency because other things stumped me for a longer time. I would expect that as I find less and less of those problems that stump me as a beginner, the time I waste stripping classNames and HTML tags will frustrate me more and I will find more efficient ways to handle myself to avoid that scenario.

##2. Avoid HTML hacks

I’m web guy so I like my DOM/HTML hacks. For example passing data through data-attributes. In the world of hacks, I’ve done worse, like styling using jQuery and setTimeout. It’s not ideal to do this though, since I’m limiting my solution to the browser DOM and I have to struggle later on with a foreign bunch of native components at which point I actually implement the solution as React would expect me to.

##3. In short: homogenise between React and React Native

React helps you do this very well since you’re building up your component library with each new one you write. It stays quite modular, and most of all, it doesn’t feel like forced modularisation. I can start off with hardcoded “div”s (and “View” elements natively), then move that subcomponent into a separate React Component but in the same file and eventually migrating it to its own file and require/export-ing it into the original file.

This is great. It means you can incrementally modularise your code, just like jQuery allows you to. With the distinction that React modules very easily and almost naturally end up as modules whereas my jQuery hacks never end up more than reference snippets.

#The good things of React/React Native 

##1. Handlers reuse

It seems quite obvious that the code that would change the most would be the HTML/Native Components parts of the app. What actually surprised me was how well React abstracted the communication between Components. I barely had to adjust my top-level container/Component when taking it from web to native.

This means I reused most of the handlers with little to no modification even in the lower-level components. Usually I had to change the function calls pertaining to the “event” object since they behave differently on web/native platforms.

##2. Structure reuse (high level components stayed identical)

The component structure actually helped me transfer the app to native. I knew I could just take one module at a time with little to no problems.

Re-implementation was quite seamless since everything was written in javascript so things like state and state changes stayed the same. The same mindset was also apparent throughout the experience. Modularise when you need to, both because it makes sense (from a design perspective) but also because it’s necessary. As stated before the modularisation is done incrementally which is great for me, and people who like to hack away and then feel too lazy to refactor. React Components provide you with some APIs you can’t just ignore and creating a Component actually gives you an advantage, it’s not an empty refactoring excercise for the sake of it.

###3. Less context switches thanks to a unified API

We all know that context switches are very expensive actions, when developing as much as computationally. So less context switches are better. React actually made me code closer to the DOM. There were points where I just wanted to drop jQuery in to do some class toggling but as always, there’s an equivalent way that is more portable (to Native for example).



So there it is, if you haven’t used React to build anything, do it, it’s an interesting experience. Getting your answers isn’t as easy as when using jQuery but the lovely thing about React is being able to reason quite accurately and being able to hack in it. Incremental modularity is also great, especially when you are not sure of the scope of the project. Refactoring is done slowly but surely because it confers an advantage over having just the one javascript (jsx) file that does all the things. It’s great.

It’s not necessary for small projects but React plays nice with a lot of things so it’s plug and play :)

If you liked this and would like to hear more I tweet from [@hugo__df](http://twitter.com/hugo__df) and you would probably hear about anything I have an opinion on including my latest fad, Turbolinks :P not looking for controversy, and that’s a story for another day.