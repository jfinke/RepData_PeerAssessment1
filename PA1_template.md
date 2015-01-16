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

Plotting the timeseries of the average daily activity:

```r
plot(x=steps2$interval, y=steps2$stepsavg, type="l", xlab="5 Minute Time Interval", ylab="Average Number of Steps", main="Average Number of Steps Taken\nAveraged Across All Days ")
```

![](./PA1_template_files/figure-html/unnamed-chunk-8-1.png) 

Getting the max interval averaged out over all days:

```r
stepssorted<-steps2[order(steps2$stepsavg),]
tail(stepssorted, n=1)
```

```
##     interval steps stepsavg
## 104      835 10927 206.1698
```

## Imputing missing values
Calculating the number of NA values in steps:

```r
sum(is.na(activity$steps))
```

```
## [1] 2304
```




## Are there differences in activity patterns between weekdays and weekends?
