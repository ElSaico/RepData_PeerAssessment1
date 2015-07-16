# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data

```r
activity <- read.csv(unz('activity.zip', 'activity.csv'))
```


## What is mean total number of steps taken per day?

```r
dailysteps <- aggregate(activity$steps, by=list(activity$date), FUN=sum)
hist(dailysteps$x, breaks=8, main="Distribution of daily step totals", xlab="Amount of steps", ylab="Number of days")
```

![](PA1_template_files/figure-html/unnamed-chunk-2-1.png) 

```r
mean(dailysteps$x, na.rm=TRUE)
```

```
## [1] 10766.19
```

```r
median(dailysteps$x, na.rm=TRUE)
```

```
## [1] 10765
```

## What is the average daily activity pattern?

```r
avginterval <- with(activity, aggregate(steps ~ interval, FUN=mean, na.rm=TRUE))
plot(avginterval, type='l', main="Average step total per 5-minute interval", xlab="Time", ylab="Amount of steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 

```r
avginterval[which.max(avginterval$steps), 'interval']
```

```
## [1] 835
```


## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
