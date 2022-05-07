# Logging Amazon Monitron actions with AWS CloudTrail<a name="logging-using-cloudtrail"></a>

Amazon Monitron is integrated with AWS CloudTrail, a service that provides a record of actions taken by a user, role, or an AWS service in Amazon Monitron\. CloudTrail captures API calls for Amazon Monitron as events\. CloudTrail captures calls from both the Amazon Monitron console and the Amazon Monitron mobile app\. If you create a trail, you can enable continuous delivery of CloudTrail events to an Amazon Simple Storage Service \(Amazon S3\) bucket, including events for Amazon Monitron\. If you don't configure a trail, you can still view the most recent events in the CloudTrail console in **Event history**\. Using the information collected by CloudTrail, you can determine the console or mobile app request that was made to Amazon Monitron, the IP address from which the request was made, who made the request, when it was made, and additional details\. 

To learn more about CloudTrail, including how to configure and enable it, see the [AWS CloudTrail User Guide](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/)\.

**Topics**
+ [Amazon Monitron information in CloudTrail](#service-name-info-in-cloudtrail)
+ [Example: Amazon Monitron log file entries](#understanding-service-name-entries)

## Amazon Monitron information in CloudTrail<a name="service-name-info-in-cloudtrail"></a>

CloudTrail is enabled on your AWS account when you create the account\. When supported event activity occurs in Amazon Monitron, that activity is recorded in a CloudTrail event along with other AWS service events in **Event history**\. You can view, search, and download recent events in your AWS account\. For more information, see [Viewing Events with CloudTrail Event History](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/view-cloudtrail-events.html)\. 

For an ongoing record of events in your AWS account, including events for Amazon Monitron, create a trail\. A *trail* enables CloudTrail to deliver log files to an Amazon S3 bucket\. By default, when you create a trail in the console, the trail applies to all AWS Regions\. The trail logs events from all Regions in the AWS partition and delivers the log files to the Amazon S3 bucket that you specify\. Additionally, you can configure other AWS services to further analyze and act upon the event data collected in CloudTrail logs\. For more information, see the following: 
+ [Overview for Creating a Trail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-create-and-update-a-trail.html)
+ [CloudTrail Supported Services and Integrations](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-aws-service-specific-topics.html#cloudtrail-aws-service-specific-topics-integrations)
+ [Configuring Amazon SNS Notifications for CloudTrail](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/getting_notifications_top_level.html)
+ [Receiving CloudTrail Log Files from Multiple Regions](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/receive-cloudtrail-log-files-from-multiple-regions.html) and [Receiving CloudTrail Log Files from Multiple Accounts](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-receive-logs-from-multiple-accounts.html)

Amazon Monitron supports logging a number of actions as events\. Although the operations are publicly accessible through the AWS console or the Amazon Monitron mobile app, the APIs themselves are not public and are subject to change\. They are meant for logging purposes only, and applications should not be built with them\.

Amazon Monitron supports the following actions as events in CloudTrail log files:
+ [CreateProject](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mp-creating-project.html)
+ [UpdateProject](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mp-updating-project.html)
+ [DeleteProject](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mp-delete-project.html)
+ [GetProject](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mp-project-tasks.html)
+ [ListProjects](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mp-project-tasks.html)
+ [AssociateProjectAdminUser](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mu-adding-user.html)
+ [DisassociateProjectAdminUser](https://docs.aws.amazon.com/Monitron/latest/admin-guide/mu-remove-project-admin.html)
+ [ListProjectAdminUsers](https://docs.aws.amazon.com/Monitron/latest/admin-guide/user-management-chapter.html)
+ [GetProjectAdminUser](https://docs.aws.amazon.com/Monitron/latest/admin-guide/user-management-chapter.html)
+ [TagResource](https://docs.aws.amazon.com/Monitron/latest/admin-guide/tagging.html#tag-original-1)
+ [UntagResource](https://docs.aws.amazon.com/Monitron/latest/admin-guide/tagging.html#modify-tag-1)
+ [ListTagsForResource](https://docs.aws.amazon.com/Monitron/latest/admin-guide/tagging.html)
+ [AmazonMonitronApp:CreateSensor](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-add-sensors.html)
+ [AmazonMonitronApp:UpdateSensor](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-edit-sensorposition.html)
+ [AmazonMonitronApp:DeleteSensor](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-delete-sensor.html)
+ [AmazonMonitronApp:CreateGateway](https://docs.aws.amazon.com/Monitron/latest/user-guide/adding-gateway.html)
+ [AmazonMonitronApp:DeleteGateway](https://docs.aws.amazon.com/Monitron/latest/user-guide/deleting-gateway.html)
+ [AmazonMonitronApp:CreateSite](https://docs.aws.amazon.com/Monitron/latest/user-guide/SM-creating-site.html)
+ [AmazonMonitronApp:UpdateSite](https://docs.aws.amazon.com/Monitron/latest/user-guide/SM-editing-site.html)
+ [AmazonMonitronApp:DeleteSite](https://docs.aws.amazon.com/Monitron/latest/user-guide/SM-deleting-site.html)
+ [AmazonMonitronApp:CreateAsset](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-add-assets.html)
+ [AmazonMonitronApp:UpdateAsset](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-edit-assets.html)
+ [AmazonMonitronApp:DeleteAsset](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-delete-assets.html)
+ [AmazonMonitronApp:CreateAssetStateTransition](https://docs.aws.amazon.com/Monitron/latest/user-guide/as-assets.html)
+ [AmazonMonitronApp:CreateUserAccessRoleAssociation](https://docs.aws.amazon.com/Monitron/latest/user-guide/what-is-monitron.html)
+ [AmazonMonitronApp:UpdateUserAccessRoleAssociation](https://docs.aws.amazon.com/Monitron/latest/user-guide/what-is-monitron.html)
+ [AmazonMonitronApp:DeleteUserAccessRoleAssociation](https://docs.aws.amazon.com/Monitron/latest/user-guide/what-is-monitron.html)

Every event or log entry contains information about who generated the request\. This contains details about the type of IAM identity that made the request, and which credentials were used\. If temporary credentials were used, the element shows how the credentials were obtained\. The identity information helps you determine the following: 
+ Whether the request was made with root or AWS Identity and Access Management \(IAM\) user credentials 
+ Whether the request was made with temporary security credentials for a role or federated user
+ Whether the request was made by another AWS service

For more information, see the [CloudTrail userIdentity Element](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html) in the *AWS CloudTrail User Guide*\.

## Example: Amazon Monitron log file entries<a name="understanding-service-name-entries"></a>

A trail is a configuration that enables delivery of events as log files to an Amazon S3 bucket that you specify\. CloudTrail log files contain one or more log entries\. An event represents a single request from any source and includes information about the requested action, the date and time of the action, request parameters, and so on\. CloudTrail log files aren't an ordered stack trace of the public API calls, so they don't appear in any specific order\.

The following examples show CloudTrail log entries that demonstrate the project deletion \(`DeleteProject`\) action\.

### Successful DeleteProject action<a name="collapsible-section-1"></a>

The following example show what might appear in the CloudTrail log following a successful `DeleteProject` action\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "AssumedRole",
    "principalId": "principal ID",
    "arn": "ARN",
    "accountId": "account ID",
    "accessKeyId": "access key ID",
    "sessionContext": {
      "sessionIssuer": {
        "type": "Role",
        "principalId": "principal ID",
        "arn": "ARN",
        "accountId": "account ID",
        "userName": "user name"
      },
      "webIdFederationData": {},
      "attributes": {
        "mfaAuthenticated": "false",
        "creationDate": "timestamp"
      }
    }
  },
  "eventTime": "timestamp",
  "eventSource": "monitron.amazonaws.com",
  "eventName": "DeleteProject",
  "awsRegion": "region",
  "sourceIPAddress": "source IP address",
  "userAgent": "user agent",
  "requestParameters": {
    "Name": "name"
  },
  "responseElements": {
    "Name": "name"
  },
  "requestID": "request ID",
  "eventID": "event ID",
  "readOnly": false,
  "eventType": "AwsApiCall",
  "recipientAccountId": "account ID"
}
```

### Failed DeleteProject action \(authorization error\)<a name="collapsible-section-2"></a>

The following example shows what might appear in the CloudTrail log following a failed `DeleteProject` action due to an error occurring\. In this case, the error is an authorization error, where the user does not have permission to delete the specified project\.

```
{
    "eventVersion": "1.05",
    "userIdentity": {
        "type": "IAMUser",
        "principalId": "principal ID",
        "arn": "ARN",
        "accountId": "account ID",
        "accessKeyId": "access key ID",
        "userName": "user name",
        "sessionContext": {
            "sessionIssuer": {},
            "webIdFederationData": {},
            "attributes": {
                "mfaAuthenticated": "false",
                "creationDate": "timestamp"
            }
        }
    },
    "eventTime": "timestamp",
    "eventSource": "monitron.amazonaws.com",
    "eventName": "DeleteProject",
    "awsRegion": "region",
    "sourceIPAddress": "source IP address",
    "userAgent": "user agent",
    "errorCode": "AccessDenied",
    "requestParameters": {
        "Name": "name"
    },
    "responseElements": {
        "Message": "User: user ARN is not authorized to perform: monitron:DeleteProject on resource: resource ARN"
    },
    "requestID": "request ID",
    "eventID": "event ID",
    "readOnly": false,
    "eventType": "AwsApiCall",
    "recipientAccountId": "account ID"
}
```

### Failed DeleteProject action \(conflict exception error\)<a name="collapsible-section-3"></a>

The following example shows what might appear in the CloudTrail log following a failed `DeleteProject` action due to an error occurring\. In this case, the error is a conflict exception, where sensors are still present when Amazon Monitron attempts to delete a project\.

```
{
  "eventVersion": "1.05",
  "userIdentity": {
    "type": "AssumedRole",
    "principalId": "principal ID",
    "arn": "ARN",
    "accountId": "account ID",
    "accessKeyId": "access key ID",
    "sessionContext": {
      "sessionIssuer": {
        "type": "Role",
        "principalId": "principal ID",
        "arn": "ARN",
        "accountId": "account ID",
        "userName": "user name"
      },
      "webIdFederationData": {},
      "attributes": {
        "mfaAuthenticated": "false",
        "creationDate": "timestamp"
      }
    }
  },
  "eventTime": "timestamp",
  "eventSource": "monitron.amazonaws.com",
  "eventName": "DeleteProject",
  "awsRegion": "region",
  "sourceIPAddress": "source IP address",
  "userAgent": "user agent",
  "errorCode": "ConflictException",
  "requestParameters": {
    "Name": "name"
  },
  "responseElements": {
    "message": "This project still has sensors associated to it and cannot be deleted."
  },
  "requestID": "request ID",
  "eventID": "event ID",
  "readOnly": false,
  "eventType": "AwsApiCall",
  "recipientAccountId": "account ID"
}
```