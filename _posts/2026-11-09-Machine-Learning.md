---
layout: post
title: "Machine Learning and Neural Networks - Ongoing Notes"
date: 2026-11-09
categories: [Machine Learning]
tags: [machine-learning, neural-networks]
description: "Learning notes on machine learning and neural networks."
published: true
---

# Introduction to Neural Networks

A neural network is a machine learning model that learns patterns and relationships from data.

We provide the neural network with training data consisting of inputs and their corresponding expected outputs. During training, the neural network adjusts its internal weights to minimize the difference between its predicted outputs and the expected outputs.

# How Neural Networks Work

1. **Input:** We provide input data (e.g., temperature, pressure and flow rate).
2. **Prediction:** The neural network processes the inputs using its current weights and produces a predicted output.
3. **Comparison:** The predicted output is compared with the expected output (target).
4. **Error calculation:** A loss function calculates how different the predicted output is from the expected output.
5. **Weight adjustment:** An optimization algorithm, typically gradient descent combined with backpropagation, adjusts the weights to reduce the error.
6. **Iteration:** This process repeats over many training examples and iterations (epochs) until the network has learned the underlying patterns.

# An Important Distinction

The network does not adjust the weights so that the input matches the output. Instead, it adjusts the weights so that its predicted output approaches the expected output.

# Ideas for Inputs and Outputs in Industrial Processes

Neural networks can be used in industrial processes to learn relationships between different process variables and predict desired outputs.
Some examples:

| Input variables | Expected output |
|---|---|
| Temperature, pressure and flow rate | Energy consumption |
| Upstream pressure and downstream pressure | Valve position |
| Flow rate and system pressure | Pump speed |
| Inlet humidity and temperature | Drying time |

These are illustrative examples. In a real application, the neural network would typically require historical process data, including the relevant inputs and corresponding measured outputs, to learn these relationships.

---

**Work in Progress**

# References

- [Introduction to Neural Networks - YouTube](https://www.youtube.com/watch?v=YmLp8qe87A0)
