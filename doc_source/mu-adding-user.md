# User directory setup<a name="mu-adding-user"></a>

Amazon Monitron uses AWS Single Sign\-On \(AWS SSO\) to manage user access\. Users are added from this AWS SSO user directory\.

How you add an admin user depends on how AWS SSO has been set up for your organization\. 

**Topics**
+ [Understanding SSO requirements](#sso-requirements)
+ [Adding admin users using the native AWS SSO directory](#mp-project-admin2)
+ [Adding admin users using Microsoft Active Directory](#mp-project-admin3)
+ [Adding admin users using an external ID provider](#mp-project-admin4)

## Understanding SSO requirements<a name="sso-requirements"></a>

When you create a project, Amazon Monitron automatically detects whether AWS SSO has been enabled and configured on your account and whether all prerequisites for using AWS SSO with Amazon Monitron are satisfied\. If not, Amazon Monitron produces an error and provides a list of prerequisites that are needed\. You must meet all prerequisites before you can add admin users\. For more information about enabling and configuring AWS SSO for your organization, see [AWS Single Sign\-On](https://docs.aws.amazon.com/singlesignon/latest/userguide/what-is.html)\. 

**Important**  
In order to use Amazon Monitron, you must configure AWS SSO in one of the two regions where Amazon Monitron is currently supported:  
US East \(N\. Virginia\): us\-east\-1
Europe \(Ireland\): eu\-west\-1

### AWS SSO prerequisites<a name="prereqs"></a>

Before you can set up AWS SSO, you must:
+ Have first set up the AWS Organizations service and have **All features** set to enabled\. For more information about this setting, see [Enabling All Features in Your Organization](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org_support-all-features.html) in the *AWS Organizations User Guide*\.
+ Sign in with the AWS Organizations management account credentials before you begin setting up AWS SSO\. These credentials are required to enable AWS SSO\. For more information, see [Creating and Managing an AWS Organization](http://docs.aws.amazon.com/organizations/latest/userguide/orgs_manage_org.html) in the *AWS Organizations User Guide*\. You cannot set up AWS SSO while signed in with credentials from an Organization’s member account\.
+ Have chosen an identity source to determine which pool of users has SSO access to the user portal\. If you choose to use the default AWS SSO identity source for your user store, no prerequisite tasks are required\. The AWS SSO store is created by default once you enable AWS SSO and is immediately ready for use\. There is no cost for using this store\. Alternatively, you can choose to [Connect to your external identity provider](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-ad.html) using Azure Active Directory\. If you choose to connect to an existing Active Directory for your user store, you must have the following:
  + An existing AD Connector or AWS Managed Microsoft AD directory set up in AWS Directory Service, and it must reside within your organization's management account\. You can connect only one AWS Managed Microsoft AD directory at a time\. However, you can change it to a different AWS Managed Microsoft AD directory or change it back to an AWS SSO store at any time\. For more information, see [Create a AWS Managed Microsoft AD Directory](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/create_directory.html) in the *AWS Directory Service Administration Guide*\.
  + Set up AWS SSO in the Region where your AWS Managed Microsoft AD directory is set up\. AWS SSO stores the assignment data in the same Region as the directory\. To administer AWS SSO, you should switch to the Region where you have setup AWS SSO\. Also, note that AWS SSO’s user portal uses the same [access URL](http://docs.aws.amazon.com/directoryservice/latest/admin-guide/access_url.html) as your connected directory\.
+ If you currently filter access to specific Amazon Web Service \(AWS\) domains or URL endpoints using a web content filtering solution such as next\-generation firewalls \(NGFW\) or secure web gateways \(SWG\), you must add the following domains and/or URL endpoints to your web\-content filtering solution allow\-lists in order for AWS SSO to work properly:

  **Specific DNS domains**
  + \*\.awsapps\.com \(http://awsapps\.com/\)
  + \*\.signin\.aws

  **Specific URL End\-points**
  + https://\[yourdirectory\]\.awsapps\.com/start
  + https://\[yourdirectory\]\.awsapps\.com/login
  + https://\[yourregion\]\.signin\.aws/platform/login

We highly recommend that before you enable AWS SSO you first check to see if your AWS account is approaching the quota limit for IAM roles\. For more information, see [IAM object quotas](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_iam-quotas.html#reference_iam-quotas-entities)\. If you are nearing the quota limit, consider increasing the quota\. Otherwise, you may have issues with AWS SSO as you provision permission sets to accounts that have exceeded the IAM role limit\.

## Adding admin users using the native AWS SSO directory<a name="mp-project-admin2"></a>

The simplest way to add admin users to your project is by using the AWS SSO native directory\. You can use it by starting to use Amazon Monitron and letting it configure AWS SSO at a basic level for you\. You can also set up AWS SSO before using Amazon Monitron and set it to use the native directory\. Either way, you can add users manually and without potentially exposing user identity information to other admin users beyond name and email\.

**To add an admin user when using the native AWS SSO directory**

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron ](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\.

1. In the navigation pane, choose the project you want\. 

1. On the **Users** page, choose the users that you want to assign as admin users\. If you can't see a user, search for them\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/users.png)

   The users you choose are displayed in the **Selected users** section\.

1. If the user you want isn't in the directory, choose **Create user** to add the user\. 

   1. Under **Create a user**, for **Email**, enter the new admin user's email address\.

        
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/create-user.png)

   1. For **First name** and **Last name**, enter the admin's name\.

   1. Choose **Create User**\. 

1. When the user's name appears in the directory list, choose **Add** to add the admin users you've selected\. 

1. Email the admin users an invitation to the project that includes a link to download the Amazon Monitron mobile app\. For more information, see [Sending an email invitation](mu-email-invitation.md)\.

   Amazon Monitron takes you to the project page for your project, where it lists all admin users\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/project-admin-user-list.png)

1. To add additional admin users, choose **Add admin**\. 

   Any admin user can add other users using the Amazon Monitron mobile app\. For more information, see [Adding a User](https://docs.aws.amazon.com/Monitron/latest/user-guide/adding-user.html) in the *Amazon Monitron User Guide*\.

## Adding admin users using Microsoft Active Directory<a name="mp-project-admin3"></a>

If you use Microsoft Active Directory \(AD\) for your organization's primary user directory, you can configure AWS SSO to use it\. AWS SSO enables you to connect your self\-managed Active Directory as your AWS Managed Microsoft AD directory using AWS Directory Service\. This Microsoft AD directory provides you with the pool of identities that you can pull from when using the Amazon Monitron console \(or Amazon Monitron mobile app\) to assign user roles\.

All Amazon Monitron admin users have access to identity information in the user directory that is configured in AWS SSO for Amazon Monitron\. We strongly recommend using an isolated directory if you want to limit access to user organization information\.

**To add an admin user using Microsoft Active Directory**

1. Configure AWS SSO to connect with your Microsoft Active Directory\. The steps involved in this differ depending on whether you're using a self\-managed Active Directory or an AWS Managed Microsoft AD directory\. For more information, see [Connect to Microsoft AD Directory](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-ad.html)\.

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron ](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\.

1. In the navigation pane, choose the project you want\. 

1. For **Active directory domain**, choose the directory domain from which you want to add identities\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/activedirectory.png)

1. Choose **Users** or **Groups**, depending on how you want to search the user directory\. 

1. Enter a string in the search box to find the identity you want to add and then choose ** Search**\. 

   To limit the number of users returned, enter a longer string in the search box\. For example, if you enter "olg" in the search box, the list returns all users with the letters "olg" in their names, such as "Olga Kurth" and "Jamie Folgman\." 

1. Choose the users you want to assign as admin users\. 

1. Choose **Add** to add the admin users\. 

## Adding admin users using an external ID provider<a name="mp-project-admin4"></a>

If you're using an external Identity provider \(IdP\), you can configure AWS SSO to use that provider through the Security Assertion Markup Language \(SAML\) 2\.0 standard\. This provides you with the pool of identities in your IdP directory\. You can pull this pool when using the Amazon Monitron console \(or Amazon Monitron mobile app\) and assign them as admin users\. This also enables your users to sign in to Amazon Monitron with their corporate credentials\. 

All Amazon Monitron admin users have access to identity information in the user directory that is configured in AWS SSO for Amazon Monitron\. We strongly recommend using an isolated directory if you want to limit access to user organization information\.

**To add an admin user using an external ID provider \(IdP\)**

1. Configure AWS SSO to connect with your external IdP\. The steps involved in this differ based on the provider you're using\. For more information, see [Connect to Your External ID Provider](https://docs.aws.amazon.com/singlesignon/latest/userguide/manage-your-identity-source-idp.html)\.

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron ](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\.

1. In the navigation pane, choose the project you want\. 

1. On the **Users** page, choose the users that you want to assign as admin users\. If you can't see a user, search for them\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/IdPscreen.png)

1. Choose **Add** to add the admin users\. 