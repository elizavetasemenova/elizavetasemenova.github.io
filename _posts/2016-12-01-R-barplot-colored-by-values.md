---
layout: post
title: "Barplot colored by vlaues, R code snippet."
date: 2016-12-01
comments: true
---

Barplot in R colored by values: by varying intensity of a color, highlight bars with larger values with more intense colors.
Would be too boring not to animate.
{% gist 6f0c98313fe78079f272bc03e0fe3d73 %}  

```ruby
for (t in 1:5){  
  n <- 100  
  y <- sample(1:5, n, replace = T)  
  y <- tabulate(y)    
  col.seq <- seq(0.2,1,1/length(unique(y)))  
  col.seq <- col.seq[match(y, sort(y))]    
  cols <- alpha('mistyrose3', col.seq)     
  pl <- barplot(y,           
                col=cols,          
                border="mistyrose",          
                beside = T,          
                yaxt='n')    
   text(pl, min(y)/2, y,cex=1.2, pos=3, col='mistyrose4')  
   Sys.sleep(1)}
```
