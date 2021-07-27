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

<!-- ---

## Objective
The goal is to create predictive models using the Backblaze dataset to determine when a hard drive will fail. Ideally, the model should be able to predict the health of a hard drive in terms of "good" (>6 weeks till failure), "warning" (2-6 weeks till failure), and "bad" (<2 weeks till failure). This setup is similar to [DiskProphet](https://www.prophetstor.com/diskprophet/), a disk health prediction solution from ProphetStor.

At inference time, 6 days of SMART data (6 rows from the Backblaze dataset) will be available to feed to this multiclass classification model. How the model makes use of this is a design choice. It may predict on all 6 individually, or generate features using multiple days data, or use only the last day data, etc. For details on how this model would be integrated into Ceph (API, preprocessing at inference time, etc) see [this](https://github.com/ceph/ceph/tree/master/src/pybind/mgr/diskprediction_local).

**NOTE:** Although the end goal is a multiclass classifier, building a binary classifier ("no fail"/"fail") could be a good starting point in understanding the problem and setup. Additionally, data exploration and insightful analysis could also be useful. These would be welcome contributions to this project as well.


## Dataset
The Backblaze Hard Drive dataset will be used for this project. This dataset consists of daily snapshots of basic information, SMART metrics, and status (failure label) for the hard drives in the Backblaze data center. Details about this dataset can be found [here](https://www.backblaze.com/b2/hard-drive-test-data.html). To learn more about the SMART system and SMART metrics, see [this](https://en.wikipedia.org/wiki/S.M.A.R.T.) Wikipedia article.

--- -->

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