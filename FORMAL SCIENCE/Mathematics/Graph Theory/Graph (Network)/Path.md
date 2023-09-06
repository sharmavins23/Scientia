In [[Graph (Network)|graphs]], a path between [[Node|vertices]] $v_x$ and $v_y$ is an ordered sequence of vertices, starting at $v_x$ and ending with $v_y$ where each consecutive vertex is adjacent (and shares an [[Edge|edge]]). Simply, a path between two nodes is a series of connections.

Paths can either be represented by the nodes that are connected, or by edges that are traversed as well:

$$
\begin{align}
\text{path }v_x\to v_y &: \{v_x, v_i, v_j, ..., v_k, v_y\} \\
\text{path }v_x\to v_y &: \{(v_x, v_i), (v_i, v_j), ..., (v_k, v_y)\}
\end{align}
$$

The length of a path can be computed from the number of edges traversed, or one less than the number of vertices:

$$
\begin{align}
\text{length} &= |(v_i, v_j) \in \text{path}| \\
&=|v_i \in \text{path}| - 1
\end{align}
$$

The distance between vertices $v_i$ and $v_j$, or $d_{ij}$, can also be computed. This is simply the length of the *shortest* path. If for some $x,y$, if there exists no path between $v_x$ and $v_y$, then we say that $d_{xy}=\infty$.