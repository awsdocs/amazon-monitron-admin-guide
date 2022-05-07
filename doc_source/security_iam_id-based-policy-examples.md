# Amazon Monitron Identity\-Based Policy Examples<a name="security_iam_id-based-policy-examples"></a>

By default, IAM users and roles don't have permission to create or modify Amazon Monitron resources\. They also can't perform tasks using the AWS Management Console\. An IAM administrator must create IAM policies that grant users and roles permission to perform specific operations on the specified resources they need\. The administrator must then attach those policies to the IAM users or groups that require those permissions\.

To learn how to create an IAM identity\-based policy using these example JSON policy documents, see [Creating Policies on the JSON Tab](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_create.html#access_policies_create-json-editor) in the *IAM User Guide*\.

**Topics**
+ [Policy Best Practices](#security_iam_service-with-iam-policy-best-practices)
+ [Using the Amazon Monitron Console](#security_iam_id-based-policy-examples-console)
+ [Example: List All Amazon Monitron Projects](#security_iam_id-based-policy-examples-access-one-bucket)
+ [Example: List Amazon Monitron Projects Based on Tags](#security_iam_id-based-policy-examples-view-widget-tags)

## Policy Best Practices<a name="security_iam_service-with-iam-policy-best-practices"></a>

Identity\-based policies are very powerful\. They determine whether someone can create, access, or delete Amazon Monitron resources in your account\. These actions can incur costs for your AWS account\. When you create or edit identity\-based policies, follow these guidelines and recommendations:
+ **Get started using AWS managed policies** – To start using Amazon Monitron quickly, use AWS managed policies to give your employees the permissions they need\. These policies are already available in your account and are maintained and updated by AWS\. For more information, see [Get started using permissions with AWS managed policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#bp-use-aws-defined-policies) in the *IAM User Guide*\.
+ **Grant least privilege** – When you create custom policies, grant only the permissions required to perform a task\. Start with a minimum set of permissions and grant additional permissions as necessary\. Doing so is more secure than starting with permissions that are too lenient and then trying to tighten them later\. For more information, see [Grant least privilege](https://docs.aws.amazon.com/IAM/latest/UserGuide/best-practices.html#grant-least-privilege) in the *IAM User Guide*\.
+ **Enable MFA for sensitive operations** – For extra security, require IAM users to use multi\-factor authentication \(MFA\) to access sensitive resources or API operations\. For more information, see [Using multi\-factor authentication \(MFA\) in AWS](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_mfa.html) in the *IAM User Guide*\.
+ **Use policy conditions for extra security** – To the extent that it's practical, define the conditions under which your identity\-based policies allow access to a resource\. For example, you can write conditions to specify a range of allowable IP addresses that a request must come from\. You can also write conditions to allow requests only within a specified date or time range, or to require the use of SSL or MFA\. For more information, see [IAM JSON policy elements: Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) in the *IAM User Guide*\.

## Using the Amazon Monitron Console<a name="security_iam_id-based-policy-examples-console"></a>

To set up Amazon Monitron using the console, please complete the initial setup process using a high privilege user \(such as one with the `AdministratorAccess` managed policy attached\)\. 

To access the Amazon Monitron console for day\-to\-day operations after the initial setup, you must have a minimum set of permissions\. These permissions must allow you to list and view details about the Amazon Monitron resources in your AWS account and include a set of permissions related to AWS SSO\. If you create an identity\-based policy that is more restrictive than these minimum required permissions, the console won't function as intended for entities \(IAM users or roles\) with that policy\. For basic Amazon Monitron Console functionality, you need to attach the `AmazonMonitronFullAccess` managed policy\. Depending on the circumstances, you may also need additional permissions to the Organizations and SSO service\. Contact AWS support if you need more information\.



## Example: List All Amazon Monitron Projects<a name="security_iam_id-based-policy-examples-access-one-bucket"></a>

This example policy grants an IAM user in your AWS account permission to list all projects in your account\. 

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": "monitron:ListProject"
            "Resource": "*"
        }
    ]
}
```

## Example: List Amazon Monitron Projects Based on Tags<a name="security_iam_id-based-policy-examples-view-widget-tags"></a>

You can use conditions in your identity\-based policy to control access to Amazon Monitron resources based on tags\. This example shows how you might create a policy that allows listing projects\. However, permission is granted only if the project tag `location` has the value of `Seattle`\. This policy also grants the permissions necessary to complete this action on the console\.

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "ListProjectsInConsole",
            "Effect": "Allow",
            "Action": "monitron:ListProjects",
            "Resource": "*"
       
            "Condition": {
                "StringEquals": {
                     "aws:ResourceTag/location": "Seattle"
                }
            }
        }
    ]
}
```

For more information, see [IAM JSON Policy Elements: Condition](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) in the *IAM User Guide*\.