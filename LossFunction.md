In a neural network classification task (like the Human Action Recognition you're working on), the **loss function** measures how well the model's predictions match the true labels. The most commonly used **loss function for multi-class classification** is:

---

### ✅ **Cross-Entropy Loss**

#### 🔹 In PyTorch:

```python
import torch.nn as nn

loss_fn = nn.CrossEntropyLoss()
```

* Used when the model’s output is raw scores (logits), and labels are **integers**, e.g.:

  ```python
  labels = torch.tensor([0, 2, 1])  # not one-hot
  output = model(inputs)  # shape: (batch_size, num_classes)
  loss = loss_fn(output, labels)
  ```

---

#### 🔹 In TensorFlow/Keras:

```python
from tensorflow.keras.losses import SparseCategoricalCrossentropy

loss_fn = SparseCategoricalCrossentropy(from_logits=True)
```

OR, if your labels are one-hot encoded:

```python
from tensorflow.keras.losses import CategoricalCrossentropy

loss_fn = CategoricalCrossentropy(from_logits=True)
```

---

### 🎯 Summary:

| Framework | Labels Type | Use This Loss                                     |
| --------- | ----------- | ------------------------------------------------- |
| PyTorch   | Integer     | `nn.CrossEntropyLoss()`                           |
| Keras     | Integer     | `SparseCategoricalCrossentropy(from_logits=True)` |
| Keras     | One-hot     | `CategoricalCrossentropy(from_logits=True)`       |

---

Let me know if you're using PyTorch or TensorFlow and whether your labels are **one-hot or integers**, and I can help you plug it into your training loop.
