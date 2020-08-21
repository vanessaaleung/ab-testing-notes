# Metric Choice
to Refining Hypothesis

## Customer Funnel
*   Homepage Visits
*   Exploring the site
*   Create account
*   Complete

### Expanding Customer Funnel
Each stage is a metric
*   Homepage Visits
*   Course List Visits
*   Exploring the site
*   Visit to course pages
*   Create account
*   Enrollment
*   Coaching used
*   Completion
*   Jobs

Measured in 

*   Absolute number, the count
*   Usability, the rate
    *   E.g. increase the size of the button
*   Progression, the probability


## Click-Through-Rate (CTR)
_How often users find the button, how easy it is to find the button_

### Click-Through-Probability
_How often users went to the second page_

Don’t count double clicks, reload, and other issues.

Example

**Initial hypothesis**: Changing the “Start Now” button from orange to pink will increase how many students explore Audacity’s courses.

**Updated hypothesis**: Changing the “Start Now” button from orange to pink will increase the <span style="text-decoration:underline;">click-through-probability</span> of the button


## Invariant Checking
_Metrics that shouldn’t change across experiment and control_

_E.g. population, distribution_


## Evaluation
### High-Level Business Metrics
E.g. revenue, market share, # users

### Detailed Metrics
E.g. User experience

### Overall Evaluation Criterion (OEC)
Objective function, composite metric, weighted function that combines all the metrics.

### Difficult Metrics
*   Don’t have data
*   Take  too long

## [Gathering Additional Data](https://s3-us-west-2.amazonaws.com/gae-supplemental-media/additional-techniquespdf/additional_techniques.pdf)
_For brainstorming and validating ideas_

### External Data
*   Agencies
*   Research papers

### Gather Own Data
*   **User Experience Research (UER)**
    *   In-depth,  qualitative
    *   Use special equipment, e.g. track eyes movement
    *   Validate the results with retrospective analyses
*   **Surveys**
    *   More quantitative, not deep
    *   Users may not tell the truth
    *   Ensure the population is representative
    *   Wording of questions may affect answers
*   **Retrospective/observational analyses**
    *   Running analyses on the **<span style="text-decoration:underline;">existing</span>** set of observational data without an experiment structure 
    *   E.g. Experiments you’ve run, big spikes in business, etc.
*   **Focus group**
    *   Bring a bunch of users together for discussion
    *   Risk of groupthink
*   Talk with colleagues

### Human Evaluation
E.g. Pay people to rate the website

## Choosing a Technique
*   **Validating metrics: <span style="text-decoration:underline;">External data</span>** and** <span style="text-decoration:underline;">retrospective analyses</span>**. The data is usually collected over a large enough population that there are likely fewer sampling biases or other measurement issues
*   The bigger the decision, the more time you may want to invest in getting additional data
*   Issue of time: **<span style="text-decoration:underline;">retrospective analyses</span>**

## Defining a Metric
### Example

**Def #1** (Cookie probability):

**Def #2** (Pageview probability): 

**Def #3** (Rate)

## Filtering and Segmenting
Filter just the affected traffic

Compute metrics on different slices, e.g. countries, platforms, etc., to identify spam or fraud

E.g. Plot week-over-week, i.e. divide the data by last week’s data

E.g. Plot by country

## Summary Metrics
*   Sum and count
    *   E.g. # users who visited pages
*   Distributional: mean, median, 25th, 75th, 90th percentiles
    *   Mean age of users who visited pages
*   Probabilities and rates
    *   Probability: 0 or 1
    *   Rate: 0 or more
*   Ratios
    *   E.g. 


## Sensitivity  vs Robustness
- Mean is sensitive to outliers, not robust

- Median is robust but not sensitive to changes
