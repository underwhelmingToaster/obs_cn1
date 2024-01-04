The goal of congestion control is to avoid sending more traffic onto a network than the network can handle, thus slowing it down unneccessairily. There are many congestion avoidance algorithms for TCP, all operating on the same principle of _additive increase/multiplicative decrease_ (AIMD).

> [!NOTE] Example of TCP Reno
>
> ![[Congestion Control.png]]
> `cwnd`: Congestion Window
> `ss`: Slow Start Algorithm
> `ca`: Congestion avoidance Algorithm
> `ssthresh`: Slow start threshold

## Slow Start
Slow Start begins with a CWND of 1 [[Transport Control Protocol#Maximum Segment Size|MSS]] (can vary). With each recieved ACK, the window size is doubled.

This continues until either `sshthresh` is reached or packet loss is detected. Once sshtresh is reached, Congestion Avoidance will take over.

## Congestion Avoidance Algorithm
Here, for each received ACK, windows size increases by 1 MSS until packet loss.

## Loss Event
If packet loss is detected, the algorithm takes measures to reduce network load.

### RTO Timeout
If packet loss times out, both TCP Tahoe and TCP Reno set the Congestion Window to 1 and initiate a slow start.

### Duplicate ACK
If the same `ACK` is recieved three consecutive times, the following actions are taken.

#### TCP Tahoe
- retransmission is sent

- sshtresh is set to $$ \fraq{\text{current window size}} / 2 $$

- slow start begins

#### TCP Reno
- [[Flow Control#Fast Retransmit|Fast Retransmit]] is sent
- Window size and sshtresh are set to
