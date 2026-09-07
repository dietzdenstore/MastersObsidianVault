# Slides
![[Lecture 1 - Introduction.pdf]]
# How would you solve this?
	You have to receive 1 PB of data
	Process it on the fly while you receive it
	You have to store all of the data
	You have to run analytics on this data with a response time of maximum 3 minutes

## One way to solve this problem:
![[Pasted image 20260907141655.png]]
# The Apache Stack (Diagram)
![[Pasted image 20260907141731.png]]
# **Production Metrics and Concepts**

## SLA - Service Level Agreement
The agreement you make with your clients or users
	E.g. "99.9% uptime, or you get credited."
## SLO - Service Level Objectives
The objectives your team must hit to meet that agreement
	E.g. "99.95% uptime" (buffer before breaching the SLA).
## SLI - Service Level Indicators
The real numbers on your performance
	E.g. "Uptime this month: 99.97%."
## Availability = 
$$
\frac{MTBF}{MTBF+MTTR}
$$
**Incident Metrics**
	**MTBF** 
		Mean Time Between Failures
	**MTTD** 
		Mean Time to Detect
	**MTTR** 
		Mean Time to Recovery / Repair / Response / Resolve
	**MTTA**
		Mean Time to Acknowledge
## Error Budget
![[Pasted image 20260907142454.png]]
## Severity Levels
![[Pasted image 20260907142404.png]]

## Non-functional Requirements
- ### **Availability**
	![[Pasted image 20260907142142.png]]
- ### **Deployability**
	![[Pasted image 20260907142216.png]]
- Energy Efficiency
- Integrability
- **Modifiability**
	![[Pasted image 20260907142243.png]]
- Performance
- Safety
- Security
- Traceability
- Testability
- Usability
- Documentation
# **Big Data - What and Why?**

Big Data is defined in three Vs:

**Volume**
	Large amounts of data
**Variety**
	Data comes in different forms - or from different sources - including databases, images, documents and complex records
**Velocity**
	The content of the data is constantly changing, through the absorption of complementary data collection, through the introduction of previously archived data or legacy collections, and form streamed data arriving from multiple sources

![[Pasted image 20260907142531.png]]
## Horizontal vs Vertical scaling
![[Pasted image 20260907142545.png]]