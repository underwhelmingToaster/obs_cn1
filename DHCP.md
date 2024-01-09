A Dynamic Host Configuration Protocol Server is a Network Management tool that is able to automatically configure everything a client in the same network needs to access the internet. This can include but is not limited to: IP Address, Subnet, default Gateway, DNS).

## Definitions
- **IP Pool**: A range of network addresses from which the DHCP Server will assign to newly connected hosts.
- **Lease Time**: The time a IP is assigned to a host. The lease has to be renewed before the lease time runs out.
- **Prefix Length**: Number of bits in the network prefix. Most commonly, IPv6 Subnets are allocated a /64 network, where the prefix length would be 64.
- **DHCP Relay Agent**: A network device that extends the range of a DHCP Server by forwarding DHCP Messages between Subnets. A Relay Agent will have a helper address with which it can be accessed.

## DHCPv4
The DHCP Process in an [[IPv4]] Network.
![[DHCPv4 Process.png]]

> [!TAG]- Wireshark Captures
>
> [[dhcpv4.pcap]]
> ### DHCPDISCOVER
> ![[DHCPv4 DHCPDISCOVER.png]]
> ### DHCPOFFER
> ![[DHCPv4 DHCPOFFER.png]]
> ### DHCPREQUEST
> ![[DHCPv4 DHCPREQUEST.png]]
> #### DHCPACK
> ![[DHCPv4 DCCPACK.png]]

- **DHCPDISCOVER**: This packet is broadcasted by the client when first connecting to a network. Source IP is 0.0.0.0 as the client lacks an IP Address at this point. Sent per UDP (Port 67).
- **DHCPOFFER**: Response from Server with an IP Address from Pool. Sent per UDP (Port 68).
- **(ARP)**: Clients adhering to the standard will check if this IP is already in use using [[ARP]].
- **DHCPREQUEST**: Client accepts offered IP Address.
- **DHCPACK**: DHCP Server acknowledges assignment.
When a client no longer needs an IP Address, it sends a **DHCPRELEASE** message to the server.

When a lease is about to expire, the client sends a **DHCPRENEW** message to the server, which it will Acknowledge with a **DHCPACK.**

## DHCPv6
### Address Configuration
#### Stateful DHCPv6
Stateful autoconfiguration of [[IPv6]] is the equivalent to the use of DHCP in IPv4. It requires a DHCPv6 service to provide the IPv6 address to the client device and that both client device and server maintain the "state" of that address (i.e. lease time, etc).

##### Process

![[DHCPv6 Process.png]]

> [!NOTE]- Wireshark Captures
> #todo

> [!Info]
> Instead of using 0.0.0.0, the [[IPv6#Link Local|Link-Local Address]] of the requesting device is used in the whole DHCPv6 Process.

- **RS** (Router Solicitation): Sending to All-Routers Multicast Address using Link-local Address.
- **RA** (Router Advertisement): Router responds with Network Prefix and DHCP Server Address. The "Managed Bit" is set, indicating to the client that stateful Configuration should be used.
- **SOLICIT**: Client sends SOLICIT Message to the all-DHCP-Server address to request IP Address.
- **Advertise message**: DHCP Server sends advertise message containing address prefix length and lease time.
- **[[DAD]]**
- REQUEST message: Client requests suggested IP per unicast request message to DHCP Server.
- Reply: DHCP Server Replies with IPv6 address, lease time, prefix length.

#### Stateless DHCPv6
Stateless autoconfiguration ([[SLAAC]]) of IPv6 allows the client device to self-configure its IPv6 address and routing based on the router advertisements.
