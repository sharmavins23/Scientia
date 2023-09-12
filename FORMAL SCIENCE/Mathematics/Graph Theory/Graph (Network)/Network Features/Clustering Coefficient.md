Clustering coefficient measures the degree to which nodes in a graph tend to cluster together. Evidence suggests that in real-world networks (and in particular, [[social networks]]), nodes tend to cluster together tightly due to high density of ties.

More formally, local clustering coefficient of a vertex $v_i$ is defined as:

$$
\begin{align}
C_i &= \frac{\Delta_i}{\binom{k_i}{2}} \\
&= \frac{\Delta_i}{\frac{k_i(k_i-1)}{2}}
\end{align}
$$

In this, $k_i$ is the [[Degree|degree]] of $v_i$, and $\Delta_i$ is the number of 'triangles' that $v_i$ participates in. 'Triangles' here are sets of cyclic loops. The fraction can also be read as "the total number of pairs of neighbors of $v_i$ that are adjacent to each other" divided by "the total possible number of pairs of neighbors of $v_i$".

By definition, the clustering coefficient of a fully connected/complete graph is $1$ for every node.

## Extensions of the Definition

### Average Clustering Coefficient

The average clustering coefficient, $\bar{C}$, can be defined as:

$$
\begin{align}
\bar{C} &= \frac{1}{n} \sum_{i=1}^{n}{C_i} \\
&= \frac{1}{n} \sum_{i=1}^{n}{\frac{\Delta_i}{\binom{k_i}{2}}}
\end{align}
$$
### Global Clustering Coefficient

We can extend clustering coefficient to the entire graph:

$$
C_\Delta = \frac{3\Delta}{\sum_{i=1}^{n}{\binom{k_i}{2}}}
$$

Conceptually, this is not always equivalent to $\bar{C}$. They can vary significantly in some cases, and computationally, global clustering coefficient is simpler.