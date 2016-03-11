---
layout: post
title: Using Docker for Reproducible Research
excerpt: "In my reproducible research toolbox, there are several tools that I routinely use. These include, R & Python, the Bash Shell,
Make and Git."
modified: 
categories: 
excerpt:
tags: [science]
image:
  feature:
date: 2016-03-11T13:24:49-08:00
---

In my reproducible research toolbox, there are several tools that I routinely use. These include, R & Python, the Bash Shell,
Make and Git. Although I have had Docker sitting in my toolbox since Titus Brown introduced me to it via [this tutorial](http://angus.readthedocs.org/en/2015/week3/CTB_docker.html)
during [week 3 of #NGS2015](http://angus.readthedocs.org/en/2015/week3.html) at the Kellogg's Biology Station last summer, I 
have yet felt the need to use it.

Why had I not reached for Docker yet? Well, although I have been developing [this](https://github.com/ttimbers/Million-Mutation-Project-dye-filling-SKAT) complex analysis pipeline for whole-genome 
rare-variant association analysis, my development primarily depended on me using my laptop. I did not have to run the analysis
on other computers, and so the software and package environment stayed fairly stable. It wasn't until my computing demands
drove my beyond my laptop's capabilities, to having to work on a remote machine, that I immediately saw the utility and finally
reached for Docker.

Why did I reach for Docker now? Well to work on the remote machines, I needed to install four different pieces of software
and 5 different R packages. To ensure that my research would be reproducible from machine to machine, I wanted to same versions
of these that I had working on my laptop. Doing this manually once or twice, might be OK, but if I had to do this anymore times
than that, I would likely run out of patience. And since I am not sure which remote machines are going to best for my next
piece of analysis, this is a likely scenario I might run into as I test out different machines. Additionally, if I built a 
Docker image for the environment used to run my analysis, this would facilitate anyone else who wanted to reproduce my 
analysis in the future (including future me).

