Used to address Devices in [[IPv4#Private Address Spaces|Private IP Ranges]]. It involves the process of swapping one IP address with another.

## Types of NAT
### Static NAT
Assigning each internal IP Address a static external IP Address. Useful when device needs to be accessible from the outside network.

### Dynamic NAT
Dynamically assigning an external IP Address from a designated pool of Addresses to an internal IP when needed.

### Overloading NAT, PAT
Mapping multiple internal IP addresses to one external IP address by utilizing PAT (Port Address Translation).

Each internal IP Address is assigned a Port over which communication with the outside Network will occur. For example:

```
Internal IP Addr.                                        External IP Addr

192.168.10.1     <-----                        ----->    241.14.4.2:10001
.                          |--------------|
192.168.10.2     <-----    |    Router    |    ----->    241.14.4.2:10002
.                          |--------------|    
192.168.10.3     <-----                        ----->    241.14.4.2:10003


```

### Overlapping NAT
Two hosts have the same internal IP Addresses. The router intercepts their package and, with the help of a lookup table, replaces the internal Address with a unique external one.
