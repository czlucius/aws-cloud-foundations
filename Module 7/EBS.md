# Amazon EBS
[Student Guide](https://awsacademy.instructure.com/courses/45181/modules/items/3885315)
## About
Persistent block storage volumes for use with EC2.
Persistent/non-volatile
- able to retain data after being shut down
Automatically replicated within AZ to protect from component failure   

Consistent, low latency perf
Scale usage up/down in min, paying as you go.

## vs. Object Storage
When changing a character in a large file:

|Block|Object|
|------|-------|
|Change 1 block that contains the character|Entire file must be updated|
![image](/Pasted%20image%2020230628145755.png)
## Information
- create indiv. storage volumes, and attach to EC2.
- Volumes auto replicated within AZ
- Low latency storage to EC2
- **Can be** Backed up to S3 (thru snapshots)

### Uses
- Boot volumes, storage for EC2
	- Using AMIs
- Data storage within FS
- DB Hosts
- Enterprise apps

## Types
- Provisioned IOPS SSD
- General purpose SSD
- HDD
Only **SSDs** can be used as boot volumes

## Snapshots
> How snapshots are stored: 
> - On the 1st time, a baseline snapshot is stored
> - Subsequently, only diffs between latest and baseline is stored

- Point-in-time snapshots
- Can recreate a volume anytime
- Share snapshots anywhere around the world
## Encryption
EBS Volumes are encrypted at no extra cost 
<strike>$ extra cost $</strike> 
## Elasticity (Elastic Volumes) [^1] 
- Change the following
	- Capacity/size
	- Type (SSD, HDD, etc.)
	- IOPS
	- Throughput (`gp3` only)
- Dynamically change without detaching (hence, without shutting down the EC2)
> NOTE: a boot volume cannot be changed without stopping and starting the associated EC2 Instance.

## Key takeaways
![image](/Pasted%20image%2020230628150711.png)
[^1]: https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/requesting-ebs-volume-modifications.html
