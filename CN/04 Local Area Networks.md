# Lecture 4

### How to rate networks

- Speed
  - Bitrate
  - Goodput
- Last long
- Reliable
- Cost

### Token ring vs CSMA

| Token Ring                               | CSMA                                     |
| ---------------------------------------- | ---------------------------------------- |
| You can calculate the longest delay (deterministic) | If one machine is disconnected there wont be any problems |
| Better speed                             | Cheaper                                  |
| Token needs to be passed constantly, only one at all times. | Longest delay cannot be reliably calculated |
| If a machine detaches that currently owns the token, the whole network is blocked |                                          |

### Transmission Error Detection

- Simple parity bits can be added to code words to detect bit b_nb_{n-1}...b_1b_0errors, however, aren't very strong in detecting errors which affect multiple bits
- Computation of error check codes must be efficient

### Cyclic Redundancy Check (CRC)

A bit sequence (bit block) $b_nb_{n-1}...b_1b_0$ is represented as a polynomial $B(x) = b_nx^n + b_{n-1}x^{n-1} + ... + b_1x + b_0$. A generator polynomial $G(x) = g_rx^r + ... + g_1x + g_0$ with $g_r = 1$ and $g_0 = 1$ is agreed upon between the sender and the receiver. The sender transmits $U(x) = x^r \cdot B(x) + t(x)$ with $t(x) = (x^r \cdot B(x))\mod G(x)$. Then the receiver tests whether the polynomial corresponding to the received bit sequence can be divided by $G(x)$ without a remainder.

- Efficient hardware implementation possible using XOR gates and shift registers
- Only errors divisible by $G(x)$ will go undetected

##### Choosing Generator Polynomials

- $G(x)$ detects all single-bit errors if $G(x)$ has more than one non-zero term
- $G(x)$ detects all double-bit errors, as long as $G(x)$ has a factor with three terms
- $G(x)$ detects any odd number of errors, as long as $G(x)$ contains the factor $(x + 1)$
- $G(x)$ detects any burst errors for which the length of the burst is less than or equal to $r$
- $G(x)$ detects a fraction of error bursts of length $r + 1$; the fraction equals to $1 - 2^{-r}$ 
- $G(x)$ detects a fraction of error bursts of length greater than $r + 1$; the fraction equals to $1 − 2^{−r}$

### Internet Checksum

##### Properties

- Summation is commutative
- Computation independent of the byte order
- Computation can be parallelized on processors with word sizes larger than 16-bit
- Individual data fields can be modified without having to recompute the whole checksum
- Can be integrated in a copy loop
- Often implemented in assembler or special hardware

##### Further Error Situations

- Despite bit errors, the following transmission errors can occur:
  - Loss of complete data frames
  - Duplication of complete data frames
  - Receipt of data frames that are never sent
  - Reordering of data frames during transmission
- The sender must adapt its speed to the speed of the receiver (end-to-end flow control)
- The sender must react to congestion situations in a network (congestion control)