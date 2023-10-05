The Watts-Strogatz model is a [[Random Graph|random graph]] generation model that produces graphs with small-world properties, including short average path lengths. It creates low [[Diameter|diameter]], high [[Clustering Coefficient|clustering coefficient]] graphs.

## Definition

Given a network with $n$ [[Node|nodes]] and average degree $\bar{k}$, Watts and Strogatz defined the 'small-world' property through the following two conditions:

1. The diameter is 'small' as n an [[Erdos-Renyi Model|Erdos-Renyi graph]], i.e:$$d_{max}=\frac{\log(n)}{\log(\bar{k})}$$
2. The clustering coefficient is much larger than the $G(n;p)$ Erdos-Renyi model. More precisely, they define it as: $$P_r(v_i\sim v_j\mid \exists v_x:v_i\sim v_x \text{ and }v_j\sim v_x) \gg P_r(v_i\sim v_j)$$

This 'small-world' definition does not talk about distribution, but notably, they are *not* power-law distributions.

### Construction of a Lattice

An alternative to make a less 'random' Erdos-Renyi graph would be to design a regular lattice with inputs $n, k$, where $n$ is the number of vertices and $k$ is the number of edges per vertex. Vertices are simply placed on a circular or rectangular grid, and are connected to the $k$ others that are closest.

Conceptually, this is problematic - With a diameter of $\frac{n}{k}$, the diameter of this structure would be extremely large (as with all graphs where nodes are only 'proximal'). The clustering coefficient of this graph is also not extremely large.

The construction Watts and Strogatz made was to take the small-world model, starting with the regular lattice. For every node, they randomly decided to rewire or keep each of its edges with probability $p$ and $1-p$ respectively. The 'rewiring' is redrawing the edge to an arbitrarily chosen (random) node in the graph. When $p=1$, we get an Erdos-Renyi graph; When $p=0$, we keep the lattice. Presumably, within $0<p<1$, we get a 'small-world'.