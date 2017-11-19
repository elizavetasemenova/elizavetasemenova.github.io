---
layout: post
title: Connectivity issues while teaching at a robotics worshop.
date: 2017-11-19
comments: true
---
Today I was mentoring a workshop, called “Build and program a drawing robot”. The party was thrown by a swiss non-profit organisation 
women++ (womenplusplus.ch), striving to increase diversity in tech. Two months ago I joined women++ by becoming a Board Member and can 
gladly report that things have been rolling nicely since then: three of us were accepted to teach a workshop at Machine Learning Days in 
Lausanne (https://www.appliedmldays.org/) in January 2018, we keep building multiple partnerships with educational and industrial institutions, 
we have done the planning for 2018 and are very excited about all the upcoming workshops - from hands-on tutorials on Blockchain to networking 
events and coaching sessions with recruiters.

But back to today’s robots! During the event participants were supposed to assemble their first robot and program it with JavaScript or 
Python to make a drawing. You can read more about the robot, Arduino-driven Mirobot, here: https://mime.co.uk/. The audience of the 
workshop was versatile - some people had extensive prior programming experience, some not at all. We tried to bring everybody under one 
umbrella with two brief presentations on JS (by Mila) and Python (by myself), specific to using them with the Mirobots.

Needless to say, the workshop was fun. Some troubleshooting was needed though, especially when it came to connectivity. In theory, it 
should be straightforward: once your Mirobot is turned on, you can find it among the WiFi networks and connect. Anyhow, when 20 Mirobots 
happen to be in the same room… which one is yours? At this point participants started connecting to random Mirobots and sending them
commands to move, while someone else in the room would suddenly notice their Mirobot moving and scream “Who is moving my Mirobot?!”. 
Ah, these Adults! :) Then a moment came, when laptops were not able to connect to Mirobots at all, literally saying 
“too many Mirobot connections”. So we had to connect all of the Mirobots to the common external WiFi, and then be fetching them 
individually from there.

<img src="/images/Mirobot_too_many.JPG" width="50">

Among tasks, we proposed participants to draw a square, a triangle, a polygon, a letter, their own name or the entire English alphabet. 
It was very entertaining to observe some experimental maths going on: people would not remember trigonometry too well, and would try to 
find out the lengths of lines by trying out, until it fits.

Except for drawing (moving), Mirobots can also beep. Coming back to the alphabet, Morse code would do as well!

One participant did not have a laptop with her and was controlling the Mirobot from her phone via the drag-and-drop menu: it works jst fine!

All Apps of the Mirobot have simulation mode: apps.mirobot.io. So, even if you do not have a robot at hand, you can practice programming 
it there. Here is what came out when I programmed it to write my name: 

<img src="/images/Mirobot_drawing.png">
