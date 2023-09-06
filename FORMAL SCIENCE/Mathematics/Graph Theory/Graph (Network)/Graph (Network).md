Graphs (also known as networks) are representations, or models, of physical, [[Biology|biological]], social, and engineering-based systems. Often, they are visually depicted as graphs, and studied in a process known as [[Graph Theory|graph theory]]. Graphs can also be represented via [[Adjacency Matrix|adjacency matrices]].

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
- [[Betweenness Centrality]]
- [[Assortative/Dissortative Mixing]]
- [[Largest Component]]
- [[Connectivity]]

### Clustering Coefficient

A clustering coefficient is a measure of the degree to which nodes in a graph tend to cluster together. Evidence suggests that in real-world networks (and in particular, [[social networks]]), nodes tend to cluster together tightly due to high density of ties.

### Diameter

Diameter is the greatest distance between any two connected nodes. This links back to a "small-world" theory - Human social connections are theorized to have a diameter of 6, as humans have 6 degrees of separation, supposedly.

### Betweenness Centrality

Betweenness centrality is a way of detecting the amount of influence one node has over information flow in a graph.

### Assortative/Dissortative Mixing

This value asks whether nodes with similar attributes are more or less likely to link to each other.

### Largest Component

Components are groupings of nodes that are all interconnected. As such, the largest component is simply the largest set of nodes that are all interconnected.

### Connectivity

Connectivity refers to whether a path is connected between two nodes. A graph is connected if all nodes are connected to each other. A graph is $k$-connected if there are at least $k$ mutually disjoint paths between any two nodes. As such, the graph will remain connected despite the removal of any $(k-1)$ nodes or edges.
