---
layout: post
title: "React - To JSX or not to JSX"
date: 2017-01-15
---
I strongly dislike JSX. (I originally typed “hate” but that's just too strong a word.) I can see some uses for it but, as a friend recently said, “I just want JS that looks like real JS”. 

My first introduction to React was only in November or December of 2016, when someone at work suggested it might be useful for a project of mine. This, of course, meant that the first example React code I saw used ES6 and JSX. 

I didn't like it.

My problems with ES6 are minor and specific (mostly I don't like classes), but one glance at JSX code and I almost gave up on React. 

It looks wrong, and it feels risky.

Have you ever participated in a debate over innerHTML versus createElement? I have, a couple times. People argue that using innerHTML makes your code easier to read, it's less lines of code, it's easier to know exactly what output you'll get, etc. I disagree. 

Why are people so fond of putting HTML in their JS? You're writing JS, stick to JS. I personally don't like having to mentally switch languages when I'm reading code, just because someone decided to use innerHTML on several lines of stringified HTML. The only times I use innerHTML are to add text to an existing element (e.g. adding a label to a button), to do something that's painful use JS (e.g. some properties of some elements), or to get the HTML from something. I don't ever create elements using innerHTML. 

I guess my other argument against using innerHTML is that it's too easy to screw up. People are stupid, and only human. If you write bad createElement code JS will hopefully yell at you. If you write bad HTML and inject it into the DOM, I'm pretty sure the chances of the browser just trying to render it anyway are much, much higher.

So yes, sometimes my code is longer than it would be if I'd used innerHTML, sometimes it can look a bit complex, and sometimes it can be harder to understand what's happening. But at least I'm not directly injecting (potentially bad) HTML into the DOM.

When I started looking at React, I quickly started equating JSX to innerHTML and traditional React using React.createElement to JS’s createElement. This is most likely not a perfect comparison - I hope that React is more likely to yell at you for bad JSX than if you used innerHTML - but I prefer the createElement methods for similar reasons. Not only does JSX require switching languages in the middle of code, but it introduces those HTML injection problems I would like to avoid.

The only situation I can think of where I wouldn't mind JSX is if a page’s, or even site's, whole JS was contained in a HTML file. That is, the JS was in a script tag in the head or body. In that case, you already have HTML in the file, you're most likely going to have more HTML than JS, and the page or site is probably simple enough that injecting bad HTML isn't a massive problem. Then sure, use JSX. But if not - if your JS is in a separate file, etc. - nope. 

Now, maybe I'm wrong. JSX is hopefully much less fraught with danger than innerHTML is, and perhaps my worries about HTML injection are unfounded. But even if that is the case, to me it still looks wrong to have HTML in my JS code. And I feel like using JSX is a slippery slope towards more people using innerHTML. So, no, I won't be using JSX any time soon. Maybe you should think about doing the same?
