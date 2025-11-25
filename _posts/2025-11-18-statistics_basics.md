---
layout: post
title: "Statistics Basics"
date: 2025-10-16
toc: true
---
## Measures of central tendency
### Mean
The mean is the average of a set of values, in other words the sum of all values divided by the number of values in the set

$$
Mean = \frac{\sigma{x_i}}{N}
$$

### Median
The median is the middle of a set of ordered values. If there is an even number of values in the set, it is the middle two values divided by two.

### Mode
The mode is the most often occuring value in a set.

## Measures of Dispersion
Measures of dispersion assign a value to how spread out your data is around the
mean. The value is going to be small, when the data is clustered around the
mean, and large, when it is widely dispersed.

### Variance
Variance is the most basic measure of dispersion.

$$
\sigma^2=\frac{\sum_{i=1}^{N_1} (X_{1i} -\bar{X}_1)^2}{N}
$$

The downside of the variance measure is, that the output is squared, and so the
units are not the same as those of the data. If you take the square root, it
becomes the standard deviation.

### Standard Deviation
The standard deviation is a measure of dispersion (how wide the data is spread
around the mean/average distance to the mean). It is calculated by taking the
sum of the squared difference of each value to the mean, dividing it by the sample
size and taking the square root.

$$
\sigma=\sqrt{\frac{\sum_{i=1}^{N_1} (X_{1i} -\bar{X}_1)^2}{N}}
$$

### Standard error
The standard error is a measure of how confident we are that our sample mean reflects the true population mean.

$$
SE=\frac{\sigma}{\sqrt{N}}
$$
