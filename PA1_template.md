# Reproducible Research: Peer Assessment 1


## Loading and preprocessing the data


```r
setwd("E:/Data/Coursera/Reproducible Research/week2/RepData_PeerAssessment1")

activity <- read.csv("activity.csv")
library("ggplot2")

# stepCounts <- aggregate(activity$steps, list(activity$date), sum) change
# to S3 method for forumula rather than class data.frame

stepCounts <- aggregate(steps ~ date, data = activity, sum)
colnames(stepCounts) <- c("date", "steps")
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

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 


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

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

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





## Imputing missing values



## Are there differences in activity patterns between weekdays and weekends?
