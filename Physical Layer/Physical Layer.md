This layer defines:
- Which cables and plugs are used
- How are signals transmitted (Voltage, Modulation)
- Which [[Encodings]] is used

> [!NOTE] Related Subjects
> - [[Encodings]]
> - [[Auto-Negotiation]]

## Composition
- Preamble (7B)
- Start Frame Delimiter (1B)
- [[Data Link Layer]] PDU
- Interframe Gap (12B)

## Definitions
### Bit Time
The time it takes to put a but on the wire (or other media). Calculated as:

$$
\text{Bit time} = \frac{1}{\text{NIC Speed in bits/s}}
$$

### Slot Time
The time it takes for a signal to travel the longest possible distance through an entire network and back to the sender. Depends on transmission speed and size of the network.

## Cables
Nowadays Ethernet mostly runs on twisted Pair or glass fibre cables. In the past, there were other combination. [[Ethernet#Cables|See here for other cables]]

## Signal Propagation
The time it takes for a signal to spread out over a certain distance. Signals in a Coaxial Cable propagate at about 2/3 of the speed of light.

## Wireless Signal Strength
#todo

## Fiber-Optic
#todo eye diagram, single mode/multi mode, lenght calc

