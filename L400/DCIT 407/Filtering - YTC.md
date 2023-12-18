- Filtering can be classified in to *linear*  and *non-linear*  filtering.
- Filtering is used in image enhancement for mainly noise removal
- Also used for 
	1. feature extraction
	2. feature enhancement
## 1. Mean Filter
- Simplest filter
- Gives equal weight to all pixels in the neighbourhood.
- A *weight*  is has the effect of *smoothing* the image
- Degree of smoothing is controlled by *absolute value of kernel size*
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
- The median filter is a special case of a **generalised order** or **rank** filter
- Rank filter is a *non-linear*  filter
- Steps:
	1. Define the neighbourhood of the target pixel
	2. Rank them in ascending order
	3. Choose the order of the filter (from ***1*** to ***N***)
	4. Set the filtered value to be equal to the value of the chosen rank pixel

## 3. Maximum and Minimum Filter
- **Order filters** that select the max and min values in the defined neighbourhood.
- Relatively effective at removing Gaussian noise, at the expense of image detail ( mostly the background lightening ).
- Salt and pepper-type noise have its high values amplified by a maximum filter.
## 4. Gaussian Filter
- Image is filtered using a discrete kernel 
- Kernel is derived from a radially symmetric form of continuous 2-D Gaussian function
- Has **2** parameters
	1. Discrete size of the kernel
	2. Value of the standard deviation of the function
- There is a trade-off between accurate function sampling and computational time required for implementation.
- Gaussian filters also smooth the image, similar to mean filters
- Degree of smoothing is controlled by *choice of standard deviation parameter*

## Filtering for edge detection 
- An edge is a discontinuity or gradient within the image. 
- Edge detection is a method of segmenting an image into regions based on discontinuity
- It allows the user to observe those features of an image where there is an abrupt change in grey level or texture,
`An abrupt change indicates the end of one region in the image and the beginning of another.`
- Makes use of differential operators  to detect changes in gradients
- Divided into two main categories
	1. **First-order** edge detection
	2. **Second-order** edge detection
`The sum of weights in a kernel must sum up to zero. This ensures that the kernel's response is 0 in completely smooth regions`

## First-order Edge Detection
Most common are
1. Roberts
2. Prewitt
3. Sobel
- Implemented as a combination of two kernels: one for *x-derivative*  and one for *y-derivative*
**Roberts operator**
- Commonly known as **Roberts-cross**
- One of the earliest methods for edge detection
- Calculates a simple 2D spatial gradient measurement on an image and highlights edge regions.
- Implemented using **2** convolution masks/kernels