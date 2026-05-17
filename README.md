# MNIST CNN Experiments

## Project Overview

This project implements and compares two Convolutional Neural Network (CNN) architectures for handwritten digit classification using the MNIST dataset.

The main objective is to evaluate the effect of architectural improvements such as Batch Normalization and Dropout on classification performance.

### Models Implemented

1. **Simple CNN**
2. **Enhanced CNN**

---

## Dataset Information

The project uses the MNIST dataset, which contains grayscale images of handwritten digits from 0 to 9.

|          Property | Value          |
| ----------------: | :------------- |
|   Training Images | 60,000         |
|       Test Images | 10,000         |
|        Image Size | 28 × 28 pixels |
| Number of Classes | 10             |
|          Channels | 1 (Grayscale)  |

---

## Data Preprocessing

The following transformations are applied to each image:

```python
transform = transforms.Compose([
    transforms.ToTensor(),
    transforms.Normalize((0.1307,), (0.3081,))
])
```

### Explanation

* `ToTensor()` converts the image to a PyTorch tensor.
* `Normalize()` standardizes pixel values using the MNIST mean and standard deviation.

---

## Dataset Split

The original training set is split into:

|               Subset | Number of Images |
| -------------------: | ---------------: |
|   Training Set (80%) |           48,000 |
| Validation Set (20%) |           12,000 |
|             Test Set |           10,000 |

---

## Hyperparameters

|     Parameter |       Value      |
| ------------: | :--------------: |
|    Batch Size |        32        |
|        Epochs |         5        |
| Learning Rate |       0.001      |
|     Optimizer |       Adam       |
| Loss Function | CrossEntropyLoss |

---

# Model Architectures

## 1. Simple CNN

### Architecture

1. Conv2D (1 → 16, kernel size = 3, padding = 1)
2. ReLU
3. MaxPool2D (2 × 2)
4. Conv2D (16 → 32, kernel size = 3, padding = 1)
5. ReLU
6. MaxPool2D (2 × 2)
7. Flatten
8. Linear (1568 → 128)
9. ReLU
10. Linear (128 → 10)

### Description

This model is a lightweight CNN consisting of two convolutional layers followed by two fully connected layers.

---

## 2. Enhanced CNN

### Architecture

1. Conv2D (1 → 32)
2. BatchNorm2D
3. ReLU
4. MaxPool2D
5. Conv2D (32 → 64)
6. BatchNorm2D
7. ReLU
8. MaxPool2D
9. Dropout (0.25)
10. Flatten
11. Linear (3136 → 256)
12. ReLU
13. Dropout (0.5)
14. Linear (256 → 10)

### Description

This model extends the Simple CNN by:

* Increasing the number of filters.
* Using Batch Normalization for more stable training.
* Applying Dropout to reduce overfitting.
* Using a larger fully connected layer.

---

# Training Procedure

For each model, the following steps are performed for every epoch:

1. Set the model to training mode.
2. Perform forward propagation.
3. Compute the loss using CrossEntropyLoss.
4. Perform backpropagation.
5. Update weights using Adam.
6. Evaluate on the validation set.
7. Record loss and accuracy.

After completing all epochs, the model is evaluated on the test set.

---

# Training Results

## Simple CNN

| Epoch | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| ----: | ---------: | -------------: | --------------: | ------------------: |
|     1 |     0.1490 |         95.44% |          0.0590 |              98.10% |
|     2 |     0.0493 |         98.42% |          0.0489 |              98.43% |
|     3 |     0.0342 |         98.86% |          0.0392 |              98.72% |
|     4 |     0.0234 |         99.29% |          0.0347 |              98.94% |
|     5 |     0.0209 |         99.29% |          0.0344 |              98.93% |

### Final Test Accuracy

**99.03%**

---

## Enhanced CNN

| Epoch | Train Loss | Train Accuracy | Validation Loss | Validation Accuracy |
| ----: | ---------: | -------------: | --------------: | ------------------: |
|     1 |     0.2002 |         93.89% |          0.0612 |              97.99% |
|     2 |     0.0978 |         97.06% |          0.0449 |              98.63% |
|     3 |     0.0775 |         97.71% |          0.0418 |              98.71% |
|     4 |     0.0647 |         98.03% |          0.0365 |              98.97% |
|     5 |     0.0571 |         98.25% |          0.0301 |              99.03% |

### Final Test Accuracy

**99.06%**

---

# Final Comparison

|        Model | Test Accuracy |
| -----------: | ------------: |
|   Simple CNN |        99.03% |
| Enhanced CNN |        99.06% |

### Best Performing Model

**Enhanced CNN** achieved the highest accuracy.

---

# Analysis and Discussion

### Why Did Enhanced CNN Perform Better?

The Enhanced CNN achieved slightly better results because it includes:

* **Batch Normalization**: stabilizes and accelerates training.
* **Dropout**: reduces overfitting.
* **More Filters**: extracts richer image features.
* **Larger Fully Connected Layer**: increases learning capacity.

### Why Was the Improvement Small?

MNIST is a relatively simple dataset, so even a small CNN can achieve excellent accuracy. Therefore, advanced techniques produce only modest gains.

---

# Validation Curves

Two graphs were generated:

1. Validation Accuracy vs. Epochs
2. Validation Loss vs. Epochs

### Observations

* Both models converged quickly.
* Validation accuracy exceeded 98% after the first epoch.
* Validation loss steadily decreased.
* Overfitting was minimal.

---

# Conclusion

This project demonstrates that CNNs are highly effective for handwritten digit recognition.

### Key Findings

* Both models achieved excellent performance above 99% accuracy.
* The Simple CNN provided strong results with fewer parameters.
* The Enhanced CNN slightly outperformed the Simple CNN.
* Batch Normalization and Dropout improved generalization.

### Final Result

The best model, Enhanced CNN, achieved a test accuracy of **99.06%**.

---

# Requirements

Install the required libraries using:

```bash
pip install torch torchvision matplotlib scikit-learn
```


