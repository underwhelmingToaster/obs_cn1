Stateless Address Autoconfiguration is used in IPv6 Networks to automatically configure devices with globally unique IPv6 Addresses without the need for a [[DHCP]] Server.

## When is SLAAC used
A [[DHCP#Process|Router Advertisement]] contains two important flags that help a new client decide how it should configure its IPv6 Address and DNS information.

- **Managed Flag (M-bit)**: A DHCP Server is available in this network. It will supply IP addresses and DNS Information
	- In this case, the O-bit will be ignored
- Other-Flag (O-bit): DNS Information is available via a DHCP Server. Clients can auto-configure their Addresses and then contact DHCP Server for DNS
If neither Flag is set, there is no DHCPv6 Server available in this network.

## Process
1. When a node joins an IPv6 network, it generates a [[IPv6#Link Local|Link-local]] address (including [[DAD]] check)
2. Node sends a RS
4. The RA does not have the M-Bit set.
	1. The RA contains the network prefix. This prefix is combined with the [[EUI-64]] client identifier, which results in the **global unicast address**
	2. The default gateway is set as the Link-Local address of the router which sent the RA
5. The client performs a DAD for its newly generated global unicast address.
