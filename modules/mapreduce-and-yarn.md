<!--
{
"name" : "mapreduce-and-yarn",
"version" : "0.1",
"title" : "Concepts: MapReduce & YARN",
"description" : "Get familiar with MapReduce and how YARN addresses some of its limitations",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_4",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

## Introduction

Cluster computing faces several challenges such as how to store data persistently and keep it available if nodes fail or how to deal with node failures during a long running computation. Then there is network bottleneck which delays the time of processing data. MapReduce offers a solution by bring computation close to data thereby minimizing data movement. It is a simple programming model designed for process large volumes of data in parallel by dividing the job into a set of independent tasks.

The biggest limitation with MapReduce programming is that map and reduce jobs are not stateless. This means that Reduce jobs have to wait for map jobs to be completed first. This limits maximum parallelism and therefore [YARN](http://hortonworks.com/blog/philosophy-behind-yarn-resource-management/) was born as a generic resource management and distributed application framework.

**Goals of the Module**

*   Understanding Map and Reduce jobs.
*   Understanding YARN

### [APACHE MapReduce](http://hortonworks.com/hadoop/mapreduce/)

MapReduce is the key algorithm that the Hadoop data processing engine uses to distribute work around a cluster. A MapReduce job splits a large data set into independent chunks and organizes them into key, value pairs for parallel processing. This parallel processing improves the speed and reliability of the cluster, returning solutions more quickly and with greater reliability.

The **Map** function divides the input into ranges by the InputFormat and creates a map task for each range in the input. The JobTracker distributes those tasks to the worker nodes. The output of each map task is partitioned into a group of key-value pairs for each reduce.

*   map(key1,value) -> list<key2,value2>

The **Reduce** function then collects the various results and combines them to answer the larger problem that the master node needs to solve. Each reduce pulls the relevant partition from the machines where the maps executed, then writes its output back into HDFS. Thus, the reduce is able to collect the data from all of the maps for the keys and combine them to solve the problem.

*   reduce(key2, list<value2>) -> list<value3>

The current Apache Hadoop MapReduce System is composed of the JobTracker, which is the master, and the per-node slaves called TaskTrackers. The JobTracker is responsible for _resource management_ (managing the worker nodes i.e. TaskTrackers), _tracking resource consumption/availability_ and also _job life-cycle management_ (scheduling individual tasks of the job, tracking progress, providing fault-tolerance for tasks etc).

The TaskTracker has simple responsibilities – launch/teardown tasks on orders from the JobTracker and provide task-status information to the JobTracker periodically.

![MapR_1](http://hortonworks.com/wp-content/uploads/2015/07/MapR_1.png)

The Apache Hadoop projects provide a series of tools designed to solve big data problems. The Hadoop cluster implements a parallel computing cluster using inexpensive commodity hardware. The cluster is partitioned across many servers to provide a near linear scalability. The philosophy of the cluster design is to bring the computing to the data. So each datanode will hold part of the overall data and be able to process the data that it holds. The overall framework for the processing software is called MapReduce. Here’s a short video introduction to MapReduce:

<!-- @asset, "contentType": "outlearn/video", "provider": "youtube", "url": "https://www.youtube.com/embed/ht3dNvdNDzI" -->


![MapR_2](http://hortonworks.com/wp-content/uploads/2015/07/MapR_2.png)

### [Apache YARN](http://hortonworks.com/blog/apache-hadoop-yarn-background-and-an-overview/) (Yet Another Resource Negotiator):

Hadoop HDFS is the data storage layer for Hadoop and MapReduce was the data-processing layer in Hadoop 1x. However, the MapReduce algorithm, by itself, isn’t sufficient for the very wide variety of use-cases we see Hadoop being employed to solve. Hadoop 2.0 presents YARN, as a generic resource-management and distributed application framework, whereby, one can implement multiple data processing applications customized for the task at hand. The fundamental idea of YARN is to split up the two major responsibilities of the JobTracker i.e. resource management and job scheduling/monitoring, into separate daemons: a global **ResourceManager** and per-application **ApplicationMaster** (AM).

The ResourceManager and per-node slave, the NodeManager (NM), form the new, and generic, **system** for managing applications in a distributed manner.

The ResourceManager is the ultimate authority that arbitrates resources among all the applications in the system. The per-application ApplicationMaster is, in effect, a _framework specific_ entity and is tasked with negotiating resources from the ResourceManager and working with the NodeManager(s) to execute and monitor the component tasks.

[ResourceManager](http://hortonworks.com/blog/apache-hadoop-yarn-resourcemanager/) has a pluggable **Scheduler**, which is responsible for allocating resources to the various running applications subject to familiar constraints of capacities, queues etc. The Scheduler is a _pure scheduler_ in the sense that it performs no monitoring or tracking of status for the application, offering no guarantees on restarting failed tasks either due to application failure or hardware failures. The Scheduler performs its scheduling function based on the _resource requirements_ of the applications; it does so based on the abstract notion of a **_Resource Container_** which incorporates resource elements such as memory, cpu, disk, network etc.

[NodeManager](http://hortonworks.com/blog/apache-hadoop-yarn-nodemanager/) is the per-machine slave, which is responsible for launching the applications’ containers, monitoring their resource usage (cpu, memory, disk, network) and reporting the same to the ResourceManager.

The per-application ApplicationMaster has the responsibility of negotiating appropriate resource containers from the Scheduler, tracking their status and monitoring for progress. From the system perspective, the ApplicationMaster itself runs as a normal _container_.

Here is an architectural view of YARN:

![MapR_3](http://hortonworks.com/wp-content/uploads/2015/07/MapR_3.png)

One of the crucial implementation details for MapReduce within the new YARN **system** that I’d like to point out is that we have reused the existing MapReduce **framework** without any major surgery. This was very important to ensure **compatibility** for existing MapReduce applications and users. Here is a short video introduction for YARN

<!-- @asset, "contentType": "outlearn/video", "provider": "youtube", "url": "https://www.youtube.com/embed/wlouNFscZS0?start=147" -->



#### Suggested Readings:

> **NOTE:** HDFS is one of the 4 components of [Apache Hadoop](http://hadoop.apache.org/) the other 3 are Hadoop Common, [Hadoop YARN](http://hadoop.apache.org/docs/current/hadoop-yarn/hadoop-yarn-site/YARN.html) and [Hadoop MapReduce](http://hortonworks.com/hadoop/mapreduce/). To learn more about HDFS watch the following [HDFS introduction video](https://www.youtube.com/watch?v=1_ly9dZnmWc). To learn more about YARN watch the following [YARN introduction video](https://www.youtube.com/watch?v=ZYXVNxmMchc&list=PL2y_WpKCCNQc-7RJNoYym4_g7EZb3yzJW).

**Hadoop 2.0 Blogs:**  
>[Hadoop 2.7.0 Blog](http://hortonworks.com/blog/apache-hadoop-2-7-0-released/)  
>[Understanding Hadoop 2.0](http://hortonworks.com/blog/understanding-hadoop-2-0/)  
>
>**YARN Blogs:**  
 >[YARN series-1](http://hortonworks.com/blog/resource-localization-in-yarn-deep-dive/)  
>[YARN series-2](http://hortonworks.com/blog/apache-hadoop-yarn-hdp-2-2-substantial-step-forward-enterprise-hadoop/)  
>
> **Slider Blogs:**  
>[Announcing Apache Slider 0.60.0](http://hortonworks.com/blog/announcing-apache-slider-0-60-0/)  
>[Onboarding Long Running Services to Apache Hadoop YARN Using Apache Slider](http://hortonworks.com/blog/onboarding-long-running-services-apache-hadoop-yarn-using-apache-slider/)  
>[Build YARN Apps on Hadoop with Apache Slider: Technical Preview Now Available](http://hortonworks.com/blog/apache-slider-technical-preview-now-available/)
>
>**Capacity Scheduler Blogs:**  
>[Understanding Apache Hadoop’s Capacity Scheduler](http://hortonworks.com/blog/understanding-apache-hadoops-capacity-scheduler/)  
>[Configuring YARN Capacity Scheduler with Ambari](http://hortonworks.com/hadoop-tutorial/configuring-yarn-capacity-scheduler-ambari/)  
>[Multi-Tenancy in HDP 2.0: Capacity Scheduler and YARN](http://hortonworks.com/blog/multi-tenancy-in-hdp-2-0-capacity-scheduler-and-yarn/)  
>[Better SLAs via Resource-preemption in YARN’s Capacity Scheduler](http://hortonworks.com/blog/better-slas-via-resource-preemption-in-yarns-capacityscheduler/)  
