Graphs (also known as networks) are representations, or models, of physical, [[Biology|biological]], [[Social Science|social]], and engineering-based systems. Often, they are visually depicted as graphs, and studied in a process known as [[Graph Theory|graph theory]]. Graphs can also be represented via [[Adjacency Matrix|adjacency matrices]].

## Formal Definition

A graph $G$ is formally defined as an ordered pair:

$$
\begin{align}
G&=(V,E) \\
V&=\{v_1, ..., v_n\}\\
E&=\{(v_i, v_j), ..., (v_k, v_l)\}
\end{align}
$$

Where in this case, $V$ is the set of [[Node|vertices]], and $E$ is the set of ordered pairs representing [[Edge|edges]]. The total number of edges in the graph, $m$, can also be computed as $|E|=m$.

Graphs can be directed or undirected. A graph is also called 'simple' if it does not have any self-edges (no edges $(v_i, v_j)$ such that $i=j$), and has at most one edge between two nodes.

## Features

Networks have a series of different values that can be computed from them:

- [[Degree]]
- [[Clustering Coefficient]]
- [[Diameter]]
- [[Component]]
- [[Connectivity]]
- [[Degree Centrality]]
- [[Betweenness Centrality]]
- [[Assortative/Dissortative Mixing]]
### Assortative/Dissortative Mixing

This value asks whether nodes with similar attributes are more or less likely to link to each other.
