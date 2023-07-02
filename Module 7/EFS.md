# EFS
- Storage that can be accessed by multiple EC2 simultaneously.
- Network File System
- Compatible with Linux based AMIs

https://aws.amazon.com/efs/
https://awsacademy.instructure.com/courses/45181/modules/items/3885315

## Features
- file storage in AWS
- Big data & analytics, media processing, CMS, web serving, Linux home dir
- **Petabyte scale**
- **Low latency**
- Shared storage
- Elastic cap


## Arch

![arch](Pasted%20image%2020230703011849.png)
access EFS within the same VPC, multiple AZs


## Implementation
- Create EC2
- Create EFS filesystem
- **Mount targets in subnets**
- Connect EC2 to mount targets
- Verify resources/protection of acct.

## Resources/Properties
- Filesystem
	- ID
	- Creation token
	- Creation time
	- Size
	- num. mount targets
	- FS State
- Mount target
	- Subnet ID
	- Sec grp
	- filesystem
	- IP for mounting
	- Mount target state
- Tags
	- K-V pairs for metadata

## Key takeaways

![Key takeaways](Pasted%20image%2020230703012245.png)