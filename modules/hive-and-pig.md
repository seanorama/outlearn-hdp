<!--
{
"name" : "hive-and-pig",
"version" : "0.1",
"title" : "Concepts: Hive and Pig",
"description" : "Hive is a SQL like query language that enables analysts familiar with SQL to run queries on large volumes of data. With Pig, data structures are much richer and the transformations you can apply to data are much more powerful.",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_5",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

### Introduction: Apache Hive

Hive is a SQL like query language that enables analysts familiar with SQL to run queries on large volumes of data. Hive has three main functions: data summarization, query and analysis. Hive provides tools that enable easy data extraction, transformation and loading (ETL).

#### [Apache Hive](https://hive.apache.org/)™:

Data analysts use Hive to explore, structure and analyze that data, then turn it into business insight. Hive implements a dialect of SQL (Hive QL) that focuses on analytics and presents a rich set of SQL semantics including OLAP functions, sub-queries, common table expressions and more. Hive allows SQL
 developers or users with SQL tools to easily query, analyze and process data stored in Hadoop.Hive also allows programmers familiar with the MapReduce framework to plug in their custom mappers and reducers to perform more sophisticated analysis that may not be supported by the built-in capabilities of the language.

Hive users have a choice of 3 runtimes when [executing SQL queries](http://hortonworks.com/blog/5-ways-make-hive-queries-run-faster/). Users can choose between Apache Hadoop MapReduce, Apache Tez or
 Apache Spark frameworks as their execution backend

Here are some advantageous characteristics of Hive for enterprise SQL in Hadoop:

| **Feature** | **Description** |
|--------------|----------------|
| **Familiar** | Query data with a SQL-based language |
| **Fast** | Interactive response times, even over huge datasets |
| **Scalable and Extensible** | As data variety and volume grows, more commodity machines can be added, without a corresponding reduction in performance |

**How Hive Works**

The tables in Hive are similar to tables in a relational database, and data units are organized in a taxonomy from larger to more granular units. Databases are comprised of tables, which are made up of partitions. Data can be accessed via a simple query language and Hive supports overwriting or appending data.

Within a particular database, data in the tables is serialized and each table has a corresponding Hadoop Distributed File System (HDFS) directory. Each table can be sub-divided into partitions that determine how data is distributed within sub-directories of the table directory. Data within partitions can be further broken down into buckets.

**Components of Hive**

*   [**HCatalog**](https://cwiki.apache.org/confluence/display/Hive/HCatalog) is a component of Hive. It is a table and storage management layer for Hadoop that enables users with different data processing tools — including Pig and MapReduce — to more easily read and write data on the grid. HCatalog holds a set of files paths and metadata about data in a Hadoop cluster. This allows scripts, MapReduce and Tez, jobs to be decoupled from data location and metadata like the schema. Additionally, since HCatalog also supports tools like Hive and Pig, the location and metadata can be shared between tools. Using the open APIs of HCatalog external tools that want to integrate, such as Teradata Aster, can also use leverage file path location and metadata in HCatalog.

> **NOTE:** At one point HCatalog was its own Apache project. However, in March, 2013, [HCatalog’s project merged](https://hive.apache.org/hcatalog_downloads.html) with Hive. HCatalog is currently released as part of Hive.

*   [**WebHCat**](https://cwiki.apache.org/confluence/display/Hive/WebHCat) provides a service that you can use to run Hadoop MapReduce (or YARN), Pig, Hive jobs or perform Hive metadata operations using an HTTP (REST style) interface.

Here is a short video introduction on Hive:

<!-- @asset, "contentType": "outlearn/video", "provider": "youtube", "url": "https://www.youtube.com/embed/Pn7Sp2-hUXE" -->

#### [Apache Tez](https://tez.apache.org/)**:**

Apache™ Tez is an extensible framework for building high performance batch and interactive data processing applications, coordinated by YARN in Apache Hadoop. Tez improves the MapReduce paradigm by dramatically improving its speed, while maintaining MapReduce’s ability to scale to petabytes of data. Important Hadoop ecosystem projects like Apache Hive and Apache Pig use Apache Tez, as do a growing number of third party data access applications developed for the broader Hadoop ecosystem.

Apache Tez provides a developer API and framework to write native [YARN](http://hortonworks.com/hadoop/yarn/) applications that bridge the spectrum of interactive and batch workloads. It allows those data access applications to work with petabytes of data over thousands nodes. The Apache Tez component library allows developers to create Hadoop applications that integrate natively with Apache Hadoop YARN and perform well within mixed workload clusters.

Since Tez is extensible and embeddable, it provides the fit-to-purpose freedom to express highly optimized data processing applications, giving them an advantage over end-user-facing engines such as [MapReduce](http://hortonworks.com/hadoop/mapreduce/) and [Apache Spark](http://hortonworks.com/hadoop/spark/). Tez also offers a customizable execution architecture that allows users to express complex computations as dataflow graphs, permitting dynamic performance optimizations based on real information about the data and the resources required to process it.

![Hive_1](http://hortonworks.com/wp-content/uploads/2015/07/Hive_1.png)

![Hive_2](http://hortonworks.com/wp-content/uploads/2015/07/Hive_2.png)

![Hive_3](http://hortonworks.com/wp-content/uploads/2015/07/Hive_3.png)

Here is a short video introduction on Tez.

<!-- @asset, "contentType": "outlearn/video", "provider": "youtube", "url": "https://www.youtube.com/embed/cPSfA1bhgVA?start=50" -->

<!-- @section -->

### Stinger and Stinger.next

The Stinger Initiative was started to enable Hive to support an even broader range of use cases at truly Big Data scale: bringing it beyond its Batch roots to support interactive queries – all with a common SQL access layer.

Stinger.next is a continuation of this initiative focused on even further enhancing the [speed](http://hortonworks.com/blog/benchmarking-apache-hive-13-enterprise-hadoop/), scale and breadth of SQL support to enable truly real-time access in Hive while also bringing support for transactional capabilities. And just as the original Stinger initiative did, this will be addressed through a familiar three-phase delivery schedule and developed completely in the open Apache Hive community.

![Hive_4](http://hortonworks.com/wp-content/uploads/2015/07/Hive_4.png)

**Ambari Hive User Views on Hortonworks Sandbox**

To make it easy to interact with Hive we use a tool in the Hortonworks Sandbox called the Ambari Hive User View. Ambari Hive User View provides an interactive interface to Hive. We can create, edit, save and run queries, and have Hive evaluate them for us using a series of MapReduce jobs or Tez jobs.

Let’s now open the Ambari Hive User View and get introduced to the environment, go to the Ambari User VIew icon and select Hive :

![Screen-Shot-2015-07-21-at-10.10.18-AM](http://hortonworks.com/wp-content/uploads/2015/07/Screen-Shot-2015-07-21-at-10.10.18-AM.png)

Ambari Hive User View

![Hive_6](http://hortonworks.com/wp-content/uploads/2015/07/Hive_6.png)

Now let’s take a closer look at the SQL editing capabilities in the User View:

1.  There are four tabs to interact with SQL:
    1.  **Query**: This is the interface shown above and the primary interface to write, edit and execute new SQL statements
    2.  **Saved Queries**: You can save your favorite queries and quickly have access to them to rerun or edit.
    3.  **History**: This allows you to look at past queries or currently running queries to view, edit and rerun. It also allows you to see all SQL queries you have authority to view. For example, if you are an operator and an analyst needs help with a query, then the Hadoop operator can use the History feature to see the query that was sent from the reporting tool.
    4.  **UDF**s: Allows you to define UDF interfaces and associated classes so you can access them from the SQL editor.
2.  **Database Explorer:** The Database Explorer helps you navigate your database objects. You can either search for a database object in the Search tables dialog box, or you can navigate through Database -> Table -> Columns in the navigation pane.
3.  The principle pane to write and edit SQL statements. This editor includes content assist via **CTRL + Space** to help you build queries. Content assist helps you with SQL syntax and table objects.
4.  Once you have created your SQL statement you have 3 options:
    1.  **Execute**: This runs the SQL statement.
    2.  **Explain**: This provides you a visual plan, from the Hive optimizer, of how the SQL statement will be executed.
    3.  **Save as**: Allows you to persist your queries into your list of saved queries.
5.  When the query is executed you can see the Logs or the actual query results.
    1.  **Logs:** When the query is executed you can see the logs associated with the query execution. If your query fails this is a good place to get additional information for troubleshooting.
    2.  **Results**: You can view results in sets of 50 by default.
6.  There are four sliding views on the right hand side with the following capabilities, which are in context of the tab you are in:
    1.  **Query**: This is the default operation,which allows you to write and edit SQL.
    2.  **Settings**: This allows you to set properties globally or associated with an individual query.
    3.  **Visual Explain**: This will generate an explain for the query. This will also show the progress of the query.
    4.  **TEZ**: If you use TEZ as the query execution engine then you can view the DAG associated with the query. This integrates the TEZ User View so you can check for correctness and helps with performance tuning by visualizing the TEZ jobs associated with a SQL query.
    5.  **Notifications**: This is how to get feedback on query execution.

The Apache Hive project provides a data warehouse view of the data in HDFS. Using a SQL dialect, [HiveQL](https://cwiki.apache.org/confluence/display/Hive/LanguageManual) (HQL), Hive lets you create summarizations of your data and perform ad-hoc queries and analysis of large datasets in the Hadoop cluster. The overall approach with Hive is to project a table structure on the dataset and then manipulate it with SQL. The notion of projecting a table structure on a file is often referred to as [Schema-On-Read](http://hortonworks.com/blog/hivehcatalog-data-geeks-big-data-glue/). Since you are using data in HDFS, your operations can be scaled across all the datanodes and you can manipulate huge datasets.

<!-- @section -->

### Introduction: Apache Pig

MapReduce allows allows you to specify map and reduce functions, but working out how to fit your data processing into this pattern may sometimes require you to write multiple MapReduce stages. With Pig, data structures are much richer and the transformations you can apply to data are much more powerful.

**Goals of this Module**

*   Understanding Apache Pig
*   Understanding Apache Pig on Tez
*   Understanding Ambari Pig User Views on Hortonworks Sandbox

[**Apache Pig**](https://pig.apache.org/)**™**

Apache Pig allows Apache Hadoop users to write complex MapReduce transformations using a simple scripting language called Pig Latin. Pig translates the Pig Latin script into MapReduce so that it can be executed within YARN for access to a single dataset stored in the Hadoop Distributed File System (HDFS).

Pig was designed for performing a long series of data operations, making it ideal for three categories of Big Data jobs:

*   **Extract-transform-load (ETL)** data pipelines,
*   **Research** on raw data, and
*   **Iterative data processing.**

Whatever the use case, Pig will be:

| **Characteristic** | **Benefit** |
|--------------------|--------------|
| **Extensible** | Pig users can create custom functions to meet their particular processing requirements |
| **Easily programmed** | Complex tasks involving interrelated data transformations can be simplified and encoded as data flow sequences. Pig programs accomplish huge tasks, but they are easy to write and maintain. |
| **Self-optimizing** | Because the system automatically optimizes execution of Pig jobs, the user can focus on semantics. |

Please refer the following video on Pig for more clarity:

<!-- @asset, "contentType": "outlearn/video", "provider": "youtube", "url": "https://www.youtube.com/embed/PQb9I-8986s" -->


**How Pig Works**

Pig runs on Apache Hadoop YARN and makes use of MapReduce and the Hadoop Distributed File System (HDFS). The language for the platform is called Pig Latin, which abstracts from the Java MapReduce idiom into a form similar to SQL. While SQL is designed to query the data, Pig Latin allows you to write a data flow that describes how your data will be transformed (such as aggregate, join and sort).

Since Pig Latin scripts can be graphs (instead of requiring a single output) it is possible to build complex data flows involving multiple inputs, transforms, and outputs. Users can extend Pig Latin by writing their own functions, using Java, Python, Ruby, or other scripting languages. Pig Latin is sometimes extended using UDFs (User Defined Functions), which the user can write in any of those languages and then call directly from the Pig Latin.

The user can run Pig in two modes, using either the “pig” command or the “java” command:

*   **MapReduce Mode.** This is the default mode, which requires access to a Hadoop cluster. The cluster may be a pseudo- or fully distributed one.
*   **Local Mode.** With access to a single machine, all files are installed and run using a local host and file system

**Ambari Pig User Views on Hortonworks Sandbox****:**

To get to the Ambari Pig User View on Sandbox, click on the User Views icon at top right and select **Pig**:

![Screen-Shot-2015-07-21-at-10.12.41-AM](http://hortonworks.com/wp-content/uploads/2015/07/Screen-Shot-2015-07-21-at-10.12.41-AM.png)

This will bring up the Ambari Pig User View interface. Your Pig View does not have any scripts to display, so it will look like the following:

![Pig_2](http://hortonworks.com/wp-content/uploads/2015/07/Pig_2.png)

On the left is a list of your scripts, and on the right is a composition box for writing scripts. A special feature of the interface is the Pig helper at the bottom. The Pig helper will provide us with templates for the statements, functions, I/O statements, HCatLoader() and Python user defined functions. At the very bottom are status areas that will show the results of our script and log files.

The following screenshot shows and describes the various components and features of the Pig User View:

![Pig_3](http://hortonworks.com/wp-content/uploads/2015/07/Pig_3.png)

**Suggested Readings**

> **NOTE** [Apache Ambari](https://ambari.apache.org/) is an open source and open community based web based tool for Hadoop operations which has been extended via [Ambari User Views](https://cwiki.apache.org/confluence/display/AMBARI/Views) to provide a growing list of developer tools as User Views. Follow this link to learn more about the [Ambari User VIews included in HDP](http://hortonworks.com/hadoop/ambari/).

**Hive Blogs**:  
>[Cost-Based Optimizer Makes Apache Hive 0.14 More Than 2.5X Faster](http://hortonworks.com/blog/cost-based-optimizer-makes-apache-hive-0-14-more-than-2-5x-faster/)  
>[Discover HDP 2.2: Even Faster SQL Queries with Apache Hive and Stinger.next](http://www.slideshare.net/hortonworks/discoverhdp22faster-sql-queries-with-hive)  
>[Announcing Apache Hive 1.2](http://hortonworks.com/blog/announcing-apache-hive-1-2/)  
>[HIVE 0.14 Cost Based Optimizer (CBO) Technical Overview](http://hortonworks.com/blog/hive-0-14-cost-based-optimizer-cbo-technical-overview/)  
>[5 Ways to Make Your Hive Queries Run Faster](http://hortonworks.com/blog/5-ways-make-hive-queries-run-faster/)  
>[Secure JDBC and ODBC Clients’ Access to HiveServer2](http://hortonworks.com/blog/secure-jdbc-odbc-clients-access-hiveserver2/)  
>[Speed, Scale and SQL: The Stinger Initiative, Apache Hive 12 & Apache Tez](http://hortonworks.com/blog/speed-scale-sql-stinger-initiative-apache-hive-12-apache-tez/)  
>[Hive/HCatalog – Data Geeks & Big Data Glue](http://hortonworks.com/blog/hivehcatalog-data-geeks-big-data-glue/)

**Tez Blogs**:  
>[Apache Tez: A New Chapter in Hadoop Data Processing](http://hortonworks.com/blog/apache-tez-a-new-chapter-in-hadoop-data-processing/)  
>[Data Processing API in Apache Tez](http://hortonworks.com/blog/expressing-data-processing-in-apache-tez)

**ORC Blogs:**  
>[Apache ORC Launches as a Top-Level Project](http://hortonworks.com/blog/apache-orc-launches-as-a-top-level-project/)  
>[ORCFile in HDP 2: Better Compression, Better Performance](http://hortonworks.com/blog/orcfile-in-hdp-2-better-compression-better-performance/)  
