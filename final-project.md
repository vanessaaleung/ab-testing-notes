# A/B Testing Project - Udacity Free Trial Screener
## Table of Contents
1. [Overview](#overview)
2. [Metric Choice](#metric-choice)
3. [Measuring Variability](#measuring-variability)
4. [Sizing](#sizing)

## Overview

At the time of this experiment, Udacity courses currently have two options on the course overview page: **"start free trial"**, and **"access course materials"**. 
If the student clicks "start free trial", they will be asked to enter their credit card information, and then they will be enrolled in a free trial for the paid version of the course. After 14 days, they will automatically be charged unless they cancel first. If the student clicks "access course materials", they will be able to view the videos and take the quizzes for free, but they will not receive coaching support or a verified certificate, and they will not submit their final project for feedback.

In the experiment, Udacity tested a change where if the student clicked "start free trial", they were asked how much time they had available to devote to the course. 
If the student indicated 5 or more hours per week, they would be taken through the checkout process as usual. 
If they indicated fewer than 5 hours per week, a message would appear indicating that Udacity courses usually require a greater time commitment for successful completion, and suggesting that the student might like to access the course materials for free. 
At this point, the student would have the option to continue enrolling in the free trial, or access the course materials for free instead. 
[This screenshot](https://drive.google.com/a/knowlabs.com/file/d/0ByAfiG8HpNUMakVrS0s4cGN2TjQ/view?usp=sharing) shows what the experiment looks like.

<img src="Final Project_ Experiment Screenshot.png" width="700px">

The hypothesis was that this might set clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time—without significantly reducing the number of students to continue past the free trial and eventually complete the course. 
If this hypothesis held true, Udacity could improve the overall student experience and improve coaches' capacity to support students who are likely to complete the course.

The **unit of diversion** is a **cookie**, although if the student **enrolls** in the free trial, they are tracked by **user-id** from that point forward. 
The same user-id cannot enroll in the free trial twice. 
For users that do not enroll, their user-id is not tracked in the experiment, even if they were signed in when they visited the course overview page.

## Metric Choice
- The practical significance boundary for each metric, that is, the difference that would have to be observed before that was a meaningful change for the business, is given in parentheses. 
- All practical significance boundaries are given as absolute changes.
- Any place "unique cookies" are mentioned, the uniqueness is determined by day. 
- User-ids are automatically unique since the site does not allow the same user-id to enroll twice.

### Invariant Metric
_Metrics that shouldn’t change across experiment and control_
1. **Number of cookies:** 
The number of unique cookies to view the course overview page. (d<sub>min</sub>=3000)
2. **Number of clicks:** 
The number of unique cookies to click the "Start free trial" button (which happens before the free trial screener is trigger). (d<sub>min</sub>=240)
3. **Click-through-probability:** 
The number of unique cookies to click the "Start free trial" button divided by number of unique cookies to view the course overview page. (d<sub>min</sub>=0.01)

### Evalution Metrics
1. **Gross conversion:** 
The number of user-ids to complete checkout and enroll in the free trial divided by number of unique cookies to click the "Start free trial" button. (d<sub>min</sub>= 0.01)

2. **Net conversion:** 
The number of user-ids to remain enrolled past the 14-day boundary (and thus make at least one payment) divided by the number of unique cookies to click the "Start free trial" button. (d<sub>min</sub>= 0.0075)

## Measuring Variability
_For each evaluation metric, estimate its standard deviation analytically, given a sample size of 5,000 cookies visiting the course overview page_

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Estimate&space;Standard&space;Deviation}=\sqrt{\frac{\hat{P}(1-\hat{P})}{N}}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Estimate&space;Standard&space;Deviation}=\sqrt{\frac{\hat{P}(1-\hat{P})}{N}}" title="\text{Estimate Standard Deviation}=\sqrt{\frac{\hat{P}(1-\hat{P})}{N}}" /></a>

The rough estimates of the baseline values for these metrics:
<table>
<tr>
<td>Unique cookies to view course overview page per day:</td>
<td>40000</td>
</tr>
<tr>
<td>Unique cookies to click "Start free trial" per day:</td>
<td>3200</td>
</tr>
<tr>
<td>Enrollments per day:</td>
<td>660</td>
</tr>
<tr>
<td>Click-through-probability on "Start free trial":</td>
<td>0.08</td>
</tr>
<tr>
<td>Probability of enrolling, given click:</td>
<td>0.20625</td>
</tr>
<tr>
<td>Probability of payment, given enroll:</td>
<td>0.53</td>
</tr>
<tr>
<td>Probability of payment, given click</td>
<td>0.1093125</td>
</tr>
</table>

### Gross Conversion
<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{N}=\text{\&hash;&space;unique&space;cookies&space;to&space;click&space;the&space;Start&space;Free&space;Trial&space;Button}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{N}=\text{\&hash;&space;unique&space;cookies&space;to&space;click&space;the&space;Start&space;Free&space;Trial&space;Button}" title="\text{N}=\text{\# unique cookies to click the Start Free Trial Button}" /></a>

&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\frac{\text{rough&space;estimate&space;of&space;unique&space;cookies&space;to&space;click&space;the&space;button}}{\text{rough&space;estimate&space;of&space;unique&space;cookies&space;to&space;view&space;the&space;page}}\times{\text{\&hash;&space;sample&space;of&space;unique&space;cookies&space;to&space;view&space;the&space;course&space;page}}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;=\frac{\text{rough&space;estimate&space;of&space;unique&space;cookies&space;to&space;click&space;the&space;button}}{\text{rough&space;estimate&space;of&space;unique&space;cookies&space;to&space;view&space;the&space;page}}\times{\text{\&hash;&space;sample&space;of&space;unique&space;cookies&space;to&space;view&space;the&space;course&space;page}}" title="=\frac{\text{rough estimate of unique cookies to click the button}}{\text{rough estimate of unique cookies to view the page}}\times{\text{\# sample of unique cookies to view the course page}}" /></a>

&nbsp;&nbsp;&nbsp;&nbsp;<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;=\frac{3,200}{40,000}\times5,000=400" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;=\frac{3,200}{40,000}\times5,000=400" title="=\frac{3,200}{40,000}\times5,000=400" /></a>

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Estimate&space;Standard&space;Deviation}=\sqrt{\frac{0.20625\times(1-0.20625))}{400}}=0.0202" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Estimate&space;Standard&space;Deviation}=\sqrt{\frac{0.20625\times(1-0.20625))}{400}}=0.0202" title="\text{Estimate Standard Deviation}=\sqrt{\frac{0.20625\times(1-0.20625))}{400}}=0.0202" /></a>

### Net Conversion
<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Estimate&space;Standard&space;Deviation}=\sqrt{\frac{0.1093125\times(1-0.1093125))}{400}}=0.0156" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Estimate&space;Standard&space;Deviation}=\sqrt{\frac{0.1093125\times(1-0.1093125))}{400}}=0.0156" title="\text{Estimate Standard Deviation}=\sqrt{\frac{0.1093125\times(1-0.1093125))}{400}}=0.0156" /></a>

## Sizing
### Choosing Number of Samples given Power
_How many pageviews total (across both groups) would be needed to collect given an alpha of 0.05 and a beta of 0.2_

- Bonferroni Correction: <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\alpha_{individual}=\frac{\alpha_{overall}}{2}=0.025" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\alpha_{individual}=\frac{\alpha_{overall}}{2}=0.025" title="\alpha_{individual}=\frac{\alpha_{overall}}{2}=0.025" /></a>

#### Gross Conversion
- Minimum Detectable Effect:  0.01
- Baseline conversion rate: 0.20625
- Sample Size:&nbsp;&nbsp;<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\frac{33,014&plus;29,844}{2}=31,429" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\frac{33,014&plus;29,844}{2}=31,429" title="\frac{33,014+29,844}{2}=31,429" /></a>&nbsp;&nbsp;per group

#### Net Conversion
- Minimum Detectable Effect:  0.0075
- Baseline conversion rate: 0.1093125
- Sample Size:&nbsp;&nbsp;<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\frac{35,016&space;&plus;&space;31,660}{2}=33,338" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\frac{35,016&space;&plus;&space;31,660}{2}=33,338" title="\frac{35,016 + 31,660}{2}=33,338" /></a>&nbsp;&nbsp;per group

#### Page View Needed
<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;33,338\times2\div\frac{3,200}{40,000}=833,450" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;33,338\times2\div\frac{3,200}{40,000}=833,450" title="33,338\times2\div\frac{3,200}{40,000}=833,450" /></a>


### Choosing Duration vs. Exposure
#### Exposure
As the change is not risky, 100% of Udacity's traffic would be diverted to this experiment, assuming there were no other experiments running simultaneously.

#### Duration
_How long would the experiment take to run_

<a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Duration}=\frac{\text{833,450&space;page&space;views&space;needed}}{\text{estimate&space;of&space;40,000&space;page&space;views&space;per&space;day}}\approx&space;21\text{days}" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Duration}=\frac{\text{833,450&space;page&space;views&space;needed}}{\text{estimate&space;of&space;40,000&space;page&space;views&space;per&space;day}}\approx&space;21\text{days}" title="\text{Duration}=\frac{\text{833,450 page views needed}}{\text{estimate of 40,000 page views per day}}\approx 21\text{days}" /></a>

## Analysis
The data for you to analyze is [here](https://docs.google.com/a/knowlabs.com/spreadsheets/d/1Mu5u9GrybDdska-ljPXyBjTpdZIUev_6i7t4LRDfXM8/edit#gid=0).

### Sanity Checks
_Checking whether the invariant metrics are equivalent between the two groups_

- If the invariant metric is a simple count that should be randomly split between the 2 groups, use a binomial test. 
- Otherwise, construct a confidence interval for a difference in proportions, then check whether the difference between group values falls within that confidence level.

#### Number of cookies
- Total cookies in control: 345,543
- Total cookies in experiment: 344,660
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Standard&space;Error}=\sqrt{\frac{0.5\times0.5}{345,543&plus;344,660}}=0.0006" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Standard&space;Error}=\sqrt{\frac{0.5\times0.5}{345,543&plus;344,660}}=0.0006" title="\text{Standard Error}=\sqrt{\frac{0.5\times0.5}{345,543+344,660}}=0.0006" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Margin&space;of&space;error}=\text{SD}\times1.96=0.0012" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Margin&space;of&space;error}=\text{SD}\times1.96=0.0012" title="\text{Margin of error}=\text{SD}\times1.96=0.0012" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Confidence&space;Interval}=[0.4988,&space;0.5012]" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Confidence&space;Interval}=[0.4988,&space;0.5012]" title="\text{Confidence Interval}=[0.4988, 0.5012]" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Observed&space;fraction}=\hat{\beta}=\frac{28,378}{28,378&plus;28,325}=0.5005" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Observed&space;fraction}=\hat{\beta}=\frac{28,378}{28,378&plus;28,325}=0.5005" title="\text{Observed fraction}=\hat{\beta}=\frac{28,378}{28,378+28,325}=0.5005" /></a>
- Observed fraction is within the CI - passed the check

#### Net Conversion
- Total clicks in control: 28,378
- Total cookies in experiment: 28,325
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Standard&space;Error}=\sqrt{\frac{0.5\times0.5}{28,378&plus;28,325}}=0.0021" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Standard&space;Error}=\sqrt{\frac{0.5\times0.5}{28,378&plus;28,325}}=0.0021" title="\text{Standard Error}=\sqrt{\frac{0.5\times0.5}{28,378+28,325}}=0.0021" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Margin&space;of&space;error}=\text{SD}\times1.96=0.0041" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Margin&space;of&space;error}=\text{SD}\times1.96=0.0041" title="\text{Margin of error}=\text{SD}\times1.96=0.0041" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Confidence&space;Interval}=[0.4959,&space;0.5041]" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Confidence&space;Interval}=[0.4959,&space;0.5041]" title="\text{Confidence Interval}=[0.4959, 0.5041]" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Observed&space;fraction}=\hat{\beta}=\frac{28,378}{38,278&plus;28,325}=0.5005" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Observed&space;fraction}=\hat{\beta}=\frac{28,378}{38,278&plus;28,325}=0.5005" title="\text{Observed fraction}=\hat{\beta}=\frac{28,378}{38,278+28,325}=0.5005" /></a>
- Observed fraction is within the CI - passed the check

#### Click-through-probability
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\hat{P_{pool}}=\frac{X_{control}&plus;X_{experiment}}{N_{control}&plus;N_{experiment}}=\frac{28,378&plus;28,325}{345,543&plus;344,660}=0.0822" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\hat{P_{pool}}=\frac{X_{control}&plus;X_{experiment}}{N_{control}&plus;N_{experiment}}=\frac{28,378&plus;28,325}{345,543&plus;344,660}=0.0822" title="\hat{P_{pool}}=\frac{X_{control}+X_{experiment}}{N_{control}+N_{experiment}}=\frac{28,378+28,325}{345,543+344,660}=0.0822" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}&plus;\frac{1}{N_{experiment}})}=0.0007" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}&plus;\frac{1}{N_{experiment}})}=0.0007" title="SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}+\frac{1}{N_{experiment}})}=0.0007" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Margin&space;of&space;error}=SE_{pool}\times1.96=0.0013" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Margin&space;of&space;error}=SE_{pool}\times1.96=0.0013" title="\text{Margin of error}=SE_{pool}\times1.96=0.0013" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\text{Confidence&space;Interval}=[-0.0013,&space;0.0013]" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\text{Confidence&space;Interval}=[-0.0013,&space;0.0013]" title="\text{Confidence Interval}=[-0.0013, 0.0013]" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{28,325}{344,660}-\frac{28,378}{345,543}=0.0001" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{28,325}{344,660}-\frac{28,378}{345,543}=0.0001" title="\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{28,325}{344,660}-\frac{28,378}{345,543}=0.0001" /></a>
- Observed difference is within the CI - passed the check

#### Summary
|Metric|Lower Bound|Upper Bound|Observed|Passes|
|---|---|---|---|---|
|Number of Cookies|0.4988|0.5012|0.5006|✓|
|Number of Clicks|0.4959|0.5041|0.5005|✓|
|Click-through-probability|-0.0013|0.0013|0.0001|✓|

### Check for Practical and Statistical Significance
_Calculate a confidence interval for the difference between the experiment and control groups, and check whether each metric is statistically and/or practically significance_

#### Significance definitions
A metric is statistically significant if the confidence interval does not include 0, that is, you can be confident there was a change. And it is practically significant if the confidence interval does not include the practical significance boundary, that is, you can be confident there is a change that matters to the business.

- Bonferroni Correction: <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\alpha_{individual}=\frac{\alpha_{overall}}{2}=0.025" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\alpha_{individual}=\frac{\alpha_{overall}}{2}=0.025" title="\alpha_{individual}=\frac{\alpha_{overall}}{2}=0.025" /></a>

#### Gross conversion
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{3,423}{17,260}-\frac{3,785}{17,293}=-0.0206" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{3,423}{17,260}-\frac{3,785}{17,293}=-0.0206" title="\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{3,423}{17,260}-\frac{3,785}{17,293}=-0.0206" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\hat{P_{pool}}=\frac{X_{control}&plus;X_{exp}}{N_{control}&plus;N_{exp}}=\frac{3,423&plus;3,785}{17,260&plus;17,293}=0.2086" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\hat{P_{pool}}=\frac{X_{control}&plus;X_{exp}}{N_{control}&plus;N_{exp}}=\frac{3,423&plus;3,785}{17,260&plus;17,293}=0.2086" title="\hat{P_{pool}}=\frac{X_{control}+X_{exp}}{N_{control}+N_{exp}}=\frac{3,423+3,785}{17,260+17,293}=0.2086" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}&plus;\frac{1}{N_{exp}})}=0.0044" target="_blank"><img src="https://latex.codecogs.com/svg.latex?SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}&plus;\frac{1}{N_{exp}})}=0.0044" title="SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}+\frac{1}{N_{exp}})}=0.0044" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\text{Margin&space;of&space;error}=SE_{pool}\times2.24=0.0098" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\text{Margin&space;of&space;error}=SE_{pool}\times2.24=0.0098" title="\text{Margin of error}=SE_{pool}\times2.24=0.0098" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\text{Confidence&space;Interval}=[-0.0303,&space;-0.0108]" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\text{Confidence&space;Interval}=[-0.0303,&space;-0.0108]" title="\text{Confidence Interval}=[-0.0303, -0.0108]" /></a>
- CI does not includes 0 - statistically significant
- CI does not include d<sub>min</sub>= - 0.01, practical significant

#### Net conversion
- <a href="https://www.codecogs.com/eqnedit.php?latex=\inline&space;\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{1,945}{17,260}-\frac{2,033}{17,293}=-0.0049" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\inline&space;\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{1,945}{17,260}-\frac{2,033}{17,293}=-0.0049" title="\hat{d}=\hat{P_{exp}}-\hat{P_{control}}=\frac{1,945}{17,260}-\frac{2,033}{17,293}=-0.0049" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\hat{P_{pool}}=\frac{X_{control}&plus;X_{exp}}{N_{control}&plus;N_{exp}}=\frac{1,945&plus;2,033}{17,260&plus;17,293}=0.1151" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\hat{P_{pool}}=\frac{X_{control}&plus;X_{exp}}{N_{control}&plus;N_{exp}}=\frac{1,945&plus;2,033}{17,260&plus;17,293}=0.1151" title="\hat{P_{pool}}=\frac{X_{control}+X_{exp}}{N_{control}+N_{exp}}=\frac{1,945+2,033}{17,260+17,293}=0.1151" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}&plus;\frac{1}{N_{exp}})}=0.0034" target="_blank"><img src="https://latex.codecogs.com/svg.latex?SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}&plus;\frac{1}{N_{exp}})}=0.0034" title="SE_{pool}=\sqrt{\hat{P_{pool}}\times(1-\hat{P_{pool}})\times(\frac{1}{N_{control}}+\frac{1}{N_{exp}})}=0.0034" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\text{Margin&space;of&space;error}=SE_{pool}\times2.24=0.0077" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\text{Margin&space;of&space;error}=SE_{pool}\times2.24=0.0077" title="\text{Margin of error}=SE_{pool}\times2.24=0.0077" /></a>
- <a href="https://www.codecogs.com/eqnedit.php?latex=\text{Confidence&space;Interval}=[-0.0126,&space;0.0028]" target="_blank"><img src="https://latex.codecogs.com/svg.latex?\text{Confidence&space;Interval}=[-0.0126,&space;0.0028]" title="\text{Confidence Interval}=[-0.0126, 0.0028]" /></a>
- CI includes 0 - not significant
- CI includes d<sub>min</sub>= - 0.0075, not practical significant

#### Summary
|Metric|Lower Bound|Upper Bound|Statistical Significance|Practical Significance|
|---|---|---|---|---|
|Gross Conversion|-0.0303|-0.0108|✓|✓|
|Net Conversion|-0.0126|0.0028|╳|╳|

### Run Sign Tests
_Perform sign test using the day-by-day breakdown to see if it agree with the confidence interval for the difference_

- [Online Calculator for Sign and binomial test](https://www.graphpad.com/quickcalcs/binomial1.cfm)

#### Gross conversion
- #days: 23
- #days with positive change: 19
- The two-tail P value is 0.0026, which is the chance of observing either 19 or more successes, or 4 or fewer successes, in 23 trials
- p-value < 0.025, statistically significant
 
#### Net conversion
- #days: 23
- #days with positive change: 13
- The two-tail P value is 0.6776, which is the chance of observing either 13 or more successes, or 10 or fewer successes, in 23 trials
- p-value > 0.025, not significant

### Summary
|Metric|p-value|Statistical Significance|
|---|---|---|
|Gross Conversion|0.0026|✓|
|Net Conversion|0.6776|╳|

### Make a Recommendation

Finally, make a recommendation. Would you launch this experiment, not launch it, dig deeper, run a follow-up experiment, or is it a judgment call? If you would dig deeper, explain what area you would investigate. If you would run follow-up experiments, briefIy describe that experiment. If it is a judgment call, explain what factors would be relevant to the decision.


## Follow-Up Experiment: How to Reduce Early Cancellations

If you wanted to reduce the number of frustrated students who cancel early in the course, what experiment would you try? Give a brief description of the change you would make, what your hypothesis would be about the effect of the change, what metrics you would want to measure, and what unit of diversion you would use. Include an explanation of each of your choices.

