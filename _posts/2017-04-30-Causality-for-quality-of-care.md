---
layout: post
title: Study of causalities within a framework for assessment of quality of care. 
date: 2017-04-30
comments: true
---

All PhD students at out institute are inclined to volunteer for general tasks, which arise on regular basis. They do not belong to the project work, but bring benefits to the institute in one or another way. Some of the tasks are excellent time wasters. By the moment when they come up, you really do not want to have the fame of someone who never volunteered before. With this in mind, once an interesting activity appeared on the horizon, I rushed to express my willingness to help. The task comprised some work for SCIH (Swiss Centre for International Health). Surprisingly, this work not only covered me with volunteering for a long time, but, not less importantly, allowed me to learn about the assessment of quality of care, which can not hurt an epidemiology PhD. Furthermore, as a quantitative person, I was allowed to play with the available data and extend the existing analyses with some quantitative observations.

<b>A framework for assessment of quality of care.</b>

Quality of care is the level of provided health services, measured by its ability to achieve desired health outcomes and being up-to-date with the current standards of care. Whether a desired outcome was achieved, is determined by the recipients of the services.  It is not straightforward to derive one single measure to assess the quality of care. An appropriate framework was laid out by Donabedian (1988). He conceptualised a model with three dimensions: structure, process and outcome. This framework has become an operational definition.
   
Within this framework the <i>structure</i> dimension aims to evaluate the attributes of the setting <i>where</i> the service is being delivered and includes characteristics of a physical setting, available material, as well as human- and financial resources, qualifications of the care providers and organisational structure. 
  The <i>process</i> dimension focuses on the care that is delivered to patients, such as provided services and treatments and assesses whether good medical practices are followed. This includes patient’s comfort, hygiene and treatment. 
   The <i>outcome</i> variable reflects the impact of care on health status. It may also involve improvements in patient’s awareness and behaviour. Outcomes are thereby considered a consequence of the quality of care, as for example survival and recovery of a patient or more indirectly patient satisfaction.
  The three-component approach suggests that quality of care can be improved, since structure influences process and process influences outcome. The expectation behind the applications of the model is that, given the outcome dimension is credible, it should be possible to demonstrate that differences in outcome will be caused by changes in the process and structure. A known drawback of the Donabedian model is, anyhow, the difficulty in determining precise relationship between the three dimensions, as well as distributing health care factors between dimensions, since overlaps may exist.

<b>Causal inference.</b>

The available data arises from the studies in two countries, where the quality of care is of great concern. Observations with respect to the all three dimensions were made and additive indices computed. This resulted into corresponding scores for infrastructure, clinical observations and patient’s satisfaction. I have applied the <i>pcalg</i> R-package to reveal data-based causal structure between the three dimensions. 


The resulting structure is displayed below and shows that the algorithm, as well as the classical correlation, linked clinical and exit scores, but was not able to define the direction of this link. It is logical to assume, that the direction is from clinical score to the exit score since exit score is unlikely to influence clinical score.

References.

1. Donabedian, A. (1988). "The quality of care. How can it be assessed?" JAMA 260(12): 1743-1748
2. Kalish et al, "Causal Inference Using Graphical Models with the R Package pcalg". Journal of Statistical Software

<script src="https://gist.github.com/elizavetasemenova/3a7f6d5bcf8647d517cca99073b68867.js"></script>
