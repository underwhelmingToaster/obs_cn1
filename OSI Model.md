The OSI Model is a layered Model. It consists of seven Layers.
Layered Models assist in protocol design by preventing technology changes in one layer from affecting the other layers (in theory).

## The Layers

| Layer | Name | Name of SDU on this Layer |
| ---- | ---- | ---- |
| 7 | [[Application Layer]] | Message |
| 6 | [[Presentation Layer]] |  |
| 5 | [[Session Layer]] |  |
| 4 | [[Transport Layer]] | TCP Segment/UDP Datagram |
| 3 | [[Network Layer]] | Packet |
| 2 | [[Data Link Layer]] | (Ethernet) Frame |
| 1 | [[Physical Layer]] | (Physical PDU) |

### Terminoliogy
- **PDU**: Protocol Data Unit: Includes Headers and Information of this Protocol/Layer.
- **SDU**: Service Data Unit: The Data a Layer receives from the Layer above
Each PDU becomes an SDU for the Layer below.
