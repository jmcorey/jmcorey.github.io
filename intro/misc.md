# XOR and checksum notes

* definition, bitwise on a byte, hex, big message, byte by byte
* checksum byte, XOR yields 0, recovery of missing byte
* python in browser--http://www.skulpt.org/ ?
* python code for computing over a handful of bytes...
* python code to compute
* reduction to single bit--column wise or row wise
  * parity bit... morning or evening

-------------------------------------------------------------------------

# Regexes and state machines

* many names--state machine, finite automaton, discrete state machine
* bitstring longer than 7
* check allowed strings against DFA
* gate alarm example (Badge, magnetic sensor X and Y up/down, Reset)
  * normal path--start node, onto X, onto Y, all fine again
  * alarm node, and arrows for paths not allowed
  * reset arrows
  * reset actually--power cycle, zero state

-------------------------------------------------------------------------

# Graph search algorithms

-----
## DFS and BFS

-----
## BFS demo link

This shows animations of BFS for many sources one destination with different
kinds of information recorded at each node:

* https://www.redblobgames.com/pathfinding/tower-defense/

-----
## Backtracking, heuristics, branch and bound

-------------------------------------------------------------------------

# Security

## Secure copy over network

In the old days:

```
rcp myfile lab:myfile
```

Nowadays, we use SSH's secure copy:

```
scp myfile lab:myfile
```

-----
