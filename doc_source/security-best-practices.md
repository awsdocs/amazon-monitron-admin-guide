# Security Best Practices for Amazon Monitron<a name="security-best-practices"></a>

Amazon Monitron provides a number of security features to consider as you develop and implement your own security policies\. The following best practices are general guidelines and don’t represent a complete security solution\. Because these best practices might not be appropriate or sufficient for your environment, treat them as helpful considerations rather than prescriptions\.

The following best practices for Amazon Monitron can help prevent security incidents:
+ When creating an AWS Single Sign\-On \(AWS SSO\) directory of users for Amazon Monitron enable multi\-factor authentication \(MFA\) for the directory for better directory security\.
+ Be aware that all project and site admins using the Amazon Monitron mobile app will have read access to all users in your organization who are listed in the user directory you choose when setting up your project\. We strongly recommend using an isolated directory if you want to limit access to user organization information\.
+ Because of the danger of phishing attacks, in which an attacker sends an email impersonating a Amazon Monitron project invitation email to your users, warn users to make sure that the directory name is visible on the login screen before they enter their sign\-in credentials\.
+ Because the Amazon Monitron mobile app runs on a smartphone and has access to your project, have all users enable screen lock to protect access when not in use\.