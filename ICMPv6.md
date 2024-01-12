The Implementation of [[ICMP]] for [[IPv6]].

## Composition

> [!NOTE]
> The Composition of a ICMPv6 packet is the same as for an ICMPv4 one. The message types, however, can diverge.

| 1B | 1B | 2B | 4B |
| ---- | ---- | ---- | ---- |
| Type | Code | Checksum | Rest of Header |

## Message Types
Only the most important messages are listed. For a full list see [here](https://en.wikipedia.org/wiki/ICMPv6#Types)

### 1 - Destination Unreachable
Code gives more detailed reason.

### 2 - Packet too Big
Note: IPv6 packets never get fragmented

### 3 - Time Exceeded
[[TTL|Hop Limit]] exceeded.

### 128 - Echo Request
Used for Ping

### 129 - Echo Reply
Used for ping.

### 133 - RS
[[DHCP]]

### 134 - RA
[[DHCP]]

### 135 - NS

### 136 - NA
