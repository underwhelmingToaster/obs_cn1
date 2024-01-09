PMTUD can determine the maximum size a packet can have and still travel its whole path in a network without being fragmented.

## Definition
The Internet Protocol defines the _path MTU_ of an Internet transmission path as the smallest MTU supported by any of the hops on the path between a source and destination. Put another way, the path MTU is the largest packet size that can traverse this path without suffering fragmentation.

## Process
- Send packets with the [[IPv4#Composition|DF]] (Don't Fragment) bit set
- If any device in the path has a smaller [[MTU]], it will send an _[[ICMP|ICMP]] Destination Unreachable (Datagram Too Big)_ Message, indicating its MTU
- The host can adjust MTU Appropriately
- Repeat process until Packet arrives at location.
