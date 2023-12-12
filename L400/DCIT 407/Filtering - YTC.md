- Filtering can be classified in to *linear*  and *non-linear*  filtering.
- Filtering is used in image enhancement for noise removal
## 1. Mean Filter
- Simplest filter
- Gives equal weight to all pixels in the neighbourhood.
- A *weight*  is has the effect of smoothing the image
- Replaces every pixel with the mean value of the neighbourhood
- Reasonably effective at removing **Gaussian noise**, at the expense of high-frequency image detail (ie. edges)
- Larger kernel sizes remove more noise but also degrade image quality
- Not effective for removing **salt and pepper noise**
- Disadvantages:
	- Not robust to large noise deviation in the image
	- Will cause blurring when the mean filter straddles an edge
`Salt and pepper noise is best dealt with using a measure that is robust to statistical outliers`
## 2. Median Filter
- Overcomes the limitations of the mean filter, but is more computationally expensive
- Replaces every pixel with the statistical median of its neighbourhood.
- Preserves high-frequency details
- Effective at eliminating isolated noise spikes (salt and pepper noise)
- Requires ordering of the values in the pixel neighbourhood at every pixel location, hence the computational cost

## Rank Filtering
