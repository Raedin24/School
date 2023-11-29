A *digital image*  **I (r, c)** is represented as a *two-dimensional*  array of data, where each pixel value corresponds to the brightness of the image at the point (r, c).
- In linear algebra, **I** is known as a *matrix*, and one row or column is a *vector*.

## Image Types
1. Binary Image
	- Only takes two values ie. **black** and **white**, or **0** and **1**
	- Is a **1 bit/pixel** image, meaning it takes 1 binary digit to represent each pixel
2. Gray Scale Image
	- Known as **monochrome** or one-colour image
	- Only contains brightness information
	- Is a **8 bit/pixel** image, thus having **0 - 255**  levels of brightness
	`8 bit representation is because the byte(8 bits) is the standard small unit in computers`

**Creation of a Digital Image**
1. Analogue Image
2. Digital Sampling
3. Pixel Quantization
![[Pasted image 20231129090837.png]]

## Colour Image
A colour image can be modelled as *three bands* of monochrome image data.
- Each band of data corresponds to a different colour
- The information stored in the digital image data is the *brightness information*  in each spectral band
- The brightness information is displayed on the screen by picture elements that emit light energy corresponding to  that colour.
- Colour images are usually represented as RGB.
- The resulting colour image has **24 bits/pixel**, 8 bits for each colour band (red, green, and blue)

## Digital Image Formats
1. TIFF (.tif, .tiff)
	- Stands for *Tagged Image File Format*.
	- Is a *lossless* image format, meaning they do not compress or lose any image quality/information
	- Results in high-quality images but also larger file sizes
	- **Best for** high quality prints, professional publications, archival copies
	- Can save transparencies
2. Bitmap (.bmp)
	- Also called *BMP (Bitmap Image File)*
	- Developed by Microsoft for Windows
	- Is a *lossless* image format
	- High quality images with large file sizes
	- **Best for** high quality scans, archival copies.
	`BMP is proprietary(owned by Microsoft), hence TIFF is recommended for use.`
3. JPEG (.jpg, .jpeg)
	- Stands for *Joint Photographic Experts Groups*
	- Is a *lossy*  file format, meaning the image is compressed to make a smaller file.
	- The loss in quality is generally not noticeable.
	- **Best for** web images, non-professional printing, e-mail, powerpoints
	- **Special Attribute**: Can choose amount of compression when saving 