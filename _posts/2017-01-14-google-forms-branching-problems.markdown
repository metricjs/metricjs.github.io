---
layout: post
title: "Google Forms Branching Problems"
date: 2017-01-21
---
So I just made a Google Form, and it ended up being 35 pages long because the branching feature can apparently only handle one branching question per page.

The survey asks the user about all these different websites - whether they use them and if so, how. To make it easier on the user I wanted to make the first page ask the user if they used each of the websites, and choose which pages they went to from their responses. So, say the questions were:

- Do you use Google? Yes / No
- Do you use Bing? Yes / No

If the user selected "Yes" for both they would go to a page asking questions about Google and then a page asking questions about Bing. If they selected "Yes" for only one question they would only go to the relevant page, and if they selected "No" for both they wouldn't go to either. Makes sense? It does to me.

Google Forms can't do that. 

The easy way, probably, would have just been to have a page for each website and make the first question "Do you use...". Then, you would somehow tell the user (because I never assume all users will be able to extrapolate for themselves) that they don't have to answer the rest of the questions on that page if they answer "No" to the first one. But you can't add random text to pages, and I have quite a few questions on the pages about each site. I believe that if the user were to even glimpse all those questions on every page they would quickly think it was too much and give up. Even if the user doesn't use the first few websites and just clicks through those pages, seeing all those questions could be quite daunting.

So instead, I decided to separate my page of "Do you use..." questions (because, yes, I made them all before I realised this) into multiple pages, each with only one question. So now the user gets presented with a "Do you use..." page and if they select "Yes" they're taken to the relevant page of questions. If they select "No", or on submitting the page of questions about a site, they are directed to the next "Do you use..." page.

This works, but it's not as nice as I would have liked. It also means I have 35 pages instead of the 20 I had originally (there's a few extra pages) and the user has to click through a lot more pages, which makes them more likely to not complete the survey. It also makes the survey harder for me to manage, since all the pages are shown on one webpage when I'm editing it, and I now have to scroll a lot more to find anything.

So, my suggestions for Google: add some kind of question format that allows you to filter which pages the user will go to, not just one branch per page, and please add some kind of navigation to the editing page because all that scrolling is driving me insane!
