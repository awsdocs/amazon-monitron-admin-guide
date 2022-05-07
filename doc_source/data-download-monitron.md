# Downloading your data from Amazon Monitron<a name="data-download-monitron"></a>

You may sometimes want to access the raw data that Amazon Monitron is storing for you, in order to stay informed about exactly what kind of data you’re securely storing with AWS\.

You can get your raw data by filing a support ticket with AWS, and by giving Amazon Monitron permission to deliver your data to you\.

## <a name="exporting-data-procedure"></a>

To successfully export your Amazon Monitron data, the following prerequisites must be met\.
+ You must not already have another export \(of Amazon Monitron data\) running in the same region\.
+ You cannot have run another export in same region in past 24 hours\.

### Exporting your data with AWS CloudFormation \(recommended option\)<a name="onetime-download-cflink"></a>

#### Step 1: Create your Amazon S3 bucket, IAM role, and IAM policies\.<a name="gdpr-cloudfront-makestack"></a>

1. Sign in to your AWS account\.

1. Open a new browser tab with the following URL\.

   ```
   https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/create/review?templateURL=https://s3.us-east-1.amazonaws.com/monitron-cloudformation-templates-us-east-1/monitron_manual_download.yaml&stackName=monitronexport
   ```

1. On the AWS CloudFormation page that opens, in the upper right corner, select the region in which you are using Amazon Monitron\.

1. Check the box that says *I acknowledge that AWS CloudFormation might create IAM resources\.*

1. Choose **Create stack**\.

1. On the next page, choose the refresh icon as often as you like until the status of the stack \(monitronexport\) is CREATE\_COMPLETE\.

#### Step 2: Note your resources<a name="gdpr-cloudfront-resources"></a>

1. Choose the **Outputs** tab\.

1. Note the value of the key `MonRoleArn`\.

1. Note the value of the key `S3BucketArn`\.

1. Note your account ID from the upper right corner of the page\)\.

1. Note the region you chose in Step 1\. It also now appears at the top of the page, to the left of your account ID\.

#### Step 3: Create the support case<a name="gdpr-cloudfront-case"></a>

1.  From your AWS console, choose the question mark icon near the upper right corner of any page, then choose **Support Center**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-support-question-mark.png)

1.  On the next page, choose **Create case**\. 

1.  Choose **Account and billing support**\. 

1.  Under **Type**, choose **Account**\. 

1.  Under **Category**, choose **Compliance & Accreditations**\. 

1.  Choose **Severity**, if that option is available to you based on your support subscription\. 

1.  Under **Subject**, enter Amazon Monitron data export request\. 

1. In the **Description** field, enter:

   1. your account ID

   1. the region of the bucket you created

   1. the ARN of the bucket you created \(for example: "arn:aws:s3:::bucketname"\)

   1. the ARN of the role you created \(for example: "arn:aws:iam::273771705212:role/role\-for\-monitron"\)

1. Choose **Submit**\.

 An AWS customer support specialist will get back to you as soon as possible\. If there are any issues with the steps listed, the specialist may ask you for more information\. If all the necessary information has been provided, the specialist will let you know as soon as your data has been copied to the Amazon S3 bucket that you created above\. 

### Exporting your data with the console<a name="onetime-download-console"></a>

#### Step 1: Setting up your Amazon S3 bucket<a name="gdpr-console-s3"></a>

1. Open the [Amazon S3 console](https://console.aws.amazon.com/s3/)\.

1. Choose **Create bucket**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-bucket.png)

1. Name your bucket and select an appropriate region\. Then, at the bottom of the page, choose **Create bucket**\.
**Important**  
At this time, Amazon Monitron is only supported in two regions:  
US East \(N\. Virginia\) us\-east\-1
EU \(Ireland\) eu\-west\-1
Therefore, your Amazon S3 bucket must be in one of those regions\.

   It must also be the same region in which you are using the Amazon Monitron service\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-bucket-2.png)

1. Review the rest of the options on the page, and make the appropriate choices, depending on your security needs and policies\.
**Important**  
You are responsible for taking the appropriate steps to secure your data\. We strongly recommend using server\-side encryption and blocking public access to your bucket\.

1. Using the search box, find the bucket you just created, and then choose it\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-choose-s3-bucket.png)

1. From the **Properties** tab, make a note of the name, ARN, and region of the bucket\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-s3-properties-tab.png)

#### Step 2: Give Amazon Monitron permission to access Amazon S3<a name="gdpr-console-set-policy"></a>

1. Open the [IAM console](iam/) and choose **Policies**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-iam-policies.png)

1. Choose Create Policy\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-policy.png)

1. Select the JSON tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-policy-json.png)

1. Delete the default JSON text so that the form is empty\.

1. Paste in the bucket access policy\.

   ```
   			  				  
   {
       "Statement": [
           {
               "Action": [
                   "s3:GetBucketAcl",
                   "s3:GetBucketLocation",
                   "s3:ListBucket"
               ],
               "Effect": "Allow",
               "Resource": [
                   "arn:aws:s3:::bucketname"
               ]
           },
           {
               "Action": [
                   "s3:PutObject",
                   "s3:GetBucketAcl"
               ],
               "Effect": "Allow",
               "Resource": [
                   "arn:aws:s3:::bucketname/*"
               ]
           }
       ],
       "Version": "2012-10-17"
   }
   ```

1. Change "bucketname" to the actual name of your bucket\.

1. Choose **Next: Tags**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-policy-next-tags.png)

1. Choose **Next: Review**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-policy-next-review.png)

1. Give the policy a name\.

1. Choose **Create policy**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-name-policy.png)

#### Step 3: Create the role<a name="gdpr-console-create-role"></a>

1. Choose Roles\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-choose-roles-after-policies.png)

1. Choose Create role\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-role-from-roles.png)

1. Choose Another AWS account\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-another-aws-account.png)

1. Copy your own AWS account number\. Paste it into the Account ID box\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-role-your-account-ID.png)

   You may be wondering why you're referencing your own account, while referring to it as another account\. You also may have noticed that there is an option called AWS service that you did not choose, even though Amazon Monitron is an AWS service\.

   The reason is that Amazon Monitron is not currently listed under the **AWS service** option\. This is a workaround\.

1. Choose **Next: Permissions**\.

1. Search for the policy you just created in the search box, and select your policy\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-role-search-policy.png)

1. Choose **Next: Tags**\.

1. Choose Next: Review\.

1. Give your role a name\. Then choose **Create role**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-create-role-name-role.png)

#### Step 4: Create the trust policy<a name="gdpr-console-trust-policy"></a>

1. Search for the role you just created and choose the role\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-search-for-role.png)

1. Select the **Trust relationships** tab\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-trust-relationships.png)

1. Choose **Edit trust relationship**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-edit-trust-relationship.png)

1. Erase the default JSON text so that the form is empty\.

1. Paste in the policy that allows Amazon Monitron to assume the role\.

   ```
   {
   	"Version": "2012-10-17",
   	"Statement": [{
   		"Effect": "Allow",
   		"Principal": {
   			"Service": ["monitron.amazonaws.com"]
   		},
   		"Action": "sts:AssumeRole"
   	}]
   }
   ```

1. Choose **Update Trust Policy**\.

#### Step 4: Create the support case<a name="gdpr-console-case"></a>

1.  From your AWS console, choose the question mark icon near the upper right corner of any page, then choose **Support Center**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-support-question-mark.png)

1.  On the next page, choose **Create case**\. 

1.  Choose **Account and billing support**\. 

1.  Under **Type**, choose **Account**\. 

1.  Under **Category**, choose **Compliance & Accreditations**\. 

1.  Choose **Severity**, if that option is available to you based on your support subscription\. 

1.  Under **Subject**, enter Amazon Monitron data export request\. 

1. In the **Description** field, enter:

   1. your account ID

   1. the region of the bucket you created

   1. the ARN of the bucket you created \(for example: "arn:aws:s3:::bucketname"\)

   1. the ARN of the role you created \(for example: "arn:aws:iam::273771705212:role/role\-for\-monitron"\)

1. Choose **Submit**\.

 An AWS customer support specialist will get back to you as soon as possible\. If there are any issues with the steps listed, the specialist may ask you for more information\. If all the necessary information has been provided, the specialist will let you know as soon as your data has been copied to the Amazon S3 bucket that you created above\. 

### Exporting your data with CloudShell<a name="export-shell"></a>

#### Creating an Amazon S3 bucket \(with AWS CloudShell\)<a name="create-s3-with-shell"></a>

1. Log in to the AWS Console\. 

1. OpenAWS CloudShell

   [AWS CloudShell](https://docs.aws.amazon.com/cloudshell/latest/userguide/welcome.html) is a command\-line environment that operates inside your browser\. Inside AWS CloudShell, you can use the AWS Command Line Interface to launch and configure many AWS services\.

1. In AWS CloudShell, enter the following command, where bucketname is the name of the bucket you are creating:

   ```
   $ aws s3api create-bucket --bucket bucketname --region us-east-1
   ```

   This command creates an Amazon S3 bucket to store your raw data\. You will be able to easily access your bucket from the console, and download your data at your convenience\. For more information, see [Creating, configuring, and working with Amazon S3 buckets](https://docs.aws.amazon.com/AmazonS3/latest/userguide/creating-buckets-s3.html)\.
**Important**  
You are responsible for taking the appropriate steps to secure your data\. We strongly recommend using server\-side encryption and blocking public access to your bucket\.

   In the command above, the bucket is created in the US East \(N\. Virginia\) Region\. You can optionally specify a different Region in the request body\. For more information, see [Regions, Availability Zones, and Local Zones](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Concepts.RegionsAndAvailabilityZones.html)\.

   You should see output that looks something like this:

   ```
   { "Location": "/bucketname" }
   ```

1. Identify the [Amazon Resource Name \(ARN\)](https://docs.aws.amazon.com/general/latest/gr/aws-arns-and-namespaces.html) of the bucket you created, which will be:

   ```
   arn:aws:s3:::bucketname
   ```

#### Granting Amazon Monitron access to your Amazon S3 bucket \(with AWS CloudShell\)<a name="create-policy-with-shell"></a>

1. Paste the code below into a text editor, and save it as: monitron\-assumes\-role\.json\. Do not use Microsoft Word, which will add extra characters\. Use a simple text editor like Notepad or TextEdit\.

   This policy gives Amazon Monitron permission to assume the role that will allow it to access your S3 bucket\. For more information, see [ Policies and permissions in IAM\.](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html) 

   ```
   {
   	"Version": "2012-10-17",
   	"Statement": [{
   		"Effect": "Allow",
   		"Principal": {
   			"Service": ["monitron.amazonaws.com"]
   		},
   		"Action": "sts:AssumeRole"
   	}]
   }
   ```

1.  Paste the text below into a text editor, and save it as: monitron\-role\-accesses\-s3\.json 

    This policy will allow Amazon Monitron \(using the role created above\) to access your Amazon S3 bucket\. 

   ```
   {
       "Statement": [
           {
               "Action": [
                   "s3:GetBucketAcl",
                   "s3:GetBucketLocation",
                   "s3:ListBucket"
               ],
               "Effect": "Allow",
               "Resource": [
                   "arn:aws:s3:::bucketname"
               ]
           },
           {
               "Action": [
                   "s3:PutObject",
                   "s3:GetBucketAcl"
               ],
               "Effect": "Allow",
               "Resource": [
                   "arn:aws:s3:::bucketname/*"
               ]
           }
       ],
       "Version": "2012-10-17"
   }
   ```

1. In the text file you just created, replace every occurrence of *bucketname* with the name of your bucket\.

   For example, if the name of your bucket is relentless, then your file will look like this:

   ```
   {
       "Statement": [
           {
               "Action": [
                   "s3:GetBucketAcl",
                   "s3:GetBucketLocation",
                   "s3:ListBucket"
               ],
               "Effect": "Allow",
               "Resource": [
                   "arn:aws:s3:::relentless"
               ]
           },
           {
               "Action": [
                   "s3:PutObject",
                   "s3:GetBucketAcl"
               ],
               "Effect": "Allow",
               "Resource": [
                   "arn:aws:s3:::relentless/*"
               ]
           }
       ],
       "Version": "2012-10-17"
   }
   ```

1. Upload both of the json files that you just created to CloudShell in the home directory\. 

   To upload a file, choose Actions from the upper right hand corner of the CloudShell console page, then choose Upload file\. 

1. Enter the following on the command line in CloudShell:

   aws iam create\-role \-\-role\-name role\-for\-monitron \-\-assume\-role\-policy\-document "cat monitron\-assumes\-role\.json"

   This command creates the role and attaches the monitron\-assumes\-role policy\. 

    You should see output that looks something like this: 

   ```
    {
   	"Role": {
   		"Path": "/",
   		"RoleName": "role-for-monitron",
   		"RoleId": "AROAT7PQQWN6BMTMASVPP",
   		"Arn": "arn:aws:iam::273771705212:role/role-for-monitron",
   		"CreateDate": "2021-07-14T02:48:15+00:00",
   		"AssumeRolePolicyDocument": {
   			"Version": "2012-10-17",
   			"Statement": [{
   				"Sid": "",
   				"Effect": "Allow",
   				"Principal": {
   					"Service": [
   						"monitron.amazonaws.com"
   					]
   				},
   				"Action": "sts:AssumeRole"
   			}]
   		}
   	}
   }
   ```

    Take note of the ARN value for the role you just created\. You will need it later\. 

   In our example, the ARN value is: `arn:aws:iam::273771705212:role/role-for-monitron`

1. Enter the following on the command line in CloudShell:

     aws iam create\-policy \-\-policy\-name role\-uses\-bucket \-\-policy\-document "cat role\-uses\-bucket\.json" 

    This command creates the monitron\-role\-accesses\-s3 policy\. 

    You should see output that looks something like this: 

   ```
    {
   	"Policy": {
   		"PolicyName": "role-uses-bucket",
   		"PolicyId": "ANPAT7PQQWN6I5KLORSDQ",
   		"Arn": "arn:aws:iam::273771705212:policy/role-uses-bucket",
   		"Path": "/",
   		"DefaultVersionId": "v1",
   		"AttachmentCount": 0,
   		"PermissionsBoundaryUsageCount": 0,
   		"IsAttachable": true,
   		"CreateDate": "2021-07-14T02:19:23+00:00",
   		"UpdateDate": "2021-07-14T02:19:23+00:00"
   	}
   }
   ```

    Take note of the ARN value for the policy that you just created\. You will need it for the next step\. 

    In our example, the ARN value is: 

   ```
   arn:aws:iam::273771705212:policy/role-uses-bucket
   ```

1. Enter the following on the command line in CloudShell, replacing the ARN with the ARN for your role\-uses\-bucket policy: 

   ```
    aws iam attach-role-policy --role-name role-for-monitron --policy-arn
         arn:aws:iam::273771705212:policy/role-uses-bucket
   ```

   This command attaches the monitron\-role\-accesses\-s3 policy to the role you just created\.

    Now you have created and provisioned an Amazon S3 bucket, a role that Amazon Monitron can assume, a policy that will allow Amazon Monitron to assume that role, and another policy that will allow the service using that role to use your Amazon S3 bucket\.

   You are responsible for taking the appropriate steps to secure your data\. We strongly recommend using server\-side encryption and blocking public access to your bucket\. For more information, see [ Blocking public access](https://docs.aws.amazon.com/AmazonS3/latest/userguide/access-control-block-public-access.html)\.

#### Step 3: Creating your support ticket<a name="create-support-ticket"></a>

1.  From your AWS console, choose the question mark icon near the upper right corner of any page, then choose **Support Center**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/gdpr-support-question-mark.png)

1.  On the next page, choose **Create case**\. 

1.  Choose **Account and billing support**\. 

1.  Under **Type**, choose **Account**\. 

1.  Under **Category**, choose **Compliance & Accreditations**\. 

1.  Choose **Severity**, if that option is available to you based on your support subscription\. 

1.  Under **Subject**, enter Amazon Monitron data export request\. 

1. In the **Description** field, enter:

   1. your account ID

   1. the region of the bucket you created

   1. the ARN of the bucket you created \(for example: "arn:aws:s3:::bucketname"\)

   1. the ARN of the role you created \(for example: "arn:aws:iam::273771705212:role/role\-for\-monitron"\)

 An AWS customer support specialist will get back to you as soon as possible\. If there are any issues with the steps listed above, then the specialist may ask you for more information\. If all the necessary information has been provided, then the specialist will let you know as soon as your data has been copied to the Amazon S3 bucket that you created above\. 