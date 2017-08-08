---
layout: post
title:  C++ easily compiled in the cammand line.
date: 2017-08-08
comments: true
---

"Compiling C++ is easy!", - my terminal said this morning. You can get yours to do the same in under 5 minutes as well after reading this blogpost. 

C++ has the fame of being intricate and hard to start with for people coming from R, Python, JavaScript, Matlab, Matematica, SAS - you name it. Indeed, it is much more strict and less forgiving than all the languages listed above. Anyhow, the speed-ups that it offers are unprecedented and are worth going through the pain of learning. Let's concentrate on compiling our first program.

To begin with, we need to create the C++ code itself (see below). After navigating to the directory with the code, compile with

<b>g++ -Wall first_compile.cc -o first_compile</b>

where 'first_compile.cc' and 'first_compile' are the names of the input and output files, respectively. Now run the program with

<b>./first_compile</b>

Here is the code that gets you started:
<script src="https://gist.github.com/elizavetasemenova/6b89a0a9ccc9337dbbd4faf4a83114af.js"></script>

Now we can compile away and develop some high performance routines.

