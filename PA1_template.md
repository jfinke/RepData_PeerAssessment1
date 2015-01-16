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
Aggregating data by intervals:

```r
steps2<-aggregate(steps ~ interval, data=activity, sum)
```
Averaging out over the number of days:

```r
steps2$stepsavg<-steps2$steps / nrow(steps)
```

Plotting the 

Getting the max interval averaged out over all days:

```r
#stepsmax<-max(steps2$stepsavg)
#filter(steps2, steps2$stepsavg==stepsmax)
#intervalmax<-filter(steps2, steps2$stepsavg==stepsmax)
#print(intervalmax)
stepssorted<-steps2[order(steps2$stepsavg),]
tail(stepssorted, n=1)
```

```
##     interval steps stepsavg
## 104      835 10927 206.1698
```

## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
