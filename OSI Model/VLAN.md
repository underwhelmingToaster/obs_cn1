A VLAN is a way for one Switch to create multiple [[Media Access Control (MAC)#Broadcast Domain|Broadcast Domains]] (LAN). This has multiple advantages:
- Reducing overhead by shrinking broadcast domains
- Improve security for sensitive data
- Reduce [[Spanning Tree Protocol]] Workload
- and more…

## VLANs on a Single switch
Simply configure which ports can talk to which ports on a switch.

## VLANs on multiple Switches without Trunking
When multiple Links between two Switches are available, they can be each used for one VLAN. This is a simple solution to the multiple Switch Problem, but doesn't scale well.

## Trunking
When using VLANs in Networks with multiple Switches and only one link between them, Trunking has to be used: Each Frame that is sent between the Router is tagged with a VLAN ID.
![[VLAN Trunking.png]]

### 802.1Q
This standard defines the Trunking System.
