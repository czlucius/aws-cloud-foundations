[Student Guide](https://awsacademy.instructure.com/courses/45181/modules/items/3885326)

AWS RDS is a Relational Database Service, a.k.a. a service for structured SQL databases.
It uses MySQL, PostgreSQL, etc.
## Managed vs Unmanaged services
- EC2 vs RDS
- EC2 is an unmanaged solution.
Challenges of self hosting or using EC2 to host relational DB:
- Server maintenance
- S/W installations
- Backups and availability
- Scalability 
- Security
- OS install


## Deployment
Generally, RDS is launched in private subnets, as sensitive data may be within RDS. This is within a VPC (Virtual Private Cloud).
RDS is launched as DB instances in AWS Cloud.  
![image](/Pasted%20image%2020230628105537.png)

### Availability
High availability can be achieved by using a Multi-AZ deployment.
AWS autogenerates a standby copy of the DB in another AZ in the same VPC. 
Transactions are synchronously replicated to the standby copy.
This can help to enhance availability when there's **system maintenance, DB instance failure and AZ disruption.**    
![image](/Pasted%20image%2020230628105520.png)

### Read replicas
- For MySQL, MariaDB, Postgres, Aurora
- Updates to source DB instance are async. copied to read replica instance
- **Reduce the load on source DB**
- Scale beyond capacity constraints
- Can be created in a different region  
![image](/Pasted%20image%2020230628103811.png)

## Use cases
- Web & Mobile
- E-commerce
- Mobile & online

## When to use?
### Use when:
- Complex Transcations/queries
- Medium-high query/write rate (max. 30,000 IOPS)
- Max 1 worker node/shard.
	- [Partition](https://en.wikipedia.org/wiki/Shard_(database_architecture))
	- 1 DB with multiple partitions (like subroutines)
- High durability.

### Don't use when:
- Massive read/write rate
- Sharding (high data size, throughput demand)
- GET/PUT req/queries - NoSQL DB can handle
- RDBMS customisation

#### What to use instead?
- NoSQL DB e.g. DynamoDB
- Run your Relational DB engine on EC2 - more customisation

## Billing
The DB is billed by the clock-hour, based on characteristics
- Engine (e.g. MySQL)
- Size
- Memory class

## Storage
### Provisioned
- No charge - backup storage for ACTIVE DB.
- Charge (GB/mo) - backup storage for **TERMINATED** DB.
### Additional
- Charge (GB/mo)


## Purchase Type
- On-demand instances
- Reserved instances (1y or 3y)
	- 1y fee always > 3y, no mattery AURI, PURI, or NURI.
Number of DB instances also matter, you can provision multiple instances for peak load.
