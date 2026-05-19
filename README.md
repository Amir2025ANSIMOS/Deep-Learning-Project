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
