STDP is a training method based closely on [[Hebbian Theory|Hebbian learning]] that adjusts the strength of connections between neurons based on the _timing_ of the pre-synaptic and post-synaptic spike.

STDP is usually described as an unsupervised training method for [[Spiking Neuron|spiking neurons]], as backpropagation does not function properly.

## Kheradpisheh, Et Al

In a [2016 paper](https://arxiv.org/abs/1611.01421), researchers at the University of Tehran developed a simplified setup of rules for STDP updating and unsupervised learning. The procedure for the connection between pre-synaptic neuron $i$ and post-synaptic neuron $j$ is as follows:

$$
\Delta w_{ij}=
\begin{cases}
\alpha^+ \cdot w_{ij}(1-w_{ij}) &\text{ if } t_i-t_j\leq 0 \\
\alpha^- \cdot w_{ij}(1-w_{ij}) &\text{ if } t_i-t_j\gt 0 \\

\end{cases}
$$

Note here that $\alpha^+$ and $\alpha^-$ are parameters here that can be controlled to increase or decrease spiking. The multiplier by $(1-w_{ij})$ was originally designed to keep the values within $[0,1]$ in the paper.

This ruleset can be further simplified: Choose two values $\alpha^+ > 1$ and $0 < \alpha^- < 1$. It may be helpful to have them be fractional inverses, i.e. $\alpha^+ = \frac{1}{\alpha^-}$. Also, choose some $w_{max}$ and $w_{min}$ such that the values never overflow (and saturate too high!) and underflow. In order to train some neuron $j$ based on its pre-synaptic pulse timing $i$, the following rule can be applied:

$$
\Delta w_{ij} = \begin{cases}
\min(\alpha^+\cdot w_{ij}, w_{max})&\text{ if } t_i \leq t_j \\
\max(\alpha^- \cdot w_{ij}, w_{min}) &\text{ if } t_i > t_j
\end{cases}
$$

The writers posit that selection of the training values $\alpha^*$ carries with it some importance towards the problem. Selecting larger values (in magnitude) will make the network more 'forgetful', as the change in knowledge per step will heighten. Furthermore, $\alpha^+$ being more influential than $\alpha^-$ will encourage the network to learn more than forget.

## Nair, Shen, Smith

In their [2021 paper](https://arxiv.org/abs/2105.13262), the team at NCAL proposes a series of rules for STDP update. It is implemented locally at each [[Synapse|synaptic connection]] for [[Spiking Neuron|temporal neurons]]. One chief difference of this structure (compared to its contemporaries) is the conceptualization of neurons that 'never spike' - Their spike timings are set to $\infty$ by default.

NCAL STDP sets a series of cases based on the timing of the input spike $t_i$ and output spike $t_j$. The cases are:

$$
\Delta w_{ij} = \begin{cases}
B(\mu_c) &\text{ if } t_i\leq t_j, & &t_j\neq\infty\\
-B(\mu_b) &\text{ if } t_i > t_j & &\\
B(\mu_s) &\text{ if } &t_i\neq \infty, &t_j=\infty
\end{cases}
$$

The notation of $B(\mu_*)$ refers to the choosing of a [[Bernoulli]] random variable, where $\mu_*$ is a parameter.

1. **Capture:** If the pre-synaptic spike comes first, then the weight is increased with a chance of $\mu_c$.
2. **Back-off:** If the pre-synaptic spike comes later (or never comes), the input didn't 'matter', so the weight is decreased with a chance of $\mu_b$.
3. **Search:** If the post-synaptic cell never spikes, the weight is increased very rarely. This encourages excitative behavior.

Note that with the mathematics prescribed, $\infty$ is greater than any value excluding $\infty$. This STDP structure also only allows for discrete increments and completely ignores floating-point values whatsoever (due to their poor hardware power efficiency).

STDP can be used in the context of a weight incoming to a particular temporal neuron. However, more often, the NCAL team applied it via a Winner-Takes-All lateral inhibition (WTA-LI) column of temporal neurons, where the STDP training rules are based on the column's inputs.

### R-STDP

The NCA lab also designates a _supervised_ form of STDP - Reinforcement Learning STDP, or R-STDP. R-STDP adds a new _reward_ signal that is two bits. These two bits can encode $-1$, $0$, $1$, or _off_ as 11, 00, 01, and 10 respectively. When R-STDP is off, unsupervised STDP is simply used.

The cases are modified as follows:

1. If the neuron's output matches the desired output, $R=1$. STDP search is disabled, but the other rules are performed as normal.
2. If the neuron's output _does not_ match the desired output, $R=-1$. Case 2 is disabled; For case 1, the weight is decremented _instead_ of increased.
3. If the neuron never spikes, only case 3 operates (and $R=0$).

R-STDP allows the temporal neuron to be trained to expect particular patterns, and is typically only applied for the final output column of a network. In this way, temporal neural networks are often treated as [[Liquid State Machine (LSM)|liquid state machines]] with particular arrangements, where training is mostly a black box (other than particular parameters).
