# DP-600-Microsoft-Fabric-Analytic-Engineer-Notes
Free study notes and cheat sheets for DP-600 exam preparation
DP-600: Implementing Analytics Solutions Using Microsoft Fabric 

Premium Practice Tests (PDF Resource) | High-Quality Question Bank 

Features:
Total Questions: [117]  
Target Certification: DP-600: Microsoft Fabric Analytic Engineer Practice Exam 
Detailed Explanations: Comprehensive rationale for correct and incorrect options 
Official References: Direct Microsoft Documentation links included for every question 
Branding: Cloud & AI Examprep 
Gumroad URL : [https://cloudprep.gumroad.com/l/dp600-practice-exam](url)

---------------------------------------------------------------------------------------------------------------------------
# DP-600: Microsoft Fabric Analytics Engineer - Free Study Guide & Resources
Welcome to the ultimate preparation repository for the Microsoft DP-600 Exam. This guide is designed to help you master Microsoft Fabric components like Lakehouses, Warehouses, Power BI, and Data Factories.

## 🚀 Ready to Pass Your DP-600 Exam?
If you have reviewed the study notes below and want to test your knowledge with **exam-style scenario questions**, I have created a comprehensive practice test set on Gumroad:

👉 **[Get Complete DP-600 Practice Tests with Detailed Explanations]([https://cloudprep.gumroad.com/l/dp600-practice-exam)** *(Special Discount Applied)*

## 📚 DP-600 Core Exam Domains & Cheat Sheet

### 1. Plan and Implement a Data Analytics Environment (10-15%)
* **Workspace Settings:** Fabric capacities, domains, and tenant settings.
* **Premium Capacities:** Understanding F-SKUs and P-SKUs for performance.

### 2. Prepare and Serve Data (40-45%)
* **Delta Lake Tables:** Fabric stores data in Delta Parquet format by default. V-Order optimization improves read performance.
* **Lakehouse vs. Data Warehouse:** 
  * *Lakehouse:* Supports Spark (Python/Scala) and SQL endpoints, ACID transactions via Delta Lake.
  * *Data Warehouse:* Pure T-SQL experience, traditional data warehousing capabilities with full DDL/DML support.
* **PySpark Snippet Example (Optimize/Z-Order):**
python Optimize a delta table for faster performance spark.sql("OPTIMIZE my_fabric_table ZORDER BY (CustomerKey)")

3. Implement and Manage Data Models (20-25%)
Direct Lake Mode: Connects Power BI directly to OneLake Delta tables without importing or querying data via SQL (Zero latency).

Star Schema: Always design Dimension and Fact tables to avoid performance bottlenecks in Power BI.

4. Explore and Analyze Data (20-25%)
DAX Queries: Using DAX query view in Power BI to analyze semantic models.
--------------------------------------------------------------------------------------------------------------------------

T## 📝 Sample DP-600 Exam Questions

Try these sample questions to check your current preparation level:

Q.1 You have a Fabric tenant that contains a warehouse. The warehouse uses row-level security (RLS).You create a Direct Lake semantic model that uses the Delta tables and RLS of the warehouse.When users interact with a report built from the model, which mode will be used by the DAX queries?
A) DirectQuery
B) Dual
C) Direct Lake
D) Import

Correct Answer: [A] 
Explanation: DirectQuery 

Row-level security simplifies the design and coding of security in your application. Row-level security helps you implement restrictions on data row access. Row-level security only applies to queries on a Warehouse or SQL analytics endpoint in Fabric. 

When using Direct Lake on SQL endpoints, a query sent to a Direct Lake semantic model can fall back to DirectQuery mode in which case the table no longer operates in Direct Lake mode. It retrieves data directly from the SQL analytics endpoint of the lakehouse or warehouse. Power BI queries on a warehouse in Direct Lake mode will fall back to Direct Query mode to abide by row-level security.  
https://learn.microsoft.com/en-us/fabric/data-warehouse/row-level-security 
https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-storage-mode#use-the-storage-mode-property 
https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-how-it-works#directquery-fallback 
 

Why other options are incorrect: 
Option B: Dual 
The table storage mode can be configured as Import, DirectQuery, or Dual. A table configured as Dual storage mode is both Import and DirectQuery, and this setting allows the Power BI service to determine the most efficient mode to use on a query-by-query basis. Dual mode is typically used in composite models where a table can act as either Import or DirectQuery.  

Composite mode can mix Import and DirectQuery modes or integrate multiple DirectQuery data sources. It is not the fallback state for a Direct Lake model encountering RLS. 
https://learn.microsoft.com/en-us/power-bi/connect-data/service-dataset-modes-understand 
https://learn.microsoft.com/en-us/power-bi/transform-model/desktop-composite-models 

Option C: Direct Lake 
Direct Lake is a Power BI semantic model table storage mode option available in Microsoft Fabric. It's optimized for large volumes of data to be quickly loaded into memory from Delta tables available in the OneLake, the single store for all analytics data. Once loaded into memory, the semantic model enables high-performance interactive analysis. This would be the mode if there were no RLS or if the security were manageable by the engine. Since Warehouse RLS is present, Direct Lake is bypassed to maintain security integrity. 
https://learn.microsoft.com/en-us/fabric/fundamentals/direct-lake-overview 
 
Option D: Import 

Import models need to be refreshed, usually on a scheduled basis. A full refresh removes all data from all tables and reloads it from the data source. The entire model must be loaded to memory before Power BI can query the model, which can place pressure on available capacity resources, especially as the number and size of Import models grow. 

Model data is only as current as the latest refresh, and so Import models need to be refreshed, usually on a scheduled basis. A full refresh removes all data from all tables and reloads it from the data source. This operation can be expensive in terms of time and resources for the Power BI service and data sources. 

https://learn.microsoft.com/en-us/power-bi/connect-data/service-dataset-modes-understand#import-mode 
--------------------------------------------------------------------------------------------------------- 

Q.2 You have a Fabric tenant that uses a Microsoft Power BI Premium capacity. You need to enable scale-out for a semantic model. What should you do first? 

A) At the semantic model level, set large dataset storage format to OFF 
B) At the tenant level, set create and use metrics to be enabled 
C) At the semantic model level, set large dataset storage format to ON 
D) At the tenant level, set Data Activator to enabled 

Correct Answer: [C] 
Explanation: At the semantic model level, set large dataset storage format to ON 
Semantic model scale-out helps Power BI deliver fast performance while your reports and dashboards are consumed by a large audience. Semantic model scale-out uses your Premium capacity to host one or more read-only replicas of your primary semantic model using the large dataset storage format. 
By default, scale-out is enabled for your tenant, but it's not enabled for semantic models in your tenant. To enable scale-out for a semantic model, you must use the Power BI REST APIs. Before enabling, the following prerequisites must be met: 
1. The Scale-out queries for large semantic models setting for your tenant is enabled (default). 
2. Your workspace resides on a Power BI Premium capacity: 
     a. Premium Per User (PPU) 
     b. Power BI Premium P SKUs 
     c. Power BI A SKUs for Power BI Embedded (also known as embed for your customers). 
     d. Fabric F SKUs 
3. The Large semantic model storage format setting is enabled. 
https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-premium-scale-out 
https://learn.microsoft.com/en-us/power-bi/enterprise/service-premium-scale-out-configure#enable-scale-out-in-power-bi-service 
 
Why other options are incorrect: 
Option A: At the semantic model level, set large dataset storage format to OFF 
This would force the model into the standard legacy format, which does not support the replica architecture needed for scaling out. 
https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-premium-large-models 

Option B: At the tenant level, set create and use metrics to be enabled 
While usage metrics help you monitor if you need scale-out by checking CPU or Memory usage, enabling them does not technically activate the scaling feature. 
https://learn.microsoft.com/en-us/fabric/admin/tenant-settings-index 
 
Option D: At the tenant level, set Data Activator to enabled 
Data Activator is a no-code event detection engine that transforms data streams into automated actions. It automatically triggers actions when specific patterns or conditions are detected in data sources. It continuously monitors these data sources with low latency, and initiates actions when thresholds are met, or specific patterns are detected. These actions can include sending emails or Teams notifications, launching Power Automate flows, or integrating with third-party systems.Data Activator is used for real-time alerting and automated actions, e.g. sending an email when a value reaches a threshold. It has no role in memory management or scaling of semantic models.
https://learn.microsoft.com/en-us/fabric/real-time-intelligence/data-activator/activator-introduction 
-------------------------------------------------------------------------------------------------------------------------
Q.3 You have a Fabric tenant that contains a data pipeline. 
You need to ensure that the pipeline runs every four hours on Mondays and Fridays. 
What should you set repeat for the schedule? 
A) Daily 
B) By the minute 
C) Weekly 
D) Hourly 
 

Correct Answer: [C] 
Explanation: Weekly 
This allows you to specify the pipeline to run on specific days of the week, in this case, every four hours on Mondays and Fridays. Scheduling options for data pipelines are available in the Azure Data Factory, which includes details on configuring recurring triggers 
This option allows you to select specific days, for example Monday and Friday. Once the days are selected, you can further define the interval within those days every 4 hours. 
You can manage your scheduled runs by selecting a schedule in the top banner of the Home tab. From there, you can edit existing schedules or enable or disable schedules using the toggle switch. 
https://learn.microsoft.com/en-us/fabric/data-factory/pipeline-runs 
https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers 

 
Option A: Daily 
This option forces the pipeline to run every day. It does not allow you to pick and choose specific weekdays like Monday and Friday. 
https://learn.microsoft.com/en-us/fabric/data-factory/pipeline-runs 
https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers 
 
Option B: By the minute 
This is used for high-frequency triggers for example every 15 minutes. These frequencies apply continuously regardless of the day of the week, unless combined with a weekly trigger configuration. 
https://learn.microsoft.com/en-us/fabric/data-factory/pipeline-runs 
https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers 

Option D: Hourly 
If you choose Hourly, you can configure it to repeat every 4 hours, but you cannot restrict it to specific days of the week. These frequencies apply continuously regardless of the day of the week, unless combined with a weekly trigger configuration. 
https://learn.microsoft.com/en-us/fabric/data-factory/pipeline-runs 
https://learn.microsoft.com/en-us/azure/data-factory/concepts-pipeline-execution-triggers 
------------------------------------------------------------------------------------------------------------------ 
Q.4 You have a Fabric tenant that contains a warehouse. A user discovers that a report that usually takes two minutes to render has been running for 45 minutes and has still not been rendered. You need to identify what is preventing the report query from completing. Which dynamic management view (DMV) should you use? 
A) sys.dm-exec_requests 
B) sys.dm_.exec._sessions 
C) sys.dm._exec._connections 
D) sys.dm_pdw_exec_requests 

 
Correct Answer: [ D ] 
Explanation: sys.dm_pdw_exec_requests 
The correct DMV to identify what is preventing the report query from completing is sys.dm_pdw_exec_requests. This DMV is specific to Microsoft Analytics Platform System previously known as SQL Data Warehouse, which is the environment assumed to be used here. It provides information about all queries and load commands currently running or that have recently run.  
https://learn.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sql-and-parallel-data-warehouse-dynamic-management-views?view=aps-pdw-2016-au7 

Why other options are incorrect: 
Option A: sys.dm-exec_requests 
While this is a standard SQL Server DMV, in the context of Fabric's distributed architecture, sys.dm_pdw_exec_requests is the specific view required to track the lifecycle of a query across the warehouse. 
https://learn.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-requests-transact-sql?view=fabric&preserve-view=true 

OptionB: sys.dm_.exec._sessions 
Returns one row per authenticated session on SQL Server. sys.dm_exec_sessions is a server-scope view that shows information about all active user connections and internal tasks. This information includes client version, client program name, client login time, login user, current session setting, and more.  

Use sys.dm_exec_sessions to first view the current system load and to identify a session of interest and then learn more information about that session by using other dynamic management views or dynamic management functions, but it doesn't give you specific details on the execution progress or blockage of a single query request. 
https://learn.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-sessions-transact-sql?view=fabric&preserve-view=true 

Option C: sys.dm._exec._connections 
Returns information about the connections established to this instance of the database engine and the details of each connection. Returns server wide connection information for SQL Server and Azure SQL Managed Instance. Returns connection information for the current database in Azure SQL Database. Returns connection information for all databases in the same elastic pool for databases in elastic pools in Azure SQL Database rather than the performance or status of a running report query. 
https://learn.microsoft.com/en-us/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-connections-transact-sql?view=fabric&preserve-view=true 
----------------------------------------------------------------------------------------------------------Q.8 You have a Q.5 You have Fabric tenant that contains a lakehouse named Lakehouse1 contains a Delta table named Customer. When you query Customer, you discover that the query is slow to execute. You suspect that maintenance was NOT performed on the table. You need to identify whether maintenance tasks were performed on Customer.  
Solution: You run the following Spark SQL statement:  
REFRESH TABLE customer  
Does this meet the goal? 
A) Yes 
B) No  

Correct Answer: [B] 
The REFRESH TABLE statement does not provide information on whether maintenance tasks were performed. It only updates the metadata of a table to reflect any changes on the data files. It simply updates the cached metadata of the table in the Spark session. It ensures that Spark is aware of the most recent files if the table was modified by another process. It does not show a history of operations or physical maintenance. 
1)https://learn.microsoft.com/en-us/azure/databricks/sql/language-manual/sql-ref-syntax-aux-cache-refresh-table 
2)https://learn.microsoft.com/en-us/azure/databricks/pyspark/reference/classes/catalog/refreshTable 

Running REFRESH TABLE customer does not provide information about maintenance tasks like compaction (OPTIMIZE) or the removal of old file versions (VACUUM). 
To identify whether maintenance tasks were performed, you should use the DESCRIBE HISTORY customer statement. 
1) https://learn.microsoft.com/en-us/fabric/data-engineering/delta-lake-time-travel?tabs=sparksql 
2) https://learn.microsoft.com/en-us/azure/databricks/delta/history 
--------------------------------------------------------------------------------------------------------------------------
