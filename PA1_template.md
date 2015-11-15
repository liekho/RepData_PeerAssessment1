---
title: "PA1_template"
---

Loading and preprocessing the data

Load the data (i.e. read.csv())

```{r,echo=TRUE}
if(!file.exists('activity.csv')){
  unzip('activity.zip')
}
activity <- read.csv('activity.csv')
```

Make a histogram of the total number of steps taken each day

```{r,echo=TRUE}
steps.date <- aggregate(steps ~ date, data = activity, FUN = sum)
barplot(steps.date$steps, names.arg = steps.date$date, xlab = "date", ylab = "steps")
```

Calculate and report the mean and median total number of steps taken per day

```{r,echo=TRUE}
mean(steps.date$steps)

median(steps.date$steps)
```

Make a time series plot (i.e. type = "l") of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)

```{r,echo=TRUE}
steps.interval <- aggregate(steps ~ interval, data = activity, FUN = mean)
plot(steps.interval, type = "l")
```

Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?

```{r,echo=TRUE}
steps.interval$interval[which.max(steps.interval$steps)]
```

Calculate and report the total number of missing values in the dataset

```{r,echo=TRUE}
sum(is.na(activity))
```

