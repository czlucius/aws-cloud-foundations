Redshift is a fully managed data warehouse for **data analysis** using using standard SQL/Business Intelligence(BI) tools.
> Google Cloud equivalent: BigQuery
![[Pasted image 20230628112124.png]]
## Parallel processing architecture

![[Pasted image 20230628112146.png]]
- Leader node manages comms with client programs and compute nodes.
- Compute nodes run compiled code, send intermediate results back to the leader node.
	- (on the data)
- Query against exabytes of data
Highly parallelised arch. makes it fast to query even on a lot of data -> compute nodes will perform queries in parallel on the data.

## Automation/scaling
![[Pasted image 20230628112737.png]]
Automation is easy for common admin task -> manage, monitor, scale clusters
Clusters can be scaled up/down as needs change.

## Compatibility
Redshift supports commonly used tools:
- Standard SQL
- JDBC (Java Database Connectivity)
- ODBC (Open Database Connectivity)

## Use-cases
### Enterprise Data Warehouse
- Migrate at a comfortable pace
- Experiment w/o large upfront cost 
- Respond faster to business needs
### Big Data
- Query massive amounts of data 
	- Small customers may not be able to procure H/W & expertise to run these systems.
- Managed service -> AWS helps to maintain & deploy the DB for you.
	- More on data, less on DB mgmt
## SaaS
- Scale data warehouse capacity as per demand
- Add analytics
- Reduce H/W & S/W cost -> all managed by AWS

## Key takeaways
![[Pasted image 20230628113926.png]]
