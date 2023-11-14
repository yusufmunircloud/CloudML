# Stock Price Prediction Project Documentation

## Overview

This comprehensive documentation guides you through the process of setting up the foundation for a stock price prediction project using Amazon SageMaker and AWS services. The project involves obtaining historical stock data, cleaning and processing the data, and setting up the necessary AWS infrastructure.

## Requirements

Before you begin, make sure you have the following:

- AWS account credentials.
- Access to the AWS Management Console.
- Basic understanding of Amazon SageMaker and S3.

## Step 1: Data Acquisition

### 1.1 Downloading Data from NASDAQ

1. Visit [nasdaq.com](https://www.nasdaq.com/).
2. Navigate to "Market Activity" > "Stocks."
3. Search for a stock symbol, e.g., "Apple (AAPL)."
4. Select "Historical Quotes" and choose a date range.
5. Download the historical data as a CSV file.

### 1.2 Organizing Local Data

1. Create a folder named "Data" in your project directory.
2. Save the downloaded CSV file into the "Data" folder.

## Step 2: Data Cleaning

### 2.1 Using Numbers (or Equivalent Tools)

1. Open the CSV file using a spreadsheet tool (e.g., Numbers, Excel, Google Sheets).
2. Add a new column named "ticker" with the value "AAPL" (or the chosen stock symbol).
3. Rename columns: "close" to "Market Close," "open" to "Market Open."
4. Format numerical columns to display as numbers with two decimals.

### 2.2 Saving Cleaned Data

1. Save the file in the preferred spreadsheet format (e.g., Numbers, Excel).
2. Export the cleaned data as a CSV file with Unicode UTF-8 encoding.

## Step 3: Setting Up AWS Infrastructure

### 3.1 Amazon SageMaker Domain

1. Navigate to the AWS Management Console.
2. In the search bar, type "SageMaker" and click on the service.
3. Go to "Domains" and create a new domain (if not already created).
4. Follow the prompts to set up the domain with a unique name.

### 3.2 Execution Role for SageMaker Domain

1. Create an execution role for the SageMaker domain.
2. Ensure the role has the "AmazonSageMakerFullAccess" policy attached.

### 3.3 Checking Domain Status

1. Confirm that the SageMaker domain is "In Service."

## Step 4: Uploading Data to Amazon S3

### 4.1 Creating an S3 Bucket

1. In the AWS Management Console, search for "S3" and click on the service.
2. Create a new bucket with a unique name and default settings.

### 4.2 Uploading Data to S3

1. Open the created bucket and upload the previously cleaned CSV file.
2. Verify that the file is successfully uploaded.

## Step 5: SageMaker Canvas

### 5.1 Launching SageMaker Canvas

1. Go to the SageMaker domain in the AWS Management Console.
2. Click on the domain and select "Canvas" from the available services.
3. Wait for the Canvas application to load.

### 5.2 Dataset Integration

1. Connect to the S3 bucket containing your dataset.
2. Import the uploaded CSV file into SageMaker Canvas for further analysis.

## Conclusion

This documentation comprehensively covered the entire process of setting up the foundation for a stock price prediction project. From obtaining data, cleaning it, and establishing AWS infrastructure to utilizing SageMaker Canvas for building and deploying machine learning models.

Stay tuned for the upcoming series of videos, where we will delve deeper into working with SageMaker Canvas and running models on the prepared dataset.

