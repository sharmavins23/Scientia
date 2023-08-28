An adjacency matrix is a method to represent networks via [[linear algebra]]. For a particular graph, the following can be constructed:

$$
A_{ij} = \begin{cases}
	1,& \text{if } n_i \leftrightarrow n_j\\
	0,& \text{otherwise}
\end{cases}
$$

Where $n_i$ represents [[Node|node]] $i$ and $n_j$ is node $j$. These can also be directed, indicating connections that occur:

$$
A_{ij} = \begin{cases}
	1,& \text{if } n_i \rightarrow n_j\\
	0,& \text{otherwise}
\end{cases}
$$
