The **Address Resolution Protocol** (ARP) is used to map Network Layer Addresses ([[IP]]) to Data Link Layer Addresses ([[Media Access Control|MAC]]).

The ARP Protocol performs two Functions:
- Resolve IP to MAC Addresses.
- Maintain a cache of mappings.

## Resolving Addresses
The device maintains a lookup table of IP and matching MAC Addresses. When a packet needs to be sent, the device uses the lookup table to get an IP Address. If no matching Address is found, the ARP Discovery Process is launched.

## Maintaining the Lookup Table
The device can gather MAC Addresses in two ways:
- Monitor the Traffic: If a Frame is received, the Addresses can be read and written in the table.
- ARP Request Broadcast: Send a [[Media Access Control#Broadcast|Broadcast]] containing the needed IP Address. If this Broadcast reaches the Device with this Address, it returns an ARP Reply (Unicast) containing its MAC Address. The host can then save this Information.

## Destinations outside the Network
If the required IP Address is outside of the Broadcast Domain (can be calculated with [[Subnet Mask]]), the frame is sent to the Default Gateway.  

## Issues
- A lot of overhead due to Broadcast
- ARP Spoofing: An attacker send a false ARP Response to catch traffic.
