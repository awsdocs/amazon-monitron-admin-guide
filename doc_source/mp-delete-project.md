# Deleting a project<a name="mp-delete-project"></a>

With the `deleteProject` operation, you must have the AWS Single Sign\-On \(SSO\) permissions for deletion\. Without these permissions, the console's delete project functionality will still remove the project\. However, it will not remove the resources from SSO and you may end up with dangling references on SSO\.

**To delete a project**

1. Open the Amazon Monitron console at [ https://console\.aws\.amazon\.com/monitron ](https://console.aws.amazon.com/monitron/)\. 

1. Choose **Create Project**\. 

1. In the navigation pane, choose **Projects**\. 

1. From the **Projects** list, choose the project you want to delete\. 

1. Choose **Delete Project**\. 

1. Enter **Delete** in the confirmation box to confirm the deletion\. 

   If the project contains any active assets or sensors, you have to remove them before deleting the project\. If this is the case, the confirmation box and option to delete don't appear\. 

   If there are active assets or sensors that need to be removed to delete this project, ask an Admin user do this or do it yourself by logging into the *Amazon Monitron mobile app*\.

1. Choose **Delete**\. 