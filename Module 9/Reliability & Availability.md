# Reliability
Probability that your system will function as intended for a specified period.

> **Mean time between Failures (MTBF)**
> A common failure measurement statistic.
>
>MTBF = MTTF + MTTR
>- MTTF = Mean Time To Failure
>- MTTR = Mean Time to Repair


# Availability
Normal operation time
$(uptime)/(total time)$
Number of 9s
- 5 9s means 99.999 % availability

If application is not operating normally, including **scheduled** interruptions and unscheduled, availability is reduced.

## High availability
![Hi avail](/Pasted%20image%2020230705110447.png)

## Tiers
![Tiers](/Pasted%20image%2020230705110653.png)  
Depends on your plan.


## Factors
- Fault Tolerance
	- Built-in redundancy of an app's components & ability to remain operational
- Scalability
	- accomodate increase in capacity needs
- Recoverability
	- ability to restore a service quickly during disaster
	- without lost data
