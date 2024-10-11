- Is a type of **neural network**
- Combines CNNs and Transformers.
	- **CNNs** : Good at processing images. Can efficiently detect patterns (edges, shapes, textures) by scanning small parts of an image at a time (*convolution operation*)
	- **Transformers**: Good at understanding relationships and context over long sequences ( eg. text, parts of an image) using self attention.
- CCTs first use a small convolutional layer to break an image into small parts (patches) to learn low-level patterns, like a CNN
- Then uses a transformer block to focus on relationships between the patches to understand the overall structure

**Benefits**
1. Has fewer parametr