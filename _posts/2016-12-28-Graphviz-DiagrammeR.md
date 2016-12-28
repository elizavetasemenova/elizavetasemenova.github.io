---
layout: post
title: "Graphviz functionality for R through DiagrammeR."
date: 2016-12-28
comments: true
---

<a href="http://www.graphviz.org/Home.php">Graphviz</a> is an open source software for graph visualization. It may be useful to display 
any object with connections, be they phisical or logical, such as networks and flowcharts. For this graphs should be described in 
the DOT-language.

Since I am currently going through simulation algorithms, it is really handy to have that diagram displaying relationships between 
various probability distributions in front of me. Here I can mark quickly which algorithms I have already implemented and which not. The
diagram was created with the <a href="http://rich-iannone.github.io/DiagrammeR/">DiagrammeR</a> package with the code presented below.

![](https://github.com/elizavetasemenova/Blog/blob/master/2016_12_28/graph.png)

<script src="https://gist.github.com/elizavetasemenova/22237673e871e76c009ae459be02df4f.js"></script>
