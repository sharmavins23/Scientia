Control signals in [[Control Systems Engineering|control systems engineering]] are functions of independent variables, usually time (but in some cases, [[voltage|voltage]] or [[current|current]]).

## Signal Types

There are many individual types of signals. Here are some:

- [[Continuous-Time Signals|Continuous-time signals]], which exist at any time on the time axis.
- [[Discrete-Time Signals|Discrete-time signals]], where the time axis is sampled at particular points.
- [[Analog Signals|Analog signals]], whose values are not restricted to countable numbers.
- [[Digital Signals|Digital signals]], where the vertical amplitude axis is sampled and contains only a finite set of discrete values.
- [[Periodic Signals|Periodic signals]], which have repeating waveforms over some time period.
- [[Energy and Power Signals|Energy and power signals]], which deal with [[Energy|energy]] and [[Power|power]] of a system.
- [[Deterministic Signals|Deterministic signals]], which can be modelled easily mathematically.
- [[Random Signals|Random signals]], which cannot be modelled mathematically easily.
## Operations

For some signal $y=Ax(t)$, the value $A$ refers to amplitude and $t$ refers to time. The following are some very basic operations:

### Time Reversal

One can 'reverse' the time dependency of a function by applying $y=Ax(-t)$.

### Time Scaling

There are two methodologies of scaling a signal $y=Ax(t)$: *Compression* and *expansion*. Compression refers to 'squeezing' the signal, or applying a scalar to the time (and thus making the entire signal more 'sensitive' to input):

$$
y=Ax(kt) \text{ for } k\geq 1
$$

Expansion can also be done, where the signal becomes less 'sensitive' to inputs:

$$
y=Ax\left(\frac{t}{k}\right) \text{ for } k\geq 1
$$

### Amplitude Scaling

We can apply a scalar to a signal to increase or decrease its amplitude without changing its time variance:

$$y=bAx(t)$$

Here, $b$ may be any value. If $b<0$, the signal can be flipped!

### Time Shifting

A time *delay* can be applied to a signal as:

$$
y=Ax(t-k) \text{ for } k>0
$$

A time *advance* can be applied as well:

$$
y = Ax(t + k) \text{ for } k>0
$$