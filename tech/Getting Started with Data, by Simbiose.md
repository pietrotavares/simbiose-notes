# Getting Started with Data
Author: Simbiose Ventures<br/>
Category: Data Analysis<br/>
Pages: 211<br/>
Release Date: 2020<br/>

---

## Chapter 1: What is Data
### Key points
1. There's a growing importance on (growing) data, because data can become knowledge after analyzed. Applied knowledge, in turn, usually leads to better decisions.
2. The **'Data Value Pyramid'** illustrates what we can get from data: information, knowledge and,
ultimately, wisdom. Have a look:
![image](https://user-images.githubusercontent.com/79336695/133491867-7cca8784-a194-41a3-8464-cc62344a7bcb.png)

### In-depth
3. Introduces the essential types of data (formally, **'Data Types'**) and skims over the **DATE**, **TIME**, **TIMESTAMP** and some of the possible (and simple) operations regarding them.

## Chapter 2: What is Information
### Key points
1. Data must be contextualized and further interpreted in order to become information.
2. Having data doesn't, necessarily, leads to "now just analyze it and you'll have information". Previous knowledge is required, data *per se* can't have any information.. you need something (or someone) capable of interpreting it (into some context) and, then, analyzing it.

## Chapter 3: How Data is Born
### Key points
1. Establishes the 3 sources of data: it can be **user-generated**, **software-generated** or **hardware-generated**.<br/>It's hard to tell the difference between hardware and software/application-generated data in some cases. For some
realms, like IoT (think of sensors and Smart Home algorithms) we can tell the difference more intuitively though.
### In-depth
2. Elaborates more on **application-generated data** types (e.g., recommended videos from Youtube are **application-generated data**, despite being derived solely from **user-generated data** it is still **only** the *application* that derives this data).
3. An end-to-end example is provided to further illustrate the "onipresence" of data (and what sorts of insights [and analytical action plans] we can get back from analyzing it)

## Chapter 4: How Data is Stored
### Key points
1. Presents the 3 essentials categories of data: **structured**, **semi-structured** and **unstructured** and what challenges, possibilities and limitations lies in efficiently storing and analyzing each of them.<br/>
1.1. Examples of **structured data**: age, name, signup date.<br/>
1.2. Examples of **semi-structured data**: Email messages, CSV, XML.<br/>
1.3. Examples of **unstructured data**: audio samples, videos, pictures.

2. Shows 3 different approaches for storing/organizing data: **via relations (Relational Theory)**, **using graphs** or **in a Data Lake**.<br/>
2.1. **Relational model**:<br/> Records are stored as *tuples* (represented as rows) having one or more *attributes* (represented as columns).<br/> Together, in a table, a group of *attributes* and their *Data Types* define a structure/model we call the *schema*. *Relations* are represented by groups of *tuples*/rows and link data between tables (e.g., in SQL this "link" is usually represented by a *Foreign Key*). There is a predefined set of supported *operations* involving tables. Finally, the logic arrangement of data into *schemas* is done following optimization and good practices (e.g., if there's data duplication in the database, the *normalization* is not being properly app??ied).<br/>
2.2. **Graphs**:<br/>
This approach is, roughly speaking, the "semi-structured data" version of the relational model. There are still schemas and there are still relations, but with more "elasticity" (less rigidity) since there's no SQL (or other implementation of First-Order Logic).<br/>
Instead of formal mathematical rules and rigid relationship/normalization rules, the graph/document-model approach is
way more loosely coupled.
Such "lack of structure" is part of it's design (and one of it's core strenghts).<br/>
2.3. **Data Lakes**:<br/>
Here we have data of all sorts, there are no restrictions as to size, shape, relations or structures. "Organization" is out of the equation, data is simply thrown into this giant data storage.<br/>
As with graphs, the "lack of structure" in this approach is one of it's core strenghts. Since there are no rules and strict models to be followed, using a Data Lake spawns a lot of new possibilities for data analysis technologies and optimization techniques.<br/>
What could be misinterpreted as "the worst and most desorganized way to store data, ever" is actually a brightly promising field of science that is already revolutionizing the way we see and treat data. We call this subset of Data Analysis as "Big Data".

3. Draws the line between Row-Store Databases vs Column-Store Databases and OLTP Databases vs OLAP Databases:<br/>
3.1. **Row-Store** vs **Column-Store**<br/>
First, let's see how **Row-Store data** is represented:<br/>
![image](https://user-images.githubusercontent.com/79336695/133505625-aeaaacef-ac26-40cf-a22f-28d2dbbc11b7.png)<br/>
And how it looks like in the disk:<br/>
![image](https://user-images.githubusercontent.com/79336695/133506305-f160deea-3b7a-483f-9b06-208af2790edb.png)<br/>
Now, see how **Column-Store data** is represented: <br/>
![image](https://user-images.githubusercontent.com/79336695/133506476-788162b1-3cb9-4fc7-9bec-d4c9d159e715.png)<br/>
And how it looks like in the disk:<br/>
![image](https://user-images.githubusercontent.com/79336695/133506539-90b6db60-635e-4cbf-8a92-36ba110946f8.png)<br/>
Keep in mind: disk operations are expensive in time.<br/>
Therefore, "hopping" through various disk sectors when analyzing something is inefficient. When dealing with a large number of records (e.g., 100k or 1M records), this lack of efficiency will result into very long processing times.<br/>
There's no better approach, Row-Store and Column-Store shine in different, somewhat opposing, scenarios/use-cases.<br/>
It boils down to a very **low-level** problem of optimization, therefore it is very complex and has no 'rule of thumb'. But, intuitively, the efficiency goal is: we don't want our cursor to be jumping around like crazy reading different disks sectors and doing heavy math for operations we don't really need.<br/>Ideally, we'd like our cursor to read our disk blocks "in a straight line" while grabbing/analyzing data.. like it already does for some cases (e.g., playing some mp3 file or overwriting a partition with zeros).<br/>
3.2. **OLTP** vs **OLAP**<br/>
Okay, we'd like our cursor to run like Usain Bolt (and not like he was drunk). But that's not the only concern in the data world. Besides speed, another huge concern is with **transactions**. <br/>
Transactions, in most use cases, must be ACID (atomic, consistent, isolated, durable) to prevent data loss, race conditions and the like. **For this use-case OLTP shines**. <br/>
**OLAP, however, shines when the worries are not about transactions/ACID but more about analytical speed**. <br/>
Most of the **OLTP databases are Row-Store** and **OLAP databases Column-Store**.<br/>
3.3. **RDBMS** vs **NoSQL**<br/>
There are approaches for designing/building databases and there are approaches for managing databases. A **RDBMS** (or Relational Database Management System) is a piece of software used to read, insert and perform various operations in a relational database (that is: **managing a relational database**). **NoSQL** is a piece of software for managing non-relational (NoSQL) databases.<br/>
Examples of **RDBMSs**: `PostgreSQL`, `Microsoft SQL Server (MSSQL)`, `MariaDB`, `Oracle Database`<br/>
Examples of **NoSQL databases**: `Amazon DynamoDB`, `Azure Cosmos DB`, `Apache Cassandra`, `Apache CouchDB`, `MongoDB`

### In-depth

4. We are presented with the 4 most famous **types of NoSQL databases**: Document Databases, Key-Value Databases, Graph Databases and Search Engines. <br/>
4.1. **Document Databases**: Data is stored in *JSON documents* and there are no joins (there are no tables, just a bunch of *JSONs*). There are no joins, but there are links: you can't reference one document from another, but you can embed a document into another one. <br/>Documents of similar "kind/purpose" are grouped into *Collections*.<br/>
4.2. **Key-Value Databases**: They store key-value pairs, as such:<br/>
![image](https://user-images.githubusercontent.com/79336695/133492406-a35eb245-5d5e-401e-8b60-0bf282f6573b.png)<br/>
In the example above, the `39587942194` after `name_` could be the hash of "John" (derived using some hash function). This is sort of what a hash table (or a hash map) is, in essence.<br/>
N.B., Although hashes are often used they are NOT necessary. Have another example:<br/>
`last_index_fetched: 398340`<br/>
4.3. **Graph Databases**: Based either in *Labeled Properties* or *RDF Triple Stores* containing (1) **entity**, (2) **type of relationship** and (3) **value**. Example:<br/>
![image](https://user-images.githubusercontent.com/79336695/133505536-1bafa2c5-cba7-42e0-82db-05908325e7c7.png)<br/>
Graph Databases usually implement their own query language (e.g., `Cypher` for `Neo4j`). However, the standard query language for *RDF Datasets* is SPARQL.<br/>
Examples of **Graph Databases**: `Neo4j` (not SPARQL-compliant, uses `Cypher`), `GraphDB` (SPARQL-compliant, uses `SPARQL`)<br/>
4.4. **Search Engines**: Instead of focusing on "what the data must look like" (as the relational model does) or "what are the relationships between data" (as the relational model and graphs do), the goal of the search engine is simply to **find the data you want**.<br/>
These engines leverage optimized text-search algorithms, ranking and many other heuristics.<br/>
Examples of **Search Engines**: `ElasticSearch` (returns JSON data), `Google` (returns a list of Web Pages)<br/>

5. Talking about Storage Location, there are 3 options: it can be `On-premises`, `Cloud-based (private or public cloud)` or `Hybrid (a combination of the previous ones)`.<br/>
5.1. **On-premises**:<br/>
Definition: Software runs (and Data is stored) on servers acquired by the company and physically situated inside it's premises.<br/>
Strengths: More freedom as to changing things and providing support. Possible easier time dealing with compliance/regulation.<br/>
Weaknesses: Initial investment. Weaker security. Having more things to manage (that could be delegated to a external provider).<br/>
5.2. **Cloud-based**:<br/>
Definition: Delegating the subject of building, running and maintaining your infrastructure to external specialists and servers.<br/>
Strenghts: Better security. Pay-as-You-Use pricing model. Initial money investment is drastically lower.<br/>
Weaknesses: Vendor lock-in. Account hijacking. Limited control flexibility. Uptime (or storage quota) may not be sufficient for your product.<br/>
5.3. **Hybryd**:<br/>
Definition: Combining both approaches (Cloud + On-premises).<br/>
Strenghts: Higher level of system adecquacy to your business/infrastructure needs.<br/>
Weaknesses: Added complexity, since you might need to develop your own integrations and manage two infrastructures. Higher possibility of future 'surprises' and other bumps on the road.<br/>

## Chapter 5: How Data is Analyzed
### Key points
1. We're introduced to the concept of **Data Analytics**: a set of techniques and tools for processes for data discovery, exploration, interpretation, pattern identification and information extracting based on statistical concepts/operations and enhanced with computation tools.<br/>
In short, **Data Analytics** are all the things we do in order to get insights from data.
2. Next, we're presented with the 4 main categories of analysis (in ascending order of difficulty/value): Descriptive, Diagnostic, Predictive, Prescriptive.<br/>
2.1. **Descriptive Analysis**:<br/>
Doesn't try to provide reasons or solutions, they are way closer to being factual evidence than being insightful knowledge or wisdom.<br/>
Examples of **Descriptive Analytics**: What percentage of users opens our email messages? Did we make more or less money than the mean value for the previous 6 months?<br/>
2.2. **Diagnostic Analysis**:<br/>
Provides reasons for "something that happened".<br/>
Examples of **Diagnostic Analytics**: Only 10% of users opens our emails because X? Our revenue for this month was lower than the mean value for the previous 6 months because Y happened.<br/>
2.3.**Predictive Analysis**:<br/>
Diagnostic Analysis are somewhat "derived" from Descriptive Analysis, that is, some event must happen first (and we must acknowledge it via Descriptive Analysis) for us to, then, perform Diagnostic Analysis.<br/>
Predictive Analysis, however, doesn't depend on "past events". Therefore, it can 'foresee' future events (that may have never occurred before).<br/>
Examples of **Predictive Analysis**: Will soy prices rise or fall next month? How strong will the upcoming Atlantic hurricane season be?<br/>
Can be enhanced with Machine Learning algorithms.<br/>
2.4. **Prescriptive Analysis**:<br/>
Instead of just 'foreseeing' the future, the goal of this analysis is to provide us with an action (or a set of actions) in order to make some tangible event happen.<br/>
Example of **Prescriptive Analysis**: What actions should be taken in order to grow the company's revenue by 10% in the next quarter?<br/>
Can be enhanced with Machine Learning algorithms.
### In-depth
3. A **Machine Learning algorithm** can be defined as: some set of algorithms, statistical functions and heuristics applied to (1) classify existing data and (2) discover what characteristics of each record contributed to the result.<br/>
4. Feeding data into a machine learning algorithm is called **modeling**. After doing it, we can say that **our data has been modeled**.<br/>
4.1. **Unsupervised learning**: Algorithms that don't leverage values from past data to learn from (e.g., *clustering* algorithms).<br/>
4.2. **Supervised learning**: Algorithms that learn how the previous results were achieved and tries to guess similar results for future (or simulated) records.<br/>
4.2.1 **Linear regression**: Algorithms that try to model the association of two variables, so having one of them is possible to predict the other.<br/>
4.2.2. **Logistic regression**: Algorithms that learn how old records were classified and guesses future classifications for new records.<br/>
5. **Data Visualization**:<br/>
Encompasses **representing data and it's relationships in a graphical way**. Ideally, it should also communicate key aspects of data in an intuitive and effective way.<br/>
The goal of data visualization is to make data analysis more palatable, easily presented and, therefore, more actionable.<br/>
Examples of **visualizations**: *timelines*, *distributions*, *correlations* (e.g., *scatter plots*), *part-to-whole* (e.g., *pie charts*)<br/>
6. **Technology for analytics**:<br/>
Don't forget the main objective behind all this: **to become data-driven**. In light of this objective, providing a space where data is (centrally) available will help tremendously in developing a **data-driven culture**.<br/>
That's why a **central storage for data** (usually geared towards to Analytics, like an OLAP database) is essential. However, there is more than one option for a central storage and choosing the most appropriate one is vital.<br/>
This choice will depend mostly on the structure of your data and there's no rule of thumb. But there is a general guideline: **Data Warehouses** for mostly structured data and **Data Lakes** for mostly unstructured data.<br/><br/>
6.1. **Data Warehouse (DW)**:<br/>
Data is superficially **transformed and prepared when loaded**, therefore being ready/trustworthy for analysis.<br/>
6.1.1. **Physical DW**:<br/>
This implementation consists of **putting a new database in place**, by buying/renting hardware and copying data to it etc.<br/>
You get a single-purpose and centralized facility for all your analytics needs but it's not cheap.<br/>
6.1.2. **Logical DW**:<br/>
Think of this implementation as an '*API Gateway* for databases'. It's not a storage. It **is a catalog that links the data you want to 'where it is'**.<br/>
With a physical DW you'd ask "give me this data". With a logical DW you'd ask, instead, "where is this data located, so I can go there fetch it?".<br/>
It's way cheaper than building a physical DW but it will increase the workloads over the databases (that are already processing application requests).<br/><br/>
6.2 **Data Lake**:<br/>
A category of storage where **every type of data can be stored in the same context**.<br/>
N.B., there's nothing stopping you from piping data from the Data Lake into a traditional Data Warehouse and performing the analytics there. In other words, Data Lakes are not a replacement for other databases.. they are, indeed, just another option.<br/>
Strength: Implementing a Data Lake as an *Object Storage* (e.g., Amazon S3) allows applications to connect and use these data sources more naturally (since most programming languages nowadays are, substantially, object-oriented) spawning more options for advanced analytics.<br/>
Weakness: The lack of organization hierarchy allows 'continuous misuses' of the Data Lake to possibly turn it into a *Data Swamp* (a mess), reducing it's analytical power and, therefore, general usefulness.
<br/><br/>
6.3. **Data Lakehouse**:<br/>
This storage paradigm applies the structure of Physical DWs while using the simple and flexible storage of Data Lakes.</br>
Strengths: Reduces costs significantly. Well suited for testing an analytics process.<br/>
Weakness: Operational problems with scalability and security are not as fully addressed as it is on enterprise databases.<br/><br/>
6.4. **Business Intelligence platforms**:<br/>
Tools built to help businesses perform analytics more easily. They wrap powerful visualization tools as well as statistical/analytics functions within user-friendly interfaces.<br/>
Benefits of using a *BI platform* include: shorter reaction times to market changes and *data democratization*, which empowers all members of the organization to provide insights and suggestions based on data (instead of relying heavily on a few executives/technicians experiences).

## Chapter 6: How Data is Managed
### Key points
1. We're introduced to the discipline of **Data Engineering**: building (and running) all infrastructure needed to support data processes and analytics. More than that, besides knowing the ins and outs of the infrastructure and database solutions, Data Engineers must be able to reason about the integrity/trustworthiness (and usefulness, to some degree) of data.<br/>
N.B., unlike *Data Scientists*, it's **not expected from Data Engineers to deliver business insights from data**. However, **data also encompasses application logs (remember?)** so it is, indeed, expected from Data Engineers to reason about, and act upon, insights from some data.. mostly for troubleshooting/optimization purposes, therein.<br/>
2. **Data Pipelines and ETL**:<br/>
We call any **predetermined/automated set of actions new data is submitted to before becoming "ready"** a *Pipeline*. In order to build a pipeline, Data Engineers must first know what are the business questions and necessities to be addressed by the analytics. In short, it's not a "technical-only" task.<br/>
Pipelines typically consist of 3 actions: **Extract, Transform, Load (ETL)**. Logically, data is first **extracted** from some source then **transformed** until becoming ready to be **loaded** into analytics tools/databases.<br/>
3. **Data Democratization and Data Governance**:<br/>
The goal of data democratization is to empower people (and their decision making) by making data more easily and quickly accessible to them.<br/>
The problem is: "what about sensitive data?". That's where *Data Governance* comes in.
4. **Data Governance frameworks**:<br/>
Memorize these two mnemonics in order to help you remember which scopes are addressed by a *Data Governance framework*: **mostosecin** and **domamequa**.<br/>
*mostosecin* stands for data **mo**deling, **sto**rage, **sec**urity and **in**tegration.<br/>
*domamequa* stands for **do**cumentation, **ma**in source of truth, **me**tadata and **qua**lity.<br/>
5. **Tips to perform a good Data Auditing**:<br/>
Map your processes and important/sensitive data. Also, never follow your arbitrary assumptions about the transformations and ETL processes on your data.. constantly ask questions!
Leverage tools such as: *metadata catalogs*, *data modification history* and *data access logs*.<br/>
Have someone (or some department) dedicated exclusively to *data quality* concerns, keep data with very different natures separate in different *data hubs*.
6. **Data Quality**:<br/>
Memorize these two mnemonics in order to help you remember what characteristics drive Data Quality: **compac-convac** and **prelinerep**<br/>
**compac-convac** stands for **comp**leteness, **ac**curacy, **con**sistency, **v**alidity, **ac**cessibility.<br/>
**prelinerep** stands for **pre**cision, **line**age and **rep**resentation.<br/>

## Exercises
1. **How can we turn *data* into *wisdom*? Elaborate.** (hint: 3 steps)<br/>
2. **What are the 6 basic data types?**<br/>
3. **Give two examples of:**<br/>
??? user-generated data<br/>
??? software-generated data<br/>
??? hardware-generated data<br/>
4. **Give two examples of:**<br/>
??? structured data<br/>
??? semi-structured data<br/>
??? unstructured data<br/>
5. **How are records stored in the *Relational model*? How are *relationships* represented?**
6. **Enunciate a scenario where a *document-model database* is better than a *relational database* but worse than a *graph database*. Justify your answer.**
7. **Enunciate a scenario where a *key-value database* is better than a *document database* but worse than a *search engine*. Justify your answer.**
8. **Which of the following statements are true?**<br/>
??? [ ] *Data lakes* can't hold structured data as they only support unstructured and semi-structured data.<br/>
??? [ ] *Row-stored data* allows fast analytics workloads and are, therefore, the standard in *data lakes*.<br/>
??? [ ] A *data lakehouse* has, generally, fewer chances of turning into a *data swamp* compared to a *data lake*.<br/>
??? [ ] Opting for a *data lakehouse* will address operational problems with scalability and security but will also increase costs significantly.<br/>
??? [ ] Implementing a *logical data warehouse* is cheaper than a *physical data warehouse* but will increase the workload over preexisting databases.<br/>
9. **Fill the blanks with, either: `relational database`, `graph database`, `key-value database`, `document-model database` or `search engine`**<br/>
??? Neo4j is a `________`.<br/>
??? MongoDB is a `________`.<br/>
??? Amazon Aurora is a `________`.<br/>
??? Redis is a `________`.<br/>
??? Apache Cassandra is a `________`.<br/>
??? Amazon DynamoDB is a `________` and a `________`.<br/>
??? MariaDB is a `________`.<br/>
??? memcached is a `________`.<br/>
??? Amazon Neptune is a `________`.<br/>
??? Apache CouchDB is a `________`.<br/>
10. **What can we find about our data by applying *linear regression*?**
11. **Can we label *logistic regression* as a type of *predictive analysis*? Justify your answer.**

## Solutions
TODO
