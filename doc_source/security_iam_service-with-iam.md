# How Amazon Monitron Works with IAM<a name="security_iam_service-with-iam"></a>

Before you use IAM to manage access to Amazon Monitron, you should understand what IAM features are available to use with Amazon Monitron\. To get a high\-level view of how Amazon Monitron and other AWS services work with IAM, see [AWS Services That Work with IAM](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html) in the *IAM User Guide*\.

**Topics**
+ [Amazon Monitron Identity\-Based Policies](#security_iam_service-with-iam-id-based-policies)
+ [Amazon Monitron Resource\-Based Policies](#security_iam_service-with-iam-resource-based-policies)
+ [Authorization Based on Amazon Monitron Tags](#security_iam_service-with-iam-tags)
+ [Amazon Monitron IAM Roles](#security_iam_service-with-iam-roles)

## Amazon Monitron Identity\-Based Policies<a name="security_iam_service-with-iam-id-based-policies"></a>

To specify allowed or denied actions and resources and the conditions under which actions are allowed or denied, use IAM identity\-based policies\. Amazon Monitron supports specific actions, resources, and condition keys\. To learn about all of the elements that you use in a JSON policy, see [IAM JSON Policy Elements Reference](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html) in the *IAM User Guide*\.

### Actions<a name="security_iam_service-with-iam-id-based-policies-actions"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Action` element of a JSON policy describes the actions that you can use to allow or deny access in a policy\. Policy actions usually have the same name as the associated AWS API operation\. There are some exceptions, such as *permission\-only actions* that don't have a matching API operation\. There are also some operations that require multiple actions in a policy\. These additional actions are called *dependent actions*\.

Include actions in a policy to grant permissions to perform the associated operation\.

In Amazon Monitron, policy actions use the following prefix before the action: `monitron:`\. For example, to grant someone permission to create a project with the Amazon Monitron `CreateProject` operation, you include the `monitron:CreateProject` action in their policy\. Policy statements must include either an `Action` or `NotAction` element\. Amazon Monitron defines its own set of actions that describe tasks that you can perform with this service\.

**Note**  
With the `deleteProject` operation, you must have the AWS Single Sign\-On \(SSO\) permissions for deletion\. Without these permissions, the delete functionality will still remove the project\. However, it will not remove the resources from SSO and you may end up with dangling references on SSO\.

To specify multiple actions in a single statement, separate them with commas as follows:

```
"Action": [
      "monitron:action1",
      "monitron:action2"
]
```

You can specify multiple actions using wildcards \(\*\)\. For example, to specify all actions that begin with the word `List`, include the following action:

```
"Action": "monitron:List*"
```

### Resources<a name="security_iam_service-with-iam-id-based-policies-resources"></a>

Amazon Monitron does not support specifying resource ARNs in a policy\.

### Condition Keys<a name="security_iam_service-with-iam-id-based-policies-conditionkeys"></a>

Administrators can use AWS JSON policies to specify who has access to what\. That is, which **principal** can perform **actions** on what **resources**, and under what **conditions**\.

The `Condition` element \(or `Condition` *block*\) lets you specify conditions in which a statement is in effect\. The `Condition` element is optional\. You can create conditional expressions that use [condition operators](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition_operators.html), such as equals or less than, to match the condition in the policy with values in the request\. 

If you specify multiple `Condition` elements in a statement, or multiple keys in a single `Condition` element, AWS evaluates them using a logical `AND` operation\. If you specify multiple values for a single condition key, AWS evaluates the condition using a logical `OR` operation\. All of the conditions must be met before the statement's permissions are granted\.

 You can also use placeholder variables when you specify conditions\. For example, you can grant an IAM user permission to access a resource only if it is tagged with their IAM user name\. For more information, see [IAM policy elements: variables and tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_variables.html) in the *IAM User Guide*\. 

AWS supports global condition keys and service\-specific condition keys\. To see all AWS global condition keys, see [AWS global condition context keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

Amazon Monitron defines its own set of condition keys and also supports using some global condition keys\. For a list of all AWS global condition keys, see [AWS Global Condition Context Keys](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_condition-keys.html) in the *IAM User Guide*\.

To see a list of Amazon Monitron condition keys, see [Actions defined by Amazon Monitron](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazonmonitron.html#amazonmonitron-actions-as-permissions) in the *IAM User Guide*\. To learn with which actions and resources you can use a condition key, see [Condition keys for Amazon Monitron](https://docs.aws.amazon.com/service-authorization/latest/reference/list_amazonmonitron.html#amazonmonitron-policy-keys)\.

### Examples<a name="security_iam_service-with-iam-id-based-policies-examples"></a>

To view examples of Amazon Monitron identity\-based policies, see [Amazon Monitron Identity\-Based Policy Examples](security_iam_id-based-policy-examples.md)\.

## Amazon Monitron Resource\-Based Policies<a name="security_iam_service-with-iam-resource-based-policies"></a>

Amazon Monitron does not support resource\-based policies\.

## Authorization Based on Amazon Monitron Tags<a name="security_iam_service-with-iam-tags"></a>

You can associate tags with certain types of Amazon Monitron resources for authorization\. To control access based on tags, provide tag information in the [condition element](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_condition.html) of a policy using the `Amazon Monitron:TagResource/${TagKey}`, `aws:RequestTag/${TagKey}`, or `aws:TagKeys` condition keys\. 

## Amazon Monitron IAM Roles<a name="security_iam_service-with-iam-roles"></a>

An [IAM role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles.html) is an entity within your AWS account that has specific permissions\.

### Using Temporary Credentials with Amazon Monitron<a name="security_iam_service-with-iam-roles-tempcreds"></a>

You can use temporary credentials to sign in with federation, assume an IAM role, or assume a cross\-account role\. You obtain temporary security credentials by calling AWS STS API operations such as [AssumeRole](https://docs.aws.amazon.com/STS/latest/APIReference/API_AssumeRole.html) or [GetFederationToken](https://docs.aws.amazon.com/STS/latest/APIReference/API_GetFederationToken.html)\. 

Amazon Monitron supports using temporary credentials\. 

### Service\-Linked Roles<a name="security_iam_service-with-iam-roles-service-linked"></a>

[Service\-linked roles](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-linked-role) allow AWS services to access resources in other services to complete an action on your behalf\. Service\-linked roles appear in your IAM account and are owned by the service\. An IAM administrator can view but not edit the permissions for service\-linked roles\. 

Amazon Monitron supports service\-linked roles\. 

### Service Roles<a name="security_iam_service-with-iam-roles-service"></a>

This feature allows a service to assume a [service role](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html#iam-term-service-role) on your behalf\. This role allows the service to access resources in other services to complete an action on your behalf\. Service roles appear in your IAM account and are owned by the account\. This means that an IAM administrator can change the permissions for this role\. However, doing so might break the functionality of the service\.

Amazon Monitron supports service roles\. 

### <a name="security_iam_service-with-iam-roles-choose"></a>