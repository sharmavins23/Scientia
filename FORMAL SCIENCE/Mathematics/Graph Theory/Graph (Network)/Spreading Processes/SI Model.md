The SI model is an example of [[Spreading Processes|spreading processes]] where individuals may either be susceptible $S$ or infected $I$.

## Analysis

For a population of $n$ individuals, let $S(t)$ refer to the number of susceptible nodes at time $t$. Let $X(t)$ be the number of infectious nodes. For all $t$, we have the following property:

$$
X(t)+S(t)=n
$$

At time $t=0$, we also have the following initial conditions:

$$
\begin{align}
X(0)& =X_0>0 \\
S(0)& =n-X_0
\end{align}
$$

Note that $X_0$ is the number of infected nodes at time $t=0$. Over time, the number of susceptible individuals $S(t)$ should decrease, and $X(t)$ should conversely increase. If each nodes get into contact with $\beta$ other nodes, on average, per discrete unit time, we can derive the differential equations for rates of change of $S(t)$ and $X(t)$:

$$
\begin{align}
X(t) &= n - S(t) \\
\frac{dX(t)}{dt} &= -\frac{dS(t)}{dt} \\
&= \beta \cdot X(t) \cdot \frac{S(t)}{n} \\
&= \beta \cdot x(t) \cdot s(t) \\
&= \beta \cdot x(t) \cdot (1-x(t))
\end{align}
$$

Similarly we can derive $\frac{dS(t)}{dt}$:

$$
\begin{align}
\frac{dS(t)}{dt} &= -X(t)\cdot \beta \cdot \frac{S(t)}{n} \\
&= -x(t)\cdot \beta \cdot s(t)
\end{align}
$$

To simplify the notation we generally let $x(t)=\frac{X(t)}{n}$ and $s(t)=\frac{S(t)}{n}$. Notably, the value of $x'(t)$ has a closed-form solution, and is known as the [[Logistic Differential Equation|logistic differential equation]] - The solution is given by the following:

$$
x(t)=\frac{x(0)e^{\beta t}}{1-x(0)+x(0)e^{\beta t}}
$$

As $t\to\infty$, we notice that $x(t)\to 1$. In other words:

$$
\lim_{t\to\infty}{x(t)} = 1
$$

