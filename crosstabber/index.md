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


--- .class #id 

## Create new data
To make new datasets to use in your own instance, you can use crosstabber-tools.

```r
physicians<-readRDS("./physicians.rds")
```

```
## Warning: cannot open compressed file './physicians.rds', probable reason
## 'No such file or directory'
```

```
## Error: cannot open the connection
```

```r
                    source("./recodeutilities")
```

```
## Warning: cannot open file './recodeutilities': No such file or directory
```

```
## Error: cannot open the connection
```

```r
##dataframe is a dataframe that contains the RAC1P variable and the HISP variable
## This function pulls all self-identified Hispanics or Latinos into a separate group
## regardless of what self-identified race category they are in.
racerecode<-function(dataframe)
{
        ## Pull out Hispanics into a separate code.
        dataframe$racerecode<-ifelse(dataframe$HISP > 1, 10, dataframe$RAC1P)
        racelabels<-c("White", "Black", "Asian", "American Indian + Alaskan Native ", "Other", "Multiple", "Latino")
        racecuts<-c(0,1,2,4,6,8,9,10)
        dataframe$Race<-cut(dataframe$racerecode, breaks=racecuts, labels=racelabels)
        return(dataframe)
}

racerecode(physicians)
```

```
## Error: object 'physicians' not found
```

```r
table(physicians$Race)
```

```
## Error: object 'physicians' not found
```

--- .class #id 

## Try it
Try crosstabber: http://elinw.shinyapps.io/crosstabber/

Get the code: https://github.com/elinw/crosstabber

Create your own data sets: https://github.com/elinw/crosstabber-tools

Get your own micro data from Data Ferret: http://dataferrett.census.gov/


