**Convolutional neural networks (CNN)** are best at processing images.
Consists of 2 parts
- *Convolutional  base* - Used to extract features from an image. Formed primarily of layers performing the convolution operation
- *Dense head* - Used to determine the class of the image. Formed primarily of dense layers
Goal of the network is to learn 2 things
1. Which features to extract from an image (base)
2. Which class goes with which feature (head)
CNNs are rarely trained from scratch. They often reuse the base of a pretrained model. The base is attached to an untrained head. ie. Use the part that has learned to extract features to learn new layers, then classify those.
> Reusing a pretrained model is known as *Transfer Learning*

