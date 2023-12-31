Operates in [[Data Link Layer]] and [[Physical Layer]]

## Cables

| Designation in [[10 Base Notation]] | Other Names | Cable Type | No. of Conductor Lines used / No. of  Lines available | Topology used | [[Duplex Modes\|Duplex]] Capabilities | Max Length |  | Notes |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 10Base5 | Thick Wire Ethernet, Yellow Cable Ethernet | Coaxial | 2 / 2 | Bus Config | Half-Duplex | 500 m |   |  |
| 10Base2 | Thin wire Ethernet | Coaxial | 2 / 2 | Bus Config | Half-Duplex | 185 m |  |  |
| 10BaseT | Twisted Pair Ethernet | Twisted | 4 / 8 | Star Shaped Config | Full-Duplex | 100 m |  |  |
| 100BaseT | Fast Ethernet | Twisted | 4 / 8 | Star Shaped Config | Full-Duplex | 100 m |  |  |
| 10BaseT |  | Twisted | 8 / 8 | Star Shaped Config | Full-Duplex | 100 m |  |  |

### Special Features

#### 10BaseT
- Sends link integrity pulse to notify activity
	- Pulse is sent each 16ms
	- If no signal received for 150ms, link is considered broken

#### 100/1000BaseT
- Instead of a Signal Integrity Pulse, a constant stream of 1 is being sent continuously when no data is transmitted. These signals are called _Idle Symbols_.

#### Bus Configuration
- 50 Ohm Resistors at the End of Bus Cable to avoid reflecting Signals

### Signals
#### Multi-Level-Transmission with 3 Levels (MLT3)
Here, a 0 means the Signal Level will remain constant while a 1 changes the Signal. This is used in 100BaseT.
![[MLT3.png]]
1000BaseT uses the same concept but with 5 logical States.

| Ethernet | No. of Logical States |
| ---- | ---- |
| 10BaseT | 2 (1, 0) |
| 100BaseT | 3 (1, 0, -1) |
| 1000BaseT | 5 (1, 0.5, 0 -0.5, -1) |

## Encodings
## 4B/5B
- Takes 4 Bits as Input, Outputs 5 Bits
- Designed to produce a minimum of 2 Transitions (changes from 1 to 0 or inverse) per 5 bits of Output. This aids clock recovery.
- Encoding with Following Input:

| HEX Input | Binary Input | 4B/5B Output |  | HEX Input | Binary Input | 4B/5B Output |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| 0 | 0000 | 11110 |  | 8 | 1000 | 10010 |
| 1 | 0001 | 01001 |  | 9 | 1001 | 10011 |
| 2 | 0010 | 10100 |  | A | 1010 | 10110 |
| 3 | 0011 | 10101 |  | B | 1011 | 10111 |
| 4 | 0100 | 01010 |  | C | 1100 | 11010 |
| 5 | 0101 | 01011 |  | D | 1101 | 11011 |
| 6 | 0110 | 01110 |  | E | 1110 | 11100 |
| 7 | 0111 | 01111 |  | F | 1111 | 11101 |
