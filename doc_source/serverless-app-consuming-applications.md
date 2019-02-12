# Consuming Applications<a name="serverless-app-consuming-applications"></a>

Following, you can learn how to find and deploy serverless applications that have been published to the AWS Serverless Application Repository\. You can browse for applications that are publicly available without having an AWS account by visiting the [public site](https://aws.amazon.com/serverless/serverlessrepo)\. Alternatively, you can browse for applications from within the AWS Lambda console\.

## Browsing, Searching, and Deploying Applications<a name="browse-and-search-applications"></a>

Find, configure, and deploy an application in the AWS Serverless Application Repository by using the following procedure\.

**To find and configure an application in the AWS Serverless Application Repository**

1. Open the [AWS Serverless Application Repository public home page](https://aws.amazon.com/serverless/serverlessrepo), or open the [AWS Lambda console](https://console.aws.amazon.com/lambda/) and choose **Serverless Application Repository**\.

1. Browse or search for an application\.
**Note**  
To show applications that contain custom IAM roles or resource policies, select the **Show apps that create custom IAM roles or resource policies** check box\. For more information about custom IAM roles and resource policies, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\. 

1. Choose an application to view details such as its permissions, capabilities, and the number of times it has been deployed by AWS customers\. 

   The deployment counts are shown for the AWS Region in which you are trying to deploy the application\.

1. On the application detail page, view the application's permissions and application resources by viewing the AWS SAM template, license, and readme file\. On this page, you can also find the **Source code URL** link for applications that are publicly shared\. If the application includes any nested applications, you can also view details of the nested applications on this page\.

1. Configure the application in the **Application settings** section\. For guidance on configuring a particular application, see that application’s readme file\. 

   For example, configuration requirements might include specifying the name of a resource that you want the application to have access to\. Such a resource might be an Amazon DynamoDB table, an Amazon S3 bucket, or an Amazon API Gateway API\.

1. Choose **Deploy**\. Doing this takes you to the **Deployment status** page\.
**Note**  
If necessary, you must select the **I acknowledge this application creates custom IAM roles or resource polices** check box before deploying the application\. Otherwise, an error will result\. For more information about custom IAM roles and resource policies, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\. 

1. On the **Deployment status** page, you can view the progress of your deployment\. While waiting for your deployment to complete, you can search and browse for other applications, and return to this page through the Lambda console\.

After your application has been successfully deployed, you can review and manage the resources that have been created using existing AWS tools\. 

## Application Deployment Permissions<a name="application-deployment-permissions"></a>

To deploy an application in the AWS Serverless Application Repository, you must have permission to do so\. There are three categories of applications that you have permissions to deploy:
+ **Private** – Applications that were created with the same account, and haven't been shared with any other account\. You have permission to deploy applications that were created using your AWS account\.
+ **Privately shared** – Applications that the publisher has explicitly shared with a specific set of AWS accounts\. You have permission to deploy applications that have been shared with your AWS account\.
+ **Publicly shared** – Applications that the publisher has shared with everyone\. You have permission to deploy any publicly shared application\.

To learn more about publishers sharing applications, see [Using Resource\-Based Policies for AWS Serverless Application Repository \(Application Policies\)](access-control-resource-based.md)\.

**Important**  
Applications that contain nested applications inherit the nested applications' sharing restrictions\. For example, suppose an application is publicly shared, but it contains a nested application that's only privately shared with the AWS account that created the parent application\. In this case, if your AWS account doesn't have permission to deploy the nested application, then you aren't able to deploy the parent application\. For more information about nested applications, see [Nested Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-nested-applications.html) in the *AWS Serverless Application Model Developer Guide*\.

## Deleting Application Stacks<a name="delete-application-stack"></a>

To delete an application that you previously deployed using the AWS Serverless Application Repository, follow the same procedure as for deleting an AWS CloudFormation stack:
+ **AWS Management Console**: To delete an application using the AWS Management Console, see [Deleting a Stack on the AWS CloudFormation Console](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-delete-stack.html) in the *AWS CloudFormation User Guide\.*
+ **AWS CLI**: To delete an application using the AWS CLI, see [Deleting a Stack ](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-cfn-cli-deleting-stack.html)in the *AWS CloudFormation User Guide\.*