The Barabasi-Albert model is an [[Algorithms|algorithm]] for generating random scale-free networks using a 'preferential' attachment mechanism. These graphs exhibit strong [[Degree Distribution#Pareto|power law distributions]].

The BA model generates graphs that have large (but not large enough!) clustering coefficients, small diameters, and power law distributions.

## Construction

Start with $m_0$ nodes. Links between these $m_0$ nodes are arbitrary, but each node has one edge (at least). From here, these graphs are generated on a per-time-step inductive basis.

At each time step, we add a new node with $m_s$ edges ($m_s\leq m_0$) to be attached to the existing nodes. Let $\Pi_i$ denote the probability that the new node is connected to an existing node $v_i$. We can define $\Pi_i$ as:

$$
\Pi_i = \frac{k_i}{\sum_{j\in V}{k_j}}
$$

This 'biases' newer nodes to be connected to higher degree nodes. After $t$ rounds, we have $n=m_0+t$ nodes in the graph, and $m=\frac{m_0}{2}+m_st$  edges. The average degree can be computed as:

$$
\begin{align}
\bar{k} &= \frac{2(\frac{m_0}{2}+m_st)}{m_0+t} \\
&\approx 2m
\end{align}
$$

As $t\to\infty$, we note degree distribution is:

$$
\begin{align}
P_l &= \frac{2m(m+1)}{l(l+1)(l+2)} \\
&\approx Cl^{-3}
\end{align}
$$

Note how this is a power law distribution with an exponent of $\gamma=3$.