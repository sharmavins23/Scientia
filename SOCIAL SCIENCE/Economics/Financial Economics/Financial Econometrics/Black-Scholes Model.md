The Black-Scholes model (or Black-Scholes-Merton model) is a mathematical model for the dynamics of a financial market containing derivative investment instruments. The following notation is applied:

- $t$ is time in years, with $t=0$ representing the present year.
- $r$ is the annualized risk-free interest rate, continuously compounded.
- $S(t)$ is the price function of an underlying asset at time $t$.
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

With this, the fundamental Black-Scholes equation describes a price $V(S,t)$ of an option:

$$
\frac{\partial V}{\partial t} + \frac{1}{2}\sigma^2S^2 \frac{\partial^2V}{\partial S^2} + rS\frac{\partial V}{\partial S} - rV = 0
$$

This equation gives the fundamental insight that one can perfectly hedge an option by buying and selling the underlying asset in such a way as to "eliminate risk".

Finally, the Black-Scholes formula calculates the price of European put and call [[options]]