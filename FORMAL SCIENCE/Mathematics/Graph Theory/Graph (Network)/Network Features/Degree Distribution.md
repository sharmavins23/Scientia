For each $P=0, 1, ..., n-1$, the value $P_l$ ([[Degree|degree]] distribution) can be defined as:

$$
P_l = \frac{|v_i \text{ where } k_i=l|}{n}=P(X=l)
$$

One interpretation of $P_l$ is the probability that a randomly selected node has a degree of $l$. There are many cases where degree distribution is the key to understanding the outcome of a spreading process in a graph.

## CCDF

It's easier to identify scale-free distribution from the complementary cumulative distribution function (CCDF). Recall that the [[Cumulative Distribution Function|CDF]] of a [[Random Variable|random variable]] $X$, denoted by $F_X(x)$, is defined as $P(X\leq x)$ for any $x\in\mathbb{R}$. The CCDF can be written as:

$$
\begin{align}
\bar{F_X}(x) &= 1-F_X(x) \\
&= P(X>x)
\end{align}
$$

In this example it's easier to look at the probability that the degree is greater than some value $x$.

## Examples

### Poisson

There may also be other particular degree distributions. For instance, the Poisson degree distribution is:

$$
P_l=\frac{e^{-\bar{k}}(\bar{k})^l}{l!}
$$

For this, degree variance can simply be $\bar{k}$. There is not a lot of degree variation for these kinds of networks, and Poisson distributed networks do not contain 'hubs'.

### Pareto

The power law distribution, or Pareto distribution, is another such important distribution. Intuitively, the power law distribution can be seen in networks with 'hubs' - For instance, really popular social media accounts may gain followers at a much higher rate. Another example is city population growth.

$$
P_l = cl^{-\gamma} \text{ for } l=1,2,3,...
$$

The power law distribution contains hubs with degree much larger than $\bar{k}$, and if $2<\gamma \leq 3$, the mean degree is finite, but the variance will be infinite.

Power law distributed networks are generally robust to random attacks, but weak to targeted attacks (both in part due to their hubs).

The CCDF of this function would be $P(k>x)$, stated as:

$$
\begin{align}
P(k>x)&=\int_{x}^{\infty}{cl^{-\gamma}}dl \\
&=c\left[\frac{l^{-\gamma+1}}{-\gamma+1}\right]_{l=x}^{l=\infty} \\
&=\frac{c}{\gamma-1}\cdot x^{-\gamma+1} \\
&=c'\cdot x^(-\gamma+1) \text{ where } c'= \frac{c}{\gamma-1}
\end{align}
$$

Looking at a graph of the distribution, taking the logarithm of both sides we get:

$$
\begin{align}
\log(P(k>x)) &= \log(c'x^{-\gamma+1}) \\
&= (-\gamma+1)\log(x) + \log(c')
\end{align}
$$

As such, if you indeed have a power law distribution, you can simply plot on a log-log scale and pull out the graph's slope to find the distribution $\gamma$.