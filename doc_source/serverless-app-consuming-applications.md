# Consuming Applications \(Preview\)<a name="serverless-app-consuming-applications"></a>


|  | 
| --- |
|  To request access to the AWS Serverless ApplicationRepository, [sign up for the Preview](https://pages.awscloud.com/serverlessrepo-preview.html)\.   | 

Following, you can find out how to find and deploy serverless applications that have been published to the AWS Serverless ApplicationRepository\. You can browse for applications that are publicly available without having an AWS account by visiting the public site\. Alternatively, you can browse for applications from within the AWS Lambda console\.

## Browsing and Searching for Applications<a name="browse-and-search-applications"></a>

Find an application in the AWS Serverless ApplicationRepository by using the following procedure\.

**To find an application in the AWS Serverless ApplicationRepository**

1. Open the [AWS Serverless ApplicationRepository public home page](https://aws.amazon.com/serverless/serverlessrepo), or open the [AWS Lambda console](https://console.aws.amazon.com/lambda/) and choose **Severless Application Repository**\.

1. Browse or search for an application\.

1. Choose an application to get more details about it, such as its capabilities and the number of times it has been deployed by AWS customers\. 

1. \(Optional\) On the application detail page, view the Readme\.txt file or License\.txt file for the application, or choose the **View code** link to go to the GitHub page for applications that are publicly shared\. On the application GitHub page, you can view the application's source code, GitHub star rating, and GitHub user comments\.

1. On the application detail page, choose **Deploy**\. This takes you to the AWS Lambda console, where you can configure and deploy the application to your account\. Note that if you are on the public site, you will be prompted to sign in using a valid AWS account before proceeding\.

Find more information about deploying and configuring AWS Serverless ApplicationRepository applications in the following sections\.

## Deploying and Configuring Applications<a name="select-and-configure-applications"></a>

Deploy and configure an application in the AWS Serverless ApplicationRepository by using the following procedure\.

**To deploy and configure an application from the AWS Serverless ApplicationRepository**

1. After selecting an application and choosing **Deploy** from the AWS Serverless Application Repository page, you will be on the Lambda console page\.

1. Configure the application as required\. Application configurations vary\. For guidance on configuring the application, see the application’s readme\.txt file\.

   For example, requirements might include specifying the name of an Amazon DynamoDB table, an Amazon S3 bucket, or an Amazon API Gateway API that you want the application to have access to\.

1. Choose **Deploy**, and then wait for the application to be successfully deployed in your account\.

When an application has been successfully deployed, you can review the resources created using existing AWS tools\. You can also navigate to the Lambda Application Designer to customize the application as needed\. 