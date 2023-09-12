Connectivity refers to whether a [[Path|path]] is connected between two [[Node|nodes]]. A [[Graph (Network)|graph]] is connected (or fully connected) if all nodes are connected to each other. A graph is $k$-connected if there are at least $k$ mutually disjoint paths between any two nodes. As such, the graph will remain connected despite the removal of any $(k-1)$ nodes or edges.

For a fully connected graph, $d_{ij}<\infty$ for all nodes $v_i, v_j$. Thus, the [[Diameter|diameter]] $d_{max}<\infty$ as well. By convention, we also view singleton nodes (that are not connected to any others) to be a 'fully connected' node as well. This is useful for counting [[Component|components]].

## Directed Connectivity

In directed graphs, a graph is called 'strongly connected' if any pair of vertices are connected by a path of directed edges. Directed graphs are called 'weakly connected' if this is not the case, but the undirected version is fully connected.

## Vertex-Connectivity and Edge-Connectivity

In a graph, vertex-connectivity $\kappa_v$ is the minimum number of vertices that can be removed from the graph in order to 'disconnect' it. Similarly, [[Edge|edge]]-connectivity $\kappa_E$ is defined as the minimum number of edges that can be removed from the graph in order for it to cease being fully connected.

These values are most commonly applied to undirected graphs, but can be technically defined for strong edge-connectivity, strong vertex-connectivity, etc. in directed graphs.

If a graph is not connected, $\kappa_V=\kappa_E=0$. Similarly if a graph is connected, at a minimum $\kappa_V\geq1$ and $\kappa_E\geq1$. Otherwise, $\kappa_V \leq \kappa_E$ for all graphs. Conceptually, deleting vertices deletes more edges, so deleting vertices is more efficient, and therefore the number of vertices needed to delete is lower or equal (in the worst case). This relates heavily to [[Menger's Theorem|Menger's theorem]].