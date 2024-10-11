- Is a type of **neural network**
- Combines CNNs and Transformers.
	- **CNNs** : Good at processing images. Can efficiently detect patterns (edges, shapes, textures) by scanning small parts of an image at a time (*convolution operation*)
	- **Transformers**: Good at understanding relationships and context over long sequences ( eg. text, parts of an image) using self attention.
- CCTs first use a small convolutional layer to break an image into small parts (patches) to learn low-level patterns, like a CNN
- Then uses a transformer block to focus on relationships between the patches to understand the overall structure

**Benefits**
1. Has fewer parameters
2. More efficient than a traditional transformer
3. Better for small datasets
4. Better at handling images

# Pipeline
## 1. Data Preparation
- Resize and normalise images
- Perform data augmentation techniques (rotation, flipping, cropping, etc)
## 2. Patch Creation
- Use a convolutional layer to automatically process images into patches. This layer extracts low-level features (edges, textures, corners)
- Patches are passed into the transformer part of the architecture
## 3. Transformer Block
- Use *self-attention*  to capture global relationships between different parts of the image.
- Transformer analyses the full set of patches, which allows it to learn more global patterns.
## 4. Optimisation
- Use *loss function* (eg. cross-entropy) to measure how far the model's predictions are from the true labels.
- Use the error calculated by the loss function to adjust the model's weights. This includes adjusting both the convolutional and transformer layers using *backpropagation*.
- Use an *optimiser* (eg. Adam or SDG) to minimise the loss by updating the weights in small steps.
## 5. Training Loop
For each epoch:
- Process batches of training images
- Predict class label
- Calculate loss and adjust gradients using backpropagation
- Update the model weights for next round of training
## 6. Regularisation
- Add *dropout*  layers in the transformer block to prevent the model from overfitting.
- Use *weight decay*  to prevent weights from growing too large.
## 7. Learning Rate Schedules
- Adjust the *learning rate* dynamically as training progresses to help the model converge faster and more stably
## 8. Validation
- Evaluate the model on a validation set during training to see how well the model is generalising to unseen data
## 9. Testing
- Test the final version on a separate test set to evaluate its performance on completely unseen data