Menger's theorem for [[Graph (Network)|graphs]] posits the following about [[Connectivity|connectivity]]:

1. There exist $\kappa_v$ vertex-independent paths connecting every pair of nodes.
	1. This, further translated, implies there are no common vertices among those paths.
2. There exist $\kappa_e$ edge-independent paths connecting every pair of nodes.
	1. Translated, this means there are no common edges among those paths.

This is the basis of the max-flow min-cut theorem - For a finite graph, the size of a minimum [[Cut|cut set]] is equal to the maximum number of disjoint paths found between any pair of vertices.