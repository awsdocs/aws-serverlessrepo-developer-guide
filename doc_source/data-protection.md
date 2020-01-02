# Data Protection in the AWS Serverless Application Repository<a name="data-protection"></a>

The AWS Serverless Application Repository conforms to the AWS [shared responsibility model](http://aws.amazon.com/compliance/shared-responsibility-model/), which includes regulations and guidelines for data protection\. AWS is responsible for protecting the global infrastructure that runs all the AWS services\. AWS maintains control over data hosted on this infrastructure, including the security configuration controls for handling customer content and personal data\. AWS customers and APN partners, acting either as data controllers or data processors, are responsible for any personal data that they put in the AWS Cloud\. 

For data protection purposes, we recommend that you protect AWS account credentials and set up individual user accounts with AWS Identity and Access Management \(IAM\), so that each user is given only the permissions necessary to fulfill their job duties\. We also recommend that you secure your data in the following ways:
+ Use multi\-factor authentication \(MFA\) with each account\.
+ Use SSL/TLS to communicate with AWS resources\.
+ Set up API and user activity logging with AWS CloudTrail\.
+ Use AWS encryption solutions, along with all default security controls within AWS services\.
+ Use advanced managed security services such as Amazon Macie, which assists in discovering and securing personal data that is stored in Amazon S3\.

We strongly recommend that you never put sensitive identifying information, such as AWS account numbers, into free\-form fields such as an **Author name** field\. This includes when you work with the AWS Serverless Application Repository or other AWS services using the console, API, AWS CLI, or AWS SDKs\. Any data that you enter into the AWS Serverless Application Repository or other services might get picked up for inclusion in diagnostic logs\. When you provide a URL to an external server, don't include credentials information in the URL to validate your request to that server\.

For more information about data protection, see the [AWS Shared Responsibility Model and GDPR](http://aws.amazon.com/blogs/security/the-aws-shared-responsibility-model-and-gdpr/) blog post on the *AWS Security Blog*\.

## Encryption in Transit<a name="data-protection-intransit"></a>

AWS Serverless Application Repository API endpoints only support secure connections over HTTPS\. When you manage AWS Serverless Application Repository resources with the AWS Management Console, AWS SDK, or the AWS Serverless Application Repository API, all communication is encrypted with Transport Layer Security \(TLS\)\.

For a full list of API endpoints, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the *AWS General Reference*\.

## Encryption at Rest<a name="data-protection-atrest"></a>

The AWS Serverless Application Repository encrypts files that you upload to the AWS Serverless Application Repository, including deployment packages and layer archives\.