# CSWin Transformer for Facial Expression Recognition (FER)

This project implements a Fine-Tuned CSWin Transformer model for facial expression recognition using the RAF-DB and FERPlus dataset. The training process includes detailed and summary logging, Gaussian noise augmentation, and model checkpointing.

---

## Table of Contents

1. [Requirements](#^951814)
2. [Setup](README#^bed074)
3. [Dataset Preparation](#^4afccf)
4. [Running the Training Script](#^fbab93)
5. [Logging and Checkpoints](README#^476484)
6. [Evaluation](#^660351)

---

### 1. Requirements

^951814

The necessary libraries can be installed by running the `install_req.sh` script from terminal

---

### 2. Setup

^bed074

1. Clone this repository:
    
    ```bash
    git clone https://github.com/microsoft/CSWin-Transformer.git
    cd CSWin-Transformer
    ```
    
2. Replace the `install_req.sh` in the repo with the `install_req.sh` provided and run the script:
    
    ```bash
    bash ./install_req.sh
    ```
    
3. Download the pre-trained CSWin Transformer weights: Save the weights (`cswin_tiny_224.pth`) to the directory:
    
    ```bash
    path/to/weights
    ```
    

---

### 3. Dataset Preparation

^4afccf

1. Download the [RAF-DB dataset](https://www.kaggle.com/datasets/shuvoalok/raf-db-dataset).
    
2. Organize the dataset as follows:
    
    ```plaintext
    Project_Datasets/RAF-DB/DATASET/
    ├── train/
    │   ├── class_1/
    │   ├── class_2/
    │   ├── ...
    └── test/
        ├── class_1/
        ├── class_2/
        ├── ...
    ```
    
3. Organize the [FERPlus](https://gts.ai/dataset-download/ferplus-dataset/) dataset in the same manner, combining the train and validation

4. Set the paths to the dataset in the script:
    
    ```python
    train_dir = "path/to/train"
    test_dir = "path/to/test"
    ```
    

---

### 4. Running the Training Script

^fbab93

1. Ensure the checkpoint directory exists:
    
    ```bash
    mkdir -p path/to/checkpoint
    ```
    
2. Run the training script:
    
    ```bash
    python run3.py
    ```
    
3. Monitor training progress in the console and log files:
    
    - Detailed logs: `path/to/training.log`
    - Summary logs: `path/to/training_summary.log`

---

### 5. Logging and Checkpoints

^476484

1. **Logging:**
    
    - Training logs are stored in two files for detailed and summary logs.
    - Modify paths in the script to match your system if needed.
2. **Checkpoints:**
    
    - Checkpoints are saved automatically if validation accuracy improves.
    - The checkpoints include the following:
        - Model state
        - Optimizer state
        - Current epoch
        - Training loss
        - Validation accuracy
3. **Customizing Checkpoint Directory:** Update the `checkpoint_dir` variable in the script to set your preferred directory.
    

---

### 6. Evaluation

^660351

1. To evaluate the model:
    
    - The `evaluate_model()` function calculates predictions and metrics.
    - Use it directly in the script after training or load a saved checkpoint.
2. Loading a checkpoint for evaluation:
    
    ```python
    checkpoint_path = "/path/to/your/checkpoint.pth"
    checkpoint = torch.load(checkpoint_path)
    model.load_state_dict(checkpoint['model_state_dict'])
    ```
    
3. Calculate accuracy using the `calculate_accuracy()` utility.
    
    ```python
    val_preds, val_labels = evaluate_model(model, test_loader, device)
    val_accuracy = calculate_accuracy(val_preds, val_labels)
    print(f"Validation Accuracy: {val_accuracy:.2f}%")
    ```
    

---

For additional help or troubleshooting, refer to the detailed logs or contact the repository maintainer.