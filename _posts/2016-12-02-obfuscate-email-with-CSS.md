---
layout: post
title: "Obfuscate email with CSS."
date: 2016-12-02
comments: true
---
While creating this site, I wanted to add my e-mail explicitly to the list of contacts but not become a spam bot victim. Search results 
offered such solutions as HTML-encoding or JavaScript obfuscation. I opted for the CSS workaround since found it the most elegant: 
it changes text direction right to left. The trick works with the following code:

<script src="https://gist.github.com/elizavetasemenova/60446133a5f6e4a0a20e2d5f6757f013.js"></script>

Now apply it to any text on your page to make it written right to

<script src="https://gist.github.com/elizavetasemenova/89edcac7ec498af9319d8fee08163c9f.js"></script>

This will not work unfortunately for right to left scrips such as hebrew. Otherwise happy obfuscating!
