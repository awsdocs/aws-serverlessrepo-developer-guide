# Consuming Applications<a name="serverless-app-consuming-applications"></a>

Following, you can learn how to find and deploy serverless applications that have been published to the AWS Serverless Application Repository\. You can browse for applications that are publicly available without having an AWS account by visiting the [public site](https://aws.amazon.com/serverless/serverlessrepo)\. Alternatively, you can browse for applications from within the AWS Lambda console\.

## Browsing, Searching, and Deploying Applications<a name="browse-and-search-applications"></a>

Find, configure, and deploy an application in the AWS Serverless Application Repository by using the following procedure\.

**To find and configure an application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository public home page](https://aws.amazon.com/serverless/serverlessrepo), or open the [AWS Lambda console](https://console.aws.amazon.com/lambda/) and choose **Serverless Application Repository**\.

1. Browse or search for an application\.
**Note**  
To show applications that contain custom IAM roles or resource policies, select the **Show apps that create custom IAM roles or resource policies** checkbox\. For more information about custom IAM roles and resource policies, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\. 

1. Choose an application to view details such as its permissions, capabilities and the number of times it has been deployed by AWS customers\. 

   The deployment counts are shown for the AWS Region in which you are trying to deploy the application\.

1. On the application detail page, view the application's permissions and application resources by viewing the SAM template, license, and readme file\. On this page, you can also find the **Source code URL** link for applications that are publicly shared\.

1. Configure the application in the **Application settings** section\. For guidance on configuring a particular application, see that application’s readme file\. 

   For example, configuration requirements might include specifying the name of a resource that you want the application to have access to\. Such a resource might be an Amazon DynamoDB table, an Amazon S3 bucket, or an Amazon API Gateway API\.

1. Choose **Deploy**\. Doing this takes you to the **Deployment status** page\.
**Note**  
If necessary, you must select the **I acknowledge this application creates custom IAM roles or resource polices** checkbox before deploying the application, otherwise an error will result\. For more information about custom IAM roles and resource policies, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\. 

1. On the **Deployment status** page, you can view the progress of your deployment\. While waiting for your deployment to complete, you can search and browse for other applications, and return to this page through the Lambda console\.

After your application has been successfully deployed, you can review and manage the resources that have been created using existing AWS tools\. 

## Deleting Application Stacks<a name="delete-application-stack"></a>

To delete an application that you previously deployed using the AWS Serverless Application Repository, follow the same procedure as for deleting an AWS CloudFormation stack:
+ **AWS Management Console**: To delete an application using the AWS Management Console, see [Deleting a Stack on the AWS CloudFormation Console](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-delete-stack.html) in the *AWS CloudFormation User Guide\.*
+ **AWS CLI**: To delete an application using the AWS CLI, see [Deleting a Stack ](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-cli-deleting-stack.html)in the *AWS CloudFormation User Guide\.*