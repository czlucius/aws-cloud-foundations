A type of storage class of [S3](S3.md).
S3 Glacier is a **data archiving service** that is designed for **security**, **durability**, and **extremely low costs**.

- Ideal for data backup/archival, low cost design
- 11 9s of durability for objects

-


> Base unit of storage = a document
> (any file)

## Security
 - Vault Lock
	- make sure a vault cannot be altered
	- enforced via policies
- Vault Access policy
	- Who can access data and what operations can be performed.

- Encryption
	- (in transit) Supports data encryption thru SSL/TLS 
	- (at rest)
		- Access via IAM (default: only you can access)
		- 

## Retrieval
- 3 options for access
	- Expedited (\$\$\$) - 1-5min
	- Standard (\$\$) - 3-5h
	- Bulk (\$), 5-12h


## Use cases
No upfront cost is required.
- Archiving media assets
- Healthcare info archiving
	- keep for decades
- Regulatory & compliance archiving
- Scientific data archiving
- Digital preservation
	- Regular data integrity checks
	- Self healing
- Magnetic tape replacement


## Interaction
Console
- Creating/deleting vaults
- Managing policies

**REST/(Java/.NET) SDK/CLI:**
- Everything console does
- **Other operations & interactions**  
![glacier access](Pasted%20image%2020230705165047.png)
## Lifecycle policies
Delete/move object based on age

This cycles the data at regular intervals between different storage types. This automation reduces cost -> pay less for what is less important.
https://docs.aws.amazon.com/AmazonS3/latest/userguide/object-lifecycle-mgmt.html

An example:
![lifecycle policies](Pasted%20image%2020230705165109.png)


## Comparison with S3

| |S3|Glacier|
|-|-|-|
|Volume|No limit|No limit|
|Latency|ms|min/h|
|Cost/GB/mo|Higher cost|Lower|
|Billed req|HTTP REST (refer to [^1])|UPLOAD & retrieval|
|Retrieval price|\$|\$\$|
|Encryption|**Optional\***|Default|
> **Note** 
> The video states that S3 is encrypted by default and Glacier is not, which is contradicted by the Student Guide (student guide is factual)
> 
> As per https://aws.amazon.com/about-aws/whats-new/2023/01/amazon-s3-automatically-encrypts-new-objects/, starting 2023 Jan, S3 is also encrypted by default. 
> 
> See https://docs.aws.amazon.com/amazonglacier/latest/dev/DataEncryption.html



## Key takeaways
![key takeaways](Pasted%20image%2020230705171919.png)


[^1]: HTTP REST stands for REpresentational State Transfer, which is used to refer to APIs such as PUT, COPY, POST, LIST, GET, etc... (For more info, do check the HTTP REST specification.)

