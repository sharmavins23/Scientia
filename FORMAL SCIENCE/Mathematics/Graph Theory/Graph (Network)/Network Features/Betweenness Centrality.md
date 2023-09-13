Betweenness centrality is a way of detecting the amount of influence one node has over information flow in a graph. In particular, for a node $v_i$, betweenness centrality measures the number of times $v_i$ is in the shortest path between $v_j, v_k$ for some $i\neq j$ and $i\neq k$ and $j \neq k$.

If every node wanted to pass data through their shortest path, the betweenness centrality would refer to the number of 'items' or 'flow rate' going through the node.

$$
\begin{align}
x_i &= \sum_{v_s, v_z}{1(E)} \\
\text{where }1(E) &= \begin{cases}
	0,& \text{if } \neg E\\
	1,& \text{otherwise}
\end{cases}
\end{align}
$$

More generally, when $v_s$ and $v_t$ have more than one shortest path:

$$
x_i = \sum_{v_s, v_t}{\frac{n_i(s, t)}{g(s,t)}} \text{ for } v_s\neq v_t
$$

Where $n_i(s,t)$ is the number of shortest paths between $v_s$ and $v_t$ that contain $v_i$, and $g(s,t)$ is the number of shortest paths between $v_s$ and $v_t$.
