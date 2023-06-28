[Student Guide](https://awsacademy.instructure.com/courses/45181/modules/items/3885326)

## About
Amazon Aurora is a MySQL & PostgreSQL compatible relational DB for the cloud.
(it only supports MySQL and PostgreSQL.)
It is a relational DB engine[^1] available for use in Amazon RDS.
## vs. RDS
Amazon Aurora is a relational database engine like PostgreSQL and MySQL, and can be used in RDS.
<img src="https://intellipaat.com/blog/wp-content/uploads/2019/05/Database-engines.png" height="300">

## Benefits
### Highly available by design
Built on a fast distributed storage subsystem, Amazon Aurora offers high availability, ideal for large relational database sets.
### Compatible
Drop-in compatibility with MySQL and PostgreSQL - no/little change is needed
### Pay as you go
Only pay for services and features you use
### Managed service
Works seamlessly with AWS DB Migration Svc & AWS Schema Conv. tool

## High availability
- Storing copies of data across diff AZs
- Backed up to S3
- Up to 15 read replicas -> increase perf
## Resilient design
- Instant crash recovery
- Does not need to replay redo log
	- already performed on every read operation
- Reduces restart time to <= 60s
- moves the buffer cache from the DB process -> buffer available immediately aft. restart -> reduces the need for you to throttle access until the cache is repopulated to avoid brownouts


## Key Takeaways
![](Pasted%20image%2020230628142902.png)

[^1]: https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html
