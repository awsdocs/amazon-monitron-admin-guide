# How Amazon Monitron works<a name="admin_how-monitron-works"></a>

Amazon Monitron is an end\-to\-end system that detects abnormal machine behavior so you can enable predictive maintenance and reduce lost productivity from unplanned machine downtime\. It includes sensors to capture data, gateways to transfer that data to the AWS Cloud, and machine learning\-based software that analyzes it for abnormal machine patterns\. It also includes companion apps for setup and notification\.

## The Amazon Monitron workflow<a name="deployed-workflow"></a>

The following diagram shows the basic workflow of Amazon Monitron\. 

![\[Image NOT FOUND\]](http://docs.aws.amazon.com/Monitron/latest/admin-guide/images/processimage.png)

1. An Amazon Monitron sensor captures temperature and vibration data from the equipment \(the asset\) and transmits it to the gateway\. 

1. An Amazon Monitron gateway transmits the data to the AWS Cloud using the factory's internet connection\. 

1. The Amazon Monitron ML model in the AWS Cloud analyzes the sensor data\. 

   1. Amazon Monitron looks for abnormalities in the data that could indicate developing faults\. 

   1. If Amazon Monitron finds potential equipment abnormalities, it notifies reliability managers and technicians through the Amazon Monitron mobile app so they can take appropriate action\. 

   1. Technicians investigate based on the alerts, and resolve the developing fault\. They then enter feedback on the accuracy of the alerts, and report the mode, cause, and action taken in the mobile app\. Amazon Monitron learns from this feedback and continually improves over time\. 

1. The mobile app displays current and past temperature and vibration data in charts that are easy to scan, and can be used while investigating an issue\. 

## Next steps<a name="admin-what-next"></a>

If you are new to Amazon Monitron, we recommend that you read the following topics in order:
+ [Getting Started with Amazon Monitron](https://docs.aws.amazon.com/Monitron/latest/getting-started-guide/gsg-getting-started.html) in the *Amazon Monitron Getting Started Guide*\.
+ [Quotas in Amazon Monitron](quotas.md)
+ [Managing Measurements and Anomalies](https://docs.aws.amazon.com/Monitron/latest/user-guide/what-is-monitron.html) in the *Amazon Monitron User Guide* 