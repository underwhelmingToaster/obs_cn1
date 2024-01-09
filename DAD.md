For _Duplicate Address Detection_, a neighbour solicitation is sent to the an IP address to check if anyone is already using this IP. If no response is received, the Address is considered free to use.

## Process
If a device wants to check if a certain address is already taken, it will send a neighbour solicitation to this specific [[Solicited-node Multicast]] Group. Any potential devices in this group will open the message and compare the address to check to their own address. If the addresses match, this device will reply.

If a client receives no response, it will consider the address free to use.
