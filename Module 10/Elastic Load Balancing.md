# ELB
- a load balancer to distribute traffic.

## What does it do?
- Distributes incoming app/network traffic across multiple targets in 1 or multiple AZs
- Horizontal scaling
	- Auto scales load balancer as app changes
- Distribute the load evenly among servers

## Compatible with
- EC2
- Containers
- IP Addresses
- Lambda functions

## Types
OSI - PDNTSPA  
Physical, Data Link, Network, Transport, Session, Presentation, and Application.
> (mnemonic: please do not take sausage pizza away)

- Application Load Balancer (OSI 4)
	- **Ideal for HTTP(S) traffic**
	- Uses SSL to encrypt transmission
- Network Load Balancer
	- Works well for TCP & UDP traffic
	- EC2, Microservice, Containers
- Classic Load Balancer \[LEGACY]
	-  **<u>AWS Recommends that you use a dedicated Application Load Balancer/Network Load Balancer</u>** 


## How ELB works
- Accepts traffic from clients and routes requests to targets (e.g. EC2, Network IP)
- Specify 1 or more listeners
	- A process that checks for connection requests
	- Protocol and port number
- Health checks
	- Only send requests to healthy instances

## Use-cases
- High availability & better fault tolerance
- Auto load balance containerize apps (ECS)
- Autoscale your apps
	- Works with **CloudWatch**, EC2 **Autoscaling**
	- CloudWatch alarms can trigger autoscaling, ELB will register it automatically
- VPC
- Hybrid (AWS & On-prem)
- Invoking Lambda over HTTP(S)

## Load balancer monitoring
- CloudWatch metrics
- Access logs
	- Capture detailed info
	- Store to **S3**
- CloudTrail logs
	- Calls made to ELB API
	- Store to **S3**
