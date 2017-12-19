# Using the AWS Serverless Application Model \(AWS SAM\)<a name="using-aws-sam"></a>

The AWS Serverless Application Model \(AWS SAM\) is a model that defines serverless applications\. AWS SAM is natively supported by AWS CloudFormation and defines simplified syntax for expressing serverless resources\. The specification currently covers APIs, AWS Lambda functions, and Amazon DynamoDB tables\. The specification is available under Apache 2\.0 for AWS partners and customers to adopt and extend within their own toolsets\. For details on the specification, see [AWS Serverless Application Model](https://github.com/awslabs/serverless-application-model)\.

AWS SAM supports special resource types that simplify how to express functions, APIs, mappings, and DynamoDB tables for serverless applications, in addition to some features for these services like environment variables\. The AWS CloudFormation description of these resources conforms to the [AWS Serverless Application Model](https://github.com/awslabs/serverless-application-model)\. To deploy your application, specify the resources that you need as part of your application, along with their associated permissions policies in an AWS CloudFormation template file \(written in either JSON or YAML\), package your deployment artifacts, and deploy the template\. 

## Supported AWS Resources in the AWS Serverless ApplicationRepository<a name="supported-resources-for-serverlessrepo"></a>

Serverless applications that you publish to the AWS Serverless ApplicationRepository can include additional AWS CloudFormation resources\. The following is a complete list of supported resources:

+ AWS::Serverless::Function

+ AWS::Serverless::Api

+ AWS::Serverless::SimpleTable

+ AWS::Lambda::Alias

+ AWS::Lambda::Version

+ AWS::Lambda::EventSourceMapping

+ AWS::ApiGateway::Account

+ AWS::ApiGateway::ApiKey

+ AWS::ApiGateway::Authorizer

+ AWS::ApiGateway::BasePathMapping

+ AWS::ApiGateway::ClientCertificate

+ AWS::ApiGateway::Deployment

+ AWS::ApiGateway::DocumentationPart

+ AWS::ApiGateway::DocumentationVersion

+ AWS::ApiGateway::DomainName

+ AWS::ApiGateway::GatewayResponse

+ AWS::ApiGateway::Method

+ AWS::ApiGateway::Model

+ AWS::ApiGateway::RequestValidator

+ AWS::ApiGateway::Resource

+ AWS::ApiGateway::RestApi

+ AWS::ApiGateway::Stage

+ AWS::ApiGateway::UsagePlan

+ AWS::ApiGateway::UsagePlanKey

+ AWS::Cognito::IdentityPool

+ AWS::Cognito::UserPool

+ AWS::Cognito::UserPoolClient

+ AWS::Cognito::UserPoolGroup

+ AWS::Cognito::UserPoolUser

+ AWS::Cognito::UserPoolUserToGroupAttachment

+ AWS::DynamoDB::Table

+ AWS::Logs::Destination

+ AWS::Logs::LogGroup

+ AWS::Logs::LogStream

+ AWS::Logs::MetricFilter

+ AWS::Logs::SubscriptionFilter

+ AWS::Kinesis::Streams

+ AWS::S3::Bucket

+ AWS::SNS::Subscription

+ AWS::SNS::Topic

+ AWS::SQS::Queue

+ AWS::CloudWatch::Alarm

+ AWS::CloudWatch::Dashboard

## Policy Templates<a name="serverlessrepo-policy-templates"></a>

When you add a serverless application to the AWS Serverless ApplicationRepository, AWS SAM allows you to choose from a list of policy templates\. When you choose one of these templates, your Lambda functions are scoped to the resources that are used by your application\. The following lists the permissions that are applied to each policy template in the Policy templates list\. AWS SAM automatically populates the placeholder items \(such as region and accountID\) with the appropriate information\.

The following example shows that the `SQSPollerPolicy` policy expects a `QueueName` as a resource\. The AWS SAM template retrieves the name of the "`MyQueue`" SQS queue, which can be created in the same application or requested as a parameter to the application\.

```
 1. MyFunction:
 2.     Type: 'AWS::Serverless::Function'
 3.     Properties:
 4.       CodeUri: ${codeuri}
 5.       Handler: hello.handler
 6.       Runtime: python2.7
 7.       Policies:
 8.       - SQSPollerPolicy:
 9.             QueueName:
10.               Fn::GetAtt: ["MyQueue", "QueueName"]
```

## SQSPollerPolicy: Gives Permissions to Poll an SQS Queue<a name="sqs-poller-policy"></a>

```
        "Statement": [
          {
            "Effect": "Allow",
            "Action": [
              "sqs:DeleteMessage",
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

## DynamoDBCrudPolicy: Gives CRUD Access to a DynamoDB Table<a name="dynamo-db-crud-policy"></a>

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

## ElasticsearchHttpPostPolicy: Gives POST Permissions to Elasticsearch<a name="elastic-search-http-post-policy"></a>

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

## S3ReadPolicy: Gives Read Permissions to Objects in the S3 Bucket<a name="s3-read-policy"></a>

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

## S3CrudPolicy: Gives CRUD Permissions to Objects in the S3 Bucket<a name="s3-crud-policy"></a>

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

## AMIDescribePolicy: Gives Permissions to Describe AMIs<a name="ami-describe-policy"></a>

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

## SQSSendMessagePolicy: Gives Permission to Send Message to SQS Queue<a name="sqs-send-message-policy"></a>

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

## SNSPublishMessagePolicy: Gives Permission to Publish a Message to an SNS Topic<a name="sqs-publish-message-policy"></a>

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

## VPCAccessPolicy: Gives Access to Create, Delete, Describe, and Detach ENIs<a name="vpc-access-policy"></a>

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
            "Resource": {
              "Fn::Sub": "arn:${AWS::Partition}:ec2:${AWS::Region}:${AWS::AccountId}:network-interface/*"
            }
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

## SNSCrudPolicy: Gives Permissions to Create, Publish, and Subscribe to SNS Topics<a name="sns-crud-policy"></a>

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

## KinesisCrudPolicy: Gives Permission to Create, Publish, and Delete a Kinesis Stream<a name="kinesis-crud-policy"></a>

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