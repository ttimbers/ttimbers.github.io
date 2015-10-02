---
layout: post
title: Building a Basic Database From .csv Files Using SQLite3
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2015-10-02T13:40:55-07:00
---

### Motivation 

We finally finished collecting data from our high-dimensional behavioural analysis of 
40 *C. elegans* wild-isolates from across the globe and this week I was ready to dig into
the data - I am super excited to observe the diversity of behavioural profiles of 40 
genetically distinct strains for whom we have whole genome sequences!

This is a much bigger dataset than I usually work with, and for this analysis I am not
only interested in one particular behavioural aspect, I want to look at **everything**. 
Thus I found my usual strategy of importing all of my data directly into R did not work
with this 20 GB dataset... 

Do you need all your data in R at once? In my case, the answer is no, but I do want it all
connected together somewhere so I can grab various pieces of for each part of my analysis.
Thus I was motivated to create a database that I can query from R.

### Software and installation

I decided to use SQLite from the command line because it is simple to install and use and
I had been exposed to it previously at a [Software Carpentry](http://software-carpentry.org/) 
workshop. Here are the installation instructions for SQLite for each operating system, 
courtesy of Software Carpentry:

<div id="sql"> <!-- Start of 'SQLite' section. -->
  <h3>SQLite</h3>

  <div class="row">
    <div class="col-md-4">
      <h4 id="sql-windows">Windows</h4>
      <p>
        The <a href="{{site.swc_github}}/windows-installer">Software Carpentry Windows Installer</a>
        installs SQLite for Windows.
        If you used the installer to configure nano, you don't need to run it again.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-macosx">Mac OS X</h4>
      <p>
        SQLite comes pre-installed on Mac OS X.
      </p>
    </div>
    <div class="col-md-4">
      <h4 id="sql-linux">Linux</h4>
      <p>
        SQLite comes pre-installed on Linux.
      </p>
    </div>
  </div>
</div> <!-- End of 'SQLite' section. -->


### Creating a database in SQLite

To create a database in SQLite using the command line, open a Bash instance and navigate 
to the directory where you would like to have your database, then type:

~~~
sqlite3 mydatabase
~~~

You should then see the command line change to the following:

~~~
SQLite version 3.8.5 2014-05-29 12:36:14
Enter ".help" for usage hints.
sqlite>
~~~

This indicates that Sqlite is now running and you have created an empty database named
mydatabase (hopefully you name yours something more useful than this example).

### Putting a `.csv` file in your SQLite database

To add your `.csv` file as a table in the database you just created, your `.csv` must meet 
the requirement of being a tabular flat file. There are likely ways to input `.csv` files
that don't meet this requirement, but that is beyond the scope of this simple example.

You also need to know what delimiter is used in your `.csv` file. SQLite assumes it is a 
comma (`,`) but this is not always the case, and thus you can change that if necessary.

Before you add your `.csv` file to the database, it is best to create an empty table for 
your `.csv` file to go into. This is done using the CREATE TABLE function as demonstrated
below:

~~~
sqlite> CREATE TABLE behaviour(   
   ...> strain CHAR(8) NOT NULL,
   ...> plate CHAR(15) NOT NULL,
   ...> speed REAL
   ...> );
~~~

Using CREATE TABLE you should specify the name of each column in your `.csv` file, as well
as the type expected and whether or not NULL values are allowed for that column. The code
above creates an empty table called behaviour, with columns strain, plate and speed. To 
see the tables that exist in the database we created, we can type:

~~~
sqlite> .table
behaviour
~~~

To enter our data from our `.csv` file into this empty table, we first must change the 
mode to csv:

~~~
sqlite> .mode csv
~~~

And then specify the delimiter (my file had `\t` spacing instead of `,`'s):

~~~
sqlite> .separator '\t'
~~~

*Finally* we can add our data to the database using the import command and passing it the 
name of the file to import and the name of the table.

~~~
sqlite> .import behaviourdata.csv behaviour
~~~

And now the data is in a queryable SQL database. My next post will be how to access slices
of such a database from R.