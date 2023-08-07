![](./graphics/microsoftlogo.png)

# Workshop: SQL Server 2019 Workshop

#### <i>A Microsoft workshop from the SQL Server team</i>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/textbubble.png?raw=true"><b>     SQL Server Intelligent Performance</b></h2>

SQL Server 2019 includes new capabilities designed to enhance your performance with no application changes. These enhancements include:

- Intelligent Query Processing
- Lightweight Query Profiling
- Sequential Key Insert Performance
- In-Memory Database
    - Hybrid Buffer Pool
    - Memory Optimized Tempdb Metadata
    - Persistent Memory Support

You can learn more about all of these enhancements at https://docs.microsoft.com/en-us/sql/sql-server/what-s-new-in-sql-server-ver15?view=sqlallproducts-allversions.

You will cover the following topics in this Module:

<dl>

  <dt><a href="#2-0">2.0 SQL Server Intelligent Query Processing</a></dt>
  <dt><a href="#2-1">2.1 Using Query Store for performance analysis</a></dt>
  <dt><a href="#2-2">2.2 Advanced: Memory Optimized Tempdb Metadata</a></dt>
  
</dl>

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/pencil2.png?raw=true"><b><a name="2-0">     2.0 SQL Server Intelligent Query Processing</a></b></h2>

In this module you will learn about the Intelligent Query Processing capabilities in SQL Server 2019.

<h3><b><a name="challenge">The Challenge</a></b></h3>

Application developers and DBAs want to gain performance for queries without making application changes. Query tuning can be an expensive undertaking so they want the query processor to adapt to their workload needs vs having to use options and flags to gain performance.

<h3><b><a name="solution">The Solution</a></b></h3>

Intelligent Query processing is a suite of features built into the query processor for SQL Server 2019 allowing developers and data professionals to accelerate database performance automatically **without application changes**. T-SQL queries simply need to be run with a database compatibility level of 150 to take advantage of these enhancements.

You can read more about database compatibility at https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-compatibility-level#compatibility-levels-and-sql-server-upgrades.
The following is a diagram showing the features of Intelligent Query Processing including capabilities from SQL Server 2017 and SQL Server 2019:

![iqp diagram](./graphics/IQP_diagram.png)

Intelligent Query Processing is a feature that exists for both SQL Server 2019 and Azure SQL Database. You can read the documentation for a description and example of all of these features at https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing.

> **NOTE**: *One of the features of Intelligent Query Processing, approximate count distinct, does not require database compatibility of 150*

Learn more about Intelligent Query Processing from Senior Program Manager Pedro Lopes:

<a href="http://www.youtube.com/watch?feature=player_embedded&v=LI9Jtl7m8t8" target="_blank"><img src="http://img.youtube.com/vi/LI9Jtl7m8t8/0.jpg" 
alt="Introducing SQL Server 2019" width="400" height="300" border="10" /></a>

Now proceed to the Activity to learn an example of how Intelligent Query Processing can accelerate query performance automatically with no application changes.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/point1.png?raw=true"><b><a name="activityiqp">     Activity: SQL Server Intelligent Query Processing</a></b></h2>

In this activity, you will learn how to use the built-in capabilities of Intelligent Query Processing in SQL Server 2019 simply by changing the database compatibility of WideWorldImporters to version 150 with no application changes.

> **NOTE**: *If at anytime during the Activities of this Module you need to "start over" you can go back to the first step in the Activity for 2.0 and run through all the steps again.*

You have been provided a stored procedure called **CustomerProfits** which you will deploy in the **Facts** schema of the **WideWorldImporters** database. The stored procedure uses a *table variable* to store interim results from a user table and then uses that table variable to join with other data in the **WideWorldImporters** database. In previous releases of SQL Server, this design pattern could cause an issue, since SQL Server would always estimate that the table variable only contains 1 row of data. This can cause issues with building the optimal query plan for the best performance.

SQL Server 2019 Intelligent Query Processing includes a capability called *table variable deferred compilation* to improve the performance of T-SQL code that uses table variables. The application simply needs to change the database compatibility level to 150, which is the default for SQL Server 2019, and execute the T-SQL statements with table variables to see a gain in performance.

The **WideWorldImporters** database example was created using SQL Server 2016 which has a default database compatibility level of 130. When a database is restored from a previous version of SQL Server, the compatibility level of the database is preserved to help reduce the risk of upgrades.

You will observe the performance of the **CustomerProfits** stored procedure with database compatibility level of 130 on SQL Server 2019. You will then compare the performance of the same procedure with no changes with a database compatibility of 150 which will enable the query processor to use  table variable deferred compilation.

<h3><img style="margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/checkmark.png?raw=true"><b><a name="activitysteps2.0">Activity Steps</a></b></h3>

All scripts for this activity can be found in the **sql2019workshop\02_IntelligentPerformance\iqp** folder.

Follow these steps to observe performance differences with table variable deferred compilation.

**STEP 1: Restore the WideWorldImporters backup**

> **NOTE**: If you have restored the WideWorldImporters database backup in other modules, you can skip this step.

Use a tool like SQL Server Management Studio (SSMS) or Azure Data Studio (ADS) to execute the T-SQL script **restorewwi.sql** as found in the **sql2019workshop\02_IntelligentPerformance\iqp** folder to restore the WideWorldImporters backup. The script assumes a specific path for the backup and database/log files. You may need to edit this depending on your installation. *Remember for Linux installations, the default path is /var/opt/mssql/data.* Your instructor may have provided this backup for you but if necessary you can download it from https://github.com/Microsoft/sql-server-samples/releases/download/wide-world-importers-v1.0/WideWorldImporters-Full.bak.

**STEP 2: Use a T-SQL notebook to complete the rest of the activity.**

T-SQL notebooks provide a very nice method to execute T-SQL code with documentation in the form of markdown code. All the steps and documentation to complete the rest of the activity for Module 2.0 can be found in the T-SQL notebook **iqp_tablevariabledeferred.ipynb** which can be found in the **sql2019workshop\02_IntelligentPerformance\iqp** folder.

>**NOTE**: *A T-SQL script **iqp_tablevariabledeferred.sql** is also provided if you want to go through the same steps as the notebook but use a tool like SQL Server Management Studio*.

T-SQL notebooks can be executed with Azure Data Studio. If you are familiar with using Azure Data Studio and T-SQL notebooks open up the **iqp_tablevariabledeferred.ipynb** notebook and go through all the steps. When you are done proceed to the **ActivitySummary** section for the Activity below.

If you have never opened a T-SQL notebook with Azure Data Studio, use the following instructions:

Launch the Azure Data Studio application. Look for the icon similar to this one:

<p><img style="margin: 0px 30px 15x 0px;" src="./graphics/azure_data_studio_icon.png" width="50" height="50">

The first time you launch Azure Data Studio, you may see the following choices. For the purposes of this workshop, You can select No to loading 2019 preview extensions and click X to not read the usage data statement.
    
<p><img style="margin: 0px 30px 15x 0px;" src="./graphics/ADS_initial_prompts.jpg" width="250" height="150">

You will now be presented with the following screen to enter in your connection details for SQL Server. Use connection details as provided by your instructor to connect to SQL Server or the connection you have setup yourself for your SQL Server instance.

Now click the **Connect** button to connect. An example of a connection looks similar to this graphic (your server, Auth type, and login may be different):

<p><img style="margin: 0px 30px 15x 0px;" src="./graphics/Azure_Data_Studio_Connect.jpg" width="300" height="350">

A successful connection looks similar to this (your server may be different):

![Azure Data Studio Successful Connection](./graphics/Azure_Data_Studio_Successful_Connect.jpg)

Use the power of Azure Data Studio Explorer to open up any file including notebooks. Use the File/Open Folder menu to open up the **sql2019workshop** folder. Now click the Explorer icon on the left hand side of Azure Data Studio to see all files and directories for the lab. Navigate to the **02_IntelligentPerformance\iqp** folder, open up the **iqp_tablevariabledeferred.ipynb** notebook and go through all the steps. 

>**NOTE**: Be sure to only run one notebook cell at a time for the lab.

You can now use Azure Data Studio explorer to open up a notebook or script without exiting the tool.

![Azure Data Studio Explorer](./graphics/Azure_Data_Studio_Explorer.jpg)

When you start using a notebook and use the "Play" button of a cell, you may get prompted for the connection. Choose the connection you used when you first opened up Azure Data Studio.

![Play cell in Notebook](./graphics/Play_Cell_Notebook.jpg)

There is additional documentation on how to use SQL notebooks at https://docs.microsoft.com/en-us/sql/azure-data-studio/sql-notebooks. When you are done proceed to the **Activity Summary** section for the Activity below.

<h3><b><a name="activitysummary">Activity Summary</a></b></h3>

In this activity you have learned the powerful capabilities of Intelligent Query Processing by looking at an example where no application changes were required to boost performance. All that was required was to simply change the database compatibility level to 150 for the database. This example used a concept called table variable deferred compilation. You can read more about this capability at https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing#table-variable-deferred-compilation.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/pencil2.png?raw=true"><b><a name="2-1">     2.1 Using Query Store for Performance Analysis</a></b></h2>

In this module you will learn how to use the Query Store, a built-in performance analysis feature of SQL Server, to analyze the performance differences of the queries run in Module 2.0. Even though query store is not new to SQL Server 2019, it is an excellent feature to help analyze performance differences with Intelligent Query Processing.

<h3><b><a name="challenge">The Challenge</a></b></h3>

Developers and DBA need to track query performance execution over time without having to "poll" Dynamic Management Views and save it to permanent storage. Data professionals need to easily be able to compare query execution for different query plans associated with the same query text.

<h3><b><a name="solution">The Solution</a></b></h3>

The Query Store is built into the query processing engine, enabled using an option for each database in SQL Server. Once enabled, performance statistics for queries are cached and stored in the SQL user database so they are persisted across server restarts.

In addition, the Query Store comes with a series of catalog and dynamic management views to gain insight into recorded query performance, including the ability to view execution details for different query plans over time associated with the same query.

You can read more about the Query Store at https://docs.microsoft.com/en-us/sql/relational-databases/performance/monitoring-performance-by-using-the-query-store. In addition, there were enhancements in Query Store for SQL Server 2019 for "capture policy" which you can read at https://docs.microsoft.com/en-us/sql/t-sql/statements/alter-database-transact-sql-set-options?view=sqlallproducts-allversions.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/point1.png?raw=true"><b><a name="activityquerystore">     Activity: Using Query Store for Performance Analysis</a></b></h2>

The **WideWorldImporters** sample database that you restored in Module 2.0 has the Query Store feature enabled. If you performed the Activities in Module 2.0, the Query Store recorded performance information about each query execution.

>**NOTE**: *If at anytime during the Activities of this Module you need to "start over" you can go back to the first Activity in 2.0 and run through all the steps again.*

<h3><img style="margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/checkmark.png?raw=true"><b><a name="activitysteps2.1">Activity Steps</a></b></h3>

Work through the following steps to use the Query Store to examine the query performance differences for the CustomerProfits stored procedure when executed with database compatibility 130 versus 150.

**STEP 1: Find Query Store Reports**

Open SQL Server Management Studio (SSMS). Using Object Explorer, navigate to the WideWorldImporters database. Find the Query Store folder and select the **Top Resource Consuming Queries** report.

Your screen should look similar to the following

![Query Store Reports](./graphics/Query_Store_Reports.png)

**STEP 2: Find the query from the CustomerProfits procedure**

There could be other queries in the Query Store. Click on the bars in the graph starting from left to right until you find the query for the query text

<pre>SELECT TOP 1 COUNT(i.CustomerID) as customer_count, SUM(il.LineProfit) as total_profit
FROM Sales.Invoices i
INNER JOIN @ilines il
ON i.InvoiceID = il.InvoiceID
GROUP By i.CustomerID
</pre>

When you find this query your screen should look similar to the following with the chart in the right hand corner showing two "dots" representing the variance in performance for two query plans for the same query text.

![Query Plans for Table Variable](./graphics/query_plans_for_table_variable.png)

The "higher" the dot in the chart, the longer the average duration is for that query plan. Query store knows how to store changes in query plans for the same query text. In the example you executed, you ran the same stored procedure but with different dbcompat levels. A different query plan was generated when you switched to dbcompat 150 but didn't change the stored procedure. This is because the query processor used the table variable deferred compilation technique when building the new plan.

**STEP 3: Observe query duration and plan differences**

Click on the higher dot in the chart. Observe the plan in the lower hand window showing a Clustered Index Scan for the table variable. This is the query plan with dbcompat of 130. Move your cursor over the higher dot to show the query execution numbers for this plan.

Notice the average duration is less than 1 second but the total duration for all executions is ~13 seconds (your times may vary depending on compute resources for SQL Server). This may not seem all that bad but the business requires faster query execution.

![Query Stats for Slower Plan](./graphics/query_stats_for_slower_plan.png)

In the query plan window move your cursor over the Clustered Index Scan operator for the table variable and observe how SQL Server only estimates 1 row for the scan (even though the scan is 200K+ rows). A Nested Loops join is used with the Clustered Index Scan. That wouldn't be a problem if the table variable truly only had 1 row. But that is not a good plan choice if there are some 200K+ rows in the table variable.

![Query Plan Slower](./graphics/query_plan_slower.png)

![Table Variable Estimates Slow Plan](./graphics/table_variable_estimate_slow_plan.png)

**STEP 4: Observe plan and stats for the faster plan using table variable deferred compilation**

Repeat the same process for the lower dot which represents the query plan that is faster using dbcompat of 150.

Move your cursor over the lower dot and observe the execution statistics. See how the average and total duration are significantly lower than before.

![Query Stats for Faster Plan](./graphics/query_stats_for_faster_plan.png)

Click on the dot and observe the new query plan.

![Query Plan Faster](./graphics/query_plan_faster.png)

You will notice a clustered index scan is still used but this time with a Hash Join. Additionally, the query processor has used a concept called an Adaptive Join, which was introduced in SQL Server 2017. An adaptive join allows the query processor to choose the join method at execution time based on the number of rows from input of the operator. In this case, a Hash Join is the better choice. You can read more about Adaptive Joins at https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing.

Move your cursor over the Clustered Index Scan for the table variable. Notice the estimated rows is more accurate and the query processor has also chosen batch mode for rowstore processing. This is another Intelligent Query Processing feature in SQL Server 2019 to make queries faster with no application changes.

![Table Variable Estimates Faster Plan](./graphics/table_variable_estimate_faster_plan.png)

In this example, the query processor used three different Intelligent Query Processing features to make this query faster with no application changes:

- Table Variable Deferred Compilation
- Adaptive Join
- Batch mode for rowstore

<h3><b><a name="activitysummary">Activity Summary</a></b></h3>

In this activity you have seen how to use the Query Store for performance insights including the ability to see differences for the same query text of different query plans, including those that benefit from Intelligent Query Processing. You observed the SQL Server query processor using multiple techniques to make your queries faster with no changes to the stored procedure or application.

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/pencil2.png?raw=true"><b><a name="2-2">     2.2 Advanced: Tempdb Just Runs Faster</a></b></h2>

Tempdb is a shared database used implicitly through various capabilities of SQL Server most notably temporary tables and table variables.

<h3><b><a name="challenge">The Challenge</a></b></h3>

The use of temporary tables and table variables as a table is unique because a heavy usage will results in frequent drop and create of tables. This activity requires two types of operations within the SQL Server engine:

- Modifications and access to allocation pages such as GAM, SGAM, and PFS pages
- Internal modifications to rows in system tables used to store metadata of the temporary table or table variable.

These options will result in the requirement for a resource called a page latch to physically protect concurrent access to the internals of an allocation page or page associated with a system table.

A workload with a heavy number of concurrent usage of temporary tables or table variables can result in an unexpected page latch wait (as seen by the wait_type PAGELATCH_xx).

<h3><b><a name="solution">The Solution</a></b></h3>

By creating multiple data files for tempdb, a user is helping partition access to allocation pages thus reducing pressure on page latches for those types of pages. The installation of SQL Server can help automatically configure a certain number of files or customize a number of files as required by the application. A good deep explanation of the best number of tempdb files and contention can be found in this blog post https://techcommunity.microsoft.com/t5/SQL-Server/TEMPDB-Files-and-Trace-Flags-and-Updates-Oh-My/ba-p/385937.

In many cases when a proper number of tempdb files has been configured, users can still experience unexpected page latch waits. The page latch waits are typically contention on pages of system tables. Finding this problem can be difficult. This is because SQL Server diagnostics such as Dynamic Management Views (DMV) typically show page latch waits with a resource of `<dbid`>:`<fileid`>:`<pageid`>. You would need to use an undocumented, unsupported command like DBCC PAGE on this resource to find if the page was associated with a system table.

SQL Server 2019 provides several solutions to help solve these challenges:

- **Optimized Tempdb Metadata**

Using a SQL Server configuration, the engine will internally implement specific system tables in tempdb as memory-optimized (SCHEMA_ONLY) tables. You can read more about Optimized Tempdb Metadata at https://docs.microsoft.com/en-us/sql/relational-databases/databases/tempdb-database?view=sql-server-ver15#memory-optimized-tempdb-metadata.

Lear more about how tempdb is just now faster with Optimized Tempdb Metadata from Senior Program Manager Pam Lahoud

<a href="http://www.youtube.com/watch?feature=player_embedded&v=LQejtjKERWM
" target="_blank"><img src="http://img.youtube.com/vi/LQejtjKERWM/0.jpg" 
alt="Introducing SQL Server 2019" width="400" height="300" border="10" /></a>

- **Concurrent PFS updates**

SQL Server 2019 will be default use a different scheme to update PFS pages so that multiple users can concurrently update a PFS page, thus reducing page latch waits for allocation pages.

- **Documented, supported page header access**

SQL Server 2019 provides documented, supported interfaces to determine the object of a page by examining fields of a page header. You can read more about the T-SQL statement to access page header details at https://docs.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-db-page-info-transact-sql?.

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/point1.png?raw=true"><b><a name="activityquerystore">     Advanced Activity: Tempdb just got faster</a></b></h2>

Go through the following activity to learn how tempdb is just faster in SQL Server 2019 using a concurrent temporary table workload. You will also learn how to use new T-SQL interfaces to find the object associated with a page latch.

This activity requires the following software:

- SQL Server 2019 Evaluation, Developer, or Enterprise Edition
- The sqlcmd utility
- The free tool ostress.exe which can be downloaded from https://www.microsoft.com/en-us/download/details.aspx?id=4511.
- A tool to run various T-SQL scripts such as SQL Server Management Studio (SSMS), Azure Data Studio, or sqlcmd.
- Windows Performance Monitor

This activity assumes you will run all steps on the same computer as SQL Server where the local user is authorized to run as a SQL sysadmin. You may need to modify some of the scripts if you will use SQL authentication or connect to a remote SQL Server.

Linux and MacOS users can use a SQL Server running in a container or Linux but will need to run the ostress.exe tool from a Windows client. SQL Server also provides performance monitor counter data through the Dynamic Management View sys.dm_os_performance_counters which you can read more about at https://docs.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql.

<h3><img style="margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/checkmark.png?raw=true"><b><a name="activitysteps2.2">Activity Steps</a></b></h3>

> **NOTE**: *If at anytime during the Activities of this Module you need to "start over" you can go back by executing the command script **disableoptimizetempdb.cmd**, restart SQL Server, and run through all the steps again.*

Follow these steps to see how tempdb is just faster in SQL Server 2019 using a combination of SQL scripts and Performance Monitor. All scripts for this activity can be found in the **sql2019workshop\02_IntelligentPerformance\tempdb** folder.

**STEP 1: Setup and configure Windows Performance Monitor**

- Launch Windows Performance Monitor (you could run **perfmon** from a command line easily by right-clicking the Windows "Start" icon, select Run, and type in **perfmon**)
- Add these counters to the Live Chart
    - **SQL Server: SQL Statistics/Batch Requests/Sec**. Adjust the scale to 0.01
    - **SQL Server: Wait Statistics/Page latch Waits/Waits started per second**. Adjust the scale to 0.01
- You can remove the % Processor Time counter

**Tip**: To make the chart easier to read I would double-click on each counter and increase the width. I also change the color of Batch Requests/Sec to Dark Green and Page latch waits to Red.

Your performance monitor chart should look like the following

![Perfmon Tempdb Activity](./graphics/perfmon_tempdb_activity.png)

**STEP 2: Create a procedure for the tempdb workload**

Run the command script **setup_repro.cmd** which will execute the following set of T-SQL statements:

```sql
USE MASTER;
GO
DROP DATABASE IF EXISTS DallasMavericks;
GO
CREATE DATABASE DallasMavericks;
GO
USE DallasMavericks;
GO
CREATE OR ALTER PROCEDURE letsgomavs
AS
CREATE TABLE #gomavs (col1 INT);
GO
```

**STEP 3: Run a tempdb workload**

Run a tempdb based workload with the procedure created in the previous step by executing the command script **tempstress.cmd**. This script runs the following command with ostress:

`ostress -E -Q"exec letsgomavs" -n50 -r5000 -dDallasMavericks`

**STEP 4: Observe performance monitor counters**

Observe the performance monitor chart and numbers to see the scope of page latch waits and the average throughput of batch requests/sec.

Your performance monitor chart should look similar to the following after letting the workload run:

![Perfmon Tempdb with Page Latch Waits](./graphics/tempdb_workload_with_page_latch_waits.png)

**STEP 5: Use T-SQL find out what object belongs to the page latch waits**

Run the following T-SQL statements in the script **pageinfo.sql** to observe what objects belong the majority of page latch waits.


```sql
USE tempdb;
GO
SELECT object_name(page_info.object_id), page_info.*
FROM sys.dm_exec_requests AS d
  CROSS APPLY sys.fn_PageResCracker(d.page_resource) AS r
  CROSS APPLY sys.dm_db_page_info(r.db_id, r.file_id, r.page_id,'DETAILED')
    AS page_info;
GO
```
Your results should show the object name **sysschobjs** as the primary object involved in page latch waits. This system table is the primary table to store table metadata in the tempdb database.

**STEP 6: Observe the total duration of the workload**

Go back to the command window from STEP 3 and wait for the workload to finish and return to a command prompt. Take note of the total duration as indicated by ostress (your time may vary):

`OSTRESS exiting normally, elapsed time: hh:mm:ss.ms`

**STEP 7: Enable Optimize Tempdb Metadata**

Enable the Optimize Tempdb Metadata capability with SQL Server using the script **optimizetempdb.cmd** which runs the following commands:


```powershell
sqlcmd -E -ioptimizetempdb.sql
net stop mssqlserver
net start mssqlserver
```
The **optimizetempdb.sql** T-SQL scripts runs the following statement

```sql
ALTER SERVER CONFIGURATION SET MEMORY_OPTIMIZED TEMPDB_METADATA = ON;
GO
```

A SQL Server restart is required to enable optimized tempdb metadata. The NET STOP command may require you to shutdown dependent services such as Polybase or Launchpad. The final step in this Activity will be to ensure these services are restarted.

**STEP 8: Run the tempdb workload again**

Run the same tempdb workload as you did in STEP 3 by running the command script **tempstress.cmd**

**STEP 9: Observe performance counters again**

Observe the performance monitor chart and numbers to see the scope of page latch waits and the average throughput of batch requests/sec. What differences did you see from perfmon counters now vs what you observed in STEP 3?

If everything runs as expected, there should be almost no page latch waits (note the red line is almost non-existent) and your batch requests/sec should be 3 to 4  times higher on average (a much higher green line).

Your performance monitor chart should look like the following:

![Perfmon Tempdb without Page Latch Waits](./graphics/tempdb_workload_without_page_latch_waits.png)

**STEP 10: Observe the total duration of the workload**

Go back to the command window from STEP 8 and wait for the workload to finish and return to a command prompt. Take note of the total duration as indicated by ostress (your time may vary)

`OSTRESS exiting normally, elapsed time: hh:mm:ss.ms`

Did this run faster than the first time you observed the duration? If everything runs as expected the total duration should be 4 to 5 times less than it was in STEP 8 overall.

**STEP 11: Restore services**

Some dependent services for SQL Server such as Polybase and LaunchPad may have been shutdown when using the NET STOP command. Use the **SQL Server Configuration Manager** (search for the SQL Server 2019 Configuration Manager application. For RC1 builds it could be called the SQL Server 2019 RC1 Configuration Manager) to restart any dependent service that was shutdown during this activity.

<h3><b><a name="activitysummary">Activity Summary</a></b></h3>

You have learned in this activity how to accelerate performance of tempdb based workloads with no application changes. You have also learned new diagnostics to find an object associated with a page latch.

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/owl.png?raw=true"><b>     For Further Study</b></h2>

- [Intelligent Query Processing in SQL Server](https://docs.microsoft.com/en-us/sql/relational-databases/performance/intelligent-query-processing)
- [Q&A about Intelligent Query Processing](https://techcommunity.microsoft.com/t5/Azure-SQL-Database/Intelligent-Query-Processing-Q-amp-A/ba-p/446657)
- [Monitoring performance of SQL Server using the Query Store](https://docs.microsoft.com/en-us/sql/relational-databases/performance/monitoring-performance-by-using-the-query-store)
- [Optimized Tempdb Metadata](https://docs.microsoft.com/en-us/sql/relational-databases/databases/tempdb-database?view=sql-server-ver15#memory-optimized-tempdb-metadata)
- [What is Azure Data Studio?](https://docs.microsoft.com/en-us/sql/azure-data-studio/what-is)

- [How to use Notebooks in Azure Data Studio](https://docs.microsoft.com/en-us/sql/azure-data-studio/sql-notebooks)

<p style="border-bottom: 1px solid lightgrey;"></p>

<h2><img style="float: left; margin: 0px 15px 15px 0px;" src="https://github.com/microsoft/sqlworkshops/blob/master/graphics/geopin.png?raw=true"><b>  Next Steps</b></h2>

Next, Continue to <a href="./03_Security.md" target="_blank"><i>Security</i></a>.
