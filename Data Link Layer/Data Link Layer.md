Also known as __Layer 2__, the Data Link Layer consist of two sublayers:
- [[Logical Link Control]]
- [[Media Access Control]]

- Communicates with the physical [[Physical Layer|Layer 1]] Components
- Handles Data Encapsulation and Media Access Control

## Composition

|  |  | 6B | 6B | 2B | 46-1500B | 4B |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Ethernet II |  | Destination MAC Address | Source MAC Address | Type | Data + PAD | FCS |
| IEEE 802.3 |  | Destination MAC Address | Source MAC Address | Length | LLC + Data + PAD | FCS |

- **Type**: declares the type of Frame (e.g. 0x0800 for IPv4). All Types must have codes higher than 1536, or else they would be indistinguishable from an IEEE 802.3 Frame.
- **Length**: declares the length of MAC Payload (between 0x0000 (0 B) and 0x05DC (1500B))
- **PAD**: In case the minimum packet length of 46B has not been reached, the Field is padded with an arbitrary sequence of bits.

### 802.1Q

|  |  | 6B | 6B | 4B | 2B | 46-1500B | 4B |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| IEEE 802.1Q |  | Destination MAC Address | Source MAC Address | Tag | Type | Data + PAD | FCS |

- **Tag**: Contains Information about the VLAN (not relevant for Exam) as well as the **12 bit VLAN ID** at the end.

#### VLAN ID
12 bit Field supports (4096 - 2 Reserved) VLANs

One VLAN (default VLAN 1) is the native VLAN. Packets in this VLAN will not be tagged. This way, non-trunking switches can be integrated into the VLAN.

## Data Encapsulation
Provides Three Functions:
- Frame Delimiting
- Addressing
- Error Detection
