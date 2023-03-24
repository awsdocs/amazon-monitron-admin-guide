# Using tags with your Amazon Monitron project<a name="tagging"></a>

A *tag* is a key\-value pair that you can use to categorize your projects\. For example, if you have multiple projects, you might categorize them by purpose, owner, location, or any other factor\. 

Use tags to:
+ Organize your projects\. You can search and filter by tag\. For example, you could add tags such as ‘test lab’ or ‘paint shop' to easily find those projects\. 
+ Identify and organize your AWS resources\. Many AWS services support tagging, so you can assign the same tag to resources in different services to indicate that the resources are related\. For example, you can tag a project and the Amazon Simple Storage Service \(Amazon S3\) bucket that stores related data with the same tag\.
+ Control access to your resources\. You can use tags in AWS Identity and Access Management \(IAM\) policies that control access to Amazon Monitron projects\. You can attach these policies to an IAM role or user to enable tag\-based access control\. For more information, see [Controlling access using tags](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_tags.html) in the *IAM User Guide*\. 

Each tag key must be unique within a project\. 

The following restrictions also apply to Amazon Monitron project tags:
+ The maximum number of tags per project is 50\.
+ The maximum length of a tag key is 128 characters\.
+ The maximum length of a tag value is 256 characters\.
+ Valid characters for keys and values are a–z, A–Z, space, \_ \. : / = \+ \- and @\.
+ Tag keys and values are case sensitive\.
+ The `aws:` prefix is reserved for AWS use\.
+ If you plan to use your tagging schema across multiple services and resources, remember that other services might have different restrictions for valid characters\. Refer to the documentation for that service\.

**Topics**
+ [Adding a tag to a project when you create it](#tag-original-1)
+ [Adding a tag to a project after it’s been created](#tag-existing-1)
+ [Modifying or removing a tag](#modify-tag-1)

## Adding a tag to a project when you create it<a name="tag-original-1"></a>

**To add a tag to a project when creating it**

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron ](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\.

1. In the navigation pane, choose the project you want

1. Expand the **Tags** section\.  
![\[Expand the Tags section to add tags to your project.\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-3.png)

1. Choose **Add new tag**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-a.png)

1. Enter the key\-value pair for your tag\. 

   The key must be unique for the project\. The value is optional\.  
![\[Enter a key and an optional value in the Tags section.\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-1.png)

1. Choose **Add new tag**\.

1. To add more tags, repeat steps 2 and 3\.

1. To remove a tag, choose **Remove**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-b.png)

1. Remove blank tag entries and then choose **Next**\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-c.png)

## Adding a tag to a project after it’s been created<a name="tag-existing-1"></a>

You can add a tag to a project on the project detail page\. 

**To add a tag to an existing project**

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron ](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\. 

1. In the navigation pane, choose **Projects**, and then choose the project you want\. 

1. Under **Tags**, choose **Manage tags**\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-d.png)

1. Choose **Add new tag**  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-e.png)

1. Enter the key\-value pair for your tag\. 
**Note**  
Remember that the key must be unique for the project\. The value is optional\.  
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-f.png)

1. Choose **Save**\.

## Modifying or removing a tag<a name="modify-tag-1"></a>

You can modify a tag value, but not a tag key\. To change a tag key, remove the tag, then create a new tag with a different key\. You can also remove any tag\. You modify or remove tags on the project detail page\. 

**To modify or remove a tag**

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\. 

1. In the navigation pane, choose **Projects**, and then choose the project you want\. 

1. Under **Tags**, choose **Manage tags**\.

1. To modify the tag value, make the change\. To remove the tag, choose **Remove** next to the tag\.   
![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/tag-e.png)

1. Choose **Save**\.
