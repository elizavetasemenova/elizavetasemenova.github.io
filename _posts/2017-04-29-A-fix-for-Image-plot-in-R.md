---
layout: post
title: A fix for image plot in R.
date: 2017-04-29
comments: true
---

The ’image’ functionality in R is somehow counter-intuitive. Let us say, we want to visualise a matrix of values <i>m</i>. Applying <i>image(m)</i> will result in a plot corresponding to the transformation where the matrix is first transposed (rows become columns) and then the rows are flipped (first row becomes last, second becomes second to last and s on). To fix this behaviour and plot the given matrix as it is we need to apply the inverse transform, i.e. first reverse row numbers, then transpose the resulting matrix. 

<script src="https://gist.github.com/elizavetasemenova/e7386a54d10bda2bdd36618a0764a4ed.js"></script>
