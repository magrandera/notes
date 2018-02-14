# Lecture 3

### Turing Machine

$\Omega: K \times \Sigma \rightarrow (K \cup \{h, y, n\}) \times \Sigma \times \{\leftarrow, \rightarrow, -\}$

### M(x)

where M is a TM and x is an input word

| Output     | Condition                                |
| ---------- | ---------------------------------------- |
| "yes"      | after finitely many steps, the "yes" state is reached |
| "no"       | after finitely many steps, the "no" state is reached |
| y          | where $y \in \Sigma^*$, is a tape word after k steps and M has entered the "h" state |
| $\nearrow$ | no halting state is reached              |

### Overview of Computing Tasks

|                                   | compute $f: \mathbb{N}^k \rightarrow \mathbb{N}$ | Handling L's                             |
| --------------------------------- | ---------------------------------------- | ---------------------------------------- |
| **Always terminates**             | total recursive functions                | (always terminates with y/n) <br /> Decidable L's <br /> Recursive L's |
| **M(x) = y or M(x) = $\nearrow$** | (partially) recursive functions          | $M(x) = yes, x \in L$<br /> $M(x) = \nearrow, x \not\in L$<br /> "Semi-decidable" L's<br /> Recursively enumerable L's |

### Proposition 3.1

1. If $L$ is recursive, then $L$ is also recursively enumerable
2. If $L$ is recursive, then $L^C$ is also recursive
3. $L$ is recursive, iff $L$ and $L^C$ are recursively enumerable (rec. en.)