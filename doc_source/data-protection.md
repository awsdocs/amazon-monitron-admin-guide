# Data protection in Amazon Monitron<a name="data-protection"></a>

Amazon Monitron conforms to the AWS [shared responsibility model](http://aws.amazon.com/compliance/shared-responsibility-model/), which includes regulations and guidelines for data protection\. AWS is responsible for protecting the global infrastructure that runs all the AWS services\. AWS maintains control over data hosted on this infrastructure, including the security configuration controls for handling customer content and personal data\. AWS customers and APN partners, acting either as data controllers or data processors, are responsible for any personal data that they put in the AWS Cloud\. 

For data protection purposes, we recommend that you protect AWS account credentials and set up individual user accounts with AWS Identity and Access Management \(IAM\), so that each user is given only the permissions necessary to fulfill their job duties\. We also recommend that you secure your data in the following ways:
+ Use multi\-factor authentication \(MFA\) with each account\.
+ Use TLS \(Transport Layer Security\) to communicate with AWS resources\.
+ Set up API and user activity logging with AWS CloudTrail\.
+ Use AWS encryption solutions, along with all default security controls within AWS services\.
+ Use advanced managed security services such as Amazon Macie, which assists in discovering and securing personal data that is stored in Amazon S3\.

We strongly recommend that you never put sensitive identifying information, such as your customers' account numbers, into free\-form fields such as a **Name** field\. This includes when you work with Amazon Monitron or other AWS services using the console, API, AWS CLI, or AWS SDKs\. Any data that you enter into Amazon Monitron or other services might get picked up for inclusion in diagnostic logs\. When you provide a URL to an external server, don't include credentials information in the URL to validate your request to that server\.

For more information about data protection, see the [AWS Shared Responsibility Model and GDPR](http://aws.amazon.com/blogs/security/the-aws-shared-responsibility-model-and-gdpr/) blog post on the *AWS Security Blog*\.

## Data at rest<a name="data-at-rest"></a>

Your data is encrypted at rest in the cloud using one of two types of keys through AWS Key Management Service \(AWS KMS\)\. The data is encrypted in Amazon Simple Storage Service \(Amazon S3\) using an AWS owned key\. Amazon Monitron also stores data in tables in Amazon DynamoDB\. By default, these are encrypted using an AWS owned CMK\. However, if a customer chooses **Custom encryption settings** when setting up a project, Amazon Monitron uses a customer managed CMK\.

## Data in transit<a name="data-in-transit"></a>

Amazon Monitron uses TLS \(Transport Layer Security\) to encrypt data that is transferred between your sensors and Amazon Monitron\. 

## KMS and data encryption in Amazon Monitron<a name="kms-data-encrypt"></a>

Amazon Monitron encrypts your data and project information using one of two types of keys through AWS Key Management Service \(AWS KMS\)\. You can choose one of the following: 
+ An AWS owned key\. This is the default encryption key and is used if you do not choose **Custom encryption settings** when setting up your project\.
+ A customer managed CMK\. You can use an existing key in your AWS account or create a key in the AWS KMS console or using the API\. If you're using an existing key, you choose **Choose an AWS KMS key** and then either choose a key from the list of AWS KMS keys, or enter the Amazon Resource Name \(ARN\) of another key\. If you want to create a new key, you choose **Create an AWS KMS key**\. For more information, see [Creating Keys](https://docs.aws.amazon.com/kms/latest/developerguide/create-keys.html) in the *AWS Key Management Service Developer Guide*\. 

When using AWS KMS to encrypt your data, keep the following in mind: 
+ Your data is encrypted at rest in the Cloud in Amazon S3 and Amazon DynamoDB\. 
+ When data is encrypted using an AWS owned CMK, Amazon Monitron uses a separate CMK for each customer\.
+ IAM users must have the required permissions to call the AWS KMS API operations connected with Amazon Monitron\. Amazon Monitron includes the following permissions in its managed policy for console use\. 

  ```
  {
                   "Effect": "Allow",
                   "Action": [
                           "kms:ListKeys",
                           "kms:DescribeKey",
                           "kms:ListAliases",
                           "kms:CreateGrant"
                   ],
                   "Resource": "*"
           },
  ```

   For more information, see [Using IAM Policies with AWS KMS](https://docs.aws.amazon.com/kms/latest/developerguide/iam-policies.html) in the *AWS Key Management Service Developer Guide*\. 
+ If you delete or disable your CMK, you won't be able to access the data\. For more information, see [Deleting AWS KMS keys](https://docs.aws.amazon.com/kms/latest/developerguide/deleting-keys.html) in the *AWS Key Management Service Developer Guide*\. 