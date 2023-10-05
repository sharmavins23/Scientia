The configuration model is also known as the [[Random Graph|random graph]] with arbitrary degree distribution. These are graphs that are fully random in their connectivity, but an input specified variable is the degree distribution.

## Construction

Start with an arbitrary degree distribution:

$$
P_l=P_r(k=l) \text{ for } l=0, 1, 2, ...
$$

From here, we can generate a degree sequence. For each of the $n$ nodes, we can draw an independent sample from the distribution $P_l$ and let it be the node's degree. This may generate the degree sequence $k_1, ..., k_n$.

Each edge $v_i$ is given $k_i$ stubs, or 'half-edges'. These can be randomly paired together to form full edges. There are two ways to ensure that $\sum_{i=1}{k_i}$ is even, and there are no self-loops or multi-edges - Either one can repeat the entire process until a graph is obtained without self-loops or parallel edges, or the self-loops can be deleted to form a single edge out of a multi-edge.

The [[Diameter|diameter]] of these networks is $d\approx\log(n)$, so they have a small diameter. However, the clustering coefficient is similar to [[Erdos-Renyi Model|Erdos-Renyi graphs]].