# Application Deployment Permissions<a name="application-deployment-permissions"></a>

To deploy an application in the AWS Serverless Application Repository, you must have permission to do so\. There are three categories of applications that you have permissions to deploy:
+ **Private** – Applications that were created with the same account, and haven't been shared with any other account\. You have permission to deploy applications that were created using your AWS account\.
+ **Privately shared** – Applications that the publisher has explicitly shared with a specific set of AWS accounts\. You have permission to deploy applications that have been shared with your AWS account\.
+ **Publicly shared** – Applications that the publisher has shared with everyone\. You have permission to deploy any publicly shared application\.

You can only search and browse for applications that you have permissions for\. These include applications that were created using your AWS account, privately shared with your AWS account, and publicly shared\. All other applications aren't displayed for you\.

**Important**  
Applications that contain nested applications inherit the nested applications' sharing restrictions\. For example, suppose an application is publicly shared, but it contains a nested application that's only privately shared with the AWS account that created the parent application\. In this case, if your AWS account doesn't have permission to deploy the nested application, then you aren't able to deploy the parent application\. For more information about nested applications, see [Nested Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-nested-applications.html) in the *AWS Serverless Application Model Developer Guide*\.