Results

The models were evaluated using the same held-out test set.

Model	Accuracy	Precision	Recall	F1-Score
CNN	99.15%	0.9927	0.9914	0.9920
SVM	98.90%	0.9916	0.9887	0.9901
VGG16	97.87%	0.9821	0.9740	0.9780
DenseNet121	90.80%	0.9008	0.9220	0.9113
ResNet50	67.74%	0.7561	0.7273	0.7414
EfficientNetB7	42.04%	0.1401	0.3333	0.1973


The experimental results show that the custom CNN achieved the highest classification accuracy at 99.15%, followed by SVM at 98.90% and VGG16 at 97.87%.

Some important observations were:
-> The custom CNN achieved the best overall performance.

-> SVM provided performance comparable to the CNN while using a classical ML approach.
-> VGG16 achieved strong performance through transfer learning.
-> DenseNet121 showed moderate performance with indications of overfitting.
-> ResNet50 and EfficientNetB7 performed considerably worse under the experimental conditions.
-> Greater model depth and complexity did not necessarily result in better classification performance.
-> Targeted selection of axial slices helped retain relevant anatomical information while reducing computational requirements.
-> The results demonstrate the importance of matching model complexity with the characteristics and size of the dataset.

Model Fitting Analysis
Training and validation curves were analysed to investigate model fitting behaviour.

CNN -- The CNN accuracy increased rapidly and stabilized at a high level, while the training loss decreased substantially. The reported classification metrics indicate strong predictive performance.

SVM -- Five-fold validation showed stable and consistent performance across folds, indicating robust classification behaviour.

VGG16 -- VGG16 demonstrated rapid improvement in accuracy during training and achieved strong overall classification performance.

DenseNet121 -- DenseNet121 showed a noticeable gap between training and validation performance, indicating possible overfitting.

ResNet50 -- ResNet50 showed high training performance but considerably lower and unstable validation performance, suggesting poor generalization under the experimental setup.

EfficientNetB7 -- EfficientNetB7 demonstrated low performance on both training and validation data and did not show consistent improvement across epochs.

Evaluation Metrics
The following metrics were used for model evaluation:
1. Accuracy
2. Precision
3. Recall
4. F1-Score
5. Confusion Matrix
6. Training/Validation Accuracy
7. Training/Validation Loss
8. 5-Fold Validation for SVM

