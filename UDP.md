User Datagram Protocol is a simple [[Transport Layer]] Protocol with little overhead. Adds support for Ports.

> [!Info] UDP is…
> - connectionless
> - best effort
> - media-independent

## Composition

| 2B | 2B | 2B | 2B |  |
| ---- | ---- | ---- | ---- | ---- |
| Source Port | Destination Port | Length | Checksum | Data |

- **Source/Destination Port**
- **Length**: Length of Datagram Including Header and Data
- **Checksum**: Checksum of header and data (optional in IPv4, mandatory in IPv6)

## Usage
Due to very little overhead, UDP is used in various protocols such as:
- [[DNS]]
- Various routing protocols such as [[Routing#Dynamic Routing|RIP]]
- [[DHCP]]
- Real Time Transport Protocol (RTP)
