================================================================================
                   
                   CIFAR-10 Image Classification using CNN
                         Deep Learning Project - README

================================================================================
--------------------------------------------------------------------------------
PROJECT OVERVIEW
--------------------------------------------------------------------------------

This project implements a Convolutional Neural Network (CNN) to classify images
from the CIFAR-10 dataset into 10 different categories. The model is built using
TensorFlow and Keras and trained over 20 epochs.

--------------------------------------------------------------------------------
DATASET
--------------------------------------------------------------------------------

Dataset     : CIFAR-10 (via tensorflow.keras.datasets)
Classes     : 10 (airplane, automobile, bird, cat, deer, dog, frog, horse,
              ship, truck)
Image Size  : 32 x 32 x 3 (RGB)
Training Set: 50,000 images
Test Set    : 10,000 images
Preprocessing: Pixel values normalized to [0, 1] by dividing by 255.0

--------------------------------------------------------------------------------
MODEL ARCHITECTURE
--------------------------------------------------------------------------------

Model Type: Sequential CNN

Layer (Type)              Output Shape          Parameters
----------------------------------------------------------
Conv2D (32 filters, 3x3) (None, 30, 30, 32)    896
MaxPooling2D (2x2)        (None, 15, 15, 32)    0
Conv2D (64 filters, 3x3) (None, 13, 13, 64)    18,496
MaxPooling2D (2x2)        (None, 6, 6, 64)      0
Conv2D (128 filters,3x3) (None, 4, 4, 128)     73,856
Flatten                   (None, 2048)           0
Dense (64 units, ReLU)    (None, 64)             131,136
Dense (10 units, Softmax) (None, 10)             650
----------------------------------------------------------
Total Parameters          : 225,034 (~879 KB)
Trainable Parameters      : 225,034
Non-trainable Parameters  : 0

--------------------------------------------------------------------------------
TRAINING CONFIGURATION
--------------------------------------------------------------------------------

Optimizer       : Adam
Loss Function   : Sparse Categorical Crossentropy
Metric          : Accuracy
Epochs          : 20
Validation Split: 10% of training data (5,000 images)

--------------------------------------------------------------------------------
TRAINING RESULTS (SUMMARY)
--------------------------------------------------------------------------------

Epoch   Train Accuracy   Train Loss   Val Accuracy   Val Loss
--------------------------------------------------------------
1       44.98%           1.5016       52.78%         1.3242
5       72.70%           0.7808       70.20%         0.8755
10      81.75%           0.5153       72.18%         0.9195
15      88.23%           0.3292       71.10%         1.1032
20      92.29%           0.2128       70.38%         1.4038

Key Observations:
  - Training accuracy climbed steadily to ~92.3% by epoch 20.
  - Validation accuracy peaked around epoch 7 (~72.9%) and plateaued thereafter.
  - The growing gap between training and validation accuracy/loss from epoch 8
    onwards indicates OVERFITTING.

--------------------------------------------------------------------------------
VISUALIZATIONS
--------------------------------------------------------------------------------

Two plots are generated at the end of training:

1. Accuracy Plot
   - X-axis: Epochs
   - Y-axis: Accuracy
   - Lines: Training data vs. Validation data
   - Legend: lower right

2. Loss Plot
   - X-axis: Epochs
   - Y-axis: Loss
   - Lines: Training data vs. Validation data
   - Legend: lower right

--------------------------------------------------------------------------------
DEPENDENCIES
--------------------------------------------------------------------------------

  - Python 3.x
  - TensorFlow >= 2.x
  - Keras (bundled with TensorFlow)
  - Matplotlib
  - NumPy (implicit dependency)

Install dependencies:
  pip install tensorflow matplotlib
