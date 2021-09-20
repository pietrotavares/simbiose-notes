# Dremio Fundamentals

## Datasets
### **Dremio key objects**
#### Data Source
![image](https://user-images.githubusercontent.com/79336695/134027305-4104597b-8d14-4ae4-b943-f6f098125add.png)<br/>
Any supported data source (e.g., `Amazon S3`, `Microsoft SQL Server`, `ElasticSearch`, `MongoDB`, `Hive`).<br/>
The list of all available data sources is at: [https://docs.dremio.com/rest-api/catalog/container-source-types/](https://docs.dremio.com/rest-api/catalog/container-source-types/)
> By the time of writing, ADLS Gen 2 is not supported.
#### PDS 
![image](https://user-images.githubusercontent.com/79336695/134026932-d1a2e349-370d-46d1-8e13-d727b49fe945.png)<br/>
Also called **promoted data files**. **Immutable**.<br/>
Supported formats: CSV/Excel/XLS, JSON, Parquet, ORC.<br/>
A file (or group of files that share a common schema) that either (1) came from a configured *Data Source* or (2) was uploaded.
PDS' usually have restricted access since it's files might contain sensitive information.<br/>
> Ways to create a PDS: (1) upload a file to Dremio and save the file as a PDS; (2) promote a file from a data source and save as a PDS; (3) enable *auto-promotion* in the Dremio Source, then query the dataset.
#### VDS
#### Reflection
#### Space
#### Home space
#### Folder

