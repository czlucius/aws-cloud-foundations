# Well Architected Framework
[Student Guide](https://awsacademy.instructure.com/courses/45181/modules/items/3885338)
[Video](https://awsacademy.instructure.com/courses/45181/modules/items/3885329)
[Documentation](https://aws.amazon.com/architecture/well-architected/?wa-lens-whitepapers.sort-by=item.additionalFields.sortDate&wa-lens-whitepapers.sort-order=desc&wa-guidance-whitepapers.sort-by=item.additionalFields.sortDate&wa-guidance-whitepapers.sort-order=desc)

A document of best practices for setting up your infrastructure.
The Framework consists 6 pillars.
![Well Archi Framework](Pasted%20image%2020230705102728.png)
> Take note: for quiz questions:
> - Secure
> - High performing
> - Resilient
> - Efficient

## Pillars
1. Operational Excellence
	1. Automate changes
	2. Respond to events
	3. Define standards

- Perform operations as code
	- Use API/SDK as much as possible - manual mgmt prone to human error
- Make small and reversible changes
- Anticipate failure
	- Prepare if e.g. site is down due to AZ failure, so e.g. multiple AZ...
- Learn from operational events & failures
- Refine ops proceedures frequently
![Ops Excellency qns](Pasted%20image%2020230705103856.png)

2. Security
	1. Protect info, syst, assets
	2. Data Confidentiality & Integrity
	3. Protecting systems
	4. Manage who can do what
	5. Establishing controls to detect security events

3. Reliability
> How can you ensure that your processes are reliable?

- Auto recover from failure
	- Monitor systems for key performance indicators and configure your systems to trigger an automated recovery when a threshold is breached.
- **TEST recovery procedures**
	- Expose failure scenarios
- Scale horizontally to increase aggregate workload availability
	- Don't scale vertically - increasing perf/specs of one instance - **This is a single point of failure.**
	- 
- Stop guessing capacity 
	- Monitor usage of resources and automate scaling
- Manage changes with automation
	- Use automation to make infra changes


4.  Performance Efficiency
	1. Democratise advanced tech
		1. As many people as possible are able to do
		2. akin to PCs [democratising technology](https://en.wikipedia.org/wiki/Democratization_of_technology) for the masses
	2. Go global in minutes
		1. Deploy systems in multiple regions (better experience)
	3. Use serverless architecture
		1. Removes operational burden of running/managing servers
		2. Lower transactional cost
	4. Experiment more often
		1. Perform comparative testing
			1. Instances
			2. Storage
			3. Config
			4. etc etc etc
	5. [Mechanical Sympathy](https://wa.aws.amazon.com/wat.concept.mechanical-sympathy.en.html)

![Perf eff. qns](Pasted%20image%2020230705105600.png)

5. Cost optimisation
	1. Cloud Financial Management
	2. Consumption - pay only for what you use
	3. Adopt overall efficiency
	4. Stop spending on undifferentiated heavy lifting
		1. Remove hardware from your premises to save money
	5. Analyse and attribute expenditure
		1. Cloud is easier to identify system usage cost
		2. Measure ROI
![Cost optimisation qns](Pasted%20image%2020230705105941.png)


## Key takeaways
![Takeaways](Pasted%20image%2020230705113503.png)