---
layout: post
title: Write an R package in one line.
date: 2017-04-19
comments: true
---

"This world would be a better place if we invested more in developing cleaner software and smarter algorithms, not writing longer papers.", - said I after a day of unproductive writing attempts. The concept of clean software includes packaging several routines and functionalities together, making them easy to re-use. 

Now, beyond lyrics: I have put together a wrapper-script for myself, which creates an R-package from the raw source code in one line. As proof of concept, I used the code to create a package out of itself. It is called 'packageR' and you can also  install it from my GitHub repository:

<script src="https://gist.github.com/elizavetasemenova/eb330be06bb6df9fe83cbe456ca8df22.js"></script>

The help page should be displaying information about the <i>create_package</i> function. Use <i>?update_package</i> during the development process when you want a change to become effctive. Now all is set for happy packaging! 

