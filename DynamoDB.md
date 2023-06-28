[Student Guide](https://awsacademy.instructure.com/courses/45181/modules/items/3885326)
### Short intro: RDB vs non-RDB
![[Pasted image 20230628105858.png]]

## What is DynamoDB?
DynamoDB is a fast & flexible NoSQL DB service for any scale.
![[Pasted image 20230628110915.png]]
> TL;DR: DynamoDB is a NoSQL service. It stores data in a JSON tree.

## Advantages
- Virtually unlimited storage
- Differing attributes
	- Store formats side by side, esp. when doing DB migrations.
- Low-latency
- Scalable R/W
	- Can increase throughput with manual or automatic provisioning dep. on load
- Managed by AWS, High redundancy

## Core Components
- Tables
	- A collection of data
- Items
	- A group of attributes, uniquely identifiable (e.g. a data class)
- Attributes
	- Fundemental data element (e.g. variables in a data class)

Keys supported (this key is used to reference the item)
- Partition key
	- Simple primary key
	- Composed of the sort key
Partition + sort key => **Composite primary key**
See 2nd image below.

## Partitioning
![[Pasted image 20230628111550.png]]
Data is being partitioned by the primary key.
Data can be retrieved in these 2 ways:
1. Query op. takes advantage of partitioning to locate items using primary key
	1. Access the item by using the key as the index????
2. Scanning, locating items with non-key attributes
	1. Less efficient

![[Pasted image 20230628111840.png]]
- Partition key is used for indexing the data.
- Sort key is used for sorting/ordering the data.
- Attributes contain the data.

## Key takeaways
![[Pasted image 20230628111945.png]]