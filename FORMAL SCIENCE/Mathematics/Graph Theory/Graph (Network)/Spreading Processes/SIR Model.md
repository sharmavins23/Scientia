The SIR model is a classical model for [[Spreading Processes|spreading processes]]. This represents *Susceptible* $S$, *Infected* $I$, and *Recovered* $R$. Any nodes in the graph may only be one of the three.

Classical models are based on a few assumptions:

1. Compartmentalization: At any instantaneous time during the spreading process, the 'state' of an individual may either be $S$, $I$, or $R$.
	1. Susceptible individuals are healthy individuals who may be infected with a virus if they come into contact with a carrier $I$ individual.
	2. Infected/infectious individuals currently have a virus and may pass it onto an $S$ node.
	3. Recovered individuals were infected, but have recovered. They can no longer infect others. Recovered individuals may either have 'recovered' from a disease or simply passed away.
2. Homogeneous mixing: It is assumed that any infectious individual can infect any susceptible individual. In other words, the underlying network is fully connected.

Other commonly used models are iterations of the classical $S\to I\to R$ model: $S\to I \to S$, where an infected person can loop back towards being susceptible; And $S\to I$, where individuals can only be susceptible or infected (which is known as the [[SI Model|SI model]]).

## Analysis

Let $R(t)$ be the number of recovered nodes at time $t$. Other notations from the SI model propagate here - $r(t)=\frac{R(t)}{n}$. As before, let $\beta$ be the contact rate. We let $\gamma$ be the recovery rate - Namely, at each unit time, each node has a probability of $\gamma$ to recover from its infection.

Deriving the [[Differential Equation|differential equations]] for the SIR model:

$$
\begin{align}
\frac{dS(t)}{dt} &= -\beta \cdot X(t) \cdot s(t) \\
\frac{dX(t)}{dt} &= \beta \cdot X(t) \cdot s(t) - \gamma\cdot X(t) \\
\frac{dR(t)}{dt} &= \gamma \cdot X(t)
\end{align}
$$

Simplifying this notation:

$$
\begin{align}
\frac{ds}{dt} &= -\beta \cdot x \cdot s \\
\frac{dx}{dt} &= \beta \cdot x \cdot s - \gamma \cdot x \\
\frac{dr}{dt} &= \gamma \cdot x
\end{align}
$$

Solving the differential equation, we get:

$$
\begin{align}
\frac{1}{s} \frac{ds}{dt} &= \frac{-\beta}{\gamma} \frac{dr}{dt} \\
s &= s_0 e^{\frac{-\beta}{\gamma} r} \\
\frac{dr}{dt} &= \gamma \left(1-r- s_0 e^{\frac{-\beta}{\gamma} r} \right) \\
r &= 1-e^{\frac{-\beta}{\gamma} r}
\end{align}
$$

This only has a numerical solution. As the limit increases of $t\to\infty$, we note that $x(t)\to 0$, and $r(t)\to 1$. Notably, this is analogous to the giant component result for the $G(n;p)$ [[Erdos-Renyi Model|Erdos-Renyi model]]:

$$
\lim_{t\to\infty}{r(t)} = \begin{cases}
0 &\text{if} &\frac{\beta}{\gamma}\leq 1 \\
>0 &\text{if} &\frac{\beta}{\gamma} > 1
\end{cases}
$$

We refer to the top case as 'small' contained outbreaks, and refer to the bottom case as 'epidemics'.