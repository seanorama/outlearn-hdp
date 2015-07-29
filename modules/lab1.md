<!--
{
"name" : "lab1",
"version" : "0.1",
"title" : "Lab 1: HDFS - Loading Data",
"description" : "Loading Sensor Data into HDFS.",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_7",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

##  Loading Sensor Data into HDFS

**Introduction:**

In this section you will download the sensor data and load that into HDFS using Ambari User Views. You will get introduced to the Ambari Files User View to manage files. You can perform tasks like create directories, navigate file systems and upload files to HDFS. In addition you’ll perform a few other file-related tasks as well. Once you get the basics, you will create two directories and then load two files into HDFS using the Ambari Files User View.

**Prerequisite:**

The tutorial is a part of series of hands on tutorial to get you started on HDP using Hortonworks sandbox. Please ensure you complete the prerequisites before proceeding with this tutorial.

*   Step-0 (Hortonworks sandbox set up)
*   Allow yourself around half an hour to complete this tutorial.

**Outline:**

*   HDFS backdrop
*   Step-1.1: Download data – [**Geolocation.zip**](https://app.box.com/HadoopCrashCourseData)
*   Step-1.2: Load Data into HDFS
*   Suggested readings

**HDFS backdrop:**

A single physical machine gets saturated with its storage capacity as the data grows. Thereby comes impending need to partition your data across separate machines. This type of File system that manages storage of data across a network of machines is called Distributed File Systems. [HDFS](http://hortonworks.com/blog/thinking-about-the-hdfs-vs-other-storage-technologies/) is a core component of Apache Hadoop and is designed to store large files with streaming data access patterns, running on clusters of commodity hardware. With Hortonworks Data Platform HDP 2.2, HDFS is now expanded to support [heterogeneous storage](http://hortonworks.com/blog/heterogeneous-storage-policies-hdp-2-2/) media within the HDFS cluster.

**Step 1.1: Download and Extract the Sensor Data Files**

*   You can download the sample sensor data contained in a compressed (.zip) folder here: [**Geolocation.zip**](https://app.box.com/HadoopCrashCourseData)
*   Save the Geolocation.zip file to your computer, then extract the files. You should see a Geolocation folder that contains the following files:
    *   geolocation.csv – This is the collected geolocation data from the trucks. it contains records showing truck location, date, time, type of event, speed, etc.
    *   trucks.csv – This is data was exported from a relational database and it shows info on truck model, driverid, truckid, and aggregated mileage info.

<!-- @task, "text" : "Complete Step 1.1."-->

**Step 1.2: Load the Sensor Data into HDFS**

*   Go to the Ambari Dashboard and open the HDFS User View by click on the User Views icon and selecting the HDFS Files menu item.

![Screen-Shot-2015-07-21-at-10.17.21-AM](http://hortonworks.com/wp-content/uploads/2015/07/Screen-Shot-2015-07-21-at-10.17.21-AM.png)

*   Starting from the top root of the HDFS file system, you will see all the files the logged in user (admin in this case) has access to see:

![Lab2_2](http://hortonworks.com/wp-content/uploads/2015/07/Lab2_2.png)

*   Click the ![Lab2_3](http://hortonworks.com/wp-content/uploads/2015/07/Lab2_3.png)button to create the /temp/admin directory and then create the /temp/admin/data directory.

![Lab2_4](http://hortonworks.com/wp-content/uploads/2015/07/Lab2_4.png)

*   Now traverse to the /temp/admin/data directory and upload the corresponding geolocation.csv and trucks.csv files into it.

You can also perform the following operations on a file by right clicking on the file: **Download**, **Move**, **Permissions**, **Rename** and **Delete**.

![Lab2_5](http://hortonworks.com/wp-content/uploads/2015/07/Lab2_5.png)

<!-- @task, "text" : "Complete Step 1.2."-->
