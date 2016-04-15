---
title: "dplyr + postgres"
author: "nabil Abd..."
date: "April 14, 2016"
output: html_document
---



## Introduction

For my work, I often deal with large files. Relatively large. Like up to a 
couple of gigabytes. It usually isn't a big deal waiting for them to load into 
memory, but it can get a little boring twiddling my fingers waiting sometimes, 
or having to worry about how to manage my 8Gb RAM. 

Based on a more general suggestion I recently received, though, I decided to 
get my feet wet into a part of `dplyr` I'd been holding back from: interfacing 
with data from databases.

I mean, the dplyr works [really smoothly with SQL](http://www2.stat.duke.edu/~cr173/Sta523_Fa14/slides/2014-10-20-dplyr_sql.html#1), and it's not hard [to get started](https://cran.r-project.org/web/packages/dplyr/vignettes/databases.html). But it might, especially for someone new to the everything other than the `SELECT`- statement syntax of SQL, such as setting up servers. 

Turns out that setting up the database [isn't too hard]([to get started](https://cran.r-project.org/web/packages/dplyr/vignettes/databases.html)), as long as it's the right one. Although set-up for interfacing `R` with `SQLite` is close to nil, that's not the case with all flavors of SQL. Still, it shouldn't be too hard, if you've done it before. But I hadn't, and it seemed [I wasn't the only one](http://stackoverflow.com/questions/29134755/create-postgres-database-with-r). Since `Postgres` apparently has the best mix of thorough documentation and 
ease-of-interface with `R`, as well as functionality for data manipulation, I 
thought I'd finally figure out how to set it up.

In the process of working and wading through content from different sources, it often helps me to document my steps, at least for myself if I ever need a reference. And by posting this online, perhaps it could be of use to someone else as well. 



## Preliminaries

To be clear, this is still a work in progress (at least until this line is crossed out after the document's completion). For anyone seeking to follow along, there are a few things which you might have helpful.

### Software Set-up

In terms of software, 

1. I'm using the command line tool `brew` to download and install `Postgres`. (i.e., by `brew install postgres`). If you have a Mac but don't have Homebrew, you might want to start using it. 
2. The following assumes setting up the database is with the `psql` command. For now, I'd like to work with the command line before adopting the `Postgres.app` GUI.

System and R-package information is at the end of the document.


### Setting up the Server

By now, you should have `Homebrew` and `Postgres` installed. 

First, see if you can [initialize a new database](http://www.postgresql.org/docs/current/static/tutorial-createdb.html) by running the command: `createdb mydb`. If you can, great! If you can't (like with me), then you might need to [start the database server first](http://www.postgresql.org/docs/current/static/server-start.html). Not sure how one's in the first chapter and the other in the seventeenth, though, but [that's how it's arranged](http://www.postgresql.org/docs/9.5/static/manage-ag-createdb.html).

Here, following the instructions in that latter link should set up a local Postgres server, so on your own machine (i.e., as opposed to a remote one). If you're not looking to work intensely with the database, then you may not need to set up another server later on. 

By this point, if everything is working well, you shouldn't have any error messages come up by running a command such as: `createdb mydb`. 

Congratulations, you have now already set up a database server, and initialized a database! Now to put data into it. 


### Loading the Data

To load data into a database, one has to first tell the database the format the 
table should be in. This means that you have to say beforehand what column names to expect, as well as the data types each of those columns contains. 

To tell the format of the data, can use `psql -f MY_SCHEMA.sql` which 

To load the data after the format has already been specified is [less involved ](http://www.postgresguide.com/utilities/copy.html).


##


```r
library(devtools)
dev_mode()
```

```
## Warning: /Users/nabilabd/R-dev does not appear to be a library. Are sure
## you specified the correct directory?
```

```
## Dev mode: ON
```

```r
library(dplyr)
```

```
## 
## Attaching package: 'dplyr'
```

```
## The following objects are masked from 'package:stats':
## 
##     filter, lag
```

```
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```




## 



## Conclusion



```r
session_info()
```

```
## Session info --------------------------------------------------------------
```

```
##  setting  value                       
##  version  R version 3.2.4 (2016-03-10)
##  system   x86_64, darwin13.4.0        
##  ui       X11                         
##  language (EN)                        
##  collate  en_US.UTF-8                 
##  tz       America/New_York            
##  date     2016-04-15
```

```
## Packages ------------------------------------------------------------------
```

```
##  package    * version    date       source                        
##  assertthat   0.1        2013-12-06 CRAN (R 3.2.0)                
##  DBI          0.3.1.9008 2016-04-10 Github (rstats-db/DBI@998f573)
##  devtools   * 1.10.0     2016-01-23 CRAN (R 3.2.3)                
##  digest       0.6.9      2016-01-08 CRAN (R 3.2.3)                
##  dplyr      * 0.4.3.9001 2016-04-05 Github (hadley/dplyr@053a996) 
##  evaluate     0.8.3      2016-03-05 CRAN (R 3.2.4)                
##  formatR      1.3        2016-03-05 CRAN (R 3.2.4)                
##  knitr      * 1.12.3     2016-01-22 CRAN (R 3.2.3)                
##  magrittr     1.5        2014-11-22 CRAN (R 3.2.0)                
##  memoise      1.0.0      2016-01-29 CRAN (R 3.2.3)                
##  R6           2.1.2      2016-01-26 CRAN (R 3.1.3)                
##  Rcpp         0.12.4.3   2016-04-10 Github (RcppCore/Rcpp@6294a50)
##  stringi      1.0-1      2015-10-22 CRAN (R 3.2.0)                
##  stringr      1.0.0      2015-04-30 CRAN (R 3.2.0)                
##  tibble       1.0-1      2016-04-05 Github (hadley/tibble@cb38672)
```



