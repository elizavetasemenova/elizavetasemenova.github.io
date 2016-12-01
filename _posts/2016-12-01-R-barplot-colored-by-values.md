---
layout: post
title: "Barplot colored by vlaues, R code snippet."
date: 2016-12-01
comments: true
---

Barplot in R colored by values:
```R
for (t in 1:5){  n <- 100  y <- sample(1:5, n, replace = T)  y <- tabulate(y)  barplot(y)    col.seq <- seq(0.2,1,1/length(unique(y)))  col.seq <- col.seq[match(y, sort(y))]    cols <- alpha('mistyrose3', col.seq)     pl <- barplot(y,           col=cols,          border="mistyrose",          beside = T,          yaxt='n')    text(pl, min(y)/2, y,cex=1.2, pos=3, col='mistyrose4')  Sys.sleep(1)}
```      
