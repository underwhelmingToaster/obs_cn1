## Collisions
Collisions can only occur when devices are working in [[Duplex Modes#Half-Duplex|half-duplex]] mode or in a faulty network.

### Local Collision
A local collision is a collision that happens before 512 bits (64B) are sent over the wire. This is a normal occurrence and does **not** indicate a fault in hardware or design.

### Late Collision
A collision is considered late if the jam signal is sent after the 512th bit has been sent on the wire. This either indicates a hardware fault or that the network is so large that the a signal cannot traverse the network in 32 bit time (faulty network design).

## Carrier Sense Multiple Access with Collision Detection
Operates on the [[Physical Layer]]. In a shared media environment (for example a bus system), collisions have to be avoided. This can be done with CMSA/CD:

### Carrier sense
If a station wants to send, it listens to the signal on the cable. As soon as no signal is detected, transmission begins.

During transmission, the station listens for collisions.

### Multi-Access
In networks with large distances, it can occur that two stations begin transmitting at the same time because the signal from the other station has not yet propagated to this station. This corrupts both messages.

### Collision Detection
A collision can be detected when two signals mix and produce an amplitude over the normal level. When this happens, the stations stop transmitting and begin sending a jam signal.

#### Jam Signal
This signal is sent by the transmitting devices. It notifies other devices of the collision, so they can invoke a back off algorithm.

#### Random Back off
After the jam signal is received, all devices will wait for a random amount of time before sending again to avoid another collision. The Backoff Algorythm functions as follows:
1. Jam Signal is detected
2. Duration **_t_** = Max. [[Physical Layer#Signal Propagation|Propagation Delay|]] of Network * 2
3. Contention Window K = { 0, 1 }
4. Pick number n in K
5. Wait n * t
6. Listen for signal on cable
	1. If no signal is detected, send data
7. If collision is detected again (multiple Hosts picked same number n): double Contention Window size of K -> { 0, 1, 2, 3 } and repeat from 4.
