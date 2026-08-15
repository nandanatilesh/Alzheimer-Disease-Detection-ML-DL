# Alzheimer-Disease-Detection-ML-DL
Machine learning and deep learning approaches for Alzheimer's disease classification using brain imaging data.

### Using CNN, SVM, and Deep Transfer Learning Models

A comparative machine learning and deep learning study for classifying brain MRI images into **Alzheimer's Disease (AD), Mild Cognitive Impairment (MCI), and Cognitively Normal (CN)** categories.


## Project Overview

Alzheimer's Disease (AD) is a progressive neurodegenerative disorder associated with cognitive decline and memory impairment. Early detection can support timely intervention and improve the management of the disease.

This project investigates the use of **Machine Learning (ML) and Deep Learning (DL)** techniques for classifying structural brain MRI scans into three diagnostic categories:

* **AD** — Alzheimer's Disease
* **MCI** — Mild Cognitive Impairment
* **CN** — Cognitively Normal

The study compares six different models under a common preprocessing and evaluation framework to investigate the effect of model complexity and fitting behaviour on MRI classification performance.

## Objectives

The main objectives of this project are:

* To classify MRI images into AD, MCI, and CN categories.
* To investigate the effectiveness of 2D axial MRI slices for Alzheimer's classification.
* To compare classical Machine Learning and Deep Learning approaches.
* To evaluate the effect of model complexity on classification performance.
* To compare lightweight CNN and SVM models with deeper transfer-learning architectures.
* To analyse model performance using accuracy, precision, recall, F1-score, and confusion matrices.
* To study overfitting, underfitting, and generalization behaviour across different models.

## Dataset

The study uses structural **3T MRI data from the Alzheimer's Disease Neuroimaging Initiative (ADNI)**.

The original MRI scans were available in **NIFTI (`.nii`) format** and were converted into 2D JPEG images for model training and evaluation.

### Classes

| Class | Description               |
| ----- | ------------------------- |
| AD    | Alzheimer's Disease       |
| MCI   | Mild Cognitive Impairment |
| CN    | Cognitively Normal        |

### MRI Slice Selection

Axial slices between **layers 70 and 90** were selected from the MRI volumes.

This slice range was chosen because it captures anatomically relevant regions including the **hippocampal and medial temporal areas**, which are associated with changes observed in Alzheimer's Disease.

### Dataset Split

The dataset was divided into:

* **80% — Training**
* **20% — Testing**

The same data partitioning and preprocessing conditions were maintained across the models to enable a fair comparison.

> **Note:** The original MRI dataset is not included in this repository. Users interested in reproducing the experiments should obtain the appropriate data through the official ADNI data-access process and follow its applicable terms and requirements.


##  Methodology

## Models Used

### 1. Support Vector Machine (SVM)

An **RBF-kernel SVM** was used as a classical Machine Learning baseline.

The 2D MRI images were transformed into feature vectors before being provided to the SVM classifier.


### 2. Custom Convolutional Neural Network (CNN)

A custom CNN was developed using **TensorFlow and Keras**.

The architecture includes:

* Convolutional layers with **32, 64, and 128 filters**
* ReLU activation
* MaxPooling layers
* Flatten layer
* Dense layer with **128 neurons**
* Dropout with a rate of **0.3**
* Final Dense layer with **Softmax activation**
* Three output classes: AD, MCI, and CN


### 3. VGG16

A pretrained **VGG16 model with ImageNet weights** was used through transfer learning.

The convolutional base was used for feature extraction, while additional classifier layers were adapted for the three-class MRI classification task.

Dropout was used to reduce overfitting.


### 4. DenseNet121

**DenseNet121** was evaluated as a transfer-learning architecture.

The model uses dense connectivity and feature reuse, with additional classification layers adapted for AD/MCI/CN prediction.


### 5. ResNet50

A pretrained **ResNet50** architecture with ImageNet weights was evaluated.

The model incorporated:

* GlobalAveragePooling2D
* Dropout with a rate of 0.5
* Dense output layer
* Softmax activation
* Three-class classification

### 6. EfficientNetB7

**EfficientNetB7** was evaluated to investigate the effect of a substantially deeper and more computationally complex transfer-learning architecture.

The model used:

* Pretrained EfficientNetB7 base
* GlobalAveragePooling2D
* Dropout with a rate of 0.5
* Dense output layer
* Softmax activation


## Results

The models were evaluated using the same held-out test set.

| Model          |   Accuracy |  Precision |     Recall |   F1-Score |
| -------------- | ---------: | ---------: | ---------: | ---------: |
|    **CNN**     | **99.15%** | **0.9927** | **0.9914** | **0.9920** |
|    **SVM**     | **98.90%** | **0.9916** | **0.9887** | **0.9901** |
| VGG16          |     97.87% |     0.9821 |     0.9740 |     0.9780 |
| DenseNet121    |     90.80% |     0.9008 |     0.9220 |     0.9113 |
| ResNet50       |     67.74% |     0.7561 |     0.7273 |     0.7414 |
| EfficientNetB7 |     42.04% |     0.1401 |     0.3333 |     0.1973 |

---

## Key Findings

The experimental results show that the **custom CNN achieved the highest classification accuracy at 99.15%**, followed by SVM at 98.90% and VGG16 at 97.87%.

Some important observations were:

* The custom CNN achieved the best overall performance.
* SVM provided performance comparable to the CNN while using a classical ML approach.
* VGG16 achieved strong performance through transfer learning.
* DenseNet121 showed moderate performance with indications of overfitting.
* ResNet50 and EfficientNetB7 performed considerably worse under the experimental conditions.
* Greater model depth and complexity did not necessarily result in better classification performance.
* Targeted selection of axial slices helped retain relevant anatomical information while reducing computational requirements.
* The results demonstrate the importance of matching model complexity with the characteristics and size of the dataset.

## Model Fitting Analysis

Training and validation curves were analysed to investigate model fitting behaviour.

### CNN

The CNN accuracy increased rapidly and stabilized at a high level, while the training loss decreased substantially. The reported classification metrics indicate strong predictive performance.

### SVM

Five-fold validation showed stable and consistent performance across folds, indicating robust classification behaviour.

### VGG16

VGG16 demonstrated rapid improvement in accuracy during training and achieved strong overall classification performance.

### DenseNet121

DenseNet121 showed a noticeable gap between training and validation performance, indicating possible overfitting.

### ResNet50

ResNet50 showed high training performance but considerably lower and unstable validation performance, suggesting poor generalization under the experimental setup.

### EfficientNetB7

EfficientNetB7 demonstrated low performance on both training and validation data and did not show consistent improvement across epochs.

## Evaluation Metrics

The following metrics were used for model evaluation:

* **Accuracy**
* **Precision**
* **Recall**
* **F1-Score**
* **Confusion Matrix**
* **Training/Validation Accuracy**
* **Training/Validation Loss**
* **5-Fold Validation for SVM**


One of the major findings of this study is that **higher model complexity does not always lead to better performance**.

The custom CNN and SVM achieved the strongest results despite being considerably simpler than architectures such as ResNet50 and EfficientNetB7.

This suggests that:

* Dataset size matters when selecting model complexity.
* Domain-specific preprocessing can have a significant impact on performance.
* Carefully selected MRI slices may already contain highly discriminative information.
* Large pretrained architectures may not always transfer effectively to grayscale medical images.
* Simpler architectures can provide a useful balance between accuracy, computational cost, and interpretability.


## Technologies Used

* **Python**
* **TensorFlow**
* **Keras**
* **Scikit-learn**
* **NumPy**
* **Pandas**
* **Matplotlib**
* **Seaborn**
* **Pillow**
* **OpenCV**

## Future Scope

Potential future improvements include:

* Combining MRI with PET imaging and cognitive assessment data.
* Investigating **3D CNN** architectures.
* Applying explainable AI techniques such as **Grad-CAM** and saliency maps.
* Evaluating models on larger and more diverse datasets.
* Improving model generalization through advanced preprocessing and fine-tuning.
* Exploring clinically oriented validation using external datasets.


## Disclaimer

This project is intended for **academic and research purposes only**.

The models and results presented in this repository are **not a clinically validated diagnostic system** and should not be used as a substitute for professional medical diagnosis or treatment.


## Final Result

**Project:** MRI-Based Alzheimer's Disease Classification
**Task:** Three-Class MRI Classification
**Classes:** AD / MCI / CN
**Approaches:** Machine Learning + Deep Learning
**Best Reported Model:** Custom CNN
**Best Reported Accuracy:** 99.15%



*This repository documents a comparative investigation of machine learning and deep learning approaches for MRI-based Alzheimer's disease classification.*
