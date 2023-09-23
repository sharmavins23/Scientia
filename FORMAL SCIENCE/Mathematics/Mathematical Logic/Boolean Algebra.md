In [[Logic (Mathematics)|mathematical logic]], Boolean algebra is a branch of algebra. It differs from elementary algebra in both its values and operators:

- Boolean algebra only uses variables as values, and these values may only take the state of `true` or `false`.
- Boolean algebra uses logical operators instead of normal operators.

## Operators

The following are the primary operators of Boolean algebra:

- Conjunction ($\wedge$): For some values $a$, $b$: $a\wedge b = 1$ iff $a=1$ and $b=1$.
- Disjunction ($\vee$): For some values $a$, $b$: $a\vee b=1$ if *either* $a=1$ or $b=1$, or both.
- Negation ($\neg$): For some values $a$, $b$: $\neg a=1$ iff $a=0$. $\neg b=0$ iff $b=1$.

There are also secondary operators, which are composed of the primary operations:

- Material conditional ($\to$): $x\to y = \neg x \vee y$
- Material biconditional ($\leftrightarrow$): $x \leftrightarrow y = (x \wedge y) \vee (\neg x \wedge \neg y)$
- Exclusive or/XOR ($\oplus$): $x \oplus y = \neg(x \leftrightarrow y)$
