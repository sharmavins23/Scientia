In [[Graph (Network)|graphs]], the degree of a [[Node|node]] $v_i$ is denoted by $k_i$ and is simply the number of [[Edge|edges]] incident on that node. For an undirected graph, it can be computed as:

$$
k_i = \sum_{j=1}^{n}{A_{ij}}
$$

For directed graphs, we distinguish in-degree and out-degree separately for edges coming toward the node and going out of the node, respectively. This can be defined as:

$$
\begin{align}
k_i &= k_{ii} + k_{io} \\
&= \sum_{j=1}^{n}{A_{ij}} + \sum_{j=1}^{n}{A_{ji}}
\end{align}
$$

The degree of a node in a network represents the number of connections it has, and the degree distribution is the probability distribution of these degrees over the whole network.

## Average Degree

One can compute the average degree, or average connectivity.

### Undirected Graphs

The average degree can be computed as:

$$
\bar{k}=\frac{\sum_{i=1}^{n}{k_i}}{n}
$$

There is a special relationship between $\bar{k}$ and the total number of edges in a simple graph, $m$:

$$
\bar{k}n = 2m
$$

Conceptually, this makes sense: If we have $5$ edges in a graph, then $\bar{k}n$, or the simple sum of all degrees in the graph, is double, since each edge connects two nodes. This also implies another way to compute the average degree:

$$
\begin{align}
\bar{k}&=\frac{\sum_{i=1}^{n}{k_i}}{n} \\
&=\frac{2m}{n}
\end{align}
$$

### Directed Graphs

For directed graphs, we can compute average in-degree and out-degree:

$$
\begin{align}
\bar{k_i} &= \frac{\sum_{i=1}^{n}{k_{ii}}}{n} \\
\bar{k_o} &= \frac{\sum_{i=1}^{n}{k_{io}}}{n}
\end{align}
$$

By definition, $\bar{k_i} = \bar{k_o}$. We can also compute $\bar{k} = \bar{k_i} + \bar{k_o}$ - Once again, $\bar{k}n = 2m$. Since the original definitions apply, this means:

$$
\begin{align}
\bar{k}&=\frac{\sum_{i=1}^{n}{k_i}}{n} \\
&=\frac{2m}{n} \\
\text{since }\bar{k_i}&=\bar{k_o} \text{ and } \bar{k} = \bar{k_i} + \bar{k_o}, \\
\therefore \bar{k_i}=\bar{k_o}&= \frac{m}{n}
\end{align}
$$

## Variance

Degree variance is defined similar to random variables in statistics:

$$
\begin{align}
var(k)&=\bar{k^2} - (\bar{k})^2 \\
&= \frac{1}{n} \sum_{i=1}^{n}{(k_i - \bar{k})^2} \\
&= \left(\frac{1}{n} \sum_{i=1}^{n}{k_i^2}\right) - (\bar{k})^2
\end{align}
$$

## Distribution

For each $P=0, 1, ..., n-1$, the value $P_l$ can be defined as:

$$
P_l = \frac{|v_i \text{ where } k_i=l|}{n}
$$

One interpretation of $P_l$ is the probability that a randomly selected node has a degree of $l$. There are many cases where degree distribution is the key to understanding the outcome of a spreading process in a graph.