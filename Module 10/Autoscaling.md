# Autoscaling

|Before|After|
|-|-|
|![notscaled](Pasted%20image%2020230712104946.png)|![scaled](Pasted%20image%2020230712105005.png)|


## Autoscaling groups
- Logical grouping
- Size depends on *desired capacity*
- Specify number of instances
- Adjusts size of group so it has specified number of instances
- Minimum size
- Desired capacity

## Scale out vs. scale in
![scale out vs scale in](Pasted%20image%2020230712105349.png)
Launching instance -> scale out
Terminate instance -> scale in

## How Amazon EC2 Auto Scaling works
TODO!
![EC2 Autoscaling](Pasted%20image%2020230712105506.png)

## Options
Maintain current instance levels at all times
- Manual scaling
- Scheduled scaling
- **Predictive scaling**
	- learns from past data to predict traffic
- Dynamic scaling
	- Reactive
	- Setup CloudWatch alarm

## AWS Autoscaling
- Separate service from EC2 Auto Scaling