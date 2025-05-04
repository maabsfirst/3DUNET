

# 3D UNet Tumor Segmentation of Brain

This repository contains a Jupyter notebook for training and testing a 3D UNet model for brain tumor segmentation using the MONAI library. The notebook includes data preprocessing, model training, and evaluation steps.

## Table of Contents
- [Introduction](#introduction)
- [Dependencies](#dependencies)
- [Data Preparation](#data-preparation)
- [Model Architecture](#model-architecture)
- [Training](#training)
- [Evaluation](#evaluation)
- [Visualization](#visualization)
- [Augmentation](#augmentation)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Introduction
This project aims to segment brain tumors from 3D MRI scans using a 3D UNet model. The MONAI library is used for data preprocessing, model building, and training. The notebook demonstrates the complete workflow from data loading to model evaluation.

## Dependencies
To run this notebook, you need the following dependencies installed:
- Python 3.10
- PyTorch
- MONAI
- NumPy
- Matplotlib
- Nibabel

You can install the required packages using the following command:
```bash
pip install torch monai numpy matplotlib nibabel
```

## Data Preparation
The data should be organized into the following directory structure:
```
data_dir/
├── Train_Data/
│   ├── patient1.nii.gz
│   ├── patient2.nii.gz
│   └── ...
├── Train_Label/
│   ├── patient1.nii.gz
│   ├── patient2.nii.gz
│   └── ...
├── Test_Data/
│   ├── patient1.nii.gz
│   ├── patient2.nii.gz
│   └── ...
└── Test_Label/
    ├── patient1.nii.gz
    ├── patient2.nii.gz
    └── ...
```

The notebook includes a `prepare` function to preprocess the data, including loading images, ensuring channel-first format, resampling, intensity scaling, cropping, and resizing.

## Model Architecture
The model used is a 3D UNet with the following configuration:
- Spatial dimensions: 3
- Input channels: 4
- Output channels: 2
- Channels: (16, 32, 64, 128, 256)
- Strides: (2, 2, 2, 2)
- Number of residual units: 2
- Normalization: Batch normalization

## Training
The training process involves the following steps:
1. Data loading and preprocessing using MONAI transforms.
2. Model initialization and moving to the specified device (CPU or GPU).
3. Setting up the loss function (DiceLoss) and optimizer (Adam).
4. Training the model for a specified number of epochs with periodic evaluation on the test set.
5. Saving the best model based on the Dice metric.

## Evaluation
The evaluation is performed using the Dice metric. The notebook includes code to load the best model, perform inference on test data, and visualize the results.

## Visualization
The notebook provides visualization of the original MRI slices, ground truth segmentation labels, and predicted segmentation masks. This helps in qualitative assessment of the model's performance.

## Augmentation
Data augmentation techniques such as random affine transformations, rotations, flips, and Gaussian noise are applied to the training data to improve model robustness.

## Usage
To use this notebook:
1. Clone the repository.
2. Install the required dependencies.
3. Organize your data into the specified directory structure.
4. Open the notebook and run the cells to preprocess data, train the model, and evaluate performance.

## Contributing
Contributions to this project are welcome. Please open an issue or submit a pull request with your changes.

## License
This project is licensed under the MIT License.

---

