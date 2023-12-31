Handles Data Encapsulation and Media Access Control:

## Data Encapsulation
Provides three Functions:
__Frame Delimiting__

__Addressing__

__Error Detection__
Each Frame contains a Frame Check Sequence at the End. After a frame has been received, a Cyclic Redundancy Check (CRC) is done with the frame content is done and compared to the FCS.

## Media Access Control
This includes
- Initiation of Frame Transmission
- Recovery from transmission failures due to collisions

## MAC Adresses
### Unicast
- 6B Lenght
- Hexadecimal Notation
![[MAC Address Structure.png]]

#### Globally Unique / Locally Administered Address (U/L) Bit
Defaults to Unique, where the first three Bytes are an OUI. When an address is administered locally, it can be whatever the administrator defines.

### Broadcast
For a broadcast, the address FF:FF:FF:FF:FF:FF is used. Broadcasts are used by protocols such as [[DHCP]] and [[Address Resolution Protocol]].

#### Broadcast Domain
A broadcast domain is a logical division of a computer network where all devices can directly communicate with each other by broadcasting messages.

### Multicast
MAC Addresses in the range _01-00-5E-00-00-00_ **–** _01-00-5E-7F-FF-FF_ are multicast addresses. These addresses allow a device to send a packet to a certain group of devices.
