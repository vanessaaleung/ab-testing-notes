# Design
## Unit of Diversion
_What are the units of population of test and control_

_What unit needs to be consistent?_

*   User id
    *   Multiple accounts
*   Cookie
    *   Switch platform
    *   Clear cookies
*   Event
    *   E.g. refresh page
    *   When user invisible
*   Device id
    *   Only for mobile
    *   Not identifiable on different devices
*   IP address
    *   Different locations

## Consistency of Diversion
*   User visible
    *   User id
    *   Cookie
        *   Changes between sign in, signout
        *   Latency
*   IP address
    *   Test hosting provider


#### Unit of Analysis and Unit of Diversion
_When the unit of analysis and unit of diversion are the same, the variability tends to be lower and closer to the analytical estimate_


##### Unit of  Analysis
_The denominator of the metric_


##### Measure variability of a metric Example
1. Unit of diversion: query or cookie
2. Metric: 
3. Unit of analysis: query

*   Variability of cookie is much higher
*   


## Inter- vs. Intra-user Experiments
### Intra-user Experiments
_Expose the same user to the feature being on and off overtime and analyze how they behave in different time windows_

*   Choose comparable time windows

### Interleaved Experiments
_Expose the same user to the A and the B side at the same time_

*   E.g. rank ordered list


### Inter-user Experiments
_Get different people on the A and the B side, i.e. A/B testing_


## Target Population
_Who’s gonna be affected?_

_Only run the experiment on the affected traffic_

*   Restrict users
    *   when launch is expensive
    *   Not sure if the change works on old browsers
    *   Don’t want to overlap with other experiments, e.g. experiments in different countries
*   Same filters for control and test


### Example
New Zealand
---
Global
---
Is there a statistically significant difference 

in:

New Zealand (No) and Globally (No)?

*   Adding the unaffected traffic diluted the difference in global


## Cohort
_People who enter the experiment at the same time_

### Cohort vs. Population
Cohort is harder to analyze, need more data

*   Use when need stability, want to see if the changes have a real effect on users behavior relative to their history
*   Looking for learning effect
*   Examining user retention
*   Want to increase user activity
*   Anything requiring user to be established


## [Sizing](https://www.kaggle.com/vanessaleung/a-b-testing-sizing-calculation/edit/run/37896911)
### Reduce size of an experiment
*   Change unit of diversion to the same as unit of analysis
*   Target experiment to specific traffic


## Sample Size Calculator
[Link](https://www.evanmiller.org/ab-testing/sample-size.html)

*   Baseline conversion rate: estimated CTR
*   Minimum Detectable Effect: practical significance level, 

### Example
Answer
*   Baseline conversion rate: 

*   Minimum Detectable Effect: 

## Duration vs. Exposure
_The duration of the experiment is related to the proportion of the traffic sent through the experiment_

Why not run on all the traffic and get results quicker?

*   Safety & if not sure the feature will be published
*   Run a small experiment across multiple days to see how the differences are by weekdays/weekends/different times
*   Run longer with less traffic/users


## Learning Effect
_Measure whether the users are adapted to the change or not_

*   Change aversion
*   Novelty effect
