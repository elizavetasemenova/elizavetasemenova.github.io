---
layout: post
title: ''Nature in Code'' Remake: run string as code in R and Python.
date: 2017-02-19
comments: true
---

A while ago I read a book by Marcel Salathe 'Nature in Code', which was written to teach biologists how to code. Back then I found it interesting from my own end: it is good also for teaching coders/mathematicians some biology. Today, anyhow, a new perspective came...

The code for the book was originally written in Java Script. This language was chosen since it runs on modern devices without additional installations, plus it is the language of the web. Anyhow, nowadays most of the Life Science analysis and modeling is done in R and/or Python (at least my biased perception says so). 

Since I am going to re-read the book, I decided in parallel to be translating it into R and Python. And here I started phantasizing of creating an amendement to the course where students would have to complete tasks of two levels 1). manually translate codes in-between languages 2). write a macro, translating some basic constructions of one language into another: a string in language1 as input and a string in language2 as output.

If one had an R- or Python-code stored in a string and had to execute it, how could this be done?
The answer for R is in the following snippet:  

<script src="https://gist.github.com/elizavetasemenova/eb7489a140c2d624b6d7e51c6231d0f5.js"></script>


Since we want to become bilingual, here is the Python version:
<script src="https://gist.github.com/elizavetasemenova/899c546454937dd02ae344d275179556.js"></script>

I am planning to upload the translations, once they are ready, into the <a href="https://github.com/elizavetasemenova/NatureInCode_Remake">tri-lingual repository on GitHub</a>.
