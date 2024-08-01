The Black-Scholes model (or Black-Scholes-Merton model) is a mathematical model for the dynamics of a financial market containing derivative investment instruments. The following notation is applied:

- $t$ is time in years, with $t=0$ representing the present year.
- $r$ is the annualized risk-free interest rate, continuously compounded.
- $S(t)$ is the price function of an underlying asset at time $t$. It is also written as $S_t$.
- $\mu$ is the [[Stochastic Drift|drift rate]] of $S$ annualized.
- $\sigma$ is the standard deviation of the stock's returns. This is the square root of the quadratic variation of the stock's log price process, which is a measure of its [[Volatility (Finance)|volatility]].
- $V(S,t)$ is the price of the option as a function of the underlying asset $S$ at time $t$.
- $C(S,t)$ is the price of a European call option.
- $P(S,t)$ is the price of a European put option.
- $T$ is the time of option expiration.
- $\tau$ is the time until maturity: $\tau=T-t$.
- $K$ is the strike price of the option, also known as the exercise price.
- $N(x)$ denotes the [[Standard Distribution|standard normal]] [[Cumulative Distribution Function|CDF]]: $$N(x)=\frac{1}{\sqrt{2\pi}} \int_{-\infty}^{x}{e^{\frac{-z^2}{2}}} dz$$
- $N'(x)$ denotes the standard normal PDF: $$N'(x) = \frac{dN(x)}{dx} = \frac{1}{\sqrt{2\pi}} e^{\frac{-z^2}{2}}$$

# Derivation

With this, the fundamental Black-Scholes equation describes a price $V(S,t)$ of an option:

$$
\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2S^2 \frac{\partial^2V}{\partial S^2} + rS\frac{\partial V}{\partial S} - rV = 0
$$

This equation gives the fundamental insight that one can perfectly hedge an option by buying and selling the underlying asset in such a way as to "eliminate risk".

This differential equation can be solved via the following boundary conditions:

$$
\begin{align}
C(0,t) &= 0 \text{ for all }t \\
C(S,t) &\to S-K \text{ as } S\to\infty \\
C(S,T) &= \max{(S-K, 0)}
\end{align}
$$

Solving for the value of a call option:

$$
\begin{align}
C(S_t, t) &= N(d_+)S_t - N(d_-)Ke^{-r(T-t)} \\
d_+ &= \frac{\ln{\left(\frac{S_t}{K}\right)}+\left(r+\frac{\sigma^2}{2}\right)(T-t)}{\sigma\sqrt{T-t}} \\
d_- &= d_+ - \sigma\sqrt{T-t}
\end{align}
$$

Put-call parity states that a portfolio of a long call option and a short put option is equivalent (and hence has the same value as) a single call at the strike price and expiry. With a discount factor accounting for future inflation, the following price of a corresponding put is achieved:

$$
\begin{align}
P(S_t, t) &= Ke^{-r(T-t)}-S_t+C(S_t,t)\\
&= N(-d_-)Ke^{-r(T-t)}-N(-d_+)S_t
\end{align}
$$