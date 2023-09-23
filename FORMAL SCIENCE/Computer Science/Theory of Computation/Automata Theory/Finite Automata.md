A finite automata $M$ (or deterministic finite automata, or DFA), is a 5-tuple equation $M=(Q, \Sigma, \delta, q_0, F)$ where:

1. $Q=\{q_1, q_2, ..., q_n\}$ represents the full set of states in the state machine.
2. $\Sigma=\{0, 1\}$ represents the alphabet. Usually, this is binary.
3. $\delta : Q\times \Sigma\to P(Q)$ is the set of transitions, which are usually a set of tuple pairs.
4. $q_0\in Q$ is the singular start state.
5. $F \subseteq Q$ is the set of 'end' states where the automata may accept inputs.

If $A$ is the set of all strings that the machine $M$ accepts, we say that $M$ recognizes $A$. Conceptually, a finite automata accepts a string if, by the end of the string, the current state of the machine is on an end state.

Finite automata are weaker than [[Turing Machine (TM)|Turing machines]].