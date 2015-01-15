# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

Reading in the dataset from included .zip file from clone:


```r
activity <- read.csv(unz("activity.zip","activity.csv"), stringsAsFactors=FALSE, header=T, sep=",")
```

Aggregating steps by date:


```r
steps<-aggregate(steps ~ date, data=activity, sum)
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
## [1] 10766.19
```
## What is the median total number of steps taken per day?

```r
median(steps$steps)
```

```
## [1] 10765
```



## What is the average daily activity pattern?



## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
