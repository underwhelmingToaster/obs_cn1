Also known as __Layer 2__, the Data Link Layer consist of two sublayers:
- [[Logical Link Control]]
- [[Media Access Control (MAC)]]

- Communicates with the physical [[Physical Layer|Layer 1]] Components
- Handles Data Encapsulation and Media Access Control

## Composition

| Bytes |  | 6B | 6B | 2B | 46-1500B | 4B |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Ethernet II |  | Destination MAC Address | Source MAC Address | Type | Data + PAD | FCS |
| IEEE 802.3 |  | Destination MAC Address | Source MAC Address | Length | LLC + Data + PAD | FCS |

- **Type**: declares the type of Frame (e.g. 0x0800 for IPv4)
- **Length**: declares the length of MAC Payload (between 0x0000 (0 B) and 0x05DC (1500B))
- **PAD**: In case the minimum packet length of 46B has not been reached, the Field is padded with an arbitrary sequence of bits.

## Data Encapsulation
Provides Three Functions:
- Frame Delimiting
- Addressing
- Error Detection
