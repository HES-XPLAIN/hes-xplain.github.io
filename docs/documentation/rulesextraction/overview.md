# Rules extraction

## Introduction

The **Rules Extraction** library is designed to enhance the interpretability of Convolutional Neural Networks (CNNs) by replacing their fully-connected layers with a small set of easily understandable rules. This approach aims to maintain a similar level of accuracy to the original network while providing greater transparency into the decision-making process of the model.

## Core Idea

Traditional CNNs, while powerful, are often criticized for being "black boxes," where understanding the decision-making process is challenging. The **Rules Extraction** method addresses this issue by translating the output of a CNN into human-readable rules. These rules help users gain insights into which features are most influential in the classification task, thus making the model's decisions more interpretable.

## Algorithm Overview

The algorithm can be summarized in three main steps:

1. **Feature Extraction using CNN**:
   - A pre-trained CNN, such as VGG-16, is used to extract feature representations from input images.
   - The feature activations from the last convolutional layer are averaged across a set of images to create a compact representation.

2. **Rule Generation using Random Forest**:
   - A Random Forest (RF) is trained using the extracted features, where each root-to-leaf path in the forest corresponds to a rule.
   - The RF essentially learns to mimic the decision-making process of the fully-connected layers of the CNN.

3. **Rule Ranking using Perceptron**:
   - The generated rules are then ranked based on their predictive utility using a simple perceptron model.
   - The perceptron assigns weights to the rules and optimizes them to minimize classification error with a penalty to avoid rule correlation.
   - The top-N rules are selected based on their ranking and used to classify new images through a majority vote.

## High-Level Explanation

- **CNN Feature Extraction**: The CNN serves as a feature extractor, transforming raw input images into high-dimensional feature vectors that capture important patterns relevant to the classification task.
  
- **Random Forest Rule Extraction**: The RF learns decision rules based on these features. Each tree in the forest captures different patterns, and the paths through these trees form logical "IF-THEN" rules that can be easily understood and analyzed.

- **Rule Optimization and Selection**: The perceptron further refines these rules by weighting their contributions to the classification decision. The most important rules are retained, offering a concise and interpretable model that approximates the original CNN's performance.

## Conclusion

The **Rules Extraction** library bridges the gap between model accuracy and interpretability by translating complex CNN decisions into simple, human-understandable rules. This method enables analysts to better understand and trust the outcomes of deep learning models, making it a valuable tool for tasks where interpretability is as crucial as performance.