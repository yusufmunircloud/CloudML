## Getting Started with Price Prediction Project

To get started with our price prediction project, we're going to take data from a publicly accessible dataset, download it to our computer, and then perform data cleaning and processing. This ensures that when we upload it to our Amazon S3 bucket, the data is correctly formatted.

Additionally, we'll set up the foundation for our AWS environment by creating a SageMaker domain. This enables us to use Amazon SageMaker Canvas and set up an instance that we can log into and activate.

If you're excited to begin these foundational steps for our price prediction project, follow along for the next series of steps.

## Setting Up a Domain in Amazon SageMaker

To set up a domain in Amazon SageMaker, log into the AWS Management Console, navigate to SageMaker, and create a domain. This step is crucial for running SageMaker Canvas.
‣ Once in the domains section, click `Create Domain`
‣

## Creating an Execution Role for the Domain in Amazon SageMaker

Create an execution role for the domain to work with the necessary permissions across AWS. Ensure that the role has Amazon SageMaker full access and the required policies.

## Downloading Data from NASDAQ

Visit nasdaq.com to download data for our project. Choose a stock, such as Apple (AAPL), and download historical data for the past 10 years.

## Cleaning Up the Data Using Numbers

Use a tool like Numbers, Google Sheets, or Microsoft Excel to clean up the data. Add a "ticker" column, format columns to numbers, and save the file as a CSV.

## Uploading the Data to Amazon S3

Switch to the AWS Management Console, navigate to S3, and create a new bucket. Upload the CSV file to the bucket, which acts as scalable storage for our project.

## Adding Dataset to SageMaker Canvas

Check if your SageMaker domain is ready. Once confirmed, launch the SageMaker Canvas application from the domain. This creates a user interface for working with SageMaker.

## Recap

In summary, we created an S3 bucket, downloaded stock data from NASDAQ, uploaded it to our S3 bucket, and set up a SageMaker domain. Stay tuned for the next series of videos, where we'll explore working with SageMaker Canvas and running a model on our dataset.
