## Types of IPv6 Addresses
### Link Local
A unicast network address that is valid for communication within a subnet. In IPv6, a link-local address always starts with fe80::/10.

#### Generation
The most widely adopted way of generating a link-local address is to use the prefix fe80::/64 and the [[EUI-64]] generated interface identifier. Afterwards a [[DHCP#DAD|DAD]] is performed to check if the IP address is already used.

## Composition

| 4b | 8b | 20b | 16b | 8b | 8b | 128b (16B) | 128b (16B) |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Version | Traffic Class | Flow Label | Payload Lenght | Next Header | Hop Limit | Source Address | Destination Address |

- **Version**: IPv4 or IPv6
- **Traffic Class**: Quality of Service (QoS) specification
- **Flow Label**: Experimental (allows each router in the Network path to have specific QoS requirements)
- **Payload Length**: Length of Extension Header + Data
- **Next Header**: Either Extension Header or Protocol of next Layer
- **Hop Limit**: [[TTL|TTL]] Variable

## Unicast Address
![[IPv6 Unicast.png]]
Host Address can be
- generated from MAC-Address ([[EUI-64]])
- second address generated from Random Number for better privacy ([[Privacy Extension]])
- one randomly generated Number
- Assigned via [[DHCP]]
- Assigned via manual configuration

## Multicast Address
Starts with ff00::/8

| 8b | 4b | 4b | 112b |
| ---- | ---- | ---- | ---- |
| "FF" | Flags | Scope | (Group ID) |

### Flags

| X | R | P | T |
| ---- | ---- | ---- | ---- |
| Reserved | Rendezvous | Prefix | Trancient |

A "1" for each flag indicates:
- **Rendezvous**: That the address of the Rendezvous Point is integrated in Address
- **Prefix**: That the address is based on the network prefix
- **Transient**: That the multicast address is dynamically assigned.

### Scope

| Scope Value | Scope |
| ----------- | ----- |
| 1            | Node      |
| 2            | Link      |
| 3            | Realm      |
| 4            | Admin      |
| 5            | Site      |
| 8            | Organization      |
| E            | Global      |

## Solicited Node Multicast Address
See [[Solicited-node Multicast]].

## Anycast Address
IPv6 Anycast is done by assigning multiple Devices the same IPv6 address. When the client then requests this address, he is forwarded to the next node.
