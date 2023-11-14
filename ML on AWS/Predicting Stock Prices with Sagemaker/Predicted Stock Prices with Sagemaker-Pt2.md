# Amazon SageMaker Canvas Pipeline Setup Documentation

Welcome to Pt2 for setting up your very own SageMaker Canvas pipeline. In this tutorial, we will guide you through the process of taking a dataset uploaded to your Amazon S3 bucket, configuring a model in SageMaker Canvas, and initiating a training job. By the end of this tutorial, you'll have a training job in progress, paving the way for predictive analysis.

## Prerequisites

Before you begin, ensure the following:

- Access to an AWS account.
- Dataset uploaded to an Amazon S3 bucket.
- Basic understanding of SageMaker Canvas.

## Step 1: Launching SageMaker Canvas

1. Access the SageMaker Canvas application from the AWS Management Console.
2. Upon loading, a welcome screen will appear,just click `Skip For Now`.

## Step 2: Model Creation

### 2.1 Naming and Type Selection

1. Navigate to `My Models` on the left sidebar.
2. Click `Create Model`
3. Name your model, e.g., `AAPL Prediction`
4. For Problem Type, Choose "Predictive Analysis" as the model type.
5. Click "Create."

## Step 3: Uploading Dataset to SageMaker Canvas

1. Navigate to "Datasets" on the left sidebar.
2. Create a new dataset by clicking `Create` and under the dropdown selecting `Tabular`, and then name your dataset, then click `Create` e.g., "APPLStockDataset"
3. Under `Data Source` Choose the S3 as the data source and select your S3 bucket.
4. Make sure the APPL stock .csv file is selected and click `Create Dataset`.
5. Ensure the first 100 rows are displayed correctly.
6. Finally click `Create dataset`

## Step 4: Model Configuration

### 4.1 Target Column Selection

1. Go back to the model configuration.
2. Under `My Models`, select your `APPL Predictions`, then go to "edit" and go to `Select`
3. Choose our `APPLStockDataset` or whatever you named your dataset we just created and click `Select dataset`.
4. In the dataset, under `column name` make sure to check `Ticker` and other values as well are checked off.
5. Under "Target Column," select "MarketClose" as the target column.

### 4.2 Time Series Model Configuration

1. Under `Model Type` click on "Configure Time Series Model."
2. Set "Ticker" as the Item ID.
3. Choose the timestamp column as "Date"
4. Specify a forecast horizon as `30 days`.
5. Enable holiday schedule and under `Country for Holidays` choose United States.
6. Click `Save` to save the configuration.

## Step 5: Initiating Quick Build

1. Go back to the model configuration.
2. Click "Quick Build" to start the training job.
3. Observe the progress and estimated completion time (14-20 minutes).

## Congratulations!

Congratulations! You've successfully set up your SageMaker Canvas pipeline for training a model on historical stock data. Once the training job is completed, you'll be able to analyze stock data and generate future predictions.
