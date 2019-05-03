# Publishing Applications<a name="serverlessrepo-publishing-applications"></a>

When you publish a serverless application to the AWS Serverless Application Repository, you make it available for others to find and deploy\.

You first define your application with an *AWS Serverless Application Model \(AWS SAM\) template\.* When you define your application, you must consider whether consumers of your application will be required to acknowledge the application's capabilities\. For more information about using AWS SAM and acknowledging capabilities, see [Using AWS SAM with the AWS Serverless Application Repository](using-aws-sam.md)\.

You can publish serverless applications by using the AWS Management Console, the AWS SAM command line interface \(AWS SAM CLI\), or an AWS SDK\. To learn more about the procedures for publishing applications to the AWS Serverless Application Repository, see [How to Publish Applications](serverlessrepo-how-to-publish.md)\.

When you publish your application, it's initially set to *private*, which means that it's only available to the AWS account that created it\. To share your application with others, you must either set it to *privately shared* \(shared only with a specific set of AWS accounts\), or *publicly shared* \(shared with everyone\)\.

**Note**  
*Private* and *privately shared* applications are only available in the AWS Region that they're created in\. *Publicly shared* applications are available in all AWS Regions\. To learn more about sharing applications, see [Using Resource\-Based Policies for AWS Serverless Application Repository \(Application Policies\)](access-control-resource-based.md)\.

**Topics**
+ [Using AWS SAM with the AWS Serverless Application Repository](using-aws-sam.md)
+ [How to Publish Applications](serverlessrepo-how-to-publish.md)
+ [Sharing Lambda Layers](sharing-lambda-layers.md)