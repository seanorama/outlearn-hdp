<!--
{
"name" : "hdfs",
"version" : "0.1",
"title" : "Concepts: HDFS",
"description" : "HDFS is a core component of Apache Hadoop and is designed to store large files with streaming data access patterns, running on clusters of commodity hardware.",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_3",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

## Introduction

A single physical machine gets saturated with its storage capacity as the data grows. Thereby comes impending need to partition your data across separate machines. This type of File system that manages storage of data across a network of machines is called Distributed File Systems. [HDFS](http://hortonworks.com/blog/thinking-about-the-hdfs-vs-other-storage-technologies/) is a core component of Apache Hadoop and is designed to store large files with streaming data access patterns, running on clusters of commodity hardware. With Hortonworks Data Platform HDP 2.2, HDFS is now expanded to support [heterogeneous storage](http://hortonworks.com/blog/heterogeneous-storage-policies-hdp-2-2/) media within the HDFS cluster.

**Goals of this module**

*   Understanding HDFS architecture
*   Understanding Hortonworks Sandbox Ambari File User View

**Hadoop Distributed File System**

HDFS is a distributed file system that is designed for storing large data files. HDFS is a Java-based file system that provides scalable and reliable data storage, and it was designed to span large clusters of commodity servers. HDFS has demonstrated production scalability of up to 200 PB of storage and a single cluster of 4500 servers, supporting close to a billion files and blocks. HDFS is a scalable, fault-tolerant, distributed storage system that works closely with a wide variety of concurrent data access applications, coordinated by YARN. HDFS will “just work” under a variety of physical and systemic circumstances. By distributing storage and computation across many servers, the combined storage resource can grow linearly with demand while remaining economical at every amount of storage.

![HDSF_1](http://hortonworks.com/wp-content/uploads/2015/07/HDSF_1.png)

An HDFS cluster is comprised of a NameNode, which manages the cluster metadata, and DataNodes that store the data. Files and directories are represented on the NameNode by inodes. Inodes record attributes like permissions, modification and access times, or namespace and disk space quotas.

The file content is split into large blocks (typically 128 megabytes), and each block of the file is independently replicated at multiple DataNodes. The blocks are stored on the local file system on the DataNodes.

The Namenode actively monitors the number of replicas of a block. When a replica of a block is lost due to a DataNode failure or disk failure, the NameNode creates another replica of the block. The NameNode maintains the namespace tree and the mapping of blocks to DataNodes, holding the entire namespace image in RAM.

The NameNode does not directly send requests to DataNodes. It sends instructions to the DataNodes by replying to heartbeats sent by those DataNodes. The instructions include commands to:

*   replicate blocks to other nodes,
*   remove local block replicas,
*   re-register and send an immediate block report, or
*   shut down the node.

![HDFS_2](http://hortonworks.com/wp-content/uploads/2015/07/HDFS_2.png)

For more details on HDFS: [http://hortonworks.com/hadoop/hdfs/](http://hortonworks.com/hadoop/hdfs/)

With [next generation HDFS data architecture](http://hortonworks.com/blog/hdfs-2-0-next-generation-architecture/) that comes with HDP 2.0, HDFS has evolved to provide [automated failure](http://hortonworks.com/blog/namenode-high-availability-in-hdp-2-0/) with a hot standby, with full stack resiliency. Please spare some time to go through this video for more clarity on HDFS.

<!-- @asset, "contentType": "outlearn/video", "provider": "youtube", "url": "https://www.youtube.com/embed/1_ly9dZnmWc" -->


**Ambari Files User View on Hortonworks Sandbox**

Ambari Files User View

![HDFS_3](http://hortonworks.com/wp-content/uploads/2015/07/HDFS_3.png)

Ambari Files User View provides a user friendly interface to upload, store and move data. Underlying all components in Hadoop is the Hadoop Distributed File System([HDFS](http://hortonworks.com/hadoop/hdfs/)™). This is the foundation of the Hadoop cluster. The HDFS file system manages how the datasets are stored in the Hadoop cluster. It is responsible for distributing the data across the datanodes, managing replication for redundancy and administrative tasks like adding, removing and recovery of data nodes.

#### **Suggested Readings**

> **NOTE** HDFS is one of the 4 components of [Apache Hadoop](http://hadoop.apache.org/) the other 3 are Hadoop Common, [Hadoop YARN](http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html) and [Hadoop MapReduce](http://hortonworks.com/hadoop/mapreduce/). To learn more about HDFS watch the following [HDFS introduction video](https://www.youtube.com/watch?v=1_ly9dZnmWc). To learn more about YARN watch the following [YARN introduction video](https://www.youtube.com/watch?v=ZYXVNxmMchc&list=PL2y_WpKCCNQc-7RJNoYym4_g7EZb3yzJW).
>
> **Hadoop 2.0 Blogs:**  
> [Hadoop 2.7.0 Blog](http://hortonworks.com/blog/apache-hadoop-2-7-0-released/)  
>[Understanding Hadoop 2.0](http://hortonworks.com/blog/understanding-hadoop-2-0/)  
>
> **HDFS Blogs:**  
>[Heterogeneous Storage Policies in HDP 2.2](http://hortonworks.com/blog/heterogeneous-storage-policies-hdp-2-2/)  
>[HDFS Metadata Directories Explained](http://hortonworks.com/blog/hdfs-metadata-directories-explained/)  
>[Heterogeneous Storages in HDFS](http://hortonworks.com/blog/heterogeneous-storages-hdfs/)  
>[HDFS 2.0 Next Generation Architecture](http://hortonworks.com/blog/hdfs-2-0-next-generation-architecture/)  
>[NameNode High Availability in HDP 2.0](http://hortonworks.com/blog/namenode-high-availability-in-hdp-2-0/)  
>[Introducing… Tez: Accelerating processing of data stored in HDFS](http://hortonworks.com/blog/introducing-tez-faster-hadoop-processing/)  
