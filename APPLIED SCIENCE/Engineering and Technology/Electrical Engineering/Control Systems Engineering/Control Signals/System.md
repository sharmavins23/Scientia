In [[Control Signals|control signals]], a system is a function that takes input signals and produces outputs that are a direct function of the inputs.

## Properties

### Causality

A causal system is a system that only depends on present and past inputs, and not future inputs.

### Invertibility

A system is invertible if the inputs are (at all points in time) derivable from the output.

### BIBO Stability

A system is bounded-input bounded-output (BIBO) stable if every bounded input (amplitude) produces a bounded output (amplitude).

$$
\text{If } |x(t)| < M < \infty, \text{ then } y(t) < R < \infty
$$
### Time Invariance

A system is time-invariant if a time shift of the input results in the exact same shift of the output.

### Linear (Principle of Superposition)

A system is 'linear' if:

- For every input, we have a corresponding unique output:
- If we sum two inputs, we get a sum of two outputs (also called the Principle of Superposition.)

We can mathematically depict the principle of superposition. For some pair of inputs and corresponding outputs $x_1(t)\to y_1(t)$ and $x_2(t)\to y_2(t)$, we have:

$$
ax_1(t)+bx_2(t)\to ay_1(t)+by_2(t)
$$

