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
2.1. **Relational model**:<br/> Records are stored as *tuples* (represented as rows) having one or more *attributes* (represented as columns).<br/> Together, in a table, a group of *attributes* and their *Data Types* define a structure/model we call the *schema*. *Relations* are represented by groups of *tuples*/rows and link data between tables (e.g., in SQL this "link" is usually represented by a *Foreign Key*). There is a predefined set of supported *operations* involving tables. Finally, the logic arrangement of data into *schemas* is done following optimization and good practices (e.g., if there's data duplication in the database, the *normalization* is not being properly appĺied).<br/>
2.2. **Graphs**:<br/>
This approach is, roughly speaking, the "semi-structured data" version of the relational model. There are still schemas and there are still relations, but with more "elasticity" (less rigidity) since there's no SQL (or other implementation of First-Order Logic).<br/>
Instead of formal mathematical rules and rigid relationship/normalization rules, the graph/document-model approach is
way more loosely coupled. In effect, there's even little to none mathematical involved.<br/>
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
Graph Databases usually implement their own query language (e.g., `Cypher` for `Neo4j`). However, the standard query language for RDF Datasets is SPARQL.<br/>
Examples of **Graph Databases**: `Neo4j` (not SPARQL-compliant, uses `Cypher`), `GraphDB` (SPARQL-compliant, uses `SPARQL`)<br/>
4.4. **Search Engines**: Instead of focusing on "what the data must look like" (as the relational model does) or "what are the relationships between data" (as the relational model and graphs do), the goal of the search engine is simply to **find the data you want**.<br/>
These engines leverage optimized text-search algorithms, ranking and many other heuristics.<br/>
Examples of **Search Engines**: `ElasticSearch` (returns JSON data), `Google` (returns a list of Web Pages)<br/><br/>

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
