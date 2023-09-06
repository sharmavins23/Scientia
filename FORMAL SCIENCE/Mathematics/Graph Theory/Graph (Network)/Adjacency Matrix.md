An adjacency matrix is a method to represent networks via [[linear algebra]]. For a particular graph, the following can be constructed:

$$
A_{ij} = \begin{cases}
	1,& \text{if } (v_i,v_j)\in E\\
	0,& \text{otherwise}
\end{cases}
$$

Where the ordered pair $(v_i, v_j)$ refers to some [[Edge|edge]] between two [[Node|vertices]] in the set of all edges, $E$. Another term for referring to this ordered pair existing in the set is to say the two nodes are 'adjacent' to each other.

Weights may also be applied within the adjacency matrix. As such the definition becomes:

$$
A_{ij} = \begin{cases}
	w_{ij},& \text{if } (v_i,v_j)\in E \text{ and } w_{ij}>0\\
	0,& \text{otherwise}
\end{cases}
$$

By definition, a graph with $n$ nodes may be represented by an $n\times n$ adjacency matrix (assuming the graph does not contain multiple connections from one node to another). However, non-simple graphs can also be represented, as the adjacency matrix allows for self-edges.

## Symmetries

If the graph is undirected, then its adjacency matrix $A$ must be symmetric. Thus, $A=A^T$ is always true, and $\forall i,j$, $A_{i,j} = A_{j,i}$. This is not necessarily the case for directed graphs.

If a graph is by definition simple (has no self-edges and no duplicate edges), then the matrix $A$ must have its main diagonal be zero.