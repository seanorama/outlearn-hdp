<!--
{
"name" : "lab0",
"version" : "0.1",
"title" : "Lab 0: Set-up",
"description" : "Start the Sandbox VM and Open Ambari.",
"freshnessDate" : 2015-07-23,
"homepage" : "http://hortonworks.com/",
"canonicalSource" : "http://hortonworks.com/hadoop-tutorial/hello-world-an-introduction-to-hadoop-hcatalog-hive-and-pig/#section_6",
"license" : "All Rights Reserved"
}
-->

<!-- @section -->

## Start the Sandbox VM and Open Ambari

Start the HDP Sandbox following the [Sandbox Install Guide](http://hortonworks.com/products/hortonworks-sandbox/#install) to start the VM:

![Lab0_1](http://hortonworks.com/wp-content/uploads/2015/07/Lab0_1.png)

Once you have installed the Sandbox VM, it resolves to the host on your environment, the address of which varies depending upon the Virtual Machine you are using(Vmware, VirtualBox etc). As, a general thumb rule, wait for the installation to complete and confirmation screen will tell you the host your sandbox resolves to. For example:

In case of VirtualBox: host would be 127.0.0.1

![Lab0_2](http://hortonworks.com/wp-content/uploads/2015/07/Lab0_2.png)

If you are using a private cluster or a cloud to run sandbox. Please find the host your sandbox resolves to.

Append the port number :8888 to your host address, open your browser, and access Sandbox Welcome page at http://_host_:8888/.

![Screen-Shot-2015-07-20-at-6.11.32-PM](http://hortonworks.com/wp-content/uploads/2015/07/Screen-Shot-2015-07-20-at-6.11.32-PM.png)

Navigate to Ambari welcome page using the url given on Sandbox welcome page.

Both the username and password to login are admin.

<!-- @task, "text" : "Log in to Ambari."-->

> **NOTE:**  If you want to search for the host address your sandbox is running on, ssh into the sandbox terminal upon successful installation and follow subsequent steps:

>1.  login using username as “root” and password as “hadoop”.
>2.  Type ifconfig and look for inet address under eth.
>3.  Use the inet address, append :8080 and open it into a browser. It shall direct you to Ambari login page.
>4.  This inet address is randomly generated for every session and therefore differs from session to session.



The following table has some useful URLs as well:

| **Service** | **URL** |
|----------------- |---------------- |
| Sandbox welcome page | http://_host_:8888 |
| Ambari Dashboard | http://_host_:8080 |
| Ambari Welcome | http://_host_:8080/views/ADMIN_VIEW/2.1.0/INSTANCE/#/ |
| Hive User View | http://_host_:8080/#/main/views/HIVE/1.0.0/Hive |
| Pig User View | http:/_host_:8080/#/main/views/PIG/0.1.0/MyPig |
| FIle User View | http://_host_:8080/#/main/views/FILES/0.2.0/MyFiles |
| SSH web Client | http://_host_:4200 |
| Hadoop Configuration | http://_host_:50070/dfshealth.html
 http://_host_:50070/explorer.html |

| **Service** | **User** | **Password** |
|----------------- |---------------- |------------|
| Ambari | admin | admin |
| Linux OS | root | hadoop |

Enter the Ambari Welcome URL and then you should see a similar screen:

There are 5 key capabilities to explore in the Ambari Welcome screen:

![Lab0_3](http://hortonworks.com/wp-content/uploads/2015/07/Lab0_3.png)

1.  “**Operate Your Cluster**” will take you to the Ambari Dashboard which is the primary UI for Hadoop Operators
2.  “**Manage Users + Groups**” allows you to add & remove Ambari users and groups
3.  “**Clusters**” allows you to grant permission to Ambari users and groups
4.  “**Ambari User Views**” list the set of Ambari Users views that are part of the cluster
5.  “**Deploy Views**” provides administration for adding and removing Ambari User Views

Take a few minutes to quickly explore these 5 capabilities and to become familiar their features.

<!-- @task, "text" : "Explore the 5 key capabilities of Ambari and become familiar their features."-->

Enter the Ambari Dashboard URL and you should see a similar screen:

##### ![Lab0_4](http://hortonworks.com/wp-content/uploads/2015/07/Lab0_4.png)

Briefly skim through the Ambari Dashboard links (circled above) by clicking on

1\.  **Metrics**, **Heatmap** and **Configuration**

and then the

2\.  **Dashboard**, **Services**, **Hosts**, **Alerts**, **Admin** and User Views icon (represented by 3×3 matrix ) to become familiar with the Ambari resources available to you.

> **NOTE**  To learn more about Hadoop please explore the [HDP Getting Started documentation](http://docs.hortonworks.com/HDPDocuments/HDP2/HDP-2.2.4/bk_getting-started-guide/content/ch_about-hortonworks-data-platform.html).
 If you have questions, feedback or need help getting your environment ready visit [developer.hortonworks.com](http://hortonworks.com/developer/). Please also explore the [HDP documentation](http://docs.hortonworks.com/). To ask a question check out the [Hortonworks Forums](http://hortonworks.com/community/forums/).
