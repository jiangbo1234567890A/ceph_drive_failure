# Table of Contents
- [Hard Drive Failure Prediction](#hard-drive-failure-prediction)
    - Backblaze dataset
    - Ceph telemetry dataset
    - FAST dataset
- [SMART Metric Forecasting](#smart-metric-forecasting)
    - Backblaze dataset
    - Ceph telemetry dataset
    - FAST dataset
- [Alternate Dataset Explorations](#alternate-dataset-explorations)
- [Disk Health Analytics Package](#disk-health-analytics-package)


# Hard Drive Failure Prediction

## Backblaze Dataset
In this workstream, we used the backblaze data to train failure prediction models. The notebooks for this workstream are as follows:

- Data Understanding - what does the backblaze data look like, how to convert to and
from raw smartctl output
- Data Cleaning - deal with missing and incoherent data
- Feature Extraction and Model Training - create models
- Survival Analysis - experimental
- Clustering - experimental

## Ceph Telemetry Dataset
- forthcoming

## FAST Dataset
- forthcoming

# SMART Metric Forecasting

The goal of this workstream is to create forecasting models, that can predict the future values of individual SMART metrics. The idea is that the storage system operator/SME can manually decide whether or not to remove a disk based on their unique failure tolerance level.

## Backblaze Dataset
- Univariate Forecasting
- Multivariate Forecasting

## Ceph Telemetry Dataset
- forthcoming

## FAST Dataset
- forthcoming

# Alternate Dataset Explorations

## Ceph Telemetry Dataset

The failure prediction models created in this project are based on the open source Backblaze dataset. However, since this data is collected from just one company with a specific usage (backup), it might not be able to capture the various usage patterns of real ceph users. Therefore, the ceph team has been collecting anonymized SMART metrics from their users. We have worked with them to make this data publicly available here. Under this workstream, we explore this data and determine the best path forward for training models on it.

- Exploratory notebook

## FAST Dataset

According to some recent research, using performance data in addition to SMART data can help improve failure prediction models.

- Exploratory notebook

# Disk Health Analytics Package

package all models into a python module. make available for use by everyone. decouple ceph and ML code.