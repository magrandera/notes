# Lecture 3

### Channel Characteristics

- **bit width** is the time needed to transmit a single bit 
- **delay** is the time needed to transmit a message from the source to the sink. Consists of: 
  - propagation delay
  - transmission delay

## Media Access Control

### Frequency Division Multiplexing (FDM)

Signals are carried simultaneously on the same medium by allocating to each signal a different frequency band.

### Wavelength Division Multiplexing (WDM)

- Optical fibers carry multiple wavelength at the same time
- WDM can achieve very high data rates over a single optical fiber
- Dense WDM is a variation where the wavelengths are spaced close together, which results in an even larger number of channels

### Time Division Multiplexing (TDM)

- Signals from a given sources are assigned to specific time slots
- time slot assignment might be fixed (synchronous) of dynamic (statistical)

##### Pure Aloha

- Sender sends data as soon as data becomes available
- Collisions are detected by listening to the signal
- Retransmit after a random pause after a collision
- Not very efficient (18% of the channel capacity)

##### Slotted Aloha

- Senders do not send immediately but wait for the beginning of a time slot
- Time slots may be advertised by short control signals
- Collisions only happen at the start of a transmission
- Avoids sequences of partially overlaying data blocks
- Slightly more efficient (37% of the channel capacity)

##### Carrier Sense Multiple Access (CSMA)

- Sense the media whether it is unused before starting a transmission
- Collisions are still possible (but less likely)
- 1-persistent CSMA: sender sends with probability 1
- p-persistent CSMA: sender sends with probability p
- non-persistent CSMA: sender waits for a random time period before it retries if the media is busy

##### CSMA with Collision Detection (CSMA-CD)

- Terminate the transmission as soon as a collision has been detected (and retry after some delay)
- Let $\tau$ be the propagation delay between two stations with maximum distance
- Senders can be sure that they successfully acquired the medium after 2$\tau$ time units
- Used by the classic Ethernet developed at Xerox Parc

##### Multiple Access with Collision Avoidance (MACA)

- A station which is ready to send first sends a short RTS (ready to send) message to the receiver
- The receiver responds with a short CTS (clear to send) message
- Stations who receives RTS or CTS must stay quiet
- Solves the hidden station and exposed station problem

### Token

- A token is a special bit pattern circulating between stations - only the station holding the token is allowed to send data
- Token mechanisms naturally match physical ring topologies - logical rings may be created on other physical topologies
- Care must be taken to handle lost or duplicate token
