Dataset

The study uses structural 3T MRI data from the Alzheimer's Disease Neuroimaging Initiative (ADNI).
The original MRI scans were available in NIFTI (.nii) format and were converted into 2D JPEG images for model training and evaluation.

Classes
Class	Description
AD	--  Alzheimer's Disease
MCI --	Mild Cognitive Impairment
CN	--  Cognitively Normal

MRI Slice Selection
Axial slices between layers 70 and 90 were selected from the MRI volumes.
This slice range was chosen because it captures anatomically relevant regions including the hippocampal and medial temporal areas, which are associated with changes observed in Alzheimer's Disease.

Dataset Split
The dataset was divided into:
80% — Training
20% — Testing
The same data partitioning and preprocessing conditions were maintained across the models to enable a fair comparison.

Note: The original MRI dataset is not included in this repository. Users interested in reproducing the experiments should obtain the appropriate data through the official ADNI data-access process and follow its applicable terms and requirements.
