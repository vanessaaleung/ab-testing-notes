# Analyzing Results
1. [Sanity Checks](#sanity-checks)
2. [Single Metric Evaluation](#single-metric-evaluation)
3. [Simpson’s paradox](#simpsons-paradox)
4. [Multiple Metrics](#multiple-metrics)
5. [Disappearing Launch Effect](#disappearing-launch-effect)

## Sanity Checks
i.e. invariant check

### Population Sizing Metrics
_Check if the experiment population and the control population are comparable, based on the unit of diversion_

### Other Invariant Metrics
_The metrics that shouldn’t change when running the experiment_

### Checking Invariants
1. Compute Standard Error of binomial with probability of 0.5 success
2. Multiply by z-score to get margin of error
3. Compute confidence interval around 0.5
4. Check whether the observed fraction is within interval

Example:

Run experiment for 2 weeks, unit of diversion: cookie

Total cookies in control: 64,454

Total cookies in experiment: 61,818

## Single Metric Evaluation
*   Significance
*   Magnitude
*   And Direction of the change

### Example 1

Answer

Decision: Launch
*   Run additional test with greater power
*   Communicate with decision-makers if they want to take a risk as the data  is uncertain


### Example 2
Experiment: change color and placement of “Start Now” button

Metric: Click-through-rate

Unit of diversion: cookie

**Method 1: Effect Size**

, works well if the Ns are fairly close

, significant as not includes zero

Recommendation: Launch the experiment as  the CI doesn’t include the 

**Method 2: Sign Test**
_Has lower power_

#days: 7

#days with positive change: 7

If no difference, 50% chance of positive change on each day

Cannot assume normal distribution since 7 days data is not enough for binomial to closely approximate a normal

[Online Calculator](https://www.graphpad.com/quickcalcs/binomial1.cfm) for binomial and sign test

The two-tail P value is 0.0156, which is the chance of observing either 7 or more successes, or 0 or fewer successes, in 7 trials.

Recommendation: Launch the experiment

### Example 3
Metric: click-through-rate

<table>
  <tr>
   <td>
   </td>
   <td><strong>Control # Clicks</strong></td>
   <td><strong>Control # Pageviews</strong></td>
   <td><strong>Control CTR</strong></td>
   <td><strong>Experiment # Clicks</strong></td>
   <td><strong>Experiment # Pageviews</strong></td>
   <td><strong>Experiment CTR</strong></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">196</p></td>
   <td><p style="text-align: right">2029</p></td>
   <td><p style="text-align: right">0.0966</p></td>
   <td><p style="text-align: right">179</p></td>
   <td><p style="text-align: right">1971</p></td>
   <td><p style="text-align: right">0.0908</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">200</p></td>
   <td><p style="text-align: right">1991</p></td>
   <td><p style="text-align: right">0.1005</p></td>
   <td><p style="text-align: right">208</p></td>
   <td><p style="text-align: right">2009</p></td>
   <td><p style="text-align: right">0.1035</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">200</p></td>
   <td><p style="text-align: right">1951</p></td>
   <td><p style="text-align: right">0.1025</p></td>
   <td><p style="text-align: right">205</p></td>
   <td><p style="text-align: right">2049</p></td>
   <td><p style="text-align: right">0.1</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">216</p></td>
   <td><p style="text-align: right">1985</p></td>
   <td><p style="text-align: right">0.1088</p></td>
   <td><p style="text-align: right">175</p></td>
   <td><p style="text-align: right">2015</p></td>
   <td><p style="text-align: right">0.0868</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">212</p></td>
   <td><p style="text-align: right">1973</p></td>
   <td><p style="text-align: right">0.1075</p></td>
   <td><p style="text-align: right">191</p></td>
   <td><p style="text-align: right">2027</p></td>
   <td><p style="text-align: right">0.0942</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">
185</p>

   </td>
   <td><p style="text-align: right">
2021</p>

   </td>
   <td><p style="text-align: right">
0.0915</p>

   </td>
   <td><p style="text-align: right">291</p></td>
   <td><p style="text-align: right">1979</p></td>
   <td><p style="text-align: right">0.147</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">225</p></td>
   <td><p style="text-align: right">2041</p></td>
   <td><p style="text-align: right">0.1102</p></td>
   <td><p style="text-align: right">278</p></td>
   <td><p style="text-align: right">1959</p></td>
   <td><p style="text-align: right">0.1419</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">187</p></td>
   <td><p style="text-align: right">
1980</p></td>
   <td><p style="text-align: right">
0.0944</p></td>
   <td><p style="text-align: right">
216</p></td>
   <td><p style="text-align: right">
2020</p></td>
   <td><p style="text-align: right">
0.1069</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">205</p></td>
   <td><p style="text-align: right">1951</p></td>
   <td><p style="text-align: right">0.1051</p></td>
   <td><p style="text-align: right">225</p></td>
   <td><p style="text-align: right">
2049</p>

   </td>
   <td><p style="text-align: right">
0.1098</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">
211</p></td>
   <td><p style="text-align: right">
1988</p></td>
   <td><p style="text-align: right">
0.1061</p></td>
   <td><p style="text-align: right">
207</p></td>
   <td><p style="text-align: right">
2012</p></td>
   <td><p style="text-align: right">
0.1029</p></td>
  </tr>
  <tr>
   <td></td>
   <td><p style="text-align: right">
192</p>

   </td>
   <td><p style="text-align: right">
1977</p>

   </td>
   <td><p style="text-align: right">
0.0971</p>

   </td>
   <td><p style="text-align: right">
205</p>

   </td>
   <td><p style="text-align: right">
2023</p>

   </td>
   <td><p style="text-align: right">
0.1013</p>

   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td><p style="text-align: right">
196</p>

   </td>
   <td><p style="text-align: right">
2019</p>

   </td>
   <td><p style="text-align: right">
0.0971</p>

   </td>
   <td><p style="text-align: right">
200</p>

   </td>
   <td><p style="text-align: right">
1981</p>

   </td>
   <td><p style="text-align: right">
0.101</p>

   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td><p style="text-align: right">
223</p>

   </td>
   <td><p style="text-align: right">
2035</p>

   </td>
   <td><p style="text-align: right">
0.1096</p>

   </td>
   <td><p style="text-align: right">
297</p>

   </td>
   <td><p style="text-align: right">
1965</p>

   </td>
   <td><p style="text-align: right">
0.1511</p>

   </td>
  </tr>
  <tr>
   <td>
   </td>
   <td><p style="text-align: right">
192</p>

   </td>
   <td><p style="text-align: right">
2007</p>

   </td>
   <td><p style="text-align: right">
0.0957</p>

   </td>
   <td><p style="text-align: right">
299</p>

   </td>
   <td><p style="text-align: right">
1993</p>

   </td>
   <td><p style="text-align: right">0.15</p></td>
  </tr>
  <tr>
   <td><strong>Total</strong></td>
   <td><p style="text-align: right"><strong>2840</strong></p></td>
   <td><p style="text-align: right"><strong>27948</strong></p></td>
   <td><p style="text-align: right"><strong>0.1016</strong></p></td>
   <td><p style="text-align: right"><strong>3176</strong></p></td>
   <td><p style="text-align: right"><strong>28052</strong></p></td>
   <td><p style="text-align: right"><strong>0.1132</strong></p></td>
  </tr>
</table>


**Method 1: Effect Size**

, significant

Recommendation: ~~Do not launch the experiment as  the CI include the ~~

*   Whether it’s ok if only weekends seem to have improved
*   Whether the magnitude of the change makes it worth launching

**Method 2: Sign Test**
#days: 14

#days with positive change: 9
The two-tail P value is 0.4240 > 

Recommendation: Do not launch the experiment


## Simpson’s paradox
_A trend appears in subgroups of data but disappears or reverses when these groups are combined_

Example: Women acceptance rate at Berkeley


## Multiple Metrics
### Multiple comparisons problem
_The more things you test at the same time, the more likely you are to see significant differences by chance_

**Problem**: Probability of any false positive increases as you increase number of metrics

**Solution**: Use higher confidence level for each metric

### Bonferroni Correlation
_A method used to counteract the problem of multiple comparisons_
*   No assumptions, simple
*   Problem:  too conservative - guaranteed to give

 at least as small as specified
*   The Bonferroni correction rejects the null hypothesis for each 

### Different strategies
#### **Familywise error rate (FWER)**
_Control probability that any metric shows a false positive_

#### **Control false discovery rate (FDR)**
_Out of all the statistically significant difference you declared, how many of them had a real difference_

Good to use when trying to detect significant changes across a large number of metrics.

Example: 200 metrics, cap FDR at 0.05. This means that you’re okay with 5 false positives in every experiment

**Example **

Experiment: Prompt students to contact coach more frequently

Metrics:
1. Probability that student signs up for coaching
2. How early students sign up for coaching
3. Average price paid per student

For 3 metrics, what is the chance of at least 1 false positive, with alpha= = 0.05?

**Method 1: Assuming independence among metrics** Will get an overestimate

**Method 2: Bonferroni Correlation**

Rejects the null hypothesis for each 

## Disappearing Launch Effect
Seasonality, holidays, novelty effect, change aversion, etc.

### Holdback
Launch change to everyone except a small holdback, and continue comparing their behavior.

### Cohort Analysis can help
As users discover/ adopt the change, their behavior and measured effect can change.

