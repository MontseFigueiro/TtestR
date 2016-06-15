    plot(extra ~ group, data = sleep)

![](https://github.com/MontseFigueiro/TtestR/blob/master/unnamed-chunk-1-1.png) 
Student's t-test or t-test (the real name is W.S. Gossett who hid his name due to
his position as a worker in a brewery company) is a simple yet very
useful statistical test. The basic idea behind t-test is the inference
problem from a small sample size data set to test whether its sample
mean may have large deviation from the true population mean.

A very common problem you will encounter is having two data sets and you
want to test whether the two sets are coming from the same (assuming)
normal distributions.

In t-test, the null hypothesis is that the mean of the two samples is
equal. This means that the alternative hypothesis for the test is that
the difference of the mean is not equal to zero. In a hypothesis test,
we want to reject or accept the null hypothesis with some confidence
interval. Since we test the difference between the two means, the
confidence interval in this case specifies the range of values within
which the difference may lie.

The t-test will also produce the p-value, which is the probability of
wrongly rejecting the null hypothesis. The p-value is always compared
with the significance level of the test. For instances, at 95% level of
confidence, the significant level is 5% and the p-value is reported as
p&lt;0.05. Small p-values suggest that the null hypothesis is unlikely
to be true. The smaller it is, the more confident we can reject the null
hypothesis.

In R, the test is performed by the built-in t.test() function. Let's use
the sleep data from R where there are 20 samples in two groups (group 1
and 2, each with 10 samples) that show the effect of two soporific drug
to increase the hours in sleep. Okay, we are not interested in the
details of the data, but if we plot the data like this:

A quick grasp to the plot we see that there is naturally an overlap but
the mean (half of the rectangle height) is different. Can we confidently
say that the two groups have different means?

A quick t-test reveals the result:

    t.test(extra~group,data=sleep)

    ## 
    ##  Welch Two Sample t-test
    ## 
    ## data:  extra by group
    ## t = -1.8608, df = 17.776, p-value = 0.07939
    ## alternative hypothesis: true difference in means is not equal to 0
    ## 95 percent confidence interval:
    ##  -3.3654832  0.2054832
    ## sample estimates:
    ## mean in group 1 mean in group 2 
    ##            0.75            2.33

Welch Two Sample t-test

Based on the result, you can say: at 95% confidence level, there is no
significant difference (p-value = 0.0794) of the two means. Here you
should accept the null hypothesis that the two means are equal because
the p-value is larger than 0.05. The maximum difference of the mean can
be as low as -3.37 and as high as 0.21. The output also produces
estimates of the sample means, the mean and the degree of freedom of the
t-distribution. Note that Welch's t-test is a t-test with unequal
variances.

The above example uses unpaired data sets with unequal variances. You
may have different types of data sets. For instances,

You may have paired or unpaired data sets. Paired data sets means that
if X1,X2,.,Xn are the first data set and Y1,Y2,.Yn are the second one,
then Xi corresponds to Yi. Hence, the two data set size must be the
same. In unpaired data sets, the sample size between two sets may not be
the same. In t.test(), you can set this with paired option.

You may have equal or unequal variances. Use var.equal option.

You may have a constant value, which means that the null hypothesis is
in the form that the difference between the two population means is
equal to some constant, instead of zero. Use mu option.
plot(extra~group,sleep)
