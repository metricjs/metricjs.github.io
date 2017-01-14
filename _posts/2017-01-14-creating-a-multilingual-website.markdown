---
layout: post
title: "Creating a Multilingual Website"
date: 2017-01-18
---
I'm about to start on a new project - a web site that will hopefully serve as a hub for a gaming community I'm involved with - and one of the big things I'm having to learn is how to create a multilingual website. At the start, we only need English and Japanese, but this has caused several complications and required me to do a lot of research, which I've outlined below (partly for my own reference). 

**Finding a Translator**

The first problem was finding a translator for the Japanese content. Luckily, I have a friend who speaks Japanese so that was easy to solve.

**Designing the Site**

The next was how to design the site to allow for multiple languages. The two basic options here are to have multiple versions of every page, one for each language, or to have one version and populate all text from some resource (e.g. a JSON file) that contains the various translations. But both of these have their own problems.

Having multiple versions of the site, in the code base that is, would be a pain to maintain because every time we wanted to make any changes we would have to make them in multiple places. This is extremely inefficient and annoying and not something I want to do.

Loading the text from a JSON file would therefore be a much better option during development, since we can just have separate objects in the JSON file, or even separate files, for each language. I even found examples of this approach in use when I did my research. The problem with this approach though is that we will most likely use server-side rendering, and if the code on the server has to load all the text on a page from a JSON file every time someone requests a page, that's a lot of overhead. Especially if we also have some kind of templating engine, which we probably will.

So how to solve this? Easy, by combining the two.

In the end, I decided we needed to be able to load text from JSON files in the development version of the site, but have multiple versions on the server so there's minimal loading text from files. This allows for ease of development but also cuts down on overhead on the server. 

The next problem though, was how on earth to do this. This approach basically requires the ability to pre-compile some of the code in the development version to create page templates in the different languages, which are then put on the server with the rest of the code so the website can be rendered and sent to the client. I had no idea if that was even possible when I first thought of it, and it's taken a lot of research to find possible ways of doing this, but I think I finally have a solution.

One early solution I looked into was using Webpack to pre-compile the required HTML, mostly because the [html-webpack-plugin](html-webpack-plugin) looked like it might be useful for pre-compiling the HTML files. The main feature I was interested in was the ability to tell it the name of a file (the source for the HTML file to be pre-compiled) and some variables (the JSON file) and have it use that variable in the source file. However, I think I would need to mess with the configuration quite a bit to do what I want, so I was still on the look out for something easier.

While I was doing all this research, I also approached some friends and co-workers about the problem and asked for their advice. A co-worker agreed that Webpack could be useful, since I'm also already planning to use React, and suggested I look into [Este](https://github.com/este/este) a "starter kit for universal full–fledged React apps ... one stack for browser, mobile, server" which comes with some multlilingual support baked in. I'm still yet to properly look at Este however, because something else caught my eye.

Jekyll.

The first post on this blog mentions how people I know kept talking about Jekyll, which prompted me to finally try it out. One of those times Jekyll was brought up was jokingly as a solution to my problem with pre-compiling HTML files for the server. At the time I thought Jekyll was too simple and too geared towards static sites. However, now that I've created this blog and seen just want Jekyll can do, I'm starting to think it might actually be the best solution.

The reason I'm considering Jekyll is that it takes all your HTML (content and layout), CSS, JS and resource files and compiles them into one folder of simplified files. You can also specify which files to build and where to output the compiled files to, so I think I should be able to configure Jekyll to only compile the HTML and JSON files to generate a copy of the HTML files (which will probably require running build once for each language, but that's fine) for each language. I can then use these files on the server as templates for the more dynamic parts of the site.

Of course, I may yet be wrong. Jekyll may not do what I want. But it's a simpler solution than messing with Webpack so I hope it does. 

**Language Representation in the Site URL**

The last problem was how to structure the site files and therefore the URL to allow for multiple languages. A blog post I found - [Tips for Designing and Building a Multilingual Website](https://webdesign.tutsplus.com/articles/tips-for-designing-and-building-a-multilingual-website--cms-24708) by Tuts+ - outlines a few ways this can be done. In the end, I think I'll be using subdirectories (e.g. siteurl.com/en and siteurl.com/jp) as this is the easiest way to structure the site files and URL without messing with subdomains and such.

There's a section in that post about duplicate content, and identifying the preferred version of a page for each language. This helps search engines identify who a page is targeted at, and what other versions exist. The HTML looks like this (copied from the above linked page):

```
<link rel="alternate" href="example.com" hreflang="en-uk" />
<link rel="alternate" href="example.com/us/" hreflang="en-us" />
<link rel="alternate" href="example.com/au/" hreflang="en-au" />
```

Another thing to note from that post are the comments on ensuring whatever fonts you use support all the languages you need. The easiest approach is to use fonts that support all your languages, rather than switching fonts based on the language. But this could be difficult in my case where we may add more languages later on, so a font we choose early one may not support languages we add later. Luckily, because we will be compiling different versions of the site for different languages, it's possible we might be able to easily switch the fonts based on the language by naming them in the JSON files too.

They also mention localising dates, approaches to allowing the user to change the site language - using a drop down or flags - and how to automatically detect the user's language. They link to [Should You Ask the User or their Browser?](https://www.smashingmagazine.com/2013/02/remove-interface-elements/#language) by Smashing Magazine for more information on the latter. 

**Other Resources**

Finally, there are a couple other sites I've found that contain useful information I haven't had the chance to properly look at yet. These include:

- [13 Tips for Making Responsive Web Design Multi-Lingual - Responsive News](http://responsivenews.co.uk/post/123104512468/13-tips-for-making-responsive-web-design)
- [7 Tips and Techniques For Multi-lingual Website Accessibility - Nomensa](https://www.nomensa.com/blog/2010/7-tips-for-multi-lingual-website-accessibility)
- [Multi-regional and Multilingual Sites - Google](https://support.google.com/webmasters/answer/182192?hl=en)
