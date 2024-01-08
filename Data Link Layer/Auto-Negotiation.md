A mechanism to automatically determine speed, [[Duplex Modes]] and flow control between devices. Devices on both end of a cable exchange their respective capability to find the best possible mode to communicate in.

## Electric Signals
When connected to a cable, devices will send out pulses.
- 10BaseT sends out one pulse every 16ms. These are called Normal Link Pulses (NLP)
- 100BaseT sends out 16 pulses each 16ms. These are called Fast Link Pulses (FLP)
- #todo was sändet 1000BaseT usw?
## Link Code Words
Devices that support Auto-Negotiation will send these 16 Pulse bursts with different flags set to communicate their capabilities.

### Base Link Code Word
The first Word which will always be sent.

| Bit |  | 0-4 | 5-12 | 13 | 14 | 15 |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Flag |  | Selector | Technology field | remote fault | ACK | next page |

- **Selector Field**: which standard is used
- **Technology Field**: set to 1 for each technology device supports
	- bit 0: 10BASE-T
	- bit 1: 10BASE-T in full duplex
	- bit 2: 100BASE-TX
	- bit 3: 100BASE-TX in full duplex
	- bit 4: 100BASE-T4
	- bit 5: pause frame
	- bit 6: asymmetric pause for full duplex
	- bit 7: reserved
- Remote fault: Device is detecting a link failure
- ACK: Sent once three identical copies of Base Link Code Word have been received
- Next Page: Indicates that other link code words will be sent

### Other Link Code Words
<https://en.wikipedia.org/wiki/Autonegotiation#Message_and_unformatted_next_page>

## Single-sided Auto-Negotiation
If only one station supports auto-negotiation, it can still detect the speed of the other station due to the [[#Electric Signals|pulses]] it sends. Duplex-Mode can not be detected and therefore half-duplex will always be used.

## Duplex Mismatch
A duplex mismatch occurs when one device is operating in Full-Duplex Mode, but without Auto-Negotiation. The other device, which supports Auto-Negotiation, will not be able to detect the duplex mode of the other station and will therefore switch to half-duplex.

This duplex mismatch results in very low throughput and packet loss.
