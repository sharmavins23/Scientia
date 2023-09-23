A non-deterministic [[Finite Automata|finite automata]] differs from its deterministic counterpart in the addition of $\epsilon$ to the language. $\epsilon$ may be travelled at any point *without* an input. Alongside this, NFAs also allow multiple arrows with the same character to be outgoing from a particular node.

The program flow changes:

1. If there is only one exit arrow for an input to a machine, the arrow is taken.
2. If there are multiple ways to proceed, the NFA will 'split' into multiple copies of itself and follow all possibilities in parallel.
3. If the machine, at any point, finds an arrow with the character $\epsilon$, the machine will split into as many copies as necessary, following all of the $\epsilon$ arrows *as well* as having a copy staying at the same state. This happens regardless of input.
4. If there is no remaining path to follow for a certain input, that process branch 'dies' and further processing on that branch stops.

## NFA Conversion

Despite these additional complications, a notable feature of the NFA is that **every NFA may be converted into an equivalent DFA**. The following properties hold:

1. The number of states of an equivalent DFA will always have an upper limit of the power set of the states in the NFA. So, if there are $k$ states in the NFA, and the alphabet is $2$ characters, there will (at most) be $2^k$ states in an equivalent DFA.
2. The start state of a DFA is equal to the solo start state of the NFA, as well as $E(\{\epsilon\})$, which represents the set of states reachable from the start state via an $\epsilon$ arrow.
3. The accept states for an equivalent DFA are simply the states containing the NFA's accept states.
4. The transition function is a trivial additional step - If an arrow goes to two states in the NFA, the DFA's arrow will go to the power set's. Any epsilon transitions also act as state join vectors.
5. Any states that are not the start state and have no input arrows may be safely removed.