Link State Routing allows all Routers in a Network to have an exact overview of the whole network and each of its nodes/paths.

> [!example] Link State Routing Protocols
> - OSPF
> - IS-IS

## Definition
- **Link State Advertisement (LSA)**: Contains either Router Link Information or Stub Network Information. Each LSA also contains a sequence number with which routers can decide if they have already seen this LSA or not.
	- **Router Link Information**: Advertises adjacent neighbours in a (Router ID, Neighbour ID, Cost) format.
		![[router link information.png]]
	- **Stub Network Information**: Advertises stub networks (networks with no router) in a (Router ID, Network ID, Cost) format.
		![[stub network information.png]]
- **Link State Database (LSDB)**: Saves current LSAs. Each router maintains one. Using this database, each router can reconstruct the entire network.

## Process
The process will be explained using the principles of OSPF. However, other Link State Protocols function comparably.

### 1. Become Neighbours
- Adjacent nodes send "Hello" Messages to agree on timers, capabilities etc.
- Once adjacency has been established, Messages (keepalives) are continuously sent (Hello Interval: 10s interval)
	- Links are considered dead if keepalives are not sent for extended time (Dead Interval: 40 sec.)

### 2. Exchange Database Information
- Sent to adjacent neighbours in case of topology change
- Each router forwards all LSA once.

### 3. Choose best route
- To find the route, [[Dijkstra's algorithm]] is employed
