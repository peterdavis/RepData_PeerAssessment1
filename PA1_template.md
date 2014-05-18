# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r

opts_chunk$set(fig.path = "./figures/", echo = TRUE)

activity <- read.csv("activity.csv")
library("ggplot2")

# stepCounts <- aggregate(activity$steps, list(activity$date), sum)
# colnames(stepCounts) <- c('date', 'steps')

# change to S3 method for forumula rather than class data.frame

stepCounts <- aggregate(steps ~ date, data = activity, sum)

```


## What is mean total number of steps taken per day?


```r
qplot(date, steps, data = stepCounts, geom = "histogram")
```

```
## Mapping a variable to y and also using stat="bin".
##   With stat="bin", it will attempt to set the y value to the count of cases in each group.
##   This can result in unexpected behavior and will not be allowed in a future version of ggplot2.
##   If you want y to represent counts of cases, use stat="bin" and don't map a variable to y.
##   If you want y to represent values in the data, use stat="identity".
##   See ?geom_bar for examples. (Deprecated; last used in version 0.9.2)
```

![plot of chunk unnamed-chunk-2](./figures/unnamed-chunk-2.png) 

```r

mean(stepCounts$steps, na.rm = TRUE)
```

```
## [1] 10766
```

```r
median(stepCounts$steps, na.rm = TRUE)
```

```
## [1] 10765
```



## What is the average daily activity pattern?


```r
intervalMean <- aggregate(steps ~ interval, data = activity, mean)

qplot(interval, steps, data = intervalMean, geom = "line")
```

![plot of chunk unnamed-chunk-3](./figures/unnamed-chunk-3.png) 

```r

# what is the interval, on average across all days, that contains the max
# number of steps
intervalMean[intervalMean$steps == max(intervalMean$steps), ]
```

```
##     interval steps
## 104      835 206.2
```

```r

```



## Imputing missing values



```r
# calculuate missing values

```



## Are there differences in activity patterns between weekdays and weekends?
