Erdos-Renyi [[Random Graph|random graphs]] are of the earliest studied random graph models, named after mathematicians Paul Erdos and Alfred Renyi, who introduced the models in 1959.

## Definition and Properties

The Erdos-Renyi graph can be defined as a graph $G(n;p)$, an undirected graph with $n$ [[Node|nodes]] and $p$ probability of forming an [[Edge|edge]] between every pair of nodes. Each of these node formations is *independent* of each other.

Characteristically, they have small diameters, but tend to have smaller clustering coefficients and do not have power-law degree distributions.

### Number of Edges

The total number of edges of $G(n;p)$ is simply random. We can instead compute the expected value of the number of edges, $m$, as:

$$
\begin{align}
\bar{m} &= \binom{n}{2}\cdot p \\
&= \frac{n(n-1)}{2}\cdot p
\end{align}
$$
### Degree

The expected value of the [[Degree|degree]] can be computed from a prior formula:

$$
\begin{align}
\bar{k}&=\frac{2m}{n} \\
&= \frac{2}{n}\cdot m \\
&= \frac{2}{n}\cdot \frac{n(n-1)}{2}\cdot p \\
&= (n-1)p
\end{align}
$$

The probability distribution of the degree of an arbitrary node in $G(n;p)$ can be stated as:

$$
\begin{align}
P_r(k_i=l) &= \binom{n-1}{p}\cdot p^l(1-p)^{n-1-l} \text{ for } l=0,1,...,n-1 \\
&= \text{Binomial}(n-1;p)
\end{align}
$$

Remember for the [[Binomial Distribution|binomial]], the first parameter is the number of trials, and the probability $p$ is the probability of a success.

Degree variance can also be given as:

$$
\begin{align}
\text{var}(k_i)&=(n-1)p(1-p) \\
&= \bar{k}(1-p) \leq \bar{k}
\end{align}
$$

Since the degree variance is small, we do NOT expect to see hubs in this model. In fact, the binomial distribution approximates the [[Poisson distribution|Poisson]] for $n\to\infty$ and $np=k$.

### Clustering Coefficient

The local [[Clustering Coefficient|clustering coefficient]] $C_i$ of a [[Node|node]] $v_i$ in $G(n;p)$ is random, but its mean value can be computed:

$$
\begin{align}
E[C_i] &= E\left[\frac{\Delta_i}{\binom{k_i}{2}}\right] \\
&= E\left[E\left[\frac{\Delta_i}{\binom{k_i}{2}}\mid k_i\right]\right] \\
&= \sum_{k=0}^{n-1}{\left(E\left[\frac{\Delta_i}{\binom{k_i}{2}}\mid k_i\right]\cdot P_r(k_i=k)\right)} \\
&= \sum_{k=0}^{n-1}{\left(p\cdot P_r(k_i=k)\right)} \\
&= p\sum_{k=0}^{n-1}{P_r(k_i=k)} \\
&= p
\end{align}
$$

More commonly, clustering coefficient is defined as the probability an edge exists between two nodes $v_i$ and $v_j$, given that they share a neighbor $(v_i, v_x)$ and $(v_x, v_j)$. This is written as:

$$
P_r(v_i\sim v_j\mid \exists v_x:v_i\sim v_x \text{ and }v_j\sim v_x)
$$

For Erdos-Renyi graphs, edges are drawn between nodes with probability $p$, independently, so the above definition yields a clustering coefficient of $p$. The $G(n;p)$ model notably does not have a high clustering coefficient.

### Giant Component

What should $p$ or $\bar{k}$ be for $G(n;p)$ to have a giant component with high probability (as $n\to\infty$, $p\to 1$)? We need some $\bar{k}>1$ for a giant component to exist. There are a set of theorems for this. First, let $p=\frac{c}{n}$ for some $c>0$, i.e., $\bar{k}\approx c$.

If $c<1$, then the size of the largest component $C_{max}$ satisfies:

$$
C_{max}=O(\log(n))
$$

If $c>1$, then there is a unique giant component such that:

$$
\frac{C_{max}}{n}\approx S>0
$$

More precisely, as $n\to\infty$, the value $\frac{C_{max}}{n}\to S$. This value $S$ is given by the solution of the following:

$$
S=1-e^{-cS} \text{ for } S\in (0, 1]
$$

All other components are of size $O(\log(n))$. To solve the problem, one can naively plot $y=S$ and $y=1-e^{-\bar{k}S}$ on the same figure, varying $S$, and look for intersection points. If $\bar{k}=c>1$, there will be a secondary solution.

### Connectivity

A separate theorem exists: If $p=c\cdot\frac{\log(n)}{n}$ for some $c>0$, e.g. if $\bar{k}=c\cdot\log(n)$, then:

- If $c<1$, then $G(n;p)$ is not connected with high probability.
- If $c>1$, then $G(n;p)$ is connected with high probability.

This distinction arises from the dichotomy seen in the mean number of isolated nodes in the graph - We can compute the number of isolated nodes as:

$$
\begin{align}
E[\text{isolated}]&=E\left[\sum_{i=1}^{n}{\mathbb{1}[\text{isolated}]}\right] \\
&= \sum_{i=1}^{n}{P_r(\text{isolated})} \\
&= n(1-p)^{n-1} \\
&\approx n\cdot e^{-p(n-1)} \\
&= n\cdot e^{-c\frac{\log(n)}{n}(n-1)} \\
&= e^{\log(n)-c\log(n)} \\
&= e^{(1-c)\log(n)} \\
&= n^{1-c}
\end{align}
$$

We see that if $c<1$, the expected number of nodes is $\infty$; Otherwise the number of isolated nodes trends towards $0$.

### k-Connectivity

A third theorem: With any $k=1, 2, 3, ...$, let the following $p$:

$$
p=\frac{\log(n)+(k-1)\log(\log(n)) + w_n}{n}
$$

This is the same as defining $w_n$ as:

$$
w_n=pn-(\log(n)+(k-1)\log(\log(n)))
$$

Then, the following is true:

$$
P_r(G(n;p) \text{ is }k\text{-connected})\underset{x\to\infty}{\rightarrow}\begin{cases}
1, &\text{if }w_n\to\infty \\
0, &\text{if }w_n\to-\infty \\
\end{cases}
$$

We can also compute the probability above, assuming $w_n\to w$:

$$
P_r(G(n;p) \text{ is }k\text{-connected})=e^{-e^{-w}}
$$
### Diameter and Average Path Length

Note that while Erdos-Renyi graphs do not look like most real-world social networks, they do resemble real-world networks in terms of diameter.

$$
\begin{align}
d_{max} &\approx \frac{\log(n)}{\log(np)} \\
&= \frac{\log(n)}{\log(\bar{k})}
\end{align}
$$

Thus, Erdos-Renyi models have fairly small diameters.