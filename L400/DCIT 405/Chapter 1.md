# Elements of Structure Data
Two basics types of structured data
1. **Numeric** - Expressed on a numeric scale
	- *Discrete* - Integer values only
	- *Continuous* - Floating point values
2. **Categorical** - A specific set of values representing a set of possible categories
	- *Binary* - Special case of categorical data with only two categories
	- *Ordinal* - Has an explicit ordering
The data type is important in data analysis for determining the type of visual display, data analysis or statistical model to be used. In software, it acts as a signal on how to process the data
`The outcome is also known as the dependent variable`

# Estimates of Location
A basic step in exploring data is getting a typical value for each feature: an estimate of where most of the data is located. Usually the *mean* and the *median*
- **Weighted Mean**  - The sum of all values times a weight, divided by the sum of the weights
- **Trimmed Mean** - The average of all values after dropping a fixed number of extreme values. aka *Truncated Mean*
	Trimmed Mean =     $$	 \overline{x} = \frac{\sum ^{n-p}_{i = p+1^x(i)}}{n-2p}  $$
	- Eliminates the influence of extreme values
- **Weighted Median** - The value such that one-half of the sum of the weights lies above and below the sorted data
	Weighted mean = $$ \overline{x}_w = \frac{\sum^n_{i-1}{w_ix_i}}{\sum^n_{i=1}w_i}  $$
	Reasons for using a weighted mean
	- Some values are more variable than others. Highly variable observations are given a lowe 
- **Robust** - Not sensitive to extreme values/outliers