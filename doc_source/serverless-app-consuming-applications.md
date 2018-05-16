# Consuming Applications<a name="serverless-app-consuming-applications"></a>

Following, you can find out how to find and deploy serverless applications that have been published to the AWS Serverless Application Repository\. You can browse for applications that are publicly available without having an AWS account by visiting the [public site](https://aws.amazon.com/serverless/serverlessrepo)\. Alternatively, you can browse for applications from within the AWS Lambda console\.

## Browsing, Searching, and Deploying Applications<a name="browse-and-search-applications"></a>

Find, configure, and deploy an application in the AWS Serverless Application Repository by using the following procedure\.

**To find and configure an application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository public home page](https://aws.amazon.com/serverless/serverlessrepo), or open the [AWS Lambda console](https://console.aws.amazon.com/lambda/) and choose **Serverless Application Repository**\.

1. Browse or search for an application\.

1. Choose an application to view details such as its capabilities and the number of times it has been deployed by AWS customers\. \(Note: The deployment counts are shown for the region in which you are trying to deployment application\)

1. On the application detail page, you can view the application's permissions, application resources via the SAM template, license, and readme file\. You can also find the **Source code URL** link for applications that are publicly shared\.

1. Configure the application in the **Configure application parameters** section\. For guidance on configuring a particular application, see that application’s readme file\. For example, configuration requirements might include specifying the name of an Amazon DynamoDB table, an Amazon S3 bucket, or an Amazon API Gateway API that you want the application to have access to\.

1. Choose **Deploy**\. Doing this takes you to the **Deployment status** page\.

1. On the **Deployment status** page you can view the progress of your deployment\. While waiting for your deployment to complete, you can search and browse for other applications, and return to this page through the Lambda console\.

After your application has been successfully deployed, you can review and manage the resources that have been created using existing AWS tools\. 
