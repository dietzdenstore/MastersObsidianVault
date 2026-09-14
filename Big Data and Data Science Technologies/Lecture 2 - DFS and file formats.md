# Terms

## ETL vs ELT vs EtLT

![[Pasted image 20260914122340.png]]
### ETL
Transform before you land it. The warehouse only ever sees data that already fits the schema, and you pay for that compute yourself.
### ELT
Land it now, transform in place. Practical once storage got cheap and the warehouse grew a compute engine of its own.
### EtLT
The pragmatic middle. Mask the personal data and fix the encodings before it lands; leave the business logic for later.


## Data Warehouse / Lake / Lakehouse (and Data Mesh)

Data lake = A place where you can store data

![[Pasted image 20260914122643.png]]
## Typical structure, and the usecases it misses 
![[Pasted image 20260914122549.png|640]]
## Data Lake zones
![[Pasted image 20260914122929.png|640]]

### The five zones are one pipeline
![[Pasted image 20260914123249.png|640]]

| Landing                                           | Raw                                                                   | Standardized                                                                    | Curated                                                              | Sandbox                                          |
| :------------------------------------------------ | :-------------------------------------------------------------------- | :------------------------------------------------------------------------------ | :------------------------------------------------------------------- | :----------------------------------------------- |
| Transient. Data lands as it arrives, unvalidated. | Valid data, still in its **native format**, filed by source and date. | **One** format for<br>everything. Optional, but it is what makes Curated cheap. | Cleansed, joined, partitioned by **subject area**. Ready to consume. | One folder **per project**, for data scientists. |
# Hadoop and HDFS

## What sits on top of Hadoop?
![[Pasted image 20260914124214.png]]
**Hadoop is not one program.** <span style="color:rgb(0, 112, 192)">HDFS</span> keeps the blocks, <span style="color:rgb(0, 112, 192)">YARN</span> hands out the cluster’s CPU and memory, and <span style="color:rgb(0, 112, 192)">MapReduce</span> is one of the engines that asks <span style="color:rgb(0, 112, 192)">YARN</span> for them. The same elephant stands for all three.

Everything in the top row **computes**. Where it needs durable storage it goes to <span style="color:rgb(0, 112, 192)">HDFS</span>, over the protocol the next slides work through. <span style="color:rgb(0, 112, 192)">Kafka</span> is the exception: it keeps its own log.

<span style="color:rgb(0, 112, 192)">ZooKeeper</span> stands beside the stack rather than in it. It holds the few pieces of state the others have to agree on, such as which of two masters is the live one.

<span style="color:rgb(0, 112, 192)">Flume</span> and <span style="color:rgb(0, 112, 192)">Sqoop</span> only move data in. Logs and event streams come through one, tables out of a relational database through the other.

### The stack as you meet it today
![[Pasted image 20260914124736.png]]
## DFS design: 

### chunks
Files larger than a disk (> 1 TB) cannot be stored whole, so a DFS divides every file into **chunks** of 64 or 128 MB
![[Pasted image 20260914124908.png]]

- each chunk is identified by a unique **64-bit chunk handle**
- data is read by giving a chunk handle and a byte range
- a chunk is just **an ordinary Linux file** on the chunk server, with no special storage layer underneath it
- a **large** chunk size is what makes storing big files cheap: fewer handles to track, fewer round trips to the master

### redundancy
Since cluster components fail, store all data redundantly:
- typically 3 chunk replicas, on different machines, on different racks
- if one copy is unreachable, read another copy

**To implement redundancy, you need two things**
**Metadata** for each file, mapping the file onto its chunks, and a **master** for the DFS to maintain that metadata Which is the whole design: everything after this slide is a consequence of having one master that knows where everything is.

## LFS vs DFS
![[Pasted image 20260914125256.png]]

![[Pasted image 20260914125314.png]]

## The Hadoop setup
![[Pasted image 20260914125345.png]]
**Storage** and **compute** sit on the **same machine**, on purpose: it is far cheaper to move the program to the data than the data to the program. 

One <span style="color:rgb(255, 0, 0)">coordinator</span>, many identical <span style="color:rgb(0, 112, 192)">workers</span>: the classic <span style="color:rgb(255, 0, 0)">master</span>/<span style="color:rgb(0, 112, 192)">slave</span> pattern, which you will meet by that name across databases, brokers and schedulers. Hadoop’s own config renamed the <span style="color:rgb(0, 112, 192)">slaves</span> file to <span style="color:rgb(0, 112, 192)">workers</span> in version 3, so you will see both

## The NameNode (<span style="color:rgb(255, 0, 0)">the</span> <span style="color:rgb(255, 0, 0)">master</span>)
![[Pasted image 20260914125623.png]]

- A single, global NameNode, and therefore a bottleneck.
- All metadata is kept in memory, which is what makes it fast. Most of it is also logged to disk for reliability.
- Except the block locations. The NameNode does not store them. It asks the DataNodes at startup, and they tell it. A truth you can re-derive
never has to be kept consistent.

**The GFS paper you read calls these by other names. Same design, different words:**  NameNode = **master** 
DataNode = **chunk server** 
block = **chunk**

### HDFS: A read operation
![[Pasted image 20260914125843.png]]
Then it repeats, block by block, and the NameNode is not asked again, because the client cached the locations. **User data never flows through the NameNode**: it is asked for addresses, and every byte moves directly between the client and a DataNode.

- Important to read from the closest replica

### HDFS: A write operation
![[Pasted image 20260914130058.png]]
**Why a pipeline, and why that order**
Each forwards a packet while **still receiving it**, so three copies cost little more than one. Placement is not random either: one replica on the writer’s rack, two on **one other**, so the pipeline crosses racks exactly **once**.

**What one slide cannot show**
This is **one block;** a file is many, each with its own ``pipeline.close()`` returns once **minimum** replication is met. The NameNode backfills the rest. [Animated Walkthrough](https://data-flair.training/blogs/hdfs-data-write-operation/)

## What a DFS is cheap at, and what it is not
![[Pasted image 20260914130416.png]]


# File Formats: Avro and Parquet

## Difference between them:

Both are **binary**, **splittable**, **compressed** formats carrying their **own schema** and allowing it to **evolve**. They are not rivals; they differ in one decision, and even the **compression** follows from it:

Two rows, ``(1, Ana, Odense)`` and ``(2, Bo, Aarhus)`` , laid out on disk:
![[Pasted image 20260914132503.png|396]]
Avro writes a **row** at a time; Parquet writes a **column** at a time. The rest is arithmetic.

| Avro - (row-based)                                         | Parquet (column-based)                                              |
| ---------------------------------------------------------- | ------------------------------------------------------------------- |
| cheap to read or write a whole record                      | cheap to read a few columns of very many rows                       |
| so: streaming, exchange and ingestion, one event at a time | so: analytics, scans and aggregates over wide tables                |
| schema as JSON at the head of the file                     | schema in the footer: one pass to write, one seek to read           |
| compresses a block of records at a time                    | compresses each column separately: one type, so it packs far harder |
| evolution may change existing fields                       | evolution may add columns, not change them; good at nested data     |
![[Pasted image 20260914132739.png]]

![[Pasted image 20260914133332.png]]
![[Pasted image 20260914133340.png]]

## Avro


## Parquet