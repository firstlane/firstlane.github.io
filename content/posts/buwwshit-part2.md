---
title: "Buwwshit Part2"
date: 2021-06-20T21:31:05-06:00
author: "firstlane"
---

In a previous post, I discussed Buwwshit, a tool my coworkers and I created to meme corporate-wide emails from the executive staff. The tool was rough, but it worked. You could copy/paste some text into it and it would spit out an uwufied version, while also unmasking any bullshit masquerading as corporate jargon.

I've taken a bit of time this weekend to work on the tool some more. In particular, another coworker had suggested adding the ability for the tool to take HTML input and spit it back out with just the words buwwuified, leaving other non-text tags alone. That way you could right-click an email in Outlook to view the source, paste it into the tool, and get the buwwuified version with all the original formatting. This functionality was my main focus.

I started by looking at [bullshit.js](https://mourner.github.io/bullshit.js/) to see how it replaces text content on a page. bullshit.js functions by going through all the text on a page and replacing any corporate words with the word "bullshit" (where the corporate words are pulled from a predefined list of terms). To do this, it depends on a library called [findAndReplaceDOMText](https://github.com/padolsey/findAndReplaceDOMText). As the name implies, it allows you to search for specific text and replace it, but only within the actual text content of a page.

I pulled this in as a dependency for Buwwshit and started work on integrating it. The library has one function that we are interested in:

```
findAndReplaceDOMText(documentNode, options)
```

`documentNode` is the particular node of our DOM that we are interested in. For our purposes, we want everthing in the DOM, so we can just call `getRootNode` here.

`options` is a struct with several fields that we can set. The ones we care about are:
* `find`: a string or regex we want to search for in the document text
* `replace`: a string that will replace any occurrences of the value specified in `find`. Alternatively, we can pass a function to be called on every match.

We want to pass our functions `uwuify` and `revealBullshit` to `findAndReplaceDOMText` to do our text replacement on *any* text matches. To match all text, we can just pass `/.+/` (`findAndReplaceDOMText` will only work with non-empty matches). We end up with something like the following:

```
findAndReplaceDOMText(doc.getRootNode(), {
    preset: 'prose',
    find: /(.|\n)+/,
    replace: revealBullshit
});

findAndReplaceDOMText(doc.getRootNode(), {
    preset: 'prose',
    find: /(.|\n)+/,
    replace: uwuify
});
```

To test this, I hopped onto my company email, grabbed one from the CEO, and pasted the HTML source into the tool. I took the output and put it into a test HTML file and opened it in a browser to see the result. It was wonderful! I can't share this particular example, but here is an [alternative](../../static/the&#32(runs&#32away)&#32Facebook&#32Company&#32Is&#32Nyow&#32Meta.html).

That's all I've got for this post. You can find the tool [here](https://firstlane.github.io/buwwshit/). Go find some nice, juicy corporate jargon and see how it transforms.
