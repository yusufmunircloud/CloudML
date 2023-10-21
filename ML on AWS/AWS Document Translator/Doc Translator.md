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
    - To this IAM Role lets attach the `S3FullAccess`, `TranslateFullAccess` and `CloudwatchFullAccess` policy. Note: Giving Full Access to any entity in AWS is usually never recommened nor best        practice, but for the ease of this project we will do so.
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/s3iam.png?raw=true)
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/translateiam.png?raw=true)
      ![](https://github.com/yusufmunircloud/AWS-Projects/blob/main/img/general/cwiam.png?raw=true)
    - Once you've added the proper permissions, click next, and lets give this role a name. For Eg. `LambdaTranslate`
    - Finally scroll down and click `Create Role`

      
### 3. Setting Up Lambda Function
  - Lets go to the Lambda service and click `Create Function`
  - Make the function set to `Author From Scratch`
  - Name your function. Eg. `DocTranslator`
  - For Runtime select `Python 3.9`
  - In Permissions click `Change Default Execution Role` and under that click `Use an Existing Role`. Then Select the IAM Role we made earlier you can find it through           search by typing in its name eg. LambdaTranslate
  - Once you found the role and selected it, Click `Create Function`
  - After your Function has successfully created, click `Add Trigger` and select the trigger to be `S3`, and select the S3 Input Bucket. Eg. `s3doc-inputbucket-2843`
  - Finally scroll down and acknowledge the recursivity warning and click add. Note: The acknowledgement is stating that if you select your bucket as the input and output bucket, it could cause your function to be in an infinite loop. For Eg. If i put an object(eg. image) in our bucket it would trigger the lambda function and then output it to the same bucket therefore triggering our function again resulting in a recursive and infinite loop.

## Code For Our Function
### 5. 
- In your Lambda function, click the code section. Delete the existing code and copy/paste this into it.
```
import json
import boto3

s3_client = boto3.client(service_name='s3')
translate = boto3.client('translate')



def translate_text(text, lang_code):
    result = translate.translate_text(
        Text=text,
        SourceLanguageCode='auto',
        TargetLanguageCode=lang_code
    )
    return result['TranslatedText']


def lambda_handler(event, context):
    file_name = event['Records'][0]['s3']['object']['key']
    bucketName=event['Records'][0]['s3']['bucket']['name']
    outfile="s3://outputtranslateddoc/{}".format(file_name)
    print("Event details : ",event)
    print("Input File Name : ",file_name)
    print("Input Bucket Name : ",bucketName)
    print("Output File Name : ",outfile)
    # get S3 object
    result = s3_client.get_object(Bucket=bucketName, Key=file_name) 
    #Read a text file line by line using splitlines object
    final_document_array = ""
    for line in result["Body"].read().splitlines():
        each_line = line.decode('utf-8')
        print("Input Line : ",each_line)
        if(each_line!=''):
            translated=translate_text(each_line, 'es')
            print("After translation : ",translated)
            final_document_array+=translated
            final_document_array+='\n\n'
    s3_client.put_object(Body=final_document_array, Bucket='outputtranslateddoc', Key=file_name)
    print("Done")
```
- On this line `outfile="s3://outputtranslateddoc/{}".format(file_name)` change the name of the s3 output bucket to match the name of your's, eg. `s3://myoutputbucket` and 
on the second to last line `s3_client.put_object(Body=final_document_array, Bucket='outputtranslateddoc', Key=file_name)` change the `Bucket='outputtranslateddoc'` to your the name of your output bucket eg. `Bucket='myoutputbucket'`

- This Lambda Function will transform your input file into spanish and output it to the output s3 bucket.
- I would highly recommend you try reading line by line and understanding what this code does, even if you don't know python.
  
## Deployment
### 5. Deploy the Lambda Function
- Once we have put our code into the Lambda Function code section, click `Deploy`

## Testing
### 6. Test the Translation
- To ensure everything works as expected, test the translation process. You can:
  - Upload some sample .txt files to the input S3 bucket.
  - Monitor the Lambda function's execution and check the translated documents in the output S3 bucket.
  - Verify the accuracy of the translations.


## Conclusion
Congratulations! You've successfully set up an AWS Document Translator project using Lambda, S3 buckets, and AWS Translate. This system can be a valuable asset for document translation tasks.

