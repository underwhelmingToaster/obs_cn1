In IPv6, a Solicited-Node Multicast address is a special type of multicast address used for efficient neighbour discovery.

## Process
Upon configuring an IPv6 address, every node joins a multicast group identified by the address FF02::1:FFxx:xxxx where xx:xxxx are the last 6 hexadecimal values in the IPv6 unicast address.

Therefore, for each configured unicast address, no matter if it is link-local or global, the host joins the respective auto-generated _solicited-node_ multicast group.

## Usage in DAD
See [[DAD#Process]]
