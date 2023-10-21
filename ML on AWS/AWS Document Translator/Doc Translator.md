# AWS Document Translator Project with Lambda and AWS Translate

## Introduction
Welcome to the AWS Document Translator project. This guide will walk you through the process of setting up a document translation system using AWS services, including Lambda, S3 buckets, and AWS Translate.

## Prerequisites
Before getting started, ensure you have the following in place:
- An AWS account with the necessary permissions.
- Basic knowledge of AWS services.

## Project Setup
### 1. Create the input and output S3 Buckets
- **Input S3 Bucket:** Set up an S3 bucket for storing input documents.
  - Lets name our bucket: `s3doc-inputbucket-{random numbers}`. eg s3doc-inputbucket-2843. The random numbers at the end will ensure the name is globally unique.
  - Put the S3 Bucket in the `us-east-1` region or a region close to you
![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/s3configuration.png?raw=true)
  - Once you have added a name and appropriate region, leave all the default setting and scroll down to the bottom and click `Create Bucket`
    
![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/createbucket.png?raw=true)

- **Output S3 Bucket:** Set up an S3 bucket for storing the output documents.
  - Lets name our bucket: `s3doc-outputbucket-{random numbers}`. eg s3doc-outputbucket-1934. The random numbers at the end will ensure the name is globally unique.
  - Put the S3 Bucket in the `us-east-1` region or a region close to you
  - Once you have added a name and appropriate region, leave all the default setting and scroll down to the bottom and click `Create Bucket`.




### 2. Configure Lambda Function's IAM Execution Role
- **Permissions:** Setup the necessary permissions for the Lambda Function
    - Lets go to the IAM service and under the Roles section click `Create Role`
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/IAM.png?raw=true)
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/createrole.png?raw=true)
    - Next create the role for an AWS Service and make it for a Lambda Function
    - To this IAM Role lets attach the `S3FullAccess`  and `TranslateFullAccess` policy. Note: Giving Full Access to any entity in AWS is usually never recommened nor best        practice, but for the ease of this project we will do so.
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/s3iam.png?raw=true)
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/translateiam.png?raw=true)


      
### 3. Write Lambda Function Code
- In your Lambda function code, implement the logic to:
  - Retrieve documents from the input S3 bucket.
  - Use AWS Translate to translate the documents.
  - Store the translated documents in the output S3 bucket.

## AWS Translate Integration
### 4. Using AWS Translate
- In your Lambda function, integrate with AWS Translate. You'll need to:
  - Set up the Translate service.
  - Configure the translation settings.
  - Translate documents using the service.

## Deployment
### 5. Deploy the Lambda Function
- Deploy your Lambda function to AWS using the AWS Management Console, AWS CLI, or an automation tool of your choice.

## Testing
### 6. Test the Translation
- To ensure everything works as expected, test the translation process. You can:
  - Upload sample documents to the input S3 bucket.
  - Monitor the Lambda function's execution and check the translated documents in the output S3 bucket.
  - Verify the accuracy of the translations.

## Troubleshooting
### 7. Troubleshooting Tips
- If you encounter issues during the project, here are some common troubleshooting tips and solutions to help you resolve them.

## Conclusion
Congratulations! You've successfully set up an AWS Document Translator project using Lambda, S3 buckets, and AWS Translate. This system can be a valuable asset for document translation tasks.

## References
- Include links to AWS documentation and other resources you used during the project for further reference.

Feel free to customize this GitHub .md file with specific details, code examples, and additional explanations as needed. Good luck with your project!
