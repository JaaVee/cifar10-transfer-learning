# CIFAR-10 Transfer Learning

## Overview

This project investigates the impact of different fine-tuning strategies using EfficientNetB0 pretrained on ImageNet and adapted to the CIFAR-10 dataset.

Instead of focusing solely on model accuracy, the objective was to evaluate how progressively unfreezing deeper layers affects performance, convergence and generalization.

The project follows a controlled experimental methodology, comparing multiple fine-tuning configurations under the same training conditions.

---

## Dataset

**Dataset:** CIFAR-10

Dataset characteristics:

* 10 image classes
* 60,000 RGB images
* 32×32 resolution
* Balanced class distribution

Classes:

* Airplane
* Automobile
* Bird
* Cat
* Deer
* Dog
* Frog
* Horse
* Ship
* Truck

---

## Objective

The main objective was to answer the following question:

> How much performance improvement can be achieved by progressively unfreezing more layers of a pretrained EfficientNetB0 model?

Three fine-tuning configurations were evaluated:

* 30 unfrozen layers
* 40 unfrozen layers
* 50 unfrozen layers

---

## Methodology

### Transfer Learning

The experiment used:

* EfficientNetB0 pretrained on ImageNet
* Frozen backbone initialization
* Custom classification head
* Data augmentation
* Fine-tuning with low learning rate

### Training Pipeline

1. Load pretrained ImageNet weights
2. Train classification head
3. Unfreeze selected backbone layers
4. Fine-tune using a smaller learning rate
5. Evaluate performance on the test set

### Optimization

Techniques used:

* Transfer Learning
* Fine-Tuning
* Data Augmentation
* Early Stopping
* Learning Rate Scheduling
* TensorFlow / Keras

---

## Results

| Experiment | Unfrozen Layers | Test Accuracy | Test Loss |
| ---------- | --------------- | ------------- | --------- |
| 1          | 30              | 92.86%        | 0.214     |
| 2          | 40              | 93.39%        | 0.197     |
| 3          | 50              | 93.50%        | 0.194     |

---

## Analysis

### Performance Improvement

Increasing the number of trainable layers consistently improved performance.

However, the gains became progressively smaller.

```text
30 → 40 layers : +0.53%

40 → 50 layers : +0.11%
```

This demonstrates a classic diminishing returns effect during fine-tuning.

---

### Transfer Learning Effectiveness

The results suggest that EfficientNetB0 already contained highly transferable visual representations learned from ImageNet.

Only a relatively small amount of additional adaptation was required to achieve strong CIFAR-10 performance.

---

### Engineering Insight

A key finding of this project is that:

> More trainable layers do not necessarily produce proportional performance gains.

The best-performing model achieved only a marginal improvement compared to the previous configuration despite increasing training complexity.

This highlights the importance of balancing:

* accuracy
* computational cost
* training time
* model complexity

---

## Key Takeaways

* Transfer Learning is highly effective on CIFAR-10.
* Fine-Tuning improves performance beyond feature extraction alone.
* Additional trainable layers generate diminishing returns.
* Model evaluation should consider both accuracy and efficiency.
* Controlled experimentation is essential for making informed engineering decisions.

---

## Best Result

**EfficientNetB0 — 50 Unfrozen Layers**

```text
Test Accuracy: 93.50%
Test Loss: 0.194
```

---

## Skills Demonstrated

* Deep Learning
* Transfer Learning
* Fine-Tuning
* TensorFlow / Keras
* Experimental Design
* Model Evaluation
* Performance Analysis
* Hyperparameter Exploration
* Engineering-Oriented Machine Learning

---

## Conclusion

This project demonstrates a complete transfer learning workflow using EfficientNetB0 on CIFAR-10.

Beyond achieving strong classification performance, the experiment provides practical insights into fine-tuning behavior and model adaptation.

The results show that pretrained models can achieve excellent performance with relatively limited retraining, while also illustrating the importance of evaluating performance gains against computational cost.

The most valuable outcome was not simply reaching 93.50% accuracy, but understanding how different fine-tuning strategies influence model performance and efficiency.
