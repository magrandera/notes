# Lecture 4

### k-Tape TM

A structure M = $(K, \Sigma, \delta, s)$ with transition function: $\delta$: $K \times \Sigma^k \rightarrow K \cup \{y, n, h\} \times \Sigma^k \times \{\leftarrow, \rightarrow, -\}^k$

<u>**Def**</u>: Let $F: \mathbb{N}^k \rightarrow \mathbb{N}$ be a function, such that a k-tape TM $M$ exists, which on inputs <($n_1, ..., n_k$)>, where |<($n_1, ..., n_k$)>| = $l$, terminates after at most $f(l)$ steps with output $M(n_1, ..., n_k) = <F(n_1, ..., n_k)>$ then we say $F \in TIME(f(l))$

<u>**Proposition**</u>: Let $F \in TIME_k(f(l))$ then $F \in TIME_1(O(f^2(l)))$. Whatever can be computed with k-tapes can also be computed with a single tape machine.
