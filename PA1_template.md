# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
unzip( "activity.zip")
activity<- read.csv("activity.csv")
head(activity)
```

```
##   steps       date interval
## 1    NA 2012-10-01        0
## 2    NA 2012-10-01        5
## 3    NA 2012-10-01       10
## 4    NA 2012-10-01       15
## 5    NA 2012-10-01       20
## 6    NA 2012-10-01       25
```

## What is mean total number of steps taken per day?

```r
totalstepsday  <- aggregate(data= activity,steps~date, sum, na.rm=TRUE)
head(totalstepsday)
```

```
##         date steps
## 1 2012-10-02   126
## 2 2012-10-03 11352
## 3 2012-10-04 12116
## 4 2012-10-05 13294
## 5 2012-10-06 15420
## 6 2012-10-07 11015
```


```r
hist(totalstepsday$steps, main="Total number of steps", xlab="steps")
```

![](PA1_template_files/figure-html/unnamed-chunk-3-1.png) 


```r
mean(totalstepsday$steps)
```

```
## [1] 10766.19
```

```r
median(totalstepsday$steps)
```

```
## [1] 10765
```

## What is the average daily activity pattern?


```r
stepsandinterval <- aggregate(steps ~ interval, activity, mean)
```


```r
plot(stepsandinterval, type='l')
```

![](PA1_template_files/figure-html/unnamed-chunk-6-1.png) 


```r
stepsandinterval$interval[which.max(stepsandinterval$steps)]
```

```
## [1] 835
```


## Imputing missing values
Total number of missing values

```r
sum(is.na(activity$steps))
```

```
## [1] 2304
```




## Are there differences in activity patterns between weekdays and weekends?


