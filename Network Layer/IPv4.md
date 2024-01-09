## Composition

| 4b | 4b | 8b | 16b | 16b | 3b | 13b | 8b |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Version | HLEN | Type of Service | Lenght | ID | Null/DF/More bit | Fragment offset | TTL |

| 8b | 16b | 4B | 4B | 0-40B | 20B-65536B |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Protocol | Header Checksum | Source IP | Dest. IP | _Options_ | DATA |

- **Version**: _0100_ (4) for IPv4
- **HLEN**: Header Length, number of 32bit words in header
- **Type of Service**: Can be used to specify special services such as VoIP
- **Length**: Total length of header + data
- **ID**: Identifying number for a group of fragments
- **Flags**
	- **Null Flag**: Reserved, must be zero
	- **Don't Fragment**: If this flag is set and fragmentation is required to continue the route, the packet will be dropped. Can be used for [[Path MTU Discovery]]
	- **More Fragments**: Set to 1 if there will be more fragments arriving.
- **Fragment offset**: Specifies offset of data relative to the beginning of unfragmented Data. Is always specified in units of 8 Bytes.
- **TTL**: [[TTL]] field
- **Protocol**: Protocol that is used (e.g. [[ICMP]])

## IP Classes
In classful subnetting, all networks are part of a Class.

| Class | Number of networks | Addresses per network | Start address | End address | CIDR notation |
| ---- | ---- | ---- | ---- | ---- | ---- |
| Class A | 128 (2<sup>7</sup>) | 16,777,216 (2<sup>24</sup>) | _0.0.0.0_ | 127.255.255.255 | _/8_ |
| Class B | 16,384 (2<sup>14</sup>) | 65,536 (2<sup>16</sup>) | _128.0.0.0_ | _191.255.255.255_ | _/16_ |
| Class C | 2,097,152 (2<sup>21</sup>) | 256 (2<sup>8</sup>) | _192.0.0.0_ | _223.255.255.255_ | _/24_ |
| Class D (multicast) | not defined | not defined | _224.0.0.0_ | _239.255.255.255_ | /4 |
| Class E (reserved) | not defined | not defined | _240.0.0.0_ | 255.255.255.255 | not defined |

## Classless/CIDR
CIDR stands for "Classless Inter-Domain Routing," and it is a methodology used to allocate and specify IP addresses and their routing on the Internet.

### CIDR Notation

| CIDR | SUBNET MASK | OF ADDRESSES | WILDCARD |
| ---- | ---- | ---- | ---- |
| /0 | 0.0.0.0 | 4,294,967,296 | 255.255.255.255 |
| /1 | 128.0.0.0 | 2,147,483,648 | 127.255.255.255 |
| /8 | 255.0.0.0 | 16,777,216 | 0.255.255.255 |
| /16 | 255.255.0.0 | 65,536 | 0.0.255.255 |
| /24 | 255.255.255.0 | 256 | 0.0.0.255 |
| /32 | 255.255.255.255 | 1 | 0.0.0.0 |

## Private Address Spaces
These addresses can be used by anyone for private use.

| Class | Range                         | Prefix     |
| ----- | ----------------------------- | ---------- |
| A     | 10.0.0.0 - 10.255.255.255     | 10/8       |
| B     | 172.16.0.0 - 172.31.255.255   | 172.16/12  |
| C     | 192.168.0.0 - 192.168.255.255 | 192.168/16 |
