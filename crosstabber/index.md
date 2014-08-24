---
title       : Presenting Crosstabber
subtitle    : An easy to use application for real world data
author      : Elin
job         : 
framework   : io2012        # {io2012, html5slides, shower, dzslides, ...}
highlighter : highlight.js  # {highlight.js, prettify, highlight}
hitheme     : tomorrow      # 
widgets     : []            # {mathjax, quiz, bootstrap}
mode        : selfcontained # {standalone, draft}
knit        : slidify::knit2slides
---
## The Problem

We want beginning sociology students to engage in real data analysis but ...

- Big statistical packages are too complicated; we end up teaching software not sociology.
- Many online applications are also complicated.
- Other online applications are easy but they don't give the micro data we need for what we are teaching.
- We don't want to use artifical or mini data sets.
- Many of the best applications for students are too old to run one modern browsers, new operating systems or mobile devices.
- Spreadsheets can do a lot but they won't work with large datasets and are really poor for crosstabs, which are a core tool in sociology, especially for beginning students.

We need an open source solution where instructors can supply their own data in a way.
It needs to be easy for students and pretty easy for faculty too. 

--- .class #id 

## The Solution
Use the ShinyApps infrastructure to support simple analyses using R

It makes it easy to do crosstabs

It is not overwhelming

It is easy to add your own data sets and custom recoding, which can be as complex as you want.

Much of the R code is prewritten, with good examples to follow. 

You can find helpful code at the crosstabber-tools repository.

--- .class #id 

## Create new data
To make new datasets to use in your own instance, you can use crosstabber-tools.
The census uses some standard variable names which makes sharing code easier..
For example it creates recodes easily

```r
        agebreaks<-c(0, 4, 14, 24, 34, 44, 54, 64, 200)
        agelabels=c("Under 4", "5-14", "15-24", "25-34", "35-44", "45-54", "55-64", "65+")
agebreaks
```

```
## [1]   0   4  14  24  34  44  54  64 200
```
Then to apply on your dataframe you use code like this (but substituting the name of your dataframe).

````
dataframe$Age<-cut(dataframe$AGEP, breaks=agebreaks, ordered_result=TRUE, labels=agelabels)
                    
````

You can set up your own reusable code for this by addint to the recodeutitilities.R file.

--- .class #id 

## Try it
Try crosstabber: http://elinw.shinyapps.io/crosstabber/

Get the code: https://github.com/elinw/crosstabber

Create your own data sets: https://github.com/elinw/crosstabber-tools

Get your own micro data from Data Ferret: http://dataferrett.census.gov/


