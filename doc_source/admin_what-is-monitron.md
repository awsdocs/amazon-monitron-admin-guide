# What Is Amazon Monitron?<a name="admin_what-is-monitron"></a>

Amazon Monitron is a machine learning \(ML\) end\-to\-end condition monitoring solution system that detects potential failures within equipment, enabling you to implement a predictive maintenance program and reduce lost productivity from unplanned machine downtime\. Amazon Monitron includes purpose\-built sensors to capture vibration and temperature data; gateways to automatically transfer data to the AWS Cloud; and a mobile and web application for system setup, analytics, and notiﬁcation when tracking equipment condition\. Reliability managers can quickly deploy Amazon Monitron to easily track the machine health of industrial equipment—such as bearings, motors, gearboxes, and pumps—without any development work or specialized training\.

Using sensors mounted on your equipment and industry\-recognized vibration standards and machine learning techniques, Amazon Monitron analyzes data for indications of potential equipment failure\. It notifies you about developing faults so you can resolve them before they become more serious problems\. With Amazon Monitron, you can schedule corrective maintenance activities more effectively to limit productivity losses and minimize repair costs that can result from catastrophic failure of your equipment\. 

The sensors capture both temperature and vibration data and send it to the AWS Cloud using gateways that fit unobtrusively on factory walls and use your Wi\-Fi network\. Amazon Monitron analyzes and interprets the data, then sends the information to the Amazon Monitron mobile and web app, where your team monitors the condition of your machines\. When there is a problem with one of your machines, Amazon Monitron immediately sends a notification on the mobile and web app to let you know\. 

This guide covers IT Manager tasks, including
+ Performing tasks that you need to do as AWS account user\.
+ Creating an Amazon Monitron project to contain the monitoring activities of the rest of your monitoring team \(reliability managers and technicians\)\. The *Amazon Monitron User Guide* describes how to install and operate the Amazon Monitron devices using the mobile and web app\.
+ Creating or attaching the project to an AWS Single Sign\-On \(AWS SSO\) directory\. End users will log into the app not as AWS account users, but through the credentials of the AWS SSO directory\. 

**Topics**
+ [Features of Amazon Monitron](#admin-benefits)
+ [Amazon Monitron devices and software](#admin-system-software)
+ [Getting started with Amazon Monitron](#gettingstarted)
+ [Related resources](#other-help)
+ [Pricing for Amazon Monitron](#pricing)

## Features of Amazon Monitron<a name="admin-benefits"></a>

 Amazon Monitron provides the following key features:
+ **Works out of the box** – Amazon Monitron sensors and gateways are preconfigured to work with Amazon Monitron software\. Reliability managers can install these devices easily and quickly using the mobile or web app and can start monitoring equipment in just a matter of few hours\. Amazon Monitron is simple to set up and requires no development work, knowledge of ML, or integration\. 
+ **Immediate notifications in the Amazon Monitron mobile and web app** – When it detects abnormal machine patterns, Amazon Monitron sends notifications to users in the mobile and web app\. Technicians can view, track, and provide feedback on these abnormal machine states within the mobile and web app\. 
+ **ISO\- and ML\-based analytics** – Amazon Monitron automatically detects abnormal machine operating states by analyzing vibration and temperature signals and comparing them to International Standards Organization \(ISO 20816\) standard thresholds and ML enabled models\. 
+ **Support for adding feedback in the app** –Amazon Monitron offers simple workflows for technicians to enter feedback on the accuracy and nature of the alerts in the mobile and web app\. Amazon Monitron learns from that feedback and continually improves over time\.

## Amazon Monitron devices and software<a name="admin-system-software"></a>

**Devices**

 Amazon Monitron includes two types of devices: a sensor, for collecting data from your equipment, and a gateway, for sending that data to Amazon Monitron\. You can purchase both from [Amazon\.com](https://amazon.com/) or [Amazon Business](https://business.amazon.com/)\. You mount the sensors directly on the machines \(or *assets*\) that you want to monitor\. You can place up to 20 sensors on an asset\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/real-sensor.png)

Each sensor measures temperature and vibration data from the asset and sends it to the AWS Cloud using a gateway that is mounted nearby\. If it's a Wi\-Fi gateway, it is plugged into a standard outlet\. If it's an Ethernet gateway, it gets power from the Ethernet cord plugged into its RJ\-45 socket\.

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/real-gateway.png)

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/small-lights-button-cable.png)

**Software**

Most Amazon Monitron tasks are performed by your team using the Amazon Monitron mobile app, which is installed on smartphones, or the web app, which you can use through a web browser on a laptop or desktop computer\. The reliability manager uses these apps to set up assets, sensors, gateways, and so on\. Technicians use the apps to monitor data from the sensors\. For more information about these tasks, see the *Amazon Monitron User Guide*\.

Amazon Monitron also includes a console, which is used by the IT Manager to create a project and add admin users to manage it\. This project is the framework for all the Amazon Monitron tasks that the rest of the team performs to monitor your equipment\. Until you set up the project, no other equipment monitoring can be done using Amazon Monitron\. IT Manager tasks include the following:
+ Setting up a user directory to provide users for Amazon Monitron
+ Creating a project to contain all of your team's Amazon Monitron monitoring tasks, such as creating sites, pairing sensors, adding assets, and so on
+ Adding an admin user to manage the project 

This guide describes how to perform these tasks\.

## Getting started with Amazon Monitron<a name="gettingstarted"></a>

Amazon Monitron divides tasks by whether they require the Amazon Monitron console or the app \(mobile or web\)\. This guide shows you how to create a project and initially assign admin users to manage it\. These are the tasks that require using the console\. Tasks that use the Amazon Monitron mobile or web app include managing a project, creating assets, setting up sensors \(mobile app only\), and monitoring the condition of your equipment\. For more information about these tasks, see the [Amazon Monitron User Guide](https://docs.aws.amazon.com/Monitron/latest/user-guide/what-is-monitron.html)\.

Before you can start the tasks in this guide, it's necessary to set up an AWS account and an admin user for the account, and provide permissions for that user\. For more information, see [Sign Up for AWS](https://docs.aws.amazon.com/Monitron/latest/getting-started-guide/ags-signup.html) and [Create an IAM User](https://docs.aws.amazon.com/Monitron/latest/getting-started-guide/gs-IAMUser.html) in the [Amazon Monitron Getting Started Guide](https://docs.aws.amazon.com/Monitron/latest/getting-started-guide/admin_what-is-monitron.html)\. The required permissions are listed in [Using the Amazon Monitron Console](security_iam_id-based-policy-examples.md#security_iam_id-based-policy-examples-console) in this guide\.

 For an overview of Amazon Monitron, we recommend that you begin by reading the following sections:
+ [How Amazon Monitron works](admin_how-monitron-works.md) – To learn essential Amazon Monitron concepts\. 
+ [Managing projects in Amazon Monitron](projects-chapter.md) – To learn how to set up a project for your team\. This is the foundation for all Amazon Monitron tasks\. 
+ [Measurements and Machine Abnormalities](https://docs.aws.amazon.com/Monitron/latest/user-guide/anom-monitoring-chapter.html) – To learn how to monitor your equipment and understand the data you collect\.

## Related resources<a name="other-help"></a>

The Amazon Monitron documentation set includes three guides: 
+ ** [Amazon Monitron Getting Started Guide](https://docs.aws.amazon.com/Monitron/latest/getting-started-guide/admin_what-is-monitron.html) **– For IT managers, reliability managers, and technicians, this guide gets you started using Amazon Monitron\. 
+ ** [Amazon Monitron User Guide](https://docs.aws.amazon.com/Monitron/latest/user-guide/what-is-monitron.html) **– For reliability managers \(admin users\) and technicians, this guide describes how to use Amazon Monitron to monitor your equipment for machine abnormalities\. It also describes how to use the mobile and web apps, your primary Amazon Monitron tools\. 
+ **Amazon Monitron IT Manager's Guide** – This guide provides the IT manager more in\-depth information about using Amazon Monitron than the *Amazon Monitron Getting Started Guide*\. It also shows you how to use Amazon Monitron to set up projects and assign admin users to manage the project\. 

In addition to reading the guides, we also recommend that you visit the Amazon Monitron Discussion Forum\. This community\-based forum provides the chance for developers to discuss technical questions related to Amazon Monitron\. 

## Pricing for Amazon Monitron<a name="pricing"></a>

For information, see [Amazon Monitron Pricing](https://aws.amazon.com/pricing/)\.