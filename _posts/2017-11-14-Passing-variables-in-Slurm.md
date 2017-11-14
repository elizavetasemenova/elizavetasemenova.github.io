---
layout: post
title:  Passing variables in Slurm.
date: 2017-11-14
comments: true
---
Slurm is a job scheduler for Linux and Unix-like kernels, used by our university's computer cluster (https://scicore.unibas.ch/). Transitioning 
from the system that the cluster was using before, I first just used the dictionary of commands between two schedulers. Anyhow, on the first try
the Slurm job submissions did not take off. It turned out, that one needs to be careful with passing variables in Slurm and mind the  dot('.') versus 
underscore ('_') symbols. Below are the working bash commands, submitting my cmdstan (command line unterface for Stan) programs.

<script src="https://gist.github.com/elizavetasemenova/0d8a31a3e797307adb4e743b8dbc0cdb.js"></script>
