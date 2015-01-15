# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

Reading in the dataset from included .zip file from clone:


```r
activity <- read.csv(unz("activity.zip","activity.csv"), stringsAsFactors=FALSE, header=T, sep=",")
```

Using dplyr to select out the steps column and remove the NA values:


```r
library(dplyr)
```

```
## Warning: package 'dplyr' was built under R version 3.1.1
```

```
## 
## Attaching package: 'dplyr'
## 
## The following object is masked from 'package:stats':
## 
##     filter
## 
## The following objects are masked from 'package:base':
## 
##     intersect, setdiff, setequal, union
```

```r
steps<-activity%>%
  select(steps)%>%
  na.omit
```

## Histogram of steps
Using hist to graph a histogram of the number of steps:


```r
hist(steps$steps, main="Histogram of Steps", xlab="Steps")
```

![](./PA1_template_files/figure-html/unnamed-chunk-3-1.png) 


## What is mean total number of steps taken per day?

```r
mean(steps$steps)
```

```
## [1] 37.3826
```
## What is the median total number of steps taken per day?

```r
median(steps$steps)
```

```
## [1] 0
```



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
