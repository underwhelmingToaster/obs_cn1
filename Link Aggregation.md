Link Aggregation is a way to load balance packets over different physical connections. Link aggregation combines multiple [[Physical Layer]] Links into one Logical Link called LAG (Link Aggregation Group).

## Limitations
- Up to 8 Ports can be bundled.
- All to be bundled Ports need to be the same Type (e.g. Base100T)
- All Links need be configured in the same way (Duplex, VLAN)

## Process
- Packets are distributed to different physical links using a hashing algorithm
- To ensure in-order delivery, packets from same TCP/UDP connection need to go through the same interface

> [!NOTE] LACP
> Optionally, [[LACP]] can be integrated for more reliable Link Aggregation.
