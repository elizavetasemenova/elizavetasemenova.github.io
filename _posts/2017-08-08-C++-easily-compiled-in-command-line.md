---
layout: post
title:  C++ easily compiled in the command line.
date: 2017-08-08
comments: true
---

"Compiling C++ is easy!", - my terminal said this morning. You can get yours to do the same in under 5 minutes as well after reading this blogpost. 

C++ has the fame of being intricate and hard to start with for people coming from R, Python, JavaScript, Matlab, Matematica, SAS - you name it. Indeed, it is much more strict and less forgiving than all the languages listed above. Anyhow, the speed-ups that it offers are unprecedented and are worth going through the pain of learning. For now, let us concentrate on compiling our first program.

To begin with, we need to create the C++ code itself (see below). After navigating to the directory with the code, compile with

<b>g++ -Wall first_compile.cc -o first_compile</b>

where <em>'first_compile.cc'</em> and <em>'first_compile'</em> are the names of the input and output files, respectively. Now run the program with

<b>./first_compile</b>

Alternatively, we can create a shell script called <em>'first_compile.sh'</em> and list both the compillation and execution commands in it (see below). Then it suffies to type

<b>sh first_compile.sh</b>

in your command line.

Here are the code, that gets you started, and the corresponding shell script:
<script src="https://gist.github.com/elizavetasemenova/6b89a0a9ccc9337dbbd4faf4a83114af.js"></script>

Now we can compile away and develop some high performance routines in C++!

