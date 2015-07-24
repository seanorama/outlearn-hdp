<!--
{
"name" : "prerequisites-and-overview",
"version" : "0.1",
"title" : "Prerequisites and Overview",
"description": "In this section, we will use Microsoft Excel Professional Plus 2013 to access the refined data.",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_11",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

## Prerequisites

* Hortonworks Sandbox 2.3 (installed and running).
    * [Download Hortonworks Sandbox](http://hortonworks.com/products/hortonworks-sandbox/#install)
* Data Set Used: [Geolocation.zip](https://app.box.com/HadoopCrashCourseData)
* Optional: Hortonworks ODBC driver installed and configured – see the tutorial on installing the ODBC driver for Windows or OS X. Refer to
    * [Installing and Configuring the Hortonworks ODBC driver on Windows 7](http://hortonworks.com/hadoop-tutorial/how-to-install-and-configure-the-hortonworks-odbc-driver-on-windows-7/)
    * [Installing and Configuring the Hortonworks ODBC driver on Mac OS X](http://hortonworks.com/hadoop-tutorial/how-to-install-and-configure-the-hortonworks-odbc-driver-on-mac-os-x/)
    * Microsoft Excel 2013 Professional Plus is required for the Windows 7 or later installation to be able to construct the maps.

> **Note:** In this tutorial, the Hortonworks Sandbox is installed on an Oracle VirtualBox virtual machine (VM) – your screens may be different.
>
>Install the ODBC driver that matches the version of Excel you are using (32-bit or 64-bit).
>
>We will use the Power View feature in Microsoft Excel 2013 to visualize the sensor data. Power View is currently only available in Microsoft Office Professional Plus and Microsoft Office 365 Professional Plus.
>
>Note, other versions of Excel will work, but the visualizations will be limited to charts or graphs. You can also use other visualization tool.

<!-- @section -->

## Tutorial Overview

In this tutorial we will be providing the collected geolocation and truck data.   We will import this data into HDFS and build derived tables in Hive. Then we will process the data using Pig, Hive and Spark. The processed data is then imported into Microsoft Excel where it can be visualized.

To refine and analyze Geolocation data, we will:

* Review some Hadoop Fundamentals
* Download and extract the Geolocation data files.
* Load the captured data into the Hortonworks Sandbox.
* Run Hive,Pig and Spark scripts that compute truck mileage and driver risk factor.
* Access the refined sensor data with Microsoft Excel.
* Visualize the sensor data using Excel Power View.

### Goals of the Tutorial

The goal of this tutorial is that you get familiar with the basics of following:

* Hadoop and HDP
* Ambari File User Views and HDFS
* Ambari Hive User Views and Apache Hive
* Ambari Pig User Views and Apache Pig
* Apache Spark
* Data Visualization with Excel (Optional)

### Outline

1. Introduction
2. Prerequisites
3. Tutorial Overview
4. Goals of the Tutorial (outcomes)
5. Hadoop Data Platform Concepts (New to Hadoop or HDP- Refer following)
6. Get Started with HDP Labs
7. Next Step/Try These
8. References and Resources
