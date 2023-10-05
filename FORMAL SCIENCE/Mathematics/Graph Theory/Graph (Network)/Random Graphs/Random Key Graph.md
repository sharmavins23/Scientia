A random key graph is a type of [[Random Graph|random graph]] that focuses on a more 'natural' approach to creating small-world networks, like the [[Watts-Strogatz 'Small-World' Model|Watts-Strogatz model]] attempts to do.

## Definition

For some inputs of $n$ nodes, $P$ objects/classes for the nodes to choose from, and $K$ objects that each node picks, each node selects $K$ objects uniformly at random from an object pool of size $P$. Then, $v_i\sim v_j$ if they have at least one common object.

The diameter of this graph is fairly small:

$$
d_{max}\approx\frac{\log(n)}{\log(\log(n))}
$$

The clustering coefficient is:

$$
P_r(v_i\sim v_j\mid \exists v_x:v_i\sim v_x \text{ and }v_j\sim v_x) \approx\frac{1}{K}
$$

They have a much larger clustering coefficient than [[Erdos-Renyi Model|Erdos-Renyi graphs]] when $P\gg K^3$. As such, they are 'small worlds' when $P\gg K^3$.

Notably, their distributions are *not* power-law.