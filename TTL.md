
> [!warning] DNS TTL
> For TTL relating to DNS, see [[DNS#Caching]]

> [!Warning] IPv6 TTL
> In the IPv6 Protocol, TTL is renamed by the **Hop Limit**. Functionally however, the field is the same.

The Time to Live field is set by the sender of the datagram, and reduced by every router on the route to its destination. If the TTL field reaches zero before the datagram arrives at its destination, then the datagram is discarded and an [[ICMP]] error datagram (11 - Time Exceeded is sent back to the sender.

## Purpose
To avoid situations where an undeliverable datagram circulates in a network forever.
