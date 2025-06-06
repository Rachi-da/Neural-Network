The term you're asking about is likely **"Perceptron"** — a fundamental concept in neural networks.

Let’s break it down simply:

---

### 🧠 What Is a Perceptron?

A **perceptron** is the **simplest type of artificial neural network**, created in the 1950s by **Frank Rosenblatt**.

It simulates how a **single neuron** in the brain works.

---

### 🔶 Structure of a Perceptron

A perceptron:

* Takes **multiple inputs**
* Applies **weights** to those inputs
* Adds a **bias**
* Calculates a **weighted sum**
* Passes the result through an **activation function**
* Produces a **binary output** (0 or 1)

---

### 🔧 Perceptron Formula

```text
output = activation(w₁x₁ + w₂x₂ + ... + wₙxₙ + bias)
```

* `x₁, x₂, ..., xₙ` = input values
* `w₁, w₂, ..., wₙ` = weights
* `bias` = a constant value
* `activation()` = usually a **step function** (outputs 1 if input > threshold, else 0)

---

### 🖼️ Example

Suppose you want to detect if a student will pass:

* **Inputs**:

  * x₁ = hours studied
  * x₂ = attendance %
* **Weights**:

  * w₁ = 0.6
  * w₂ = 0.4
* **Bias** = -0.5
* Output: 1 = pass, 0 = fail

---

### ✅ Important Notes

* A **single perceptron** can only solve **linearly separable problems** (like AND, OR).
* It **cannot** solve more complex tasks (like XOR) — for that, you need **multi-layer perceptrons (MLPs)**.

---

Would you like a diagram of a perceptron or a code example to try it yourself?
