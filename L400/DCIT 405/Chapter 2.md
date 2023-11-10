## Selection Bias
The practice of selectively choosing data in a way that leads to misleading conclusions
Forms:
	- *Data snooping* - Extensively hunting through data in search of something interesting
	- *Vast search effect* - Bias resulting from repeated data modeling, or modeling data with large numbers of predictor variables.
	- *Nonrandom sampling*
- Using a *holdout set* to validate performance can guard against selection bias.
- Use *target shuffling*, which is a permutation test, to test the validity of predictive associations that a model suggests
**Regression to the mean** - A phenomenon in successive measurements of a given variable where extreme observations tend to be followed by more central observations. Is a consequence of selection bias

## Sampling Distribution of a Statistic
Refers to the distribution of some sample statistic over many samples drawn from the same population
`Classical statistics is usually concerned with making inferences from samples to populations`
- *Sample statistic* - A metric calculated for a sample of data drawn from a larger population.
- *Data distribution* - The frequency distribution of **individual values** in a data set
- *Sampling distribution* - The frequency distribution of a **sample statistic** over many samples.
- *Central limit theorem* - The tendency of the sampling distribution to take a normal shape as the sample size rises
- *Standard error* - The variability of a sample statistic over many samples.
`Standard error is concerned with samples, whilst standard deviation is concerned with the variability of individual data values`

The distribution of a sample statistic is likely to be more regular and bell-shaped than the distribution of the data itself. The larger the sample, the narrower the distribution of the sample statistic.

#### Standard Error
A metric that sums up the variability in the sampling distribution. Can be estimated using the **standard deviation** of the sample values, and the **sample size**
Standard error = 
$$ SE = \frac{s}{\sqrt{n}} $$
As sample size increases, the standard error decreases. Known as the `square root of n rule`.