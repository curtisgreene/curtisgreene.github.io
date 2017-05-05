---
layout: post
title:  "What Even Is an AJAX"
date:   2017-05-5 08:16:01 -0600
categories: javascript ajax
---

When learning about common programming languages, patterns, and conventions, I always find myself asking the same two questions:

* ### What does it do? ###
* ### Why do I care? ###

Before I begin committing things to memory (or at least committing to bookmarking the documentation), I need to get satisfactory answers to these questions, particularly the latter. My most recent experience with this thought process kicked off when I was introduced to Ajax. In an effort to not bury the lede, let me say this right at the top: **You should definitely care.**


## What is Ajax? ##

![apple jacks](https://media.giphy.com/media/ell2hMOHGVeo/giphy.gif "Apple Jacks don't taste like apples")

Ajax is not a programming language, a tool, or a plugin -- It doesn't event taste like apples! -- its a concept. That's not to say that the implementation of Ajax doesn't add any concrete code to your program -- it definitely does -- but it doesn't introduce a new syntax or functions. It merely uses what Javascript has already built for us.

Ajax is the method of exchanging data with a server, and updating parts of a web page – without reloading the entire page. Any way you can implement that functionality in a JS application falls under the umbrella of Ajax.

Ajax stands for **A**synchronous **J**avaScript **a**nd **X**ML. These days, XML has almost entirely been replaced by the more friendly JSON, but the name stuck. Asynchronous means that events are happening independently from each other. An example of this in our context is a user can make a request to a server and while they are waiting to hear back from the server, they can continue to interact with the web application. No more page refreshes.

An ```XMLHttpRequest()``` where we render the response dynamically is Ajax.

A jQuery ```$.get("/some/path", function({})``` is Ajax.

And unsurprisingly, ```$.ajax({})``` is Ajax.

## What does Ajax do? ##

In today's online-landscape we take a lot for granted, but there was a time when having the content on the page change without reloading was revolutionary. Specifically that was in 2005 when Ajax was first introduced and widely acknowledged. An Ajax request means that we can send a request to the server and dynamically render what we get back using client-side scripts. Scripting on the client-side alleviates burden on your server. This means faster web applications. This means happier users. Good.

Ajax took a big step further about a year after its invention with the introduction of the jQuery library. jQuery is a Javascript wrapper that makes writing client-side code to navigate and manipulate the DOM super easy. jQuery is used to make asynchronous Ajax callbacks.

Ajax design and jQuery have become standards for the online ecosystem. Which brings us to the second question:

## Why should I care? ##

![male models](https://i.makeagif.com/media/1-23-2016/Io8PxS.gif "Logo Title Text 1")


Ajax is everywhere. Almost every modern web application in using Ajax design, either by directly using jQuery or through some other tool that was created in it's wake.

Here are a few features that we take for granted that Ajax makes possible:
* Draggable content
* Autocomplete/suggested searches
* Sliders
* Malleable Content
 * In-place editing
 * Infinite scrolling
* Submissions
 * Twitter
 * Reddit/forums

Long story short, now that you know what to look for, you'll start seeing Ajax or Ajax-like design all over the web.

Therefore, it's definitely worth learning about.

## Bonus Question: Any downsides? ##

Even though Javascript and Ajax have revolutionized the online landscape, they are also to blame for some of the [more annoying aspects](https://www.wired.com/2015/11/i-turned-off-javascript-for-a-whole-week-and-it-was-glorious/) of browsing the web in 2017. Nearly all advertisements are embedded using these tools. Every annoying widget that begs you to share the content on social media is a result of Ajax and Javascript. This leads us to broader, more philosophical questions that I leave for smarter people, but still an interesting consideration.

![apple jacks](http://media2.giphy.com/media/11o3buMsBCQsPm/giphy.gif "90s kids")
