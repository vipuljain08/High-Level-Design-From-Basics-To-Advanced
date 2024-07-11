# What is the CAP Theorem
The CAP theorem says that a distributed system can deliver only two of three desired characteristics: consistency, availability and partition tolerance (the ‘C,’ ‘A’ and ‘P’ in CAP).

## Consistency
* Consistency means that all clients see the same data at the same time, no matter which node they connect to. 
* For this to happen, whenever data is written to one node, it must be instantly forwarded or replicated to all the other nodes in the system.

## Availability
* Availability means that any client making a request for data gets a response.
* Therefore all working nodes present in the distributed system all response for any request without exception.

## Partition tolerance
* Partition means a communication break between the two nodes in a distributed system - a lost or temporary delayed. 
* Partition tolerance means that the cluster must continue to work despite any number of communication breakdowns between nodes in the system.

# Implementation of CAP theorem in Distributed Database Systems

### CP database:
> A CP database delivers consistency and partition tolerance at the expense of availability. When a partition occurs between any two nodes, the system has to shut down the non-consistent node (i.e., make it unavailable) until the partition is resolved.

### AP database:
> An AP database delivers availability and partition tolerance at the expense of consistency. When a partition occurs, all nodes remain available but those at the wrong end of a partition might return an older version of data than others. (When the partition is resolved, the AP databases typically resync the nodes to repair all inconsistencies in the system.)

### CA database: (Not Possible in DS)
> A CA database delivers consistency and availability across all nodes. It can’t do this if there is a partition between any two nodes in the system, however, and therefore can’t deliver fault tolerance.

*In a Distributed Database System, where the database nodes are spread across the network therefore in that case the distributed system can be either **Available** or **Consistent**. It cannot live without Partition Tolerance.*