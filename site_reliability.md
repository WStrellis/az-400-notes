*Software Reliability Engineering (SRE)* - Designing and engineering a system with an appropriate amount of reliability for the service it provides.  

*Service Level Indicator (SLI)* - metrics used to determine the health of a service. These values can be defined in the planning stages of an application.  

*Service Level Objective (SLO)* - metrics which define the expected or desired reliability of a service.  

*Error Budget* - The amount of time a service is allowed to not meet its SLO. This time can be used for things such as upgrades or patches.  

Properties of an Alert
- *Resource* - the resource which triggers the alert
- *Condition* - when to trigger the alert
- *Actions* - do this when the alert is triggered
- *Alert Details* - name, description, severity level

States of an Alert:
- *New* - an issue has been detected but not yet reviewed
- *Acknowledged* - An admin has reviewed the issue
- *Closed* - the issue has been resolved 

Properties of Log Search Rules:
- *Log Query* - the search to perform
- *Time Period* - time range for the query
- *Frequency* - when to run the query
- *Threshold* - point at which an alert is created

Levels Of Replication
- *N+1* - for an app that needs N nodes to function, one extra resource is provisioned as a failsafe.
- *2N* - One extra node is provisioned for every node ( double )
- *2N+1* - All nodes are duplicated, plus extras

*Tail Latency* - In a service which must perform many calculations on many individual servers all of the servers are expected to complete their task within a short period of time. If one of the servers takes an excessive amount of time to complete its work then the final response time to the client will be increased beyond the acceptable amount.

### Load Balancer
- Only handles port-forwarding for TCP and UDP traffic
- Operates on Layer 4 of ISO network stack
- cannot manipulate contents of network packets
- cannot route based on packet content

Which tools can be used to test network connectivity for VMs behind a Load Balancer?  
`PsPing`, `tcping`, and `netsh`. `ping` will not work because it uses an ICMP connection which Load Balancer will not route.   