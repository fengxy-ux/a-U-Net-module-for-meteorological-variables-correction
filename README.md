Climate UNet Prediction

This repository contains scripts for building predictor and target datasets and evaluating a UNet model for climate prediction tasks.

The workflow includes:

Preparing predictor variables from model outputs

Preparing target variables from ERA5 data

Data augmentation using temporal random sampling

Evaluating UNet checkpoints

Data Processing
Predictor

Predictor datasets are generated from atmospheric variables (e.g., var1, var2) and saved as NetCDF files.

Key steps:

Load NetCDF data

Select target region

Compute climatology

Apply normalization

Save predictor dataset

Target

Target datasets are generated from ERA5 temperature data.

Processing steps:

Load ERA5 hourly data

Select target dates and spatial region

Apply normalization

Save as NetCDF dataset

Data Augmentation

To increase the number of training samples, a temporal sampling augmentation is applied.

For each year:

Randomly select 90% of the available hourly time steps

Compute the spatial average

Repeat 1000 times to generate augmented samples

This produces a large dataset suitable for training deep learning models.

UNet Model

A convolutional UNet architecture is used for prediction.

Model characteristics:

Encoder–decoder structure

Skip connections

Batch normalization

Dropout for regularization

The model predicts spatial fields with size:

(lat, lon)
