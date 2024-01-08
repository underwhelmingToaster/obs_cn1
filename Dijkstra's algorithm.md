An algorithm that calculates the shortest Path from one node to another.
![[dijkstra01.jpg]]

> [!tldr] Basic working Principle
> 1. Set cost for all nodes to infinity, except starting node to 0. Set starting node as active
> 2. **Update Estimates**
> 	![[dij02.jpg]]
> 	1. Mark the active node as explored
> 	2. From the active node, calculate the cost to reach neighbours by adding (_active node cost_) + (_path cost to neighbour_).
> 	3. If the calculated value for a neighbours is lower than the one it currently possesses, set calculated cost as new one.
> 3. **Choose next node**
> 	![[dij03.jpg]]
> 	1. The next node will always be the node that currently has the lowest cost and is still unexplored
> 4. As soon as the node to reach is marked as explored, the algorithm can be terminated

> [!Warning] Data to Store
> For each node, the best path cost has to be stored. To retrace the best path after the algorithm has finished, the path which allows this connection has to be stored as well
