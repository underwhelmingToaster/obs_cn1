Optimizations can be taken to reduce the overhead of the [[TCP|TCP]] Protocol.

> [!NOTE]
> For all examples below, it is assumed that the client is sending and the server is receiving.

## Delayed ACK
The server waits for a specified delay value (e.g. 0.5 sec), then (if all packets have been received) acknowledges the last received packet like normal.

### Duplicate ACK
If a packet goes lost using _Delayed ACK_, the last sent ACK gets retransmitted repeatedly. Once the client has received three duplicate ACK's and the RTO has passed, all the packets which have not been acknowledged will be resent.

### Fast Retransmit
The same as **Duplicate ACK**, but the Client does not wait until RTO timeout.

### Selective ACK
Gives the server the option of specifying a range of packets which arrived correctly. This allows the client to only resend faulty packets, thus reducing overhead.

## Sliding Window
![[sliding window.jpeg]]
Each participant continuously informs the other of its own window size (TCP header field). This window size dictates how many Bytes a client can send to a server without having recieved an ACK for the previous Bytes. When this window is fully utilised, the sender will know to stop sending (because the window size has been communicated) and waits for an ACK.

### Window Scaling
Option which allows to specify a bit shift for the _window size_ field, allowing for bigger window sizes than 65 535 Bytes.
