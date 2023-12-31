
![[Routing.png]]
If a message must be dropped, a _Destination Unreachable ICMP_ is sent to the Source of the message.

Routing is done by routers. Each router has a _route table_ which contains:
- [[IP]] Addresses which are directly connected
- [[Subnetting|Subnets]]
- Gateway of Last resort ([[Default Gateway]])
with the corresponding next hop, which contains the Interface Number for directly connected hosts and an IP Address of the next router for subnets.

## Static Routing
Subnets and their next hops are manually configured.

## Dynamic Routing
Dynamic Routing is done by a routing protocol. A routing protocol allows routers to send, receive and forward Routing Updates. This allows the network to determine the quickest path from one point to another. Routing protocols include:
- Routing Information Protocol _(RIP)_
- Interior Gateway Protocol _(IGRP)_
- Open Shortest Path First _(OSPF)_
- Exterior Gateway Protocol _(EGP)_
- Enhanced Interior Gateway Routing Protocol _(EIGRP)_
- Border Gateway Protocol _(BGP)_
- Intermediate System-to-Intermediate System _(IS-IS)_

### Convergence
Convergence is a state of constancy in the network, so that each participating router agrees on the optimal way from one destination to another. Convergence is necessary in any network. If convergence is not achieved, a routing loop can happen.

### Metrics
Metrics define which path is the fastest for reaching one point from another. Metrics vary per routing protocol.

### Load Balancing
The act of distributing large amounts of data with the same destination between different connections to utilize the available bandwidth more efficiently.
