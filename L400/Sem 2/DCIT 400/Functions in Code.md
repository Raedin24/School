# run1.py
- **transforms.Compose**: A function to chain multiple image transformation operations together. Here, `transforms.Resize((224, 224))` resizes the image to 224x224 pixels, and `transforms.ToTensor()` converts the image to a PyTorch tensor.
- **ImageFolder**: A dataset class for loading images from a directory where images are arranged in class-specific subdirectories.
- **DataLoader**: A PyTorch class that provides an efficient way to iterate over datasets.
- **torch.nn**: A PyTorch module containing neural network layers and loss functions.
- **torch.optim**: A PyTorch module containing optimization algorithms.
- **numpy**: A library for numerical computations.
- **tqdm**: A library to display progress bars.


---

# CSWin Transformer Documentation

## Overview
This document describes the CSWin Transformer model, a type of vision transformer that leverages cross-shaped windows to process images more effectively. The implementation includes modifications such as SSF (Spatial-Spectral Fusion) and CBAM (Convolutional Block Attention Module) for enhanced feature extraction capabilities.

## Modules and Functions

### 1. Mlp Class
Description: This class implements a Multilayer Perceptron (MLP) used in transformer blocks. It contains two linear transformations with a dropout and activation in between.
Parameters:
- in_features: Input feature dimension.
- hidden_features: Hidden layer feature dimension. Defaults to the input feature dimension if not specified.
- out_features: Output feature dimension. Defaults to the input feature dimension if not specified.
- act_layer: Activation function, defaulting to GELU.
- drop: Dropout rate.

### 2. LePEAttention Class
Description: Implements Locally-enhanced Positional Encoding (LePE) attention mechanism, which aims to improve positional encoding with local enhancements.
Parameters:
- dim: Dimension of the feature vectors.
- resolution: Resolution of the input feature map.
- idx: Index to determine the splitting strategy.
- split_size: Size to split the attention window.
- dim_out: Output dimension, defaults to input dimension.
- num_heads: Number of attention heads.
- attn_drop: Dropout rate for the attention weights.
- proj_drop: Dropout rate for the output projection.
- qk_scale: Scaling factor for the query-key dot product, defaults to the inverse square root of the head dimension.

### 3. CSWinBlock Class
Description: Basic building block of the CSWin Transformer, containing a LePE attention layer and an MLP.
Parameters:
- dim: Dimension of the feature vectors.
- reso: Resolution of the input feature map.
- num_heads: Number of attention heads.
- split_size: Size of the split in the attention mechanism.
- mlp_ratio: Ratio of the hidden dimension to the input dimension in the MLP.
- qkv_bias: Boolean indicating if bias should be added to the QKV linear transformations.
- qk_scale: Scale factor for query-key interactions.

### 4. Merge_Block Class
Description: Performs down-sampling and channel-wise normalization to prepare features for the subsequent transformer stage.
Parameters:
- dim: Dimension of the input feature vectors.
- dim_out: Dimension of the output feature vectors.

### 5. CSWinTransformer Class
Description: The main transformer model which integrates multiple stages of CSWinBlock, along with SSF and CBAM modules for advanced feature handling.
Parameters:
- img_size: Size of the input images.
- patch_size: Size of each patch.
- in_chans: Number of input channels.
- num_classes: Number of classes for classification.
- embed_dim: Dimensionality of the embedding layer.
- depth: List detailing the number of blocks at each stage.
- split_size: List detailing the split size at each stage.
- num_heads: List detailing the number of heads at each stage.
- mlp_ratio: MLP ratio as in CSWinBlock.
- qkv_bias: Indicates if bias should be added to the QKV transformations.
- qk_scale: Scale for query-key interactions.
- drop_rate: Dropout rate for embeddings.
- attn_drop_rate: Dropout rate for attention weights.
- drop_path_rate: Rate for stochastic depth.
- hybrid_backbone: Optional CNN backbone for a hybrid architecture.

### 6. img2windows and windows2img Functions
Description: Helper functions to convert images to window partitions and vice versa, facilitating the processing of local features.