
![](./sql2019workshop/graphics/microsoftlogo.png)

# Workshop: SQL Server 2019 Workshop

#### <i>A Microsoft Course from the SQL Server team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/textbubble.png?raw=true"><b>     About this Workshop</b></h2>

Welcome to this Microsoft solutions workshop on *SQL Server 2019 Workshop*.

In this course you will learn how to solve modern data challenges with SQL Server 2019 using a hands-on lab approach.

This course is intended to be taken as a self-paced or instructor-led workshop. A supplement slide deck is available for this course in the [slides](https://github.com/microsoft/sqlworkshops-sql2019workshop/tree/master/sql2019workshop/slides) folder.

This course is designed for data professionals who have a basic working knowledge of SQL Server and the T-SQL language.

This **README.MD** file explains how the lab is structured, what you will learn, and the technologies you will use in this solution.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/checkmark.png?raw=true"><b>     Learning Objectives</b></h2>

When you complete this course, you will be able to:

- Understand and use **Intelligent Performance** and **Optimizations for TempDB** features to boost query performance with no application changes
- Understand and use **Data Classification and Auditing** to meet the needs of compliance and regulation standards.
- Understand and use **Accelerated Database Recovery** to increase database availability.
- Learn how to **extend the T-SQL Language** with Java classes.
- Understand and use **containers** and deploy **SQL Server Replication on Linux**.
- Learn how to deploy and use **SQL Server on Kubernetes**
- Understand and use **Polybase** to connect and query other data sources with no data movement.
- Learn how to use **Big Data Clusters** to gain intelligence over all your data integrating SQL Server, Hadoop, and Spark.
- Learn more about **additional capabilities** of SQL Server 2019, **Migration** tools, and **Database Compatibility**.

As part of taking this lab you are also learning about new capabilities in **Azure SQL**.

The following features in this lab also exist in Azure SQL:

- Intelligent Query Processing
- Data Classification and Auditing
- Accelerated Database Recovery

In addition, SQL Server Polybase allows you to connect to Azure SQL, Azure SQL Data Warehouse, and Azure CosmosDB.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2>
<img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/building1.png?raw=true"><b>     Business Applications of this Workshop</b></h2>

- Boost Database Performance with no application changes
- Classify data for industry or regulatory compliance
- Ensure data is highly available to outages that can disrupt your business.
- Reduce costs of expensive data movement applications
- Integrate all your data and build end-to-end machine learning application in a single solution.
- Choose different platforms for SQL Server and take advantage of containerized applications.
- Learn how to extend the T-SQL language to meet the needs of your application.
- Learn tools and techniques to modernize and migrate to SQL Server 2019.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/listcheck.png?raw=true"><b>     Technologies used in this Workshop</b></h2>

 <table style="tr:nth-child(even) {background-color: #f2f2f2;}; text-align: left; display: table; border-collapse: collapse; border-spacing: 2px; border-color: gray;">

  <tr><th style="background-color: #1b20a1; color: white;">Technology</th> <th style="background-color: #1b20a1; color: white;">Description</th></tr>

  <tr><td><i>SQL Server</i></td><td>Database Platform produced by Microsoft</td></tr>
  <tr><td><i>SQL Server 2019</i></td><td>Most current release of SQL Server</td></tr>
  <tr><td><i>Intelligent Query Processing</i></td><td>Automated query processing enhancements in SQL Server 2019</td></tr>
 <tr><td><i>Query Store</i></td><td>Built-in query performance execution statistics stored in a user database</td></tr>
 <tr><td><i>Data Classification</i></td><td>Built-in data information classification with SQL Server with auditing</td></tr>
<tr><td><i>Accelerated Database Recovery</i></td><td>Turbocharged Recovery, fast rollback, and aggressive transaction log truncation</td></tr>
<tr><td><i>Polybase</i></td><td>Data Virtualization through external tables</td></tr>
  <tr><td><i>Linux</i></td><td>Operating system used in Containers and Container Orchestration</td></tr>
  <tr><td><i>Container runtime</i></td><td>Engine for running and manage containers</td></tr>
<tr><td><i>SQL Server Management Studio (SSMS)</i></td><td>Graphical User Interface Management and Query Tool</td></tr>
    <tr><td><i>Azure Data Studio<i></td><td>Graphical User Interface to execute T-SQL queries, notebooks, and manage SQL Server</td></tr>

</table>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/owl.png?raw=true"><b>     Before Taking this Workshop</b></h2>

To complete this workshop you will need the following:

- Clone the workshop using git from https://github.com/microsoft/sqlworkshops-sql2019workshop.git. All the scripts and files in the labs are found in the **sql2019workshop** folder.
- On Windows systems, you should use the following git syntax

    `git clone --config core.autocrlf=false https://github.com/microsoft/sqlworkshops-sql2019workshop.git`

- Install the software as listed in the **Setup** section below

Each module of this workshop can be studied and used independently of each other or taken all as a single lab. The Modules are designed in a sequence but you can use each of them one at a time at your own pace.

<h3><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/bulletlist.png?raw=true"> 
<b>     Setup</b></h3>

In order to complete this workshop you need to install the following software:

- Servicing Update for SQL Server 2019 RTM or later (https://support.microsoft.com/en-us/help/4517790/servicing-update-for-sql-server-2019-rtm). You can run all of the activities from this workshop on an installed SQL Server on Windows, Linux, or Containers. You can use the client tools on a separate computer or VM provided it has access to connect to SQL Server.
    - For **Modules 2, 3, and 4** you only need the database engine installed.
    - **Module 4** requires disk space to hold a database with a 5Gb data and 10Gb or 20Gb log file.
    - **Module 5** requires a Java SDK to be installed to compile the Java classes and the Machine Learning and Language Extensions feature to be installed.
    - **Module 6** requires a container runtime like Docker. You can run this on Windows, MacOS, or Linux.
    - **Module 7** requires access to a deployed Kubernetes Cluster like Azure Kubernetes Service (AKS).
    - **Module 8** requires you to install and enable Polybase (you don't need the Java option and you can choose a stand-alone Polybase.). To run the primary notebook in Module 4 you need access to an Azure SQL Database.
    - **Module 9** requires you to deploy a SQL Server 2019 Big Data Cluster on Kubernetes.

- Install SQL Server Management Studio (SSMS) 18.2 or higher from https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms. Several of the modules require features built only into SSMS.
- Install Azure Data Studio June 2019 or higher from https://docs.microsoft.com/en-us/sql/azure-data-studio/download. T-SQL notebooks are used extensively in this course.

Azure Data Studio includes new important capabilities for the SQL Server professional called Notebooks. To learn more watch this video by Microsoft Principal Program Manager Vicky Harp on Azure Data Studio:

<a href="http://www.youtube.com/watch?feature=player_embedded&v=Nt4kIHQ0IOc
" target="_blank"><img src="http://img.youtube.com/vi/Nt4kIHQ0IOc/0.jpg" 
alt="Introducing SQL Server 2019" width="400" height="300" border="10" /></a>

- The WideWorldImporters sample backup from https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak. You can find example scripts to restore the WideWorldImporters database in the **sql2019workshop** folder.

This workshop was built and designed for a computer or VM to run SQL Server with at least 8Gb RAM and 4 CPUs.

> **NOTE**: *If you run this lab from a virtual machine in Azure running Windows, and you want to use Module 6, you will need to enable nested virtualization. Read more at https://docs.microsoft.com/en-us/azure/virtual-machines/windows/nested-virtualization*

Microsoft and any contributors grant you a license to the Microsoft documentation and other content
in this repository under the Creative Commons Attribution 4.0 International Public License,
see the LICENSE file, and grant you a license to any code in the repository under the MIT License, see the
LICENSE-CODE file. All license files are found in the LICENSES directory.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/education1.png?raw=true"><b>     Workshop Details</b></h2>

This workshop uses SQL Server 2019, SQL Server Management Studio, Azure Data Studio, containers, Kubernetes, and Azure SQL Database for you to learn how you can solve modern data challenges with SQL Server 2019.

<table style="tr:nth-child(even) {background-color: #f2f2f2;}; text-align: left; display: table; border-collapse: collapse; border-spacing: 5px; border-color: gray;">

  <tr><td style="background-color: Cornsilk; color: black; padding: 5px 5px;">Primary Audience:</td><td style="background-color: Cornsilk; color: black; padding: 5px 5px;">Data professionals looking to understand and use new capabilities of SQL Server 2019</td></tr>
  <tr><td>Secondary Audience:</td><td>Developers, Architects, IT Pros, Data Scientists, and Data Engineers</td></tr>
  <tr><td style="background-color: Cornsilk; color: black; padding: 5px 5px;">Level: </td><td style="background-color: Cornsilk; color: black; padding: 5px 5px0;">300</td></tr>
  <tr><td>Type:</td><td>Self-Paced or Instructor Led</td></tr>
  <tr><td style="background-color: Cornsilk; color: black; padding: 5px 5px;">Length: </td><td style="background-color: Cornsilk; color: black; padding: 5px 5px;">Full Day</td></tr>

</table>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/pinmap.png?raw=true"><b>     Related Workshops</b></h2>

- [SQL Server 2019 Lab](https://github.com/microsoft/sqlworkshops/tree/master/sql2019lab)
- [SQL Server Big Data Clusters Architecture](https://github.com/microsoft/sqlworkshops/tree/master/sqlserver2019bigdataclusters)
- [SQL Server 2019 on OpenShift](https://github.com/microsoft/sqlworkshops/tree/master/SQLonOpenShift)
- [SQL Ground-to-Cloud](https://github.com/microsoft/sqlworkshops/tree/master/SQLGroundToCloud)


<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/bookpencil.png?raw=true"><b>     Workshop Modules</b></h2>

This is a modular workshop, and in each section, you'll learn concepts, technologies, and processes to help you complete the solution. This table is provided for you to see the list of modules in the workshop. You can use any module in any order you like but the preferred method is to **proceed to Next Steps below to start the workshop.**

<table style="tr:nth-child(even) {background-color: #f2f2f2;}; text-align: left; display: table; border-collapse: collapse; border-spacing: 5px; border-color: gray;">

  <tr><td style="background-color: AliceBlue; color: black;"><b>Module</b></td><td style="background-color: AliceBlue; color: black;"><b>Topics</b></td></tr>

  <tr><td ><a href="./sql2019workshop/01_Introduction.md" target="_blank">01 - Introduction to SQL Server 2019</a></td><td> Learn how SQL Server 2019 solves challenges for the modern data professional</td></tr>
  <tr><td><a href="./sql2019workshop/02_IntelligentPerformance.md" target="_blank">02 - Intelligent Performance</a></td><td> Learn the how SQL Server can boost your performance with no application changes</td></tr>
  <tr><td><a href="./sql2019workshop/03_Security.md" target="_blank">03 - Security</a> </td><td > Learn new security features of SQL Server 2019 such as Data Classification and Auditing</td></tr>
  <tr><td><a href="./sql2019workshop/04_Availability.md" target="_blank">04 - Availability</a></td><td> Learn new capabilities to make your SQL Server more available such as Accelerated Database Recovery</td></tr>
  <tr><td ><a href="./sql2019workshop/05_ModernDevPlatform.md" target="_blank">05 - Modern Development Platform</a></td><td> Learn how SQL Server 2019 provides new capabilities for the modern data developer</td></tr>
  <tr><td><a href="./sql2019workshop/06_Linux_and_Containers.md" target="_blank">06 - Linux and Containers</a></td><td>Learn how to deploy SQL Server in containers and SQL Server Replication on Linux.</td></tr>
  <tr><td><a href="./sql2019workshop/07_SQLOnKubernetes.md" target="_blank">07 - SQL Server on Kubernetes</a></td><td>Learn how to deploy SQL Server on a Kubernetes Cluster</td></tr>
  <tr><td><a href="./sql2019workshop/08_DataVirtualization.md" target="_blank">08 - Data Virtualization</a> </td><td>Learn how to use SQL Server as a data hub and reduce data movement using Polybase++</td></tr> 
  <tr><td><a href="./sql2019workshop/09_BigDataClusters.md" target="_blank">09 - Big Data Clusters</a> </td><td>Learn how to use and manage an integrated solution with SQL Server, Hadoop, and Spark</td></tr>
  <tr><td><a href="./sql2019workshop/10_Additional_Migration.md" target="_blank">10 - Additional Capabilities,  Migration, and Next Steps</a></td><td>Learn more about Additional Capabilities in SQL Server 2019, Migration Tools, Database Compatibility, and Next Steps</td></tr>
  <tr></tr>
  <tr></tr>
</table>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/geopin.png?raw=true"><b>     Next Steps</b></h2>

Next, Continue to <a href="./sql2019workshop/01_Introduction.md" target="_blank"><i>Introduction to SQL Server 2019</i></a>

