The Internet Control Message Protocol is a [[Network Layer]] Protocol used to communicate error messages or operational information about network conditions. ICMP is to be used with [[IPv4]]

## Composition

| 1B | 1B | 2B | 4B |
| ---- | ---- | ---- | ---- |
| Type | Code | Checksum | Rest of Header |

- Type: Type of Message. See [[#Control Messages]]
- Code: Details of Message. 0 per default
- Rest of Header: Contents depend on Type and Code

## Control Messages
Only the most important messages are listed. For a full list see [here](https://en.wikipedia.org/wiki/Internet_Control_Message_Protocol#Control_messages)

### 0 - Reply
Used to reply to a ping.

## 3 - Destination Unreachable
Code field gives more detailed reason.

### 8 - Echo Request
Used for ping. Expects a [[#0 - Reply]]

### 9 - Router Advertisement
See [[DHCP]]

### 10 - Router Solicitation
See [[DHCP]]

### 11 - Time Exceeded
When [[TTL]] expires
