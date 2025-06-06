
# 📘 Introduction to Neural Networks

## 🔶 What is a Neural Network?

A **neural network** is a machine learning model inspired by the **human brain**. It's used to recognize patterns, classify data, and make predictions.

---

## 🔶 Basic Structure

A **neural network** has layers of **neurons**:

```
Input Layer → Hidden Layer(s) → Output Layer
```

Each layer contains **nodes (neurons)**, and each neuron:
- Takes input(s)
- Applies a **weight**
- Sums them up
- Applies an **activation function**
- Passes the result to the next layer

---

## 🔶 Simple Example

Predicting if a student will pass or fail:

- **Inputs (features):**
  - Study hours
  - Attendance

- **Output:**
  - 0 = Fail
  - 1 = Pass

---

## 🔶 How it Works

1. **Input Layer**:  
   Accepts input data (e.g., 4 hours of study, 80% attendance)

2. **Hidden Layers**:  
   Each neuron calculates:
   ```
   output = activation(weight1 * input1 + weight2 * input2 + bias)
   ```

3. **Activation Function**:  
   Adds non-linearity (e.g., ReLU, Sigmoid)

4. **Output Layer**:  
   Predicts the result (0 or 1)

5. **Training**:  
   Compare predicted output to actual result → compute **error**  
   → adjust weights using **backpropagation** and **gradient descent**

---

## 🔶 Key Concepts

| Term              | Meaning                                                                 |
|-------------------|-------------------------------------------------------------------------|
| **Neuron**        | Basic unit that performs a weighted sum and applies an activation       |
| **Weight**        | Importance of input (learned during training)                           |
| **Bias**          | Extra value added to allow flexibility                                  |
| **Activation**    | Function like `Sigmoid`, `ReLU` to decide whether a neuron fires        |
| **Loss Function** | Measures how wrong the output is                                        |
| **Backpropagation** | Algorithm to update weights by calculating gradients                  |
| **Epoch**         | One full pass over all training data                                    |

---

## 🔶 Python Example: Tiny Neural Net

```python
import numpy as np

# Sigmoid activation function
def sigmoid(x):
    return 1 / (1 + np.exp(-x))

# Inputs: [study hours, attendance]
X = np.array([[4, 80], [2, 60], [5, 90]])
y = np.array([[1], [0], [1]])

# Initialize weights randomly
weights = np.random.rand(2, 1)
bias = np.random.rand(1)

# Training loop
for epoch in range(1000):
    z = np.dot(X, weights) + bias
    prediction = sigmoid(z)

    # Error (Loss)
    error = prediction - y

    # Gradient descent (simplified)
    weights -= 0.01 * np.dot(X.T, error)
    bias -= 0.01 * np.sum(error)

print("Predictions after training:")
print(sigmoid(np.dot(X, weights) + bias))
```

---

# 📘 Continued Learning

## 🔷 The Neural Network is Exposed to a Simulated Scenario or Dataset

When training a neural network, we simulate real-world problems using data. This training dataset lets the model learn to make predictions or classifications based on patterns.

---

## 🔷 Activation Functions

Activation functions introduce non-linearity to the model. Common types:

- **Sigmoid**: Good for binary classification  
  `σ(x) = 1 / (1 + e^(-x))`
- **ReLU (Rectified Linear Unit)**: Most common in deep networks  
  `ReLU(x) = max(0, x)`
- **Tanh**: Similar to sigmoid, but outputs between -1 and 1

---

## 🔷 Backpropagation Math (Simplified)

Backpropagation is how the model learns by updating weights. Steps:

1. **Forward pass**: Calculate prediction.
2. **Compute loss**: Measure the error.
3. **Backward pass**: Use derivatives to compute gradients.
4. **Gradient Descent**: Update weights:
   ```
   weight = weight - learning_rate * gradient
   ```

---

## 🔷 Deeper Networks

Instead of one hidden layer, deeper networks use **multiple hidden layers**:

```
Input → Hidden Layer 1 → Hidden Layer 2 → ... → Output
```

This enables learning more complex patterns.

---

## 🔷 Using Keras (TensorFlow)

```python
from tensorflow.keras.models import Sequential
from tensorflow.keras.layers import Dense

model = Sequential()
model.add(Dense(16, input_dim=2, activation='relu'))
model.add(Dense(8, activation='relu'))
model.add(Dense(1, activation='sigmoid'))

model.compile(loss='binary_crossentropy', optimizer='adam', metrics=['accuracy'])

# Fit the model
model.fit(X, y, epochs=100, batch_size=1)
```

---

## 🔷 Using PyTorch

```python
import torch
import torch.nn as nn
import torch.optim as optim

class Net(nn.Module):
    def __init__(self):
        super(Net, self).__init__()
        self.fc1 = nn.Linear(2, 16)
        self.fc2 = nn.Linear(16, 8)
        self.fc3 = nn.Linear(8, 1)

    def forward(self, x):
        x = torch.relu(self.fc1(x))
        x = torch.relu(self.fc2(x))
        x = torch.sigmoid(self.fc3(x))
        return x

model = Net()
criterion = nn.BCELoss()
optimizer = optim.Adam(model.parameters(), lr=0.01)

# Dummy data
inputs = torch.tensor([[4.0, 80.0], [2.0, 60.0], [5.0, 90.0]])
labels = torch.tensor([[1.0], [0.0], [1.0]])

for epoch in range(100):
    optimizer.zero_grad()
    outputs = model(inputs)
    loss = criterion(outputs, labels)
    loss.backward()
    optimizer.step()
```

---

Let me know if you want to continue with Convolutional Neural Networks, RNNs, or other topics!
