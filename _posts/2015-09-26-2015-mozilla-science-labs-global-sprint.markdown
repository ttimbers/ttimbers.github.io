---
layout: post
title: 2015 Mozilla Science Lab's Global Sprint
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2015-06-07T20:29:46-07:00
---
date: 2015-06-07


Last Thursday and Friday I participated in the 
<a href="https://www.mozillascience.org/global-sprint-2015">Mozilla Science Lab's Global 
Sprint</a> at Mozilla's office in Vancouver. A sprint (or hackathon) is an event where 
people gather together to contribute intensively and collaboratively on software projects.
This year, Mozilla's Global Sprint spread across 2 days, with researchers from 10 
different countries working on ~ 44 open source science and/or education projects between 
the hours of 9am - 5pm in their respective time zones. This resulted in ~ 50-70 
researchers at any given time working on these projects for ~ 53 hours consecutively! 
A list of the contributors and the software products we worked on can be seen in the 
<a href="https://etherpad.mozilla.org/sciencelab-2015globalsprint">planning etherpad</a>.

<p>This was the first sprint/hackathon that I ever participated in and I wasn't really sure
what to expect. When I arrived, the site host, Mozilla's Community Manager - 
<a href="https://github.com/BillMills">Bill Mills</a>, helped me connect to the community
IRC chatroom so I could chat with all the other researchers participating at the sprint, 
directed me to projects I could help on (I chose to help with
<a href="https://github.com/goyalsid/phageParser">phageParser</a>), as well as connected
me to the project lead, Madeline Bonsma, via video conference so we could discuss how I 
could help. Two others at the Vancouver site, 
<a href="http://www.daisieirishuang.com/">Daisie Huang</a> and Evan Morien, jumped in 
with me on the project and together we submitted two pull requests with two perl scripts 
which (hopefully) helped move the project forward. 

<p>At the sprint, I also ran into <a href="http://sjackman.github.io/">Shaun Jackman</a>,
who was leading development on <a href="http://brew.sh/">Homebrew</a> at the sprint. 
Homebrew is package manager for Mac OS X, which essentially helps you install stuff that
you need that Apple didn't. In my research, I utilize a scientific software package called
the <a href="http://sourceforge.net/projects/mwt/">Multi-worm Tracker</a> to analyze the 
behaviour of a microscopic nematode worm, C. elegans. This very useful software, developed
by Rex Kerr, requires that I pass Java a .jar file for every file that I want to analyze. 
This is very annoying when writing scripts that I want to share with other researchers as 
everyone seems to install this .jar file in a different place on their computer, thus the 
path to the .jar file has to be set on every machine. At the sprint, Shaun showed me that 
you can write a shell script that calls the .jar file, and place that shell script in the 
executable PATH so that you no longer need to specify where the .jar file is on the 
computer. EXTREMELY helpful for me! 

<p>Further, because I collaborate with a lot of people who are only vaguely familiar with 
the shell, he also helped me build a Homebrew formula for the Multi-worm tracker. Now by 
copying two lines of code in the Shell (which is the same on any OS X or Linux machine) my 
collaborators can use Homebrew to automatically generate the necessary shell script to put 
the .jar file call in the executable path. I have already adopted this for two analysis 
projects I am working on: 
<a href="https://github.com/ttimbers/IBRO/tree/master/Habituation_probability"> analyzing
reversal probability</a> and 
<a href="https://github.com/ttimbers/MWT_Locomotion_summary_analysis">basal locomotion</a>.

<p>My next challenge is to find/make something this easy for my collaborators who use 
Windows. I welcome any advice/helpful hints to do this from anyone familiar with this. I 
really care about cross-platform compatibility to make sharing as easy as possible. I 
think the easier it is, the less barriers there are for code re-use and collaboration. 

<P>All and all, I found the sprint super fun, and I learned a ton. Many thanks to the 
Science Lab for organizing, Bill Mills for being an awesome host at the Vancouver site,
and the super fun atmosphere created by the Vancouver participants (Daisie Huang, 
Andrew MacDonald, Shaun Jackman, Evan Morien and Andy Teucher). Next year I am hoping to 
participate as a project lead to make some more progress on further developing the open 
source, Multi-worm tracker software with the goal of making it more user friendly and 
standardizing analysis pipelines. 
