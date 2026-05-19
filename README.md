MNIST CNN Experiments
Project Overview

This project compares two CNN models for handwritten digit classification on the MNIST dataset:

Simple CNN
Enhanced CNN

The goal is to evaluate the impact of Batch Normalization and Dropout on performance.

Dataset
60,000 training images
10,000 test images
Image size: 28 × 28
Classes: 10 digits (0–9)
Data Split
Training: 48,000
Validation: 12,000
Test: 10,000
Preprocessing
transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.1307,), (0.3081,))
])
Hyperparameters
Batch Size: 32
Epochs: 5
Learning Rate: 0.001
Optimizer: Adam
Loss Function: CrossEntropyLoss
Models
Simple CNN
Conv2D (1 → 16)
ReLU
MaxPool
Conv2D (16 → 32)
ReLU
MaxPool
Flatten
Linear (1568 → 128)
ReLU
Linear (128 → 10)
Enhanced CNN
Conv2D (1 → 32)
BatchNorm
ReLU
MaxPool
Conv2D (32 → 64)
BatchNorm
ReLU
MaxPool
Dropout (0.25)
Flatten
Linear (3136 → 256)
ReLU
Dropout (0.5)
Linear (256 → 10)
Results
Model	Test Accuracy
Simple CNN	99.03%
Enhanced CNN	99.06%
Best Model

Enhanced CNN achieved the highest accuracy: 99.06%

Conclusion

Both models achieved excellent performance above 99% accuracy. The Enhanced CNN slightly outperformed the Simple CNN due to:

Batch Normalization
Dropout
More filters
Larger fully connected layer

Since MNIST is a simple dataset, the performance improvement was small.

Requirements
pip install torch torchvision matplotlib scikit-learn
وضح عم كده شويه
MNIST CNN Experiments
Project Overview

This project implements and compares two Convolutional Neural Network (CNN) models for handwritten digit classification using the MNIST dataset. The purpose is to study how architectural improvements such as Batch Normalization and Dropout affect model performance.

Dataset Information
Property	Value
Training Images	60,000
Test Images	10,000
Image Size	28 × 28 pixels
Classes	10 (digits 0–9)
Channels	1 (Grayscale)
Data Split

The original training set is divided into:

Training Set: 48,000 images (80%)
Validation Set: 12,000 images (20%)
Data Preprocessing
transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.1307,), (0.3081,))
])
ToTensor() converts images to PyTorch tensors.
Normalize() standardizes pixel values using the MNIST mean and standard deviation.
Hyperparameters
Parameter	Value
Batch Size	32
Epochs	5
Learning Rate	0.001
Optimizer	Adam
Loss Function	CrossEntropyLoss
Model Architectures
Simple CNN

A lightweight CNN with two convolutional layers followed by two fully connected layers.

Architecture:

Conv2D (1 → 16)
ReLU
MaxPool2D
Conv2D (16 → 32)
ReLU
MaxPool2D
Flatten
Linear (1568 → 128)
ReLU
Linear (128 → 10)
Enhanced CNN

An improved version of the Simple CNN with regularization and normalization techniques.

Additional Features:

Batch Normalization
Dropout
More convolutional filters
Larger fully connected layer

Architecture:

Conv2D (1 → 32)
BatchNorm2D
ReLU
MaxPool2D
Conv2D (32 → 64)
BatchNorm2D
ReLU
MaxPool2D
Dropout (0.25)
Flatten
Linear (3136 → 256)
ReLU
Dropout (0.5)
Linear (256 → 10)
Training Procedure

For each model:

Train for 5 epochs.
Compute training loss and accuracy.
Evaluate on the validation set after each epoch.
Test the final model on the test set.
Final Results
Model	Test Accuracy
Simple CNN	99.03%
Enhanced CNN	99.06%
Analysis

The Enhanced CNN achieved slightly better accuracy because:

Batch Normalization stabilizes and speeds up training.
Dropout reduces overfitting.
More filters extract richer features.
A larger fully connected layer increases model capacity.

The improvement is small because MNIST is a relatively simple dataset, and even basic CNNs perform extremely well.

Validation Curves

The project plots:

Validation Accuracy vs. Epochs
Validation Loss vs. Epochs

These plots show that both models converged quickly and achieved high accuracy with minimal overfitting.

Conclusion

Both CNN models performed exceptionally well, achieving over 99% test accuracy. The Simple CNN provided strong results with a simpler architecture, while the Enhanced CNN delivered the best performance with a final accuracy of 99.06%.

Requirements
pip install torch torchvision matplotlib scikit-learn
