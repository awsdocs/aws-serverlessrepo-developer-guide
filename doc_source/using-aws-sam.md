# Using the AWS Serverless Application Model \(AWS SAM\)<a name="using-aws-sam"></a>

The AWS Serverless Application Model \(AWS SAM\) is an open\-source framework that you can use to build [serverless applications](https://aws.amazon.com/serverless/) on AWS\.

A **serverless application** is a combination of Lambda functions, event sources, and other resources that work together to perform tasks\. Note that a serverless application is more than just a Lambda function—it can include additional resources such as APIs, databases, and event source mappings\. For more information about using AWS SAM to build your serverless application, see the [https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/)\.

The sections below list the **AWS Resources** and **Policy Templates** that are currently supported by AWS Serverless Application Repository\. 

## Supported AWS Resources in the AWS Serverless Application Repository<a name="supported-resources-for-serverlessrepo"></a>

Serverless applications that you publish to the AWS Serverless Application Repository can include additional AWS CloudFormation resources\. The following list is a complete list of supported AWS resources\.

If you would like to request an additional AWS resource to be supported, contact [AWS Support](https://console.aws.amazon.com/support/home#/)\.

**Important**  
If your application template contains one of the following custom IAM roles or resource policies, your application will not show up by default in search results\. Also, customers need to acknowledge the application's custom IAM roles or resource policies before they can deploy the application\. For more information, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\.   
The list of resources that this applies to are:  
**IAM roles: **[AWS::IAM::Group](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-iam-group.html), [AWS::IAM::InstanceProfile](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-instanceprofile.html), [AWS::IAM::Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), and [AWS::IAM::Role](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-role.html)\.
**Resource policies: ** [AWS::Lambda::LayerVersionPermission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-layerversionpermission.html), [AWS::Lambda::Permission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-permission.html), [AWS::Events::EventBusPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-events-eventbuspolicy.html), [AWS::IAM:Policy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-policy.html), [AWS::ApplicationAutoScaling::ScalingPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-applicationautoscaling-scalingpolicy.html), [AWS::S3::BucketPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-s3-policy.html), [AWS::SQS::QueuePolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sqs-policy.html), and [AWS::SNS:TopicPolicy](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-sns-policy.html)\.
If your application contains the [AWS::Serverless::Application](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template.html#serverless-sam-template-application) resource, customers need to acknowledge the application contains a **nested application** before they can deploy the application\. For more information about nested applications, see [Nested Applications](https://docs.aws.amazon.com/serverless-application-model/latest/developerguide/serverless-sam-template-nested-applications.html) in the *AWS Serverless Application Model Developer Guide*\. For more information about acknowledging capabilities, see [ Acknowledging Application Capabilities](acknowledging-application-capabilities.md)\.

**Supported AWS resources:**
+ `AWS::ApiGateway::Account`
+ `AWS::ApiGateway::ApiKey`
+ `AWS::ApiGateway::Authorizer`
+ `AWS::ApiGateway::BasePathMapping`
+ `AWS::ApiGateway::ClientCertificate`
+ `AWS::ApiGateway::Deployment`
+ `AWS::ApiGateway::DocumentationPart`
+ `AWS::ApiGateway::DocumentationVersion`
+ `AWS::ApiGateway::DomainName`
+ `AWS::ApiGateway::GatewayResponse`
+ `AWS::ApiGateway::Method`
+ `AWS::ApiGateway::Model`
+ `AWS::ApiGateway::RequestValidator`
+ `AWS::ApiGateway::Resource`
+ `AWS::ApiGateway::RestApi`
+ `AWS::ApiGateway::Stage`
+ `AWS::ApiGateway::UsagePlan`
+ `AWS::ApiGateway::UsagePlanKey`
+ `AWS::ApiGateway::VpcLink`
+ `AWS::AppSync::ApiKey`
+ `AWS::AppSync::DataSource`
+ `AWS::AppSync::GraphQLApi`
+ `AWS::AppSync::GraphQLSchema`
+ `AWS::AppSync::Resolver`
+ `AWS::ApplicationAutoScaling::ScalableTarget`
+ `AWS::ApplicationAutoScaling::ScalingPolicy`
+ `AWS::Athena::NamedQuery`
+ `AWS::CertificateManager::Certificate`
+ `AWS::CloudFormation::CustomResource`
+ `AWS::CloudFormation::WaitConditionHandle`
+ `AWS::CloudFront::CloudFrontOriginAccessIdentity`
+ `AWS::CloudFront::Distribution`
+ `AWS::CloudFront::StreamingDistribution`
+ `AWS::CloudWatch::Alarm`
+ `AWS::CloudWatch::Dashboard`
+ `AWS::CodeBuild::Project`
+ `AWS::CodePipeline::CustomActionType`
+ `AWS::CodePipeline::Pipeline`
+ `AWS::CodePipeline::Webhook`
+ `AWS::Cognito::IdentityPool`
+ `AWS::Cognito::IdentityPoolRoleAttachment`
+ `AWS::Cognito::UserPool`
+ `AWS::Cognito::UserPoolClient`
+ `AWS::Cognito::UserPoolGroup`
+ `AWS::Cognito::UserPoolUser`
+ `AWS::Cognito::UserPoolUserToGroupAttachment`
+ `AWS::Config::AggregationAuthorization`
+ `AWS::Config::ConfigRule`
+ `AWS::Config::ConfigurationAggregator`
+ `AWS::Config::ConfigurationRecorder`
+ `AWS::Config::DeliveryChannel`
+ `AWS::DataPipeline::Pipeline`
+ `AWS::DynamoDB::Table`
+ `AWS::ECR::Repository`
+ `AWS::Elasticsearch::Domain`
+ `AWS::Events::EventBusPolicy`
+ `AWS::Events::Rule`
+ `AWS::Glue::Classifier`
+ `AWS::Glue::Connection`
+ `AWS::Glue::Crawler`
+ `AWS::Glue::Database`
+ `AWS::Glue::DevEndpoint`
+ `AWS::Glue::Job`
+ `AWS::Glue::Partition`
+ `AWS::Glue::Table`
+ `AWS::Glue::Trigger`
+ `AWS::IAM::Group`
+ `AWS::IAM::InstanceProfile`
+ `AWS::IAM::ManagedPolicy`
+ `AWS::IAM::Policy`
+ `AWS::IAM::Role`
+ `AWS::IoT::Certificate`
+ `AWS::IoT::Policy`
+ `AWS::IoT::PolicyPrincipalAttachment`
+ `AWS::IoT::Thing`
+ `AWS::IoT::ThingPrincipalAttachment`
+ `AWS::IoT::TopicRule`
+ `AWS::KMS::Alias`
+ `AWS::KMS::Key`
+ `AWS::Kinesis::Stream`
+ `AWS::Kinesis::StreamConsumer`
+ `AWS::Kinesis::Streams`
+ `AWS::KinesisAnalytics::Application`
+ `AWS::KinesisAnalytics::ApplicationOutput`
+ `AWS::KinesisFirehose::DeliveryStream`
+ `AWS::Lambda::Alias`
+ `AWS::Lambda::EventSourceMapping`
+ `AWS::Lambda::Function`
+ `AWS::Lambda::LayerVersion`
+ `AWS::Lambda::LayerVersionPermission`
+ `AWS::Lambda::Permission`
+ `AWS::Lambda::Version`
+ `AWS::Logs::Destination`
+ `AWS::Logs::LogGroup`
+ `AWS::Logs::LogStream`
+ `AWS::Logs::MetricFilter`
+ `AWS::Logs::SubscriptionFilter`
+ `AWS::Route53::HealthCheck`
+ `AWS::Route53::HostedZone`
+ `AWS::Route53::RecordSet`
+ `AWS::Route53::RecordSetGroup`
+ `AWS::S3::Bucket`
+ `AWS::S3::BucketPolicy`
+ `AWS::SNS::Subscription`
+ `AWS::SNS::Topic`
+ `AWS::SNS::TopicPolicy`
+ `AWS::SQS::Queue`
+ `AWS::SQS::QueuePolicy`
+ `AWS::SSM::Association`
+ `AWS::SSM::Document`
+ `AWS::SSM::MaintenanceWindowTask`
+ `AWS::SSM::Parameter`
+ `AWS::SSM::PatchBaseline`
+ `AWS::SSM::ResourceDataSync`
+ `AWS::Serverless::Api`
+ `AWS::Serverless::Application`
+ `AWS::Serverless::Function`
+ `AWS::Serverless::LayerVersion`
+ `AWS::Serverless::SimpleTable`
+ `AWS::StepFunctions::Activity`
+ `AWS::StepFunctions::StateMachine`

## Policy Templates<a name="serverlessrepo-policy-templates"></a>

AWS SAM allows you to choose from a list of policy templates to scope the permissions of your Lambda functions to the resources that are used by your application\. Policy templates don't require additional customer acknowledgements to deploy the application\.

Below is the list of available policy templates, along with the permissions that are applied to each one\. AWS SAM automatically populates the placeholder items \(such as AWS Region and account ID\) with the appropriate information\.

If you want to request a new policy template to be added, do the following:

1. Submit a pull request against the policy\_templates\.json source file in the develop branch of the AWS SAM GitHub project\. You can find the source file here: [policy\_templates\.json](https://github.com/awslabs/serverless-application-model/blob/develop/samtranslator/policy_templates_data/policy_templates.json)\.

1. Submit an issue in the AWS SAM GitHub project that includes the reasons for your pull request and a link to the request\. Use this link to submit a new issue: [AWS Serverless Application Model: Issues](https://github.com/awslabs/serverless-application-model/issues/new)\.

## Examples<a name="policy-template-examples"></a>

There are two AWS SAM template examples in this section, one with a policy template that includes placeholder values, and one that does not include placeholder values\.

### Example 1: Policy Template with Placeholder Values<a name="policy-template-example-1"></a>

The following example shows that the `SQSPollerPolicy` policy template expects a `QueueName` as a resource\. The AWS SAM template retrieves the name of the"`MyQueue`" Amazon SQS queue, which can be created in the same application or requested as a parameter to the application\.

```
 1. MyFunction:
 2.   Type: 'AWS::Serverless::Function'
 3.   Properties:
 4.     CodeUri: ${codeuri}
 5.     Handler: hello.handler
 6.     Runtime: python2.7
 7.     Policies:
 8.       - SQSPollerPolicy:
 9.           QueueName:
10.             !GetAtt MyQueue.QueueName
```

### Example 2: Policy Template with No Placeholder Values<a name="policy-template-example-2"></a>

The following example contains the `CloudWatchPutMetricPolicy` policy template, which has no placeholder values\.

```
1. MyFunction:
2.   Type: 'AWS::Serverless::Function'
3.   Properties:
4.     CodeUri: ${codeuri}
5.     Handler: hello.handler
6.     Runtime: python2.7
7.     Policies:
8.       - CloudWatchPutMetricPolicy: {}
```

## SQSPollerPolicy: Gives Permissions to Poll an Amazon SQS Queue<a name="sqs-poller-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "sqs:ChangeMessageVisibility",
              "sqs:ChangeMessageVisibilityBatch",
              "sqs:DeleteMessage",
              "sqs:DeleteMessageBatch",
              "sqs:GetQueueAttributes",
              "sqs:ReceiveMessage"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:sqs:${AWS::Region}:${AWS::AccountId}:${queueName}",
                {
                  "queueName": {
                    "Ref": "QueueName"
                  }
                }
              ]
            }
          }
        ]
```

## LambdaInvokePolicy: Gives Permission to Invoke a Lambda Function, Alias, or Version<a name="lambda-invoke-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "lambda:InvokeFunction"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:lambda:${AWS::Region}:${AWS::AccountId}:function:${functionName}*",
                {
                  "functionName": {
                    "Ref": "FunctionName"
                  }
                }
              ]
            }
          }
        ]
```

## CloudWatchPutMetricPolicy: Gives Permissions to Put Metrics to CloudWatch<a name="cloudwatch-put-metric-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "cloudwatch:PutMetricData"
            ],
            "Resource": "*"
          }
        ]
```

## EC2DescribePolicy: Gives Permission to Describe Amazon EC2 Instances<a name="ec2-describe-policy"></a>

```
         "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "ec2:DescribeRegions",
              "ec2:DescribeInstances"
            ],
            "Resource": "*"
          }
        ]
```

## DynamoDBCrudPolicy: Gives Create/Read/Update/Delete Permissions to a DynamoDB Table<a name="dynamo-db-crud-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "dynamodb:GetItem",
              "dynamodb:DeleteItem",
              "dynamodb:PutItem",
              "dynamodb:Scan",
              "dynamodb:Query",
              "dynamodb:UpdateItem",
              "dynamodb:BatchWriteItem",
              "dynamodb:BatchGetItem"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}",
                {
                  "tableName": {
                    "Ref": "TableName"
                  }
                }
              ]
            }
          }
        ]
```

## DynamoDBReadPolicy: Gives Read\-Only Access to a DynamoDB Table<a name="dynamo-db-read-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "dynamodb:GetItem",
              "dynamodb:Scan",
              "dynamodb:Query",
              "dynamodb:BatchGetItem"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}",
                {
                  "tableName": {
                    "Ref": "TableName"
                  }
                }
              ]
            }
          }
        ]
```

## SESSendBouncePolicy: Gives SendBounce Permission to an Amazon SES Identity<a name="ses-send-bounce-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "ses:SendBounce"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:ses:${AWS::Region}:${AWS::AccountId}:identity/${identityName}",
                {
                  "identityName": {
                    "Ref": "IdentityName"
                  }
                }
              ]
            }
          }
        ]
```

## ElasticsearchHttpPostPolicy: Gives POST Permissions to Amazon Elasticsearch Service<a name="elastic-search-http-post-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "es:ESHttpPost"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:es:${AWS::Region}:${AWS::AccountId}:domain/${domainName}",
                {
                  "domainName": {
                    "Ref": "DomainName"
                  }
                }
              ]
            }
          }
        ]
```

## S3ReadPolicy: Gives Read Permissions to Objects in the Amazon S3 Bucket<a name="s3-read-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "s3:GetObject",
              "s3:ListBucket",
              "s3:GetBucketLocation",
              "s3:GetObjectVersion",
              "s3:GetLifecycleConfiguration"
            ],
            "Resource": [
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:s3:::${bucketName}",
                  {
                    "bucketName": {
                      "Ref": "BucketName"
                    }
                  }
                ]
              },
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:s3:::${bucketName}/*",
                  {
                    "bucketName": {
                      "Ref": "BucketName"
                    }
                  }
                ]
              }
            ]
          }
        ]
```

## S3CrudPolicy: Gives Create/Read/Update Permissions to Objects in the Amazon S3 Bucket<a name="s3-crud-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "s3:GetObject",
              "s3:ListBucket",
              "s3:GetBucketLocation",
              "s3:GetObjectVersion",
              "s3:PutObject",
              "s3:GetLifecycleConfiguration",
              "s3:PutLifecycleConfiguration",
              "s3:DeleteObject"
            ],
            "Resource": [
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:s3:::${bucketName}",
                  {
                    "bucketName": {
                      "Ref": "BucketName"
                    }
                  }
                ]
              },
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:s3:::${bucketName}/*",
                  {
                    "bucketName": {
                      "Ref": "BucketName"
                    }
                  }
                ]
              }
            ]
          }
        ]
```

## AMIDescribePolicy: Gives Permissions to Describe Amazon Machine Images \(AMIs\)<a name="ami-describe-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "ec2:DescribeImages"
            ],
            "Resource": {
              "Fn::Sub": "arn:${AWS::Partition}:ec2:${AWS::Region}:${AWS::AccountId}:image/*"
            }
          }
        ]
```

## CloudFormationDescribeStacksPolicy: Gives Permission to Describe AWS CloudFormation Stacks<a name="cloud-formation-describe-stacks-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "cloudformation:DescribeStacks"
            ],
            "Resource": {
              "Fn::Sub": "arn:${AWS::Partition}:cloudformation:${AWS::Region}:${AWS::AccountId}:stack/*"
            }
          }
        ]
```

## RekognitionDetectOnlyPolicy: Gives Permission to Detect Faces, Labels, and Text<a name="rekognition-detect-only-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "rekognition:DetectFaces",
              "rekognition:DetectLabels",
              "rekognition:DetectModerationLabels",
              "rekognition:DetectText"
            ],
            "Resource": "*"
          }
        ]
```

## RekognitionNoDataAccessPolicy: Gives Permission to Compare and Detect Faces and Labels<a name="rekognition-no-data-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "rekognition:CompareFaces",
              "rekognition:DetectFaces",
              "rekognition:DetectLabels",
              "rekognition:DetectModerationLabels"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:rekognition:${AWS::Region}:${AWS::AccountId}:collection/${collectionId}",
                {
                  "collectionId": {
                    "Ref": "CollectionId"
                  }
                }
              ]
            }
          }
        ]
```

## RekognitionReadPolicy: Gives Permission to List and Search Faces<a name="rekognition-read-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "rekognition:ListCollections",
              "rekognition:ListFaces",
              "rekognition:SearchFaces",
              "rekognition:SearchFacesByImage"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:rekognition:${AWS::Region}:${AWS::AccountId}:collection/${collectionId}",
                {
                  "collectionId": {
                    "Ref": "CollectionId"
                  }
                }
              ]
            }
          }
        ]
```

## RekognitionWriteOnlyAccessPolicy: Gives Permission to Create Collection and Index Faces<a name="rekognition-write-only-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "rekognition:CreateCollection",
              "rekognition:IndexFaces"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:rekognition:${AWS::Region}:${AWS::AccountId}:collection/${collectionId}",
                {
                  "collectionId": {
                    "Ref": "CollectionId"
                  }
                }
              ]
            }
          }
        ]
```

## SQSSendMessagePolicy: Gives Permission to Send Message to Amazon SQS Queue<a name="sqs-send-message-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "sqs:SendMessage*"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:sqs:${AWS::Region}:${AWS::AccountId}:${queueName}",
                {
                  "queueName": {
                    "Ref": "QueueName"
                  }
                }
              ]
            }
          }
        ]
```

## SNSPublishMessagePolicy: Gives Permission to Publish a Message to an Amazon SNS Topic<a name="sqs-publish-message-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "sns:Publish"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:sns:${AWS::Region}:${AWS::AccountId}:${topicName}",
                {
                  "topicName": {
                    "Ref": "TopicName"
                  }
                }
              ]
            }
          }
        ]
```

## VPCAccessPolicy: Gives Access to Create, Delete, Describe, and Detach Elastic Network Interfaces<a name="vpc-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "ec2:CreateNetworkInterface",
              "ec2:DeleteNetworkInterface",
              "ec2:DescribeNetworkInterfaces",
              "ec2:DetachNetworkInterface"
            ],
            "Resource": "*"
          }
        ]
```

## DynamoDBStreamReadPolicy: Gives Permission to Describe and Read a DynamoDB Stream and Records<a name="dynamo-db-stream-read-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "dynamodb:DescribeStream",
              "dynamodb:GetRecords",
              "dynamodb:GetShardIterator",
              "dynamodb:ListStreams"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}/${streamName}",
                {
                  "tableName": {
                    "Ref": "TableName"
                  },
                  "streamName": {
                    "Ref": "StreamName"
                  }
                }
              ]
            }
          }
        ]
```

## KinesisStreamReadPolicy: Gives Permission to List and Read an Amazon Kinesis Stream<a name="kinesis-stream-read-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "kinesis:ListStreams",
              "kinesis:DescribeLimits"
            ],
            "Resource": {
              "Fn::Sub": "arn:${AWS::Partition}:kinesis:${AWS::Region}:${AWS::AccountId}:stream/*"
            }
          },
          {
            "Effect": "Allow",
            "Action": [
              "kinesis:DescribeStream",
              "kinesis:GetRecords",
              "kinesis:GetShardIterator"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:kinesis:${AWS::Region}:${AWS::AccountId}:stream/${streamName}",
                {
                  "streamName": {
                    "Ref": "StreamName"
                  }
                }
              ]
            }
          }
        ]
```

## SESCrudPolicy: Gives Permission to Send Email and Verify Identity<a name="ses-crud-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "ses:GetIdentityVerificationAttributes",
              "ses:SendEmail",
              "ses:VerifyEmailIdentity"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:ses:${AWS::Region}:${AWS::AccountId}:identity/${identityName}",
                {
                  "identityName": {
                    "Ref": "IdentityName"
                  }
                }
              ]
            }
          }
        ]
```

## SNSCrudPolicy: Gives Permissions to Create, Publish, and Subscribe to Amazon SNS Topics<a name="sns-crud-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "sns:ListSubscriptionsByTopic",
              "sns:CreateTopic",
              "sns:SetTopicAttributes",
              "sns:Subscribe",
              "sns:Publish"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:sns:${AWS::Region}:${AWS::AccountId}:${topicName}*",
                {
                  "topicName": {
                    "Ref": "TopicName"
                  }
                }
              ]
            }
          }
        ]
```

## KinesisCrudPolicy: Gives Permission to Create, Publish, and Delete an Amazon Kinesis Stream<a name="kinesis-crud-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "kinesis:AddTagsToStream",
              "kinesis:CreateStream",
              "kinesis:DecreaseStreamRetentionPeriod",
              "kinesis:DeleteStream",
              "kinesis:DescribeStream",
              "kinesis:GetShardIterator",
              "kinesis:IncreaseStreamRetentionPeriod",
              "kinesis:ListTagsForStream",
              "kinesis:MergeShards",
              "kinesis:PutRecord",
              "kinesis:PutRecords",
              "kinesis:SplitShard",
              "kinesis:RemoveTagsFromStream"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:kinesis:${AWS::Region}:${AWS::AccountId}:stream/${streamName}",
                {
                  "streamName": {
                    "Ref": "StreamName"
                  }
                }
              ]
            }
          }
        ]
```

## KMSDecryptPolicy: Gives Permission to Decrypt with an AWS KMS Key<a name="kms-decrypt-policy"></a>

```
        "Statement": [
          {
            "Action": "kms:Decrypt",
            "Effect": "Allow",
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:kms:${AWS::Region}:${AWS::AccountId}:key/${keyId}",
                {
                  "keyId": {
                    "Ref": "KeyId"
                  }
                }
              ]
            }
          }
        ]
```

## PollyFullAccessPolicy: Gives full access permissions to Amazon Polly lexicon resources<a name="polly-full-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "polly:GetLexicon",
              "polly:DeleteLexicon"
            ],
            "Resource": [
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:polly:${AWS::Region}:${AWS::AccountId}:lexicon/${lexiconName}",
                  {
                    "lexiconName": {
                      "Ref": "LexiconName"
                    }
                  }
                ]
              }
            ]
          },
          {
            "Effect": "Allow",
            "Action": [
              "polly:DescribeVoices",
              "polly:ListLexicons",
              "polly:PutLexicon",
              "polly:SynthesizeSpeech"
            ],
            "Resource": [
              {
                "Fn::Sub": "arn:${AWS::Partition}:polly:${AWS::Region}:${AWS::AccountId}:lexicon/*"
              }
            ]
          }
        ]
```

## S3FullAccessPolicy: Gives full access permissions to objects in the Amazon S3 bucket<a name="s3-full-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "s3:GetObject",
              "s3:GetObjectAcl",
              "s3:GetObjectVersion",
              "s3:PutObject",
              "s3:PutObjectAcl",
              "s3:DeleteObject"
            ],
            "Resource": [
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:s3:::${bucketName}/*",
                  {
                    "bucketName": {
                      "Ref": "BucketName"
                    }
                  }
                ]
              }
            ]
          },
          {
            "Effect": "Allow",
            "Action": [
              "s3:ListBucket",
              "s3:GetBucketLocation",
              "s3:GetLifecycleConfiguration",
              "s3:PutLifecycleConfiguration"
            ],
            "Resource": [
              {
                "Fn::Sub": [
                  "arn:${AWS::Partition}:s3:::${bucketName}",
                  {
                    "bucketName": {
                      "Ref": "BucketName"
                    }
                  }
                ]
              }
            ]
          }
        ]
```

## CodePipelineLambdaExecutionPolicy: Gives permission for a Lambda function invoked by AWS CodePipeline to report back status of the job<a name="code-pipeline-lambda-execution-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "codepipeline:PutJobSuccessResult",
              "codepipeline:PutJobFailureResult"
            ],
            "Resource": "*"
          }
        ]
```

## ServerlessRepoReadWriteAccessPolicy: Gives access permissions to create and list applications in the AWS Serverless Application Repository service<a name="serverlessrepo-read-write-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "serverlessrepo:CreateApplication",
              "serverlessrepo:CreateApplicationVersion",
              "serverlessrepo:GetApplication",
              "serverlessrepo:ListApplications",
              "serverlessrepo:ListApplicationVersions"
            ],
            "Resource": [
              {
                "Fn::Sub": "arn:${AWS::Partition}:serverlessrepo:${AWS::Region}:${AWS::AccountId}:applications/*"
              }
            ]
          }
        ]
```

## EC2CopyImagePolicy: Gives permission to copy Amazon EC2 Images<a name="ec2-copy-image-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "ec2:CopyImage"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:ec2:${AWS::Region}:${AWS::AccountId}:image/${imageId}",
                {
                  "imageId": {
                    "Ref": "ImageId"
                  }
                }
              ]
            }
          }
        ]
```

## AWSSecretsManagerRotationPolicy: Grants permissions to APIs required to rotate a secret in AWS Secrets Manager<a name="secrets-manager-rotation-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "secretsmanager:DescribeSecret",
              "secretsmanager:GetSecretValue",
              "secretsmanager:PutSecretValue",
              "secretsmanager:UpdateSecretVersionStage"
            ],
            "Resource": {
              "Fn::Sub": "arn:${AWS::Partition}:secretsmanager:${AWS::Region}:${AWS::AccountId}:secret:*"
            },
            "Condition": {
              "StringEquals": {
                "secretsmanager:resource/AllowRotationLambdaArn": {
                  "Fn::Sub": [
                    "arn:${AWS::Partition}:lambda:${AWS::Region}:${AWS::AccountId}:function:${functionName}",
                    {
                      "functionName": {
                        "Ref": "FunctionName"
                      }
                    }
                  ]
                }
              }
            }
          },
          {
            "Effect": "Allow",
            "Action": [
              "secretsmanager:GetRandomPassword"
            ],
            "Resource": "*"
          }
        ]
```

## AWSSecretsManagerGetSecretValuePolicy: Grants permissions to GetSecretValue for the specified AWS Secrets Manager secret<a name="secrets-manager-get-secret-value-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "secretsmanager:GetSecretValue"
            ],
            "Resource": {
              "Fn::Sub": [
                "${secretArn}",
                {
                  "secretArn": {
                    "Ref": "SecretArn"
                  }
                }
              ]
            }
          }
        ]
```

## CodePipelineReadOnlyPolicy: Gives read permissions to get details about a CodePipeline pipeline<a name="code-pipeline-readonly-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "cloudwatch:GetDashboard",
              "cloudwatch:ListDashboards",
              "cloudwatch:PutDashboard",
              "cloudwatch:ListMetrics"
            ],
            "Resource": "*"
          }
        ]
```

## RekognitionFacesPolicy: Gives permission to compare and detect faces and labels<a name="rekognition-faces-policy"></a>

```
        "Statement": [{
          "Effect": "Allow",
          "Action": [
            "rekognition:CompareFaces",
            "rekognition:DetectFaces"
          ],
          "Resource": {
            "Fn::Sub": [
              "arn:${AWS::Partition}:rekognition:${AWS::Region}:${AWS::AccountId}:collection/${collectionId}",
              {
                "collectionId": {
                  "Ref": "CollectionId"
                }
              }
            ]
          }
        ]
```

## RekognitionLabelsPolicy: Gives permission to compare and detect faces and labels<a name="rekognition-labels-policy"></a>

```
        "Statement": [{
          "Effect": "Allow",
          "Action": [
            "rekognition:DetectLabels",
            "rekognition:DetectModerationLabels"
          ],
          "Resource": "*"
         }
        ]
```

## DynamoDBBackupFullAccessPolicy: Gives read/write permissions to DynamoDB on\-demand backups for a table<a name="ddb-back-full-policy"></a>

```
        "Statement": [{
          "Effect": "Allow",
          "Action": [
            "dynamodb:CreateBackup",
            "dynamodb:DescribeContinuousBackups"
          ],
          "Resource": {
            "Fn::Sub": [
              "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}",
              {
                "tableName": {
                  "Ref": "TableName"
                }
              }
            ]
          }
        },
          {
            "Effect": "Allow",
            "Action": [
              "dynamodb:DeleteBackup",
              "dynamodb:DescribeBackup",
              "dynamodb:ListBackups"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}/backup/*",
                {
                  "tableName": {
                    "Ref": "TableName"
                  }
                }
              ]
            }
          }
        ]
```

## DynamoDBRestoreFromBackupPolicy: Gives permissions to restore a table from backup<a name="ddb-restore-from-backup-policy"></a>

```
        "Statement": [{
          "Effect": "Allow",
          "Action": [
            "dynamodb:RestoreTableFromBackup"
          ],
          "Resource": {
            "Fn::Sub": [
              "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}/backup/*",
              {
                "tableName": {
                  "Ref": "TableName"
                }
              }
            ]
          }
        },
          {
            "Effect": "Allow",
            "Action": [
              "dynamodb:PutItem",
              "dynamodb:UpdateItem",
              "dynamodb:DeleteItem",
              "dynamodb:GetItem",
              "dynamodb:Query",
              "dynamodb:Scan",
              "dynamodb:BatchWriteItem"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:dynamodb:${AWS::Region}:${AWS::AccountId}:table/${tableName}",
                {
                  "tableName": {
                    "Ref": "TableName"
                  }
                }
              ]
            }
          }
        ]
```

## ComprehendBasicAccessPolicy: Gives access to Amazon Comprehend APIs for detecting entities, key phrases, languages, and sentiments<a name="comprehend-basic-access-policy"></a>

```
        "Statement": [{
          "Effect": "Allow",
          "Action": [
            "comprehend:BatchDetectKeyPhrases",
            "comprehend:DetectDominantLanguage",
            "comprehend:DetectEntities",
            "comprehend:BatchDetectEntities",
            "comprehend:DetectKeyPhrases",
            "comprehend:DetectSentiment",
            "comprehend:BatchDetectDominantLanguage",
            "comprehend:BatchDetectSentiment"
          ],
          "Resource": "*"
          }
        ]
```

## MobileAnalyticsWriteOnlyAccessPolicy: Gives write only permissions to put event data for all application resources<a name="mobile-analytics-write-only-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "mobileanalytics:PutEvents"
            ],
            "Resource": "*"
          }
        ]
```

## PinpointEndpointAccessPolicy: Gives permissions to get and update endpoints for an Amazon Pinpoint application<a name="pinpoint-endpoint-access-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "mobiletargeting:GetEndpoint",
              "mobiletargeting:UpdateEndpoint",
              "mobiletargeting:UpdateEndpointsBatch"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:mobiletargeting:${AWS::Region}:${AWS::AccountId}:apps/${pinpointApplicationId}/endpoints/*",
                {
                  "pinpointApplicationId": {
                    "Ref": "PinpointApplicationId"
                  }
                }
              ]
            }
          }
        ]
```

## FirehoseWritePolicy: Gives permission to write to a Kinesis Data Firehose Delivery Stream<a name="firehose-write-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "firehose:PutRecord",
              "firehose:PutRecordBatch"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:firehose:${AWS::Region}:${AWS::AccountId}:deliverystream/${deliveryStreamName}",
                {
                  "deliveryStreamName": {
                    "Ref": "DeliveryStreamName"
                  }
                }
              ]
            }
          }
        ]
```

## FirehoseCrudPolicy: Gives permission to create, write to, update, and delete a Kinesis Data Firehose Delivery Stream<a name="firehose-crud-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "firehose:CreateDeliveryStream",
              "firehose:DeleteDeliveryStream",
              "firehose:DescribeDeliveryStream",
              "firehose:PutRecord",
              "firehose:PutRecordBatch",
              "firehose:UpdateDestination"
            ],
            "Resource": {
              "Fn::Sub": [
                "arn:${AWS::Partition}:firehose:${AWS::Region}:${AWS::AccountId}:deliverystream/${deliveryStreamName}",
                {
                  "deliveryStreamName": {
                    "Ref": "DeliveryStreamName"
                  }
                }
              ]
            }
          }
        ]
```