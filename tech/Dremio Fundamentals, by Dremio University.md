# Dremio Fundamentals

## Datasets
### **Dremio key objects**
#### **Data Source**
![image](https://user-images.githubusercontent.com/79336695/134027305-4104597b-8d14-4ae4-b943-f6f098125add.png)<br/>
Any supported data source (e.g., `Amazon S3`, `Microsoft SQL Server`, `ElasticSearch`, `MongoDB`, `Hive`)
You can find a list of all available data sources at: [https://docs.dremio.com/rest-api/catalog/container-source-types/](https://docs.dremio.com/rest-api/catalog/container-source-types/)
> By the time of writing, ADLS Gen 2 is not supported.
#### **PDS** (*Physical Datasets*)
![image](https://user-images.githubusercontent.com/79336695/134026932-d1a2e349-370d-46d1-8e13-d727b49fe945.png)<br/>
Also called **promoted data files**.<br/>
Supported formats: CSV/Excel/XLS, JSON, Parquet, ORC.<br/>
A file (or group of files that share a common schema) that either (1) came from a configured *Data Source* or (2) was uploaded. **Immutable**.<br/>
PDS files usually have restricted access since it's files might contain sensitive information.<br/>
> Ways to create a PDS: (1) upload a file to Dremio and save the file as a PDS; (2) promote a file from a data source and save as a PDS; (3) enable *auto-promotion* in the Dremio Source, then query the dataset.
#### **VDS** (*Virtual Datasets*)
Similar to *View* (from SQL), a virtual dataset is defined by an SQL statement.<br/>
Virtual datasets can be saved to your *home space* or to a *shared space*.<br/>
> Create a virtual dataset<br/>
 `CREATE VDS <virtual-dataset-path> AS <sql-query>`<br/>
#### **Shared Space** (or, simply, *Space*)
Directory-like containers for VDS files. Supports authorization/permissions.<br/>
Spaces allow grouping datasets by a common theme (e.g., project, region, owner).<br/>
#### **Home Space**
Private "user-work area" container for both PDS and VDS files.<br/>
Uploaded files go here after being promoted.<br/>
> The *home space* (or *home area*) is automatically created and is the same as your username.
#### **Folder**
Folders can be created both in the *shared space* (if they have permission) or the *home space*.
#### **Semantic Layer**
Allows a *component-based development* approach, increasing reusability of VDSs across multiple projects.<br/>
Dremio recommends starting with 3 semantic layers and customizing it later for your use case. These layers are:<br/>
- **Staging** layer: Closest to the PDS. Performs initial transformations (e.g., data cleansing, filtering/masking of sensitive data etc).<br/>
- **Business** layer: Contains business logic specific to the company's use case, goals and operational metrics.<br/>
- **Application** layer: Focuses on the aggregation and presentation of the information into reports and dashboards. This layer has the broadest availability and links to various external BI or presentation tools.<br/>
#### **Reflection**
Similar to a *Materialized View* (from SQL), a *data reflection* is a physical, optimized, representation of source data.<br/>
In other words: a "reusable cached version of SQL queries" (on steroids).<br/>
A data reflection is always associated with a single dataset, called the *anchor dataset* (which can be a PDS or VDS).<br/>
There are 3 types of *data reflections*:<br/>
- Raw reflections
- Aggregation reflections
- External reflections
> Data Reflections are stored in a high-performance, compressed, columnar representation based on Apache Parquet and Apache Arrow.<br/>

---

## **Data Curation**
### **Type conversions**
Dremio provides several type conversions functions for basic data types (e.g., strings, numbers and dates) via an intuitive graphical wizard.
### **Complex types**
Dremio provides options for curating structs and list-like objects, such as:
- Extracting individual elements (e.g., prices[5]) or sublists (e.g., prices[0:8])
- Flattening/Unnesting list types
- Referencing individual elements in a struct (e.g., `select t1.property_map.field1 from mytable t1`, n.b., aliasing the dataset that contains the nested data is a requirement for this operation)

---

## **Jobs**
A *job* is a discrete task that the cluster performs (e.g., a query from some BI tool, a backload maintenance task).<br/>
Within the jobs interface, there's a history of runned jobs holding it's details.<br/>
![image](https://user-images.githubusercontent.com/79336695/134071672-a2cc0110-5568-4045-a14a-b39fb9bcc416.png)

##
