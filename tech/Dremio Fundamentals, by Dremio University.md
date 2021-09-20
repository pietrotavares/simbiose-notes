# Dremio Fundamentals

## Datasets
### **Dremio key objects**
#### Data Source
Any supported data source (e.g., `Amazon S3`, `Microsoft SQL Server`, `ElasticSearch`, `MongoDB`, `Hive`)
You can find a list of all available data sources at: [https://docs.dremio.com/rest-api/catalog/container-source-types/](https://docs.dremio.com/rest-api/catalog/container-source-types/)
> By the time of writing, ADLS Gen 2 is not supported.
#### PDS 

Also called **promoted data files**.<br/>
Supported formats: CSV/Excel/XLS, JSON, Parquet, ORC.<br/>
A file (or group of files that share a common schema) that either (1) came from a configured *Data Source* or (2) was uploaded. **Immutable**.<br/>
PDS' usually have restricted access since it's files might contain sensitive information.<br/>
> Ways to create a PDS: (1) upload a file to Dremio and save the file as a PDS; (2) promote a file from a data source and save as a PDS; (3) enable *auto-promotion* in the Dremio Source, then query the dataset.
#### VDS
#### Reflection
#### Space
#### Home space
#### Folder

