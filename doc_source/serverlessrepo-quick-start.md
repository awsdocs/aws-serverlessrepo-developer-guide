# Quick Start: Publishing Applications<a name="serverlessrepo-quick-start"></a>

This guide walks you through the steps to download, build, test and publish an example serverless application to the AWS Serverless Application Repository using AWS SAM CLI\. You can use this example application as a starting point for developing and publishing your own serverless application\.

## Overview<a name="serverlessrepo-quick-start-steps"></a>

The following steps outline how to download, build and publish a sample serverless application:

1. **Initialize**\. Download a sample application from template using `sam init`\.

1. **Test Locally**\. Test the application locally using `sam local invoke` and/or `sam local start-api`\. Note that with these commands, even though your Lambda function is invoked locally, it reads from and writes to AWS resources in the AWS Cloud\.

1. **Package**\. When you're satisfied with your Lambda function, bundle the Lambda function, AWS SAM template, and any dependencies into an AWS CloudFormation deployment package using `sam package`\. In this step you will also include information about the application that will be uploaded to AWS Serverless Application Repository\.

1. **Publish**\. Publish the application to the AWS Serverless Application Repository using `sam publish`\. At the conclusion of this step, you're able to view your application in AWS Serverless Application Repository and deploy it to the AWS Cloud using AWS Serverless Application Repository\.

The example [Hello World Application](#serverlessrepo-quick-start-hello-world) in the next section walks you through these steps in building and publishing a serverless application\.

## Hello World Application<a name="serverlessrepo-quick-start-hello-world"></a>

In this exercise, you download and test a Hello World serverless application that represents a simple API backend\. It has an Amazon API Gateway endpoint that supports a GET operation and a Lambda function\. When a GET request is sent to the endpoint, API Gateway invokes the Lambda function\. Then, AWS Lambda executes the function, which simply returns a `hello world` message\.

The application has the following components:
+ An AWS SAM template that defines two AWS resources for the Hello Word application: an API Gateway service with a GET operation, and a Lambda function\. The template also defines the mapping between the API Gateway GET operation and the Lambda function\. 
+ Application code that's written in Python\.

## Before You Begin<a name="serverlessrepo-quick-start-hello-world-prereq"></a>

Make sure that you have the required setup for this exercise:
+ You must have an AWS account with an IAM user that has administrator permissions\. See [Set Up an AWS Account](https://docs.aws.amazon.com/lambda/latest/dg/setup.html)\.
+ You must have the AWS SAM CLI \(command line interface\) installed\. See [Installing the AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-cli-install.html)\.
+ You must have version 1\.16\.77 or later of the AWS CLI installed\. See [Installing the AWS Command Line Interface](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)\.

## Step 1: Initialize the Application<a name="serverlessrepo-quick-start-hello-world-setup-local-app"></a>

In this section, you download the sample application, which consists of an AWS SAM template and application code\.

**To initialize the application**

1. Run the following command at an AWS SAM CLI command prompt\.

   ```
   sam init --runtime python3.6 
   ```

1. Review the contents of the directory that the command created \(`sam-app/`\): 
   + `template.yaml` – Defines two AWS resources that the Hello World application needs: a Lambda function and an API Gateway endpoint that supports a GET operation\. The template also defines mapping between the two resources\.
   + Content related to the Hello World application code:
     + `hello_world/` directory – Contains the application code, which returns `hello world` when you run it\.
**Note**  
For this exercise, the application code is written in Python, and you specify the runtime in the `init` command\. AWS Lambda supports additional languages for creating application code\. If you specify another supported runtime, the `init` command provides the Hello World code in the specified language, and a `README.md` file that you can follow along for that language\. For information about supported runtimes, see [Lambda Execution Environment and Available Libraries](https://docs.aws.amazon.com/lambda/latest/dg/current-supported-versions.html)\.

## Step 2: Test the Application Locally<a name="serverlessrepo-quick-start-hello-world-test-locally"></a>

Now that you have the AWS SAM application on your local machine, follow the steps below to test it locally\.

**To test the application locally**

1. Start the API Gateway endpoint locally\. You must run the following command from the directory that contains the `template.yaml` file\.

   ```
   sam-app> sam local start-api --region us-east-1
   ```

   The command returns an API Gateway endpoint, which you can send requests to for local testing\.

1. Test the application\. Copy the API Gateway endpoint URL, paste it in the browser, and choose **Enter**\. An example API Gateway endpoint URL is `http://127.0.0.1:3000/hello`\.

   API Gateway locally invokes the Lambda function that the endpoint is mapped to\. The Lambda function executes in the local Docker container and returns `hello world`\. API Gateway returns a response to the browser that contains the text\. 

**Exercise: Change the message string**

After successfully testing the sample application, you can experiment with making a simple modification: change the message string that's returned\.

1. Edit the `/hello_world/app.py` file to change the message string from `'hello world'` to `'Hello World!'`\.

1. Reload the test URL in your browser and observe the new string\.

You will notice that your new code is loaded dynamically, without your having restart the `sam local` process\.

## Step 3: Package the Application<a name="serverlessrepo-quick-start-hello-world-package-app"></a>

After testing your application locally, you use the AWS SAM CLI to create a deployment package and a packaged AWS SAM template\.

**Note**  
In the following steps, you create a \.zip file for the contents of the `hello_world/` directory, which contains the application code\. This \.zip file is the **deployment package** for your serverless application\. For more information, see [Creating a Deployment Package \(Python\)]( https://docs.aws.amazon.com/lambda/latest/dg/lambda-python-how-to-create-deployment-package.html) in the *AWS Lambda Developer Guide*\.

**To create a Lambda deployment package**

1. Add a `Metadata` section to your AWS SAM template file providing the required application information\. For more information about the `Metadata` section of AWS SAM templates, see [AWS SAM Template Metdata Section Properties](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-publishing-applications-metadata-properties.html) in *AWS Serverless Application Model Developer Guide*\.

   Here is an example `Metadata` section:

   ```
   Metadata:
     AWS::ServerlessRepo::Application:
       Name: my-app
       Description: hello world
       Author: user1
       SpdxLicenseId: Apache-2.0
       LicenseUrl: LICENSE.txt
       ReadmeUrl: README.md
       Labels: ['tests']
       HomePageUrl: https://github.com/user1/my-app-project
       SemanticVersion: 0.0.1
       SourceCodeUrl: https://github.com/user1/my-app-project
   ```

   The `LicenseUrl` and `ReadmeUrl` properties can either be references to local files \(as in the example above\), or they can be links to Amazon S3 buckets that already host these artifacts\.

1. Create an S3 bucket in the location where you want to save the packaged code\. If you want to use an existing S3 bucket, skip this step\.

   ```
   sam-app> aws s3 mb s3://bucketname
   ```

1. Create the Lambda function deployment package by running the following `package` AWS SAM CLI command\. 

   ```
   sam-app> sam package \
       --template-file template.yaml \
       --output-template-file packaged.yaml \
       --s3-bucket bucketname
   ```

   The command does the following:
   + Zips the contents of the `aws-sam/hello_world/` directory and uploads it to Amazon S3\.
   + Uploads the deployment package, README file, and LICENSE file to the Amazon S3 bucket specified by the `--s3-bucket` option\.
   + Outputs a new template file, called `packaged.yaml`, which you use in the next step to publish the application to AWS Serverless Application Repository\. The `packaged.yaml` template file is similar to the original template file \(`template.yaml`\), but has a key difference—the `CodeUri`, `LicenseUrl`, and `ReadmeUrl` properties point to the Amazon S3 bucket and objects that contains the respective artifacts\. The following snippet from an example `packaged.yaml` template file shows the `CodeUri` property: 

     ```
     HelloWorldFunction:
         Type: AWS::Serverless::Function # For more information about function resources, see https://github.com/awslabs/serverless-application-model/blob/master/versions/2016-10-31.md#awsserverlessfunction
         Properties:
           CodeUri: s3://bucketname/fbd77a3647a4f47a352fcObjectGUID
     
     ...
     ```

## Step 4: Publish the Application<a name="serverlessrepo-quick-start-hello-world-publish-app"></a>

Now that you've created the deployment package, you use it to publish the application to AWS Serverless Application Repository\.

**To publish the serverless application to the AWS Serverless Application Repository**
+ Execute the following command to publish the new application in AWS Serverless Application Repository with the first version created as 0\.0\.1\.

  ```
  sam-app> sam publish \
      --template packaged.yaml \
      --region us-east-1
  ```

**Note**  
The application will be created as private by default\. You must share the application before other AWS accounts will be allowed to view and deploy your application\. See **Next Steps** below for more details about sharing your application\.

## Next Steps<a name="serverlessrepo-quick-start-nextstep"></a>

Now that you have published your sample application, following are a few things you might want to do with it\.
+ **View Your Application in AWS Serverless Application Repository** – The output of the `sam publish` command will include a link to the AWS Serverless Application Repository directly to the detail page of your application\. You can also go to the AWS Serverless Application Repository landing page and search for your application\.
+ **Share Your Application** – Because your application is set to private by default, it is not visible to other AWS Accounts\. In order to share your application with others, you must either make it public or grant permission to a specific list of AWS Accounts\. For information on sharing your application using the AWS CLI see [AWS Serverless Application Repository Resource\-Based Policy Examples](security_iam_resource-based-policy-examples.md)\. For information on sharing your application using the console see [Sharing an Application](serverlessrepo-how-to-publish.md#share-application)\.

## More Information<a name="serverlessrepo-quick-start-moreinfo"></a>

For more information about the `Metadata` section of AWS SAM templates, `sam package` and `sam publish` commands of AWS SAM CLI, see [Publishing Applications Using AWS SAM CLI](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-publishing-applications.html) in the *AWS Serverless Application Model Developer Guide*\.