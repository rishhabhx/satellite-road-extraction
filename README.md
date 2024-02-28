# Road Extraction from Satellite Images

This repository presents a deep learning model for road extraction from satellite images in the DeepGlobe road extraction dataset. The model leverages a hybrid architecture that combines the strengths of U-Net and Convolutional Neural Networks (CNNs).

**Table of Contents:**

* Introduction
* Architecture
* Implementation
* Results
* Future Work

## Introduction

Road extraction from satellite imagery plays a crucial role in various applications like autonomous vehicle navigation, urban planning, and infrastructure management. This project implements a hybrid deep learning model to achieve high-performance road extraction using:

* **U-Net:** This architecture captures spatial context through its contracting and expanding paths, preserving local and global features.

* **CNNs:** These networks learn high-level features from the input images.

## Architecture

The architecture combines U-Net and CNNs:

* **U-Net:**
  * **Encoder:** Captures features at different scales.
  * **Decoder:** Upsamples features and combines them with corresponding encoder features for precise localization.
  * **Skip connections:** Directly connect corresponding encoder and decoder features, preserving spatial information.
* **CNNs:** Extract high-level features from the input images.
* **Feature Fusion:** Combines features from U-Net and CNNs to leverage their complementary strengths.

## Implementation

The following steps outline the implementation:

1. **Data Loading:**
    * Load images and masks from the DeepGlobe dataset.
    * Resize and preprocess the data.

2. **Model Definition:**
    * Implement the hybrid architecture using the `unetBlock` and `Conv2dBlock` function:
        * Define the U-Net structure with encoder, decoder, and skip connections.
        * Include CNN layers for high-level feature extraction.
        * Implement feature fusion to combine U-Net and CNN features.
    * Compile the model with `optimizer = 'Adam', loss = 'binary_crossentropy', metrics = ['accuracy']`.

3. **Training:**
    * Train the model on the prepared data for a specified number of epochs. We used 83 to impliment the model.
    * Monitor training progress using metrics like loss and accuracy.

4. **Testing:**
    * Test the trained model on unseen data to assess its performance.
    * Visualize the predicted masks alongside the ground truth masks for qualitative evaluation.

5. **Evaluation:**
    * Evaluate the trained model on a separate validation or testing set.
    * Use metrics like precision, recall, F1-score, and intersection over union (IoU) to assess performance.
    * Visualize predicted masks alongside ground truth masks for qualitative evaluation.

<!-- TODO: Add images to the results part -->

## Results

The model achieved the following results:

* **Quantitative Results:**
  * Achieved an F1-score of 0.65 on the DeepGlobe road extraction dataset.
  * Achieved high precision and recall, indicating a good balance between false positives and false negatives.

* **Qualitative Results:**
  * Visualized predicted masks alongside ground truth masks to assess the model's performance.
  * Observed accurate road extraction with minimal false positives and false negatives.

## Future Work

* Experiment with different U-Net and CNN variations.
* Explore different data augmentation techniques or data sources.
* Investigate loss functions and optimization techniques tailored to the road extraction task.
* Consider post-processing steps to refine the predicted masks.
* Try different preprocessing methods.
