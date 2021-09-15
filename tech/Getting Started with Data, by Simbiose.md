# Getting Started with Data
Author: Simbiose Ventures<br/>
Category: Data Analysis<br/>
Pages: 211<br/>
Release Date: 2020<br/>

___

## Chapter 1: What is Data
### Key points
1. Draws the (growing) importance of (growing) data,<br/>..because data can become knowledge! (after analyzed)..
2. Uses the **'Data Value Pyramid'** to illustrate and explain what we can get from data: information, knowledge and,
ultimately, wisdom.
3. [IN-DEPTH] Introduces the essential types of data (formally, **'Data Types'**) and skims over the **DATE**, **TIME**, **TIMESTAMP** and some of the possible (and simple) operations regarding them.

## Chapter 2: What is Information
### Key points
1. Data must be contextualized and further interpreted in order to become information.
2. Having data doesn't, necessarily, leads to "now just analyze it and you'll have information". Previous knowledge is required, data *per se* can't have any information.. you need something (or someone) capable of interpreting and analyzing it.

## Chapter 3: How Data is Born
### Key points
1. Establishes the 3 sources of data: it can be **user-generated**, **software-generated** or **hardware-generated**.<br/>It's hard to tell the difference between hardware and software/application-generated data in some cases. For some
realms, like IoT (think of sensors and Smart Home algorithms) we can tell the difference more intuitively though.
2. [IN-DEPTH] Elaborates more on **application-generated data** types (e.g., recommended videos from Youtube are **application-generated data**, despite being derived solely from **user-generated data** it is still **only** the *application* that derives this data).
3. [IN-DEPTH] An end-to-end example is provided to further illustrate the "onipresence" of data (and what sorts of insights [and analytical action plans] we can get back from analyzing it)

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
way more loosely coupled. In effect, there are, even, little to none "formal" mathematical models or theories involved.<br/>
Such "lack of structure" is part of it's design (and one of it's core strenghts).<br/>
2.3. **Data Lakes**:<br/>
Here we have data of all sorts, there are no restrictions as to size, shape, relations or structures. "Organization" is out of the equation, data is simply thrown into this giant data storage.<br/>
As with graphs, the "lack of structure" in this approach is one of it's core strenghts. Since there are no rules and strict models to be followed, using a Data Lake spawns a lot of new possibilities for data analysis technologies and optimization techniques.<br/>
What could be misinterpreted as "the worst and most desorganized way to store data, ever" is actually a brightly promising field of science that is already revolutionizing the way we see and treat data. We call this subset of Data Analysis as "Big Data".

3. Draws the line between Row Store Databases vs Column Store Databases and OLTP Databases vs OLAP Databases:<br/>
3.1. **Row Store** vs **Column Store**<br/>
"Row-Store's Arrangement"
```
Name    Age    Job
John    38     Engineer  [row 1]
Mary    29     Astronaut [row 2]
Greg    23     Plumber   [row 3]
```

"How data looks like after being Row-Stored in the disk"

```
DISK{#1[Name, Age, Job], #2[John, 38, Engineer], #3[Mary, 29, Astronaut], #4[Greg, 23, Plumber]}
```

"Column-Store's Logic Arrangement"

```
[name,column 1] [age,column 2] [job,column 3]
   John              38            Engineer
   Mary              29            Astronaut
   Greg              23            Plumber
```

"How data looks like after being Column-Stored in the disk"

```
DISK{#1[Name], #2[Age], #3[Job], #4[John, Mary, Greg], #5[38, 29, 23], #6[Engineer, Astronaut, Plumber]}
```

<br/>

Keep in mind: disk operations are expensive in time.<br/>
Therefore, "hopping" through various disk sectors when analyzing something is inefficient. When dealing with a large number of records (e.g., 100k or 1M records), this lack of efficiency will result into very long processing times.<br/>
There's no better approach, Row-Store and Column-Store shine in different, somewhat opposing, scenarios/use-cases.<br/>
It boils down to a very **low-level** problem of optimization, therefore it is very complex and has no 'rule of thumb'. But, intuitively, the efficiency goal is: we don't want our cursor to be jumping around like crazy reading different disks sectors and doing heavy math for operations we don't really need.<br/>Ideally, we'd like our cursor to read our disk blocks "in a straight line" while grabbing/analyzing data.. like it already does for some cases (e.g., playing some mp3 file or overwriting a partition with zeros).<br/>

3.2. **OLTP** vs **OLAP**<br/>
Okay, we'd like our cursor to run like Usain Bolt (and not like he was drunk). But that's not the only concern in the data world.<br/>
Besides speed, another huge concern is with **transactions**. Transactions, in most use cases, must be ACID (atomic, consistent, isolated, durable) to prevent data loss, race conditions and the like. **For this use-case OLTP shines**. <br/>
**OLAP, however, shines when the worries are not about transactions/ACID but more about analytical speed**. 

