---
layout: post
title: Intro to using MD5 to check file transfers
excerpt: "As with anyone who copies large files, our lab has been having some issues with files being corrupt after copying."
modified: 
categories: 
excerpt:
tags: [science]
image:
  feature:
date: 2016-03-04T13:24:49-08:00
---

As with anyone who copies large files, our lab has been having some issues with files 
being corrupt after copying. To help deal with this I wrote this short tutorial to get 
people started on using the `MD5` command line tool to solve this problem. This tutorial
was written for MacOSX, but you can do this on Linux using the `md5sum` tool instead. This
tutorial was also written with the tool webdav in mind, as this is what our lab currently
uses to backup files, but you can use the MD5 hash to compare any files anywhere locally 
or remote.

This tutorial lives on Github [here](https://github.com/ttimbers/MD5_check_with_webdav), 
please send any edits to improve it as pull requests to that repo. 

# How to check if your files copied correctly to webdav using the MD5 hash

Sometimes when files are copied from your local computer to webdav mistakes are made and 
the copied files are corrupt/damaged and not useable. This can be hard to tell with a 
quick glance, especially if we have transferred a large number of files and left to have a 
coffee while this happened. What we can do after the file transfer to check that the files
copied correctly is to look at the MD5 hash between two files (the original and the copied
file) and check that they are the same. 

What is a MD5 hash? The MD5 hash for a file is a calculated 128-bit value for that file
which can act like a finger print. Each different file should have a different MD5 hash, 
unless the files are identical (i.e., copies of eachother). You can think of it as a file
fingerprint. Like a human fingerprint, there probability of getting two identical MD5 
hashes from two different files is extremely low. So we can use this feature for comparing 
the files and their integrity control while copying.

In this quick tutorial you will learn:

* How to copy files from your local machine to webdav via the command line

* How to get the MD5 hash from the original and copied files so that you can check if they were copied correctly

## Copying files to webdav via the commmand line

* We'll start with the example of copying a single file. First, connect to webdav as you 
usually do.

* Open a new Bash Shell (e.g., terminal on your Mac or Linux Machine, or Gitbash on your 
Windows machine) and use the `cp` command to copy the file. A simple way to do this is to
type `cp` in the command line then a " " and then drag the file from Finder or Explorer 
into terminal/Gitbash. Next drag the webdav folder that you want to copy it to from 
Finder or Explorer into terminal/Gitbash. Press enter to run the command. The command you
run should look something like this:

~~~
cp /Users/tiffanytimbers/Desktop/Afzelius1976.pdf /Volumes/leroux-lab-files/Tiffany_Timbers/pdfs
~~~

If you want to copy multiple files, you can drag in multiple files to the command line 
from your local machine and the the folder on webdav that you want to copy them to. For
example:

~~~
cp /Users/tiffanytimbers/Desktop/Afzelius1976.pdf /Users/tiffanytimbers/Desktop/Bacon_1998.pdf /Volumes/leroux-lab-files/Tiffany_Timbers/pdfs
~~~

If you dont want to drag everything but want to copy everything from one folder on your 
local machine to a folder on webdav with the same name you would type `cp` as well as the 
`-a` flag to mean "all files" and then drag in the folder you want to copy from your local
machine, then drag in the folder you want to copy to. If that folder doesn't exist yes, 
you have to add that to the end of the path. 

Below we copy a folder called `2007_pdfs` from our local machine to webdav. We want to put 
this folder into the folder named `pdfs`, but inside `pdfs` there is no folder named 
`2007_pdfs`. So we have to drag in the `pdfs` folder from webdav and then add `2007_pdfs`
to the end of the filepath:

~~~
cp -a /Users/tiffanytimbers/Desktop/2007_pdfs/ /Volumes/leroux-lab-files/Tiffany_Timbers/pdfs/2007_pdfs
~~~

## Checking the MD5 hash from the original and copied file via the command line

Now that the files are on webdav we can test if they copied correctly. To do this we use 
the `MD5` command to look at the MD5 hash. To get the MD5 hash of the first .pdf file we 
copied we type:

~~~
MD5 /Users/tiffanytimbers/Desktop/Afzelius1976.pdf
~~~ 

and we get the following as output:

~~~
MD5 (/Users/tiffanytimbers/Desktop/Afzelius1976.pdf) = 5dc399fc6f64b608e4995f77db41995e
~~~

`5dc399fc6f64b608e4995f77db41995e` is the MD5 hash for `Afzelius1976.pdf` and is unique to
that file. Let's now look at the MD5 hash for the copy of `Afzelius1976.pdf` on webdav:

~~~
MD5 /Volumes/leroux-lab-files/Tiffany_Timbers/pdfs/Afzelius1976.pdf
~~~

we get the following as output:

~~~
MD5 (/Volumes/leroux-lab-files/Tiffany_Timbers/pdfs/Afzelius1976.pdf) = 5dc399fc6f64b608e4995f77db41995e
~~~

We can see that `5dc399fc6f64b608e4995f77db41995e` = `5dc399fc6f64b608e4995f77db41995e` 
and so we know that the file copied correctly.

To get the MD5 hash for many files in a directory we can use a wildcard to match all files
as follows:

~~~
MD5 /Users/tiffanytimbers/Desktop/2007_pdfs/*
~~~

we get the following as output:

~~~
MD5 (/Users/tiffanytimbers/Desktop/2007_pdfs/Sieburth et al 2007.pdf) = 45e55165d940196274b1e8d11ad078d3
MD5 (/Users/tiffanytimbers/Desktop/2007_pdfs/Sossin 2007.pdf) = 96948bdc62e7d0d723976b5f13b7998a
MD5 (/Users/tiffanytimbers/Desktop/2007_pdfs/Speese et al 2007.pdf) = 3c9585eb5756733504d5f9eab251502e
~~~

Now you know how to copy files to webdav via the command line as well as how to check if 
the files copied correctly. 