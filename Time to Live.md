The TTL field is set by the sender of the datagram, and reduced by every router on the route to its destination. If the TTL field reaches zero before the datagram arrives at its destination, then the datagram is discarded and an [[Internet Control Message Protocol]] (ICMP) error datagram (11 - Time Exceeded is sent back to the sender.

## Purpose
To avoid situations where an undeliverable datagram circulates in a network forever.
