# Creating a project<a name="mp-creating-project"></a>

Although an AWS account can have multiple Amazon Monitron projects, typically you have just one per account\. The project name must be unique in your AWS account and AWS Region\.

**To create a project**

1. Open the Amazon Monitron console at [https://console\.aws\.amazon\.com/monitron](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\.

1. Under **Project Details**, for **Project name**, enter a name that: 
   + is unique in the current account 
   + consists of uppercase and lowercase letters, numbers, punctuation marks, and spaces 
   + is between 1 and 60 characters 

1. By default, Amazon Monitron uses an AWS owned key to encrypt your project through the AWS Key Management Service \(AWS KMS\)\. If you want to use a different KMS key, choose **Custom encryption settings \(advanced\)** under **Data encryption** and do one of the following:
   + If you already have a KMS key that you want to use, under **Choose an AWS KMS key**, choose the key or enter the key's Amazon Resource Name \(ARN\)\. 
   + If you want to create a key, choose **Create an AWS KMS key**\. This takes you to the AWS KMS console so you can set up a custom key\. 

   For more information about encrypting a project, see [KMS and data encryption in Amazon Monitron](data-protection.md#kms-data-encrypt)\. 

1. \(Optional\) To add a tag to the project, enter a key\-value pair under **Tags** and then choose **Add tag**\. To remove this tag before creating the project, choose **Remove tag**\. 

   For more information, see [Using tags with your Amazon Monitron project](tagging.md)\.

1. Choose **Next** to create the project\. 

Now you are ready to add users to the project\. See [User directory setup](mu-adding-user.md)\.