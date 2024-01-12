## Wired
### Collisions
Collisions can only occur when devices are working in [[Duplex Modes#Half-Duplex|half-duplex]] mode or in a faulty network.

#### Local Collision
A local collision is a collision that happens before 512 bits (64B) are sent over the wire. This is a normal occurrence and does **not** indicate a fault in hardware or design.

#### Late Collision
A collision is considered late if the jam signal is sent after the 512th bit has been sent on the wire. This either indicates a hardware fault or that the network is so large that the a signal cannot traverse the network in 32 bit time (faulty network design).

### Carrier Sense Multiple Access with Collision Detection
Operates on the [[Physical Layer]]. In a shared media environment (for example a bus system), collisions have to be avoided. This can be done with CMSA/CD:

#### Carrier sense
If a station wants to send, it listens to the signal on the cable. As soon as no signal is detected, transmission begins.

During transmission, the station listens for collisions.

#### Multi-Access
In networks with large distances, it can occur that two stations begin transmitting at the same time because the signal from the other station has not yet propagated to this station. This corrupts both messages.

#### Collision Detection
A collision can be detected when two signals mix and produce an amplitude over the normal level. When this happens, the stations stop transmitting and begin sending a jam signal.

##### Jam Signal
This signal is sent by the transmitting devices. It notifies other devices of the collision, so they can invoke a back off algorithm.

##### Random Back off
After the jam signal is received, all devices will wait for a random amount of time before sending again to avoid another collision. The Backoff Algorythm functions as follows:
1. Jam Signal is detected
2. Duration **_t_** = Max. [[Physical Layer#Signal Propagation|Propagation Delay|]] of Network * 2
3. Contention Window K = { 0, 1 }
4. Pick number n in K
5. Wait n * t
6. Listen for signal on cable
	1. If no signal is detected, send data
7. If collision is detected again (multiple Hosts picked same number n): double Contention Window size of K -> { 0, 1, 2, 3 } and repeat from 4.

## Wireless
In a [[wireless]] medium, a collision is much harder to detect due to the [[#Hidden Node Problem]]. Therefore, another approach has to be implemented for Wireless Communication.

### Hidden Node Problem
In the image below, it is impossible for one client to tell if the other one is sending because they are not detecting each others signals. Due to this, they might both send at the same time, corrupting the signals at the access point.
![[Hidden Node.png]]

### RTS/CTS
The _Request to Send/Clear to Send_ mechanism ensures that only one message will be sent at a time.
> [!tldr] Example
> ![[Wireless CSMA-CD.png]]
> 1. Device listens to medium until it is free
> 	1. If medium is not free, the device will wait for a random length as specified in the Distributed Coordination Function (DCF)
> 2. Once no signals are detected on the medium, a Request to Send (RTS) is sent to the Access Point.
> 3. If a Clear to Send (CTS) is received, Transmission happens

### Interframe Space Intervals
These defined time periods help regulate timing between frame transmission on a network. For each type of message a router wants to send, it has to wait a different amount of time depending on the contents of the message. This allows higher priority messages to be sent faster.

> [!Warning] Note
> After the Interframe Space Interval has passed, devices still wait a randomized amount of time to avoid simultaneous transmission. The window in which data could be sent, but devices still need to wait for their delay, is called the **contention window.**

#### Short Interframe Space (SIFS)
SIFS is used for the highest priority packets. Used for Clear to Send (CTS), Acknowledgment (ACK), and Block Acknowledgment (Block ACK).

#### Point Coordination Function (PIFS)
Middle Priority messages. Used for Beacon and PCF

#### Distributed Coordination Function (DIFS)
Lowest Priority, used for Data Transmission, Request to send (RTS)
