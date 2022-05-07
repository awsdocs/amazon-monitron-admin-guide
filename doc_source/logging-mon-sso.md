# Returning to Amazon Monitron with SSO<a name="logging-mon-sso"></a>

When you log out of the Amazon Monitron web app, you may still be signed in to AWS SSO\. Any other applications that you have opened from the user portal remain open and running\.

There are two ways to log out of SSO:
+ Log out directly through the SSO portal\.
+ Once an hour, AWS SSO checks to see if you are actively using any AWS services\. If you are not, then you are logged out of SSO automatically\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/log-back-in.png)

To learn about admin users using SSO, see [User directory setup](mu-adding-user.md)\.

To learn about security best practices with Amazon Monitron and SSO, see [Security Best Practices for Amazon Monitron](security-best-practices.md)\.

To learn about using the SSO user portal, see [Using the user portal](https://docs.aws.amazon.com/singlesignon/latest/userguide/using-the-portal)\.

Open the AWS Single Sign\-On console at [https://console\.aws\.amazon\.com/singlesignon/](https://console.aws.amazon.com/singlesignon/)\.