<!--
{
"name" : "lab4",
"version" : "0.1",
"title" : "Lab 4: Spark - Risk Factor",
"description" : "Use Apache Spark to compute Driver Risk Factor",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_10",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

## Use Apache Spark to compute Driver Risk Factor

**Introduction:**

In this tutorial you will be introduced to Apache Spark. In the earlier section of lab you learned how to load data into HDFS and then manipulate it using Hive. We are using the Truck sensor data to better understand risk associated with every driver. This section will teach you to compute risk using Apache spark.

**Prerequisite:**

The tutorial is a part of series of hands on tutorial to get you started on HDP using Hortonworks sandbox. Please ensure you complete the prerequisites before proceeding with this tutorial.

*   Step-0 (Hortonworks sandbox set up)
*   Lab1: Loading sensor data into HDFS
*   Lab2: Data Manipulation with Apache Hive
*   Allow yourself around one hour to complete this tutorial.

#### **Outline:**

*   Apache Spark backdrop
*   Apache Spark basics
*   Step-4.1: Configure Apache Spark services using Ambari
*   Step-4.2: Create a Hive Context
*   Step-4.3: Create RDD from Hive Context
*   Step-4.4: RDD transformations and actions
*   Step-4.5: Load and save data into Hive as ORC
*   Suggested readings

**Apache Spark backdrop:**

MapReduce has been useful, but the amount of time it takes for the jobs to run can at times be exhaustive. Also, MapReduce jobs only work for a specific set of use cases. There is a need for computing framework that works for a wider set of use cases.

Therefore Apache Spark was designed as a computing platform to be fast, general-purpose, and easy to use. It extends the MapReduce model and takes it to a whole other level. The speed comes from the in-memory computations. Applications running in memory allows for a much faster processing and response.

**Apache Spark:**

[Apache Spark](http://hortonworks.com/hadoop/spark/) is a fast, in-memory data processing engine with elegant and expressive development APIs in [Scala](https://spark.apache.org/docs/1.2.0/api/scala/index.html#org.apache.spark.package),[Java](https://spark.apache.org/docs/1.2.0/api/java/index.html), and [Python](https://spark.apache.org/docs/1.2.0/api/java/index.html) that allow data workers to efficiently execute machine learning algorithms that require fast iterative access to datasets. Spark on [Apache Hadoop YARN](http://hortonworks.com/hadoop/YARN) enables deep integration with Hadoop and other YARN enabled workloads in the enterprise.

You can run batch application such as MapReduce types jobs or iterative algorithms that builds upon each other. You can also run interactive queries and process streaming data with your application. Spark also provides number of libraries which you can easily use to expand beyond the basic Spark capabilities such as Machine Learning algorithms, SQL, streaming, and graph processing. Spark runs on Hadoop clusters such as Hadoop YARN or Apache Mesos, or even as a standalone with its own scheduler.

![Lab4_1](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_1.png)
Lets get started…!!

<!-- @section -->

## Step 4.1: Configuring Spark services using Ambari

1.  Log on to Ambari Dashboard and click on Actions tab at the bottom left corner. Hit Start All to ensure Spark is running. Ambari will take some time to start all services and you can monitor the progress of it.

![Lab4_2](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_2.png)

![Lab4_3](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_3.png)

2\. Close the Ambari browser and we will get running with some codes on Spark. ssh into the sandbox using root as login and hadoop as password.

```
login: root
password: hadoop
```
Optionally, if you don’t have an SSH client installed and configured you can use the built-in web client which can be accessed from here: **http://(_host_):4200** (use the same username and password provided above)

3\. Type the command spark-shell

This will load the default Spark Scala API.

![Lab4_4](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_4.png)

Notice it is already starting with Hive integration as we have preconfigured it on the Hortonworks Sandbox.

<!-- @task, "text" : "Complete Step 4.1."-->

<!-- @section -->

## Step 4.2: Create a HiveContext

For improved Hive integration, HDP 2.3 offers [ORC file](http://hortonworks.com/blog/orcfile-in-hdp-2-better-compression-better-performance/) support for Spark. This allows Spark to read data stored in ORC files. Spark can leverage ORC file’s more efficient columnar storage and predicate pushdown capability for even faster in-memory processing. HiveContext is an instance of the Spark SQL execution engine that integrates with data stored in Hive. The more basic SQLContext provides a subset of the Spark SQL support that does not depend on Hive. It reads the configuration for Hive from hive-site.xml on the classpath.

*   **Import these sql libraries.**

```sql
import org.apache.spark.sql.hive.orc._
import org.apache.spark.sql._
```

![Lab4_5](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_5.png)

*    **Instantiate HiveContext**

```sql
val hiveContext = new org.apache.spark.sql.hive.HiveContext(sc)
```

![Lab4_6](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_6.png)

> **NOTE** sc stands for Spark Context. SparkContext is the main entry point to everything Spark. It can be used to create RDDs and shared variables on the cluster. When you start up the Spark Shell, the SparkContext is automatically initialized for you with the variable sc.

<!-- @task, "text" : "Complete Step 4.2."-->

<!-- @section -->

## Step 4.3: Creating a RDD from HiveContext

**What is RDD?**

Spark’s primary core abstraction is called Resilient Distributed Dataset or RDD. Essentially it is just a distributed collection of elements that is parallelized across the cluster. What this means is which is that RDD is an immutable collection of objects that is partitioned and distributed across multiple physical nodes of a YARN cluster and that can be operated in parallel.

There are three methods for creating a RDD:

*   You can parallelize an existing collection. This means that the data already resides within Spark and can now be operated on in parallel.
*   The second method to create a RDD, is to reference a dataset. This dataset can come from any storage source supported by Hadoop such as HDFS, Cassandra, HBase etc.
*   The third method to create a RDD is from transforming an existing RDD to create a new RDD. We will be using the later two methods in our tutorial.

**1\. Use a simple show command to see the list of tables in Hive warehouse.**

```sql
hiveContext.sql("show tables").collect.foreach(println)
```

![Lab4_7](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_7.png)

You will notice that geolocation table and driver mileage table that we created in earlier tutorial are already listed in Hive metastore and can be directly queried upon.

**2\. Query tables to build Spark RDD**

We will do a simple select query to fetch data from geolocation and drivermileage tables to a spark variable. Getting data into Spark this way also allows to copy table schema to RDD.

```sql
val geolocation_temp1 = hiveContext.sql("select * from geolocation")
```

![Lab4_8](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_8.png)

```sql
val drivermileage_temp1 = hiveContext.sql("select * from drivermileage")
```

![Lab4_9](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_9.png)

Make sure that the RDD`s carry the exact data. You can verify through following command

```
geolocation_temp1.take(10) geolocation_temp1.take(10)
```

Both these commands will return 10 rows from respective RDD's.

**3\. Registering a Temporary table**

Now let’s give this RDD a name, so that we can use it in Spark SQL statements

```
geolocation_temp1.registerTempTable("geolocation_temp1")
drivermileage_temp1.registerTempTable("drivermileage_temp1")
```
<!-- @task, "text" : "Complete Step 4.3."-->

<!-- @section -->

## Step 4.4: RDD transformations and Actions

Typically, RDDs are instantiated by loading data from a shared filesystem, HDFS, HBase, or any data source offering a Hadoop InputFormat on a YARN cluster.

Once an RDD is instantiated, you can apply a [series of operations](https://spark.apache.org/docs/1.2.0/programming-guide.html#rdd-operations). All operations fall into one of two types:[transformations](https://spark.apache.org/docs/1.2.0/programming-guide.html#transformations) or [actions](https://spark.apache.org/docs/1.2.0/programming-guide.html#actions).

*   **Transformation** operations, as the name suggests, create new datasets from an existing RDD and build out the processing DAG that can then be applied on the partitioned dataset across the YARN cluster. Transformations do not return a value. In fact, nothing is evaluated during the definition of these transformation statements. Spark just creates these Direct Acyclic Graphs or DAG, which will only be evaluated at runtime. We call this lazy evaluation.
*   An **Action** operation, on the other hand, executes DAG and returns a value.

**1\. Querying against the table**

Now that our schema’s RDD with data has a name, we can use Spark SQL commands to query it. Remember the table below is not a Hive table, it is just a RDD we are querying with SQL.

*   Here we will try to perform iteration and filter operation. First, we need to filter drivers that have non- normal events associated to them and then count the number for non- normal events for each driver.

```sql
val geolocation_temp2= hiveContext.sql("SELECT driverid, count(driverid) occurance from geolocation_temp1  where event!='normal' group by driverid")
```

![Lab4_10](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_10.png)

> **NOTE** As stated earlier about RDD transformations, select operation is a RDD transformation and therefore does not return anything.

*   The resulting table will have count of total non normal events associated to each driver. Register this filtered table as a temporary table so that subsequent SQL queries can be applied on it.

```
geolocation_temp2.registerTempTable("geolocation_temp2")
```

*   You can view the result by doing an action operation on RDD.

```
geolocation_temp2.collect.foreach(println)
```
![Lab4_11](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_11.png)

1.  **Perform join operation**

In this section we will perform a join operation geolocation_temp2 table has details of drivers and count of their respective non-normal events. drivermileage_temp1 table has details of total miles travelled by each driver.

*   We will join two tables on common column, which in our case is driverid.

```sql
val joined= hiveContext.sql("select a.driverid,a.occurance,b.totmiles from geolocation_temp2 a,drivermileage_temp1 b where a.driverid=b.driverid")
```

![Lab4_12](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_12.png)

*   The resulting data set will give us total miles and total non normal events for a particular driver. Register this filtered table as a temporary table so that subsequent SQL queries can be applied on it.

```
joined.registerTempTable("joined")
```

*   You can view the result by doing an action operation on RDD.

```
joined.collect.foreach(println)
```

![Lab4_13](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_13.png)

1.  **Compute Driver Risk Factor**

In this section we will associate a driver risk factor with every driver. Driver risk factor will be calculated by dividing total miles travelled by non normal event occurrences.

```sql
val risk_factor_spark=hiveContext.sql("select driverid, totmiles,occurance, totmiles/occurance riskfactor from joined")
```

![Lab4_14](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_14.png)

*   The resulting data set will give us total miles and total non normal events and what is a risk for a particular driver. Register this filtered table as a temporary table so that subsequent SQL queries can be applied on it.

```
risk_factor_spark.registerTempTable("risk_factor_spark")
```

*   View the results

```
risk_factor_spark.collect.foreach(println)
```

![Lab4_15](http://hortonworks.com/wp-content/uploads/2015/07/Lab4_15.png)

<!-- @task, "text" : "Complete Step 4.4."-->

<!-- @section -->

## Step 4.5: Load and Save Data into Hive as ORC

In this section we will try to store data in orc format in Hive from Spark.ORC is a self-describing type-aware columnar file format designed for Hadoop workloads. It is optimized for large streaming reads and with integrated support for finding required rows fast. Storing data in a columnar format lets the reader read, decompress, and process only the values required for the current query. Because ORC files are type aware, the writer chooses the most appropriate encoding for the type and builds an internal index as the file is persisted.

Predicate pushdown uses those indexes to determine which stripes in a file need to be read for a particular query and the row indexes can narrow the search to a particular set of 10,000 rows. ORC supports the complete set of types in Hive, including the complex types: structs, lists, maps, and unions.

*   **Create an ORC table**

Create a table and store it as ORC. Specifying as orc at the end of the SQL statement below ensures that the Hive table is stored in the ORC format.

```sql
hiveContext.sql("create table finalresults( driverid String, occurance bigint,totmiles bigint,riskfactor double) stored as orc").toDF()
```

*   **Load data into ORC table**

Before we load the data into hive table that we created above, we will have to convert our data file into orc format too.

```sql
risk_factor_spark.saveAsOrcFile("risk_factor_spark")
```

Load the data into Hive table using load data command.

```sql
hiveContext.sql("load data inpath 'risk_factor_spark' into table finalresults")
```

*   Execute a select query to verify your table has been successfully stored.You can go to Ambari Hive user view to check whether the Hive table you created has the data populated in it.

```sql
hiveContext.sql(“select * from finalresults”)
```

<!-- @task, "text" : "Complete Step 4.5."-->
