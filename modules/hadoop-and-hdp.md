<!--
{
"name" : "hadoop-and-hdp",
"version" : "0.1",
"title" : "Concepts: Hadoop & HDP",
"description" : "In this module you will learn about Apache Hadoop and what makes it scale to large data sets.",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_2",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

### Introduction

In this module you will learn about Apache Hadoop and what makes it scale to large data sets. We will also talk about various components of Hadoop ecosystem that make Apache Hadoop enterprise ready in form of Hortonworks Data Platform(HDP) distribution. The module discusses Apache Hadoop, its capabilities as a data platform and how the core of Hadoop and its surrounding ecosystem solution vendors provides the enterprise requirements to integrate alongside the Data Warehouse and other enterprise data systems as part of a modern data architecture, and as a step on the journey toward delivering an enterprise ‘Data Lake’.

#### Apache Hadoop:

Apache Hadoop® is an open source framework for distributed storage and processing of large sets of data on commodity hardware. Hadoop enables businesses to quickly gain insight from massive amounts of structured and unstructured data. Numerous Apache Software Foundation projects make up the services required by an enterprise to deploy, integrate and work with Hadoop.

<!-- @multipleChoice -->

Apache Hadoop

- [ ] Uses customized hardware
- [ ] Is focused on the needs of small businesses
- [X] Can handle unstructured data

Read again the previous paragraph to refresh your memory.

<!-- @end -->


> **NOTE**: Hortonworks Blog : [Understanding Hadoop 2.0](http://hortonworks.com/blog/understanding-hadoop-2-0/)

The base Apache Hadoop framework is composed of the following modules:

*   **Hadoop Common** – contains libraries and utilities needed by other Hadoop modules.
*   **Hadoop Distributed File System (HDFS)** – a distributed file-system that stores data on commodity machines, providing very high aggregate bandwidth across the cluster.
*   **Hadoop YARN** – a resource-management platform responsible for managing computing resources in clusters and using them for scheduling of users’ applications.
*   **Hadoop MapReduce** – a programming model for large scale data processing.

Each project has been developed to deliver an explicit function and each has its own community of developers and individual release cycles. There are five pillars to Hadoop that make it enterprise ready:

1.  **Data Management**– Store and process vast quantities of data in a storage layer that scales linearly. Hadoop Distributed File System (HDFS) is the core technology for the efficient scale out storage layer, and is designed to run across low-cost commodity hardware. Apache Hadoop YARN is the pre-requisite for Enterprise Hadoop as it provides the resource management and pluggable architecture for enabling a wide variety of data access methods to operate on data stored in Hadoop with predictable performance and service levels.
    1.  **[Apache Hadoop YARN](http://hortonworks.com/hadoop/yarn)–** Part of the core Hadoop project, YARN is a next-generation framework for Hadoop data processing extending MapReduce capabilities by supporting non-MapReduce workloads associated with other programming models.
    2.  **[HDFS](http://hortonworks.com/hadoop/hdfs/)–** Hadoop Distributed File System (HDFS) is a Java-based file system that provides scalable and reliable data storage that is designed to span large clusters of commodity servers.
2.  **Data Access**– Interact with your data in a wide variety of ways – from batch to real-time. Apache Hive is the most widely adopted data access technology, though there are many specialized engines. For instance, Apache Pig provides scripting capabilities, Apache Storm offers real-time processing, Apache HBase offers columnar NoSQL storage and Apache Accumulo offers cell-level access control. All of these engines can work across one set of data and resources thanks to YARN and intermediate engines such as Apache Tez for interactive access and Apache Slider for long-running applications. YARN also provides flexibility for new and emerging data access methods, such as Apache Solr for search and programming frameworks such as Cascading.
    1.  **[Apache Hive](http://hortonworks.com/hadoop/hive)–** Built on the MapReduce framework, Hive is a data warehouse that enables easy data summarization and ad-hoc queries via an SQL-like interface for large datasets stored in HDFS.
    2.  **[Apache Pig](http://hortonworks.com/hadoop/pig)–** A platform for processing and analyzing large data sets. Pig consists of a high-level language (Pig Latin) for expressing data analysis programs paired with the MapReduce framework for processing these programs.
    3.  **[MapReduce](http://hortonworks.com/hadoop/mapreduce/)–** MapReduce is a framework for writing applications that process large amounts of structured and unstructured data in parallel across a cluster of thousands of machines, in a reliable and fault-tolerant manner.
    4.  **[Apache Spark](http://hortonworks.com/hadoop/spark)–** Spark is ideal for in-memory data processing. It allows data scientists to implement fast, iterative algorithms for advanced analytics such as clustering and classification of datasets.
    5.  **[Apache Storm](http://hortonworks.com/hadoop/storm)–** Storm is a distributed real-time computation system for processing fast, large streams of data adding reliable real-time data processing capabilities to Apache Hadoop® 2.x
    6.  **[Apache HBase](http://hortonworks.com/hadoop/hbase)–** A column-oriented NoSQL data storage system that provides random real-time read/write access to big data for user applications.
    7.  **[Apache Tez](http://hortonworks.com/hadoop/tez)–** Tez generalizes the MapReduce paradigm to a more powerful framework for executing a complex DAG (directed acyclic graph) of tasks for near real-time big data processing.
    8.  **[Apache Kafka](http://hortonworks.com/hadoop/kafka)–** Kafka is a fast and scalable publish-subscribe messaging system that is often used in place of traditional message brokers because of its higher throughput, replication, and fault tolerance.
    9.  **[Apache HCatalog](http://hortonworks.com/hadoop/hcatalog)–** A table and metadata management service that provides a centralized way for data processing systems to understand the structure and location of the data stored within Apache Hadoop.
    10.  **[Apache Slider](http://hortonworks.com/hadoop/slider)–** A framework for deployment of long-running data access applications in Hadoop. Slider leverages YARN’s resource management capabilities to deploy those applications, to manage their lifecycles and scale them up or down.
    11.  **[Apache Solr](http://hortonworks.com/hadoop/solr)–** Solr is the open source platform for searches of data stored in Hadoop. Solr enables powerful full-text search and near real-time indexing on many of the world’s largest Internet sites.
    12.  **[Apache Mahout](http://hortonworks.com/hadoop/mahout)–** Mahout provides scalable machine learning algorithms for Hadoop which aids with data science for clustering, classification and batch based collaborative filtering.
    13.  **[Apache Accumulo](http://hortonworks.com/hadoop/accumulo)–** Accumulo is a high performance data storage and retrieval system with cell-level access control. It is a scalable implementation of Google’s Big Table design that works on top of Apache Hadoop and Apache ZooKeeper.
3.  **Data Governance and Integration**– Quickly and easily load data, and manage according to policy.Apache Falcon provides policy-based workflows for data governance, while Apache Flume and Sqoop enable easy data ingestion, as do the NFS and WebHDFS interfaces to HDFS.
    1.  **[Apache Falcon](http://hortonworks.com/hadoop/falcon)–** Falcon is a data management framework for simplifying data lifecycle management and processing pipelines on Apache Hadoop®. It enables users to orchestrate data motion, pipeline processing,disaster recovery, and data retention workflows.
    2.  **[Apache Flume](http://hortonworks.com/hadoop/flume)–** Flume allows you to efficiently aggregate and move large amounts of log data from many different sources to Hadoop.
    3.  **[Apache Sqoop](http://hortonworks.com/hadoop/sqoop)–** Sqoop is a tool that speeds and eases movement of data in and out of Hadoop. It provides a reliable parallel load for various, popular enterprise data sources.

1.  **Security**– Address requirements of Authentication, Authorization, Accounting and Data Protection. Security is provided at every layer of the Hadoop stack from HDFS and YARN to Hive and the other Data Access components on up through the entire perimeter of the cluster via Apache Knox.
    1.  **[Apache Knox](http://hortonworks.com/hadoop/knox)–** The Knox Gateway (“Knox”) provides a single point of authentication and access for Apache Hadoop services in a cluster. The goal of the project is to simplify Hadoop security for users who access the cluster data and execute jobs, and for operators who control access to the cluster.
    2.  **[Apache Ranger](http://hortonworks.com/hadoop/ranger)–** Apache Ranger delivers a comprehensive approach to security for a Hadoop cluster. It provides central security policy administration across the core enterprise security requirements of authorization, accounting and data protection.

1.  **Operations**– Provision, manage, monitor and operate Hadoop clusters at scale.
    1.  **[Apache Ambari](http://hortonworks.com/hadoop/ambari)–** An open source installation lifecycle management, administration and monitoring system for Apache Hadoop clusters.
    2.  **[Apache Oozie](http://hortonworks.com/hadoop/oozie)–** Oozie Java Web application used to schedule Apache Hadoop jobs. Oozie combines multiple jobs sequentially into one logical unit of work.
    3.  **[Apache ZooKeeper](http://hortonworks.com/hadoop/zookeeper)–** A highly available system for coordinating distributed processes. Distributed applications use ZooKeeper to store and mediate updates to important configuration information.

Apache Hadoop can be useful across a range of use cases spanning virtually every vertical industry. It is becoming popular anywhere that you need to store, process, and analyze large volumes of data. Examples include digital marketing automation, fraud detection and prevention, social network and relationship analysis, predictive modeling for new drugs, retail in-store behavior analysis, and mobile device location-based marketing. To learn more about Apache Hadoop, watch the following introduction:

<iframe width="500" height="375" src="https://www.youtube.com/embed/6UtD53BzDNk?feature=oembed" frameborder="0" allowfullscreen=""></iframe>

<!-- @section -->

### Hortonworks Data Platform (HDP)

Hortonworks Data Platform is a packaged software hadoop distribution that aim to ease deployment and management of Hadoop clusters compared with simply downloading the various Apache code bases and trying to run them together a system. Architected, developed, and built completely in the open, Hortonworks Data Platform (HDP) provides an enterprise ready data platform that enables organizations to adopt a Modern Data Architecture.

With YARN as its architectural center it provides a data platform for multi-workload data processing across an array of processing methods – from batch through interactive to real-time, supported by key capabilities required of an enterprise data platform — spanning Governance, Security and Operations.

The Hortonworks **Sandbox** is a single node implementation of the Hortonworks Data Platform (HDP). It is packaged as a virtual machine to make evaluation and experimentation with HDP fast and easy. The tutorials and features in the Sandbox are oriented towards exploring how HDP can help you solve your business big data problems. The Sandbox tutorials will walk you through bringing some sample data into HDP and manipulating it using the tools built into HDP. The idea is to show you how you can get started and show you how to accomplish tasks in HDP. HDP is free to download and use in your enterprise and you can download it here: [Hortonworks Data Platform](http://hortonworks.com/download/)

<!-- @task, "text" : "Download the Hortonworks Data Platform."-->


**Suggested Readings****:**

> **NOTE:** HDFS is one of the 4 components of [Apache Hadoop](http://hadoop.apache.org/) the other 3 are Hadoop Common, [Hadoop YARN](http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html) and [Hadoop MapReduce](http://hortonworks.com/hadoop/mapreduce/). To learn more about HDFS watch the following [HDFS introduction video](https://www.youtube.com/watch?v=1_ly9dZnmWc). To learn more about YARN watch the following [YARN introduction video](https://www.youtube.com/watch?v=ZYXVNxmMchc&list=PL2y_WpKCCNQc-7RJNoYym4_g7EZb3yzJW).

 > Hadoop 2.0 Blogs:

 > [Hadoop 2.7.0 Blog](http://hortonworks.com/blog/apache-hadoop-2-7-0-released/)  
 > [Understanding Hadoop 2.0](http://hortonworks.com/blog/understanding-hadoop-2-0/)
