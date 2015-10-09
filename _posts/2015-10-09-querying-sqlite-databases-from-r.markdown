---
layout: post
title: Querying SQLite Databases From R
modified:
categories: 
excerpt:
tags: []
image:
  feature:
date: 2015-10-09T09:35:00-06:00
---

Last week I wrote a 
[post](http://tiffanytimbers.com/building-a-basic-database-from-csv-files-using-sqlite3/) 
on how to build a basic database from a `.csv` files using SQLite, and today I finally 
got around to writing this short post on what to do next (*i.e.,* how do your data out of 
the database and into R). 

This task requires the R packages DBI and RSQLite (use `install.packages("PackageName")` 
to install). After opening R you must load these libraries:

~~~
library(DBI)
library(RSQLite)
~~~

First, you must connect to the SQLite database file. The extension can be either `.db` or
`.sqlite`, whichever you named the database file when you created it via SQLite. *Note - 
for this to work you must either set R's working directory to the directory where your 
database lives or provide the path to the database.*

~~~
con = dbConnect(SQLite(), dbname="mydatabase.db")
~~~

Next, you build your query (*i.e.,* describe what you want to grab from the SQLite 
database). In the query below, we will be grabbing the entire column named "strain" from /
the table named "behaviour" from the database we just connected to. 

~~~
myQuery <- dbSendQuery(con, "SELECT strain FROM behaviour")
~~~

After building your query, you can use that query to fetch the data from the database and
assign that to an R object, such as a dataframe.

~~~
my_data <- dbFetch(myQuery)
~~~

Now that the data is assigned the data to an object in R, it is advised to clear the 
query. With very large datasets, this can be import for avoiding the exhaustion of 
resources (memory, file descriptors, etc.).

~~~
dbClearResult(myQuery)
~~~

And that's it! Now a subset of the data you want is in an R object. When you are done
analyzing that aspect of the data, you can remove that R object and load the next
subset of the database you need to analyze.
