The Iron Law of Performance and Power is derived off the equation for power:

$$
P=\alpha C V^2 f
$$

Power is equal to an activity factor, times capacitance, times the frequency, times the square of the voltage. Another relative relation is:

$$
P = \frac{E}{I}\times\frac{I}{C}\times f
$$

The important note here is that as you scale performance, the relative power consumption scales **super-linearly**. As such, the Iron Law states that, when designing a [[Pipelining (Computation)|pipelined]] CPU, one must consider both performance and the *square* of power.