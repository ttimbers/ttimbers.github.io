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

To set up the docker image I installed Docker locally on my mac laptop following the instructions [here](https://docs.docker.com/engine/installation/mac/), and after installing, I launched the virtual machine, which is necessary to run Docker on Windows or a Mac, via the Docker Quickstart Terminal app. 
This opens a terminal window ready for you to work with Docker. You get a lovely little whale to great
you when its ready to go (can take a few minutes depending on the speed of your laptop).

~~~

                        ##         .
                  ## ## ##        ==
               ## ## ## ## ##    ===
           /"""""""""""""""""\___/ ===
      ~~~ {~~ ~~~~ ~~~ ~~~~ ~~~ ~ /  ===- ~~~
           \______ o           __/
             \    \         __/
              \____\_______/


docker is configured to use the default machine with IP 192.168.99.100
For help getting started, check out the docs at https://docs.docker.com

~.bash_profile read
pwd: /Users/user
$
~~~

I started out with the Docker image that Titus had introduced us to in his tutorial, `ubuntu:14.04`:

~~~
$ docker run -it ubuntu:14.04
~~~

Docker will first look locally for the image you asked to open, here, `ubuntu:14.04`. If you do not already have the Docker
image that you ask Docker to run on your local machine, it will automatically pull it from https://hub.docker.com if it exists there. If it can find an image, locally or remotely, it will run it and your terminal prompt will change to something like this:

~~~
root@dc52d3e95769:/#
~~~

This means you are in the Docker container and you can use it like any ubuntu machine. For example you can list all the files and directories in your current directory:

~~~
root@dc52d3e95769:/# ls
~~~

~~~
bin  boot  dev  etc  home  lib  lib64  media  mnt  opt  prettify  proc  root  run  sbin  srv  sys  tmp  usr  var
~~~

At this point the container is a pretty bare bones machine, and so I installed the necessary software via `apt-get`. For more details about what is happening at each step, please see [this great tutorial](https://www.digitalocean.com/community/tutorials/how-to-set-up-r-on-ubuntu-14-04) from Digital Ocean. Please note this took many minutes to do on a macbook pro with 8GB of RAM.

~~~
root@dc52d3e95769:/# sudo sh -c 'echo "deb http://cran.rstudio.com/bin/linux/ubuntu trusty/" >> /etc/apt/sources.list'
root@dc52d3e95769:/# gpg --keyserver keyserver.ubuntu.com --recv-key E084DAB9
root@dc52d3e95769:/# sudo apt-get update
root@dc52d3e95769:/# sudo apt-get -y install r-base
~~~

At this point my Docker container could run base R! 

~~~
root@dc52d3e95769:/# R

R version 3.2.4 (2016-03-10) -- "Very Secure Dishes"
Copyright (C) 2016 The R Foundation for Statistical Computing
Platform: x86_64-pc-linux-gnu (64-bit)

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.
~~~

Pretty cool! Since this took some time, and this would be a good base for many future projects, I wanted to stop here and save a "snapshot" of this machine as an image that I can use in the future. To do that I exited R as I normally would from the command line:

~~~
> q()
Save workspace image? [y/n/c]: n
root@dc52d3e95769:/# 
~~~

And then I exited the Docker container:

~~~
root@dc52d3e95769:/# exit
~~~

Then I commited that version of the image:

~~~
$ docker commit -m "installed base R" dc52d3e95769 r-base
~~~

Using the command `docker images` I could look at all the Docker images on my local machine and see that in addition to `ubuntu:14.04`, I now also had one named `r-base`.

~~~
$ docker images
~~~

~~~
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
r-base              latest              7aea148299d9        1 minutes ago       570.6 MB
ubuntu              14.04               07c86167cdc4        7 days ago          188 MB
~~~

If I wanted to open a container with R installed and start working, all I need to do now is ask Docker to run `r-base`: 

~~~
docker run -it r-base
~~~

~~~
root@5d124d665cd9:/#
~~~

Note that you now get a different Docker image number showing up after `root@`. This let's you save different versions or snapshots of the Docker container. But before I get into that, let me show you that this still has R installed:

~~~
root@5d124d665cd9:/# which R
~~~

~~~
/usr/bin/R
~~~

Pretty neat right? But I need more than just R to do my analysis, I need Make, and git and plink, plus some R packages. We can install Make and git in the same way we installed R:

~~~
apt-get install -y make git
~~~

To install the R pacakges, again I turned to the Digital Ocean tutorial that I pointed you to above. I did this from outside of R and it worked easy peasy for the most recent R packages. I haven't figured out how to install older versions of the R packages, so if you are reading this and know how, I'd love to hear from you!

~~~
root@5d124d665cd9:/# sudo su - -c "R -e \"install.packages('dplyr', repos = 'http://cran.rstudio.com/')\""
root@5d124d665cd9:/# sudo su - -c "R -e \"install.packages('fdrtool', repos = 'http://cran.rstudio.com/')\""
root@5d124d665cd9:/# sudo su - -c "R -e \"install.packages('plyr', repos = 'http://cran.rstudio.com/')\""
root@5d124d665cd9:/# sudo su - -c "R -e \"install.packages('SKAT', repos = 'http://cran.rstudio.com/')\""
root@5d124d665cd9:/# sudo su - -c "R -e \"install.packages('stringr', repos = 'http://cran.rstudio.com/')\""
~~~

Then I used git to clone my scripts and data to the container from Github:

~~~
git clone https://github.com/ttimbers/Million-Mutation-Project-dye-filling-SKAT.git /home/Million-Mutation-Project-dye-filling-SKAT
~~~

The last thing I needed to do was install plink. There's no `apt-get` for plink, and I had to install by downloading a compressed file from the developers website using `wget` and unzipping it. But before I did that, I needed to install `wget`: 

~~~
root@5d124d665cd9:/# apt-get install -y wget
root@5d124d665cd9:/# wget https://www.cog-genomics.org/static/bin/plink160224/plink_linux_x86_64.zip
root@5d124d665cd9:/# mkdir /usr/bin/plink/plink
root@5d124d665cd9:/# mv plink_linux_x86_64.zip /usr/bin/plink/plink
root@5d124d665cd9:/# unzip /usr/bin/plink/plink/plink_linux_x86_64.zip
~~~

Great, now plink is installed, and I can use it, right? Wrong! This type of install doesn't put Plink in the PATH, so I had to do this manually. The only way I found I could permanently do this was to modify the `.bashrc` file:

~~~
root@5d124d665cd9:/# echo PATH="/usr/bin/plink:$PATH" >> ~/.bashrc
root@5d124d665cd9:/# echo $PATH
~~~

~~~
/usr/bin/plink:/usr/bin/plink:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
~~~

Finally, I have all my dependencies, scripts and data installed in the container within which, I or anyone else, can run on any machine if Docker is installed. So lets save this image:

~~~
root@5d124d665cd9:/# exit
$ docker commit -m "environment, scripts and data for Timbers et al (http://dx.doi.org/10.1101/027540)" 48513b14be6c mmp-dyf-skat
~~~

The last thing I needed to do was to create a "tag" for the image and then push it up to https://hub.docker.com:

~~~
$ docker tag d7e5801bb7ac ttimbers/mmp-dyf-skat:latest
$ docker push ttimbers/mmp-dyf-skat
~~~

Now I have a container saved safely on https://hub.docker.com, and as I mentioned previously, I or anyone else, can run on any machine if Docker is installed. I think this is a really great tool for reproducibility if you need to run your analysis on multiple machines. 

* update: there is one dependency that I haven't gotten the install to work for yet and that is `gzcat`. Once I figure that out I will add it to the post. If you know how to install `gzcat` on ubuntu, please let me know.*
