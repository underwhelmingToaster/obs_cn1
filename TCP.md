TCP is a [[Transport Layer]] Protocol used for reliable connections.

FPT is used in:
- [[Hyper Text Transfer Protocol]]
- [[File Transfer Protocol]]
- Mail Protocols
- [[Secure Shell Protocol]]

> [!Info] TCP is…
> - connection-oriented

## Composition

| 2B | 2B | 4B | 4B |
| ---- | ---- | ---- | ---- |
| Source Port | Destination Port | Sequence Number | Acknowledgement Number |

| 4b | 4b | 1B | 2B | 2B | 2B | 0-40B |
| ---- | ---- | ---- | ---- | ---- | ---- | ---- |
| Data Offset | Reserved | Option Flags | Window Size | Checksum | Urgent Pointer | Options  |

- **Sequence/Acknowledgement Number**: See [[#Lifecycle]]
- **Data Offset**: Size of the TCP header in 32b Words (minimum 5, maximum 15)
- **Reserved**: Should be set to 0000
- **Flags**:
	- **CWR**: Congestion window reduced
	- **ECE**: [Congestion Notification](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#TCP_segment_structure) related
	- **[[#URG]]**: Urgent field is relevant
	- **ACK**: Acknowledgement Field is relevant
	- **[[#PSH]]**: Asks to push buffered data to the application
	- **RST**: Resets (aborts) the connection
	- **SYN**: Synchronize Sequence Numbers (should only be set in the first packets from each end in the connection)
	- **FIN**: Last packet from sender
- **Window Size**: Size of [[#Sliding Window|receive Window]]
- **[[#URG|Urgent Pointer]]**: Offset from sequence number indicating last urgent data byte
- **Options**: Sometimes padded with 0 to match Data Offset Value

## Lifecycle
### Definitions
- **Socket**: Connection endpoint in a TCP connection. Always two per connection. Consists of IP Address and Port Number (e.g. `192.168.14.9:43998`)
- **Client**: The participant who initiates the connection.
- **Server**: Is contacted by the client.

### Establishing Connection
Before any communication takes place, a connection needs to be established. This is done with a _Three-Way Handshake._

> [!tldr] Three-Way Handshake
> ```mermaid
> sequenceDiagram
>     participant A as Client
>     participant B as Server
>     A-)B: SYN (seq=x)
>     B-)A: SYN, ACK (seq=y, ack=x+1)
>     A-)B: ACK (seq=x+1, ack=y+1)
> ```
> Note that x and y are randomly chosen sequence numbers.

### Data Transfer
In this example, the client wants to send 300 000 B of data.

> [!tldr] Example Data Transfer
> ```mermaid
> sequenceDiagram
>      participant A as Client
>      participant B as Server
>      A-)B: (seq=10'000) <br> DATA 
>      Note over A,B: First 1460B are sent, <br>sequence number is defined
>      B-)A: ACK (ack=11'460)
>      Note over A,B: ack is calculated as sequence <br>number + recieved Bytes
>      loop Until Done
>          A-)B: (seq=11'460) <br> DATA 
>          Note over A,B: New sequence number is <br>x + already sent data
>          B-)A: ACK (ack=12'920)
>      end
> ```

Thanks to the **sequence number**, the receiver…
- can sort the received packets in their correct order
- can recognize if it has not received a packet
Thanks to the **acknowledgement number** the sender…
- can resend a packet if it has not received the acknowledgement for it after a certain timespan, namely the _Retransmission Timeout_ (RTO).

### Connection Termination
The connection is terminated with a _Four-way Handshake_. The connection can be terminated by both participants.

> [!tldr] Four-Way Handshake
> ```mermaid
> sequenceDiagram
>      participant A as Client
>      participant B as Server
>      A-)B: FIN
>      B-)A: ACK
>      B-)A: FIN
>      A-)B: ACK
> ```

The connection could also only be closed by one side, in case a connection only Acknowledges the closure, but does not send `FIN` back. This connection would still be able to send data.

## Damage Limitation
Due to the large overhead TCP Introduces, [[Flow Control]] and [[Congestion Control]] have been implemented to reduce network usage.

### Maximum Segment Size
MSS is an option that specifies the maximum amount of payload of a single TCP Segment. Defaults to 536B but should be enlarged during the Three-Way Handshake to reduce overhead.

## Buffering
TCP is a protocol which allows its upper Layers a simple Socket for communication, masking the complexities of packet-based communications. To allow applications to read from and write to this socket at any time, buffers are implemented on both sides of a TCP connection in both directions.

For example, this becomes relevant when an application wants to send a large file. It is able to hand over this file to TCP, which will buffer it and send multiple Packets, utilizing the MSS.

## PSH
If the push flag is set in a TCP Packet:
- The sending application informs TCP that data should be sent immediately
- The PSH flag in the TCP header informs the receiving host that the data should be pushed up to the receiving application immediately

## URG
Informs the receiving station that certain data within this segment is urgent. If set, the _Urgent Data_ field indicates how much of the data in the segment, counting from the first byte, is to be considered urgent.
