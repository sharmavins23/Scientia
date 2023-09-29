The artificial [[Neuron (Computer Science)|neuron]] was found to be far simpler to compute with and construct than biological analogues, and as such was preferred over other neuron designs. The function is similar: The output $\hat{y}$ compares to its input vector $\vec{X}={x_1, x_2, ..., x_n}$ with the following computation:

$$
\hat{y}=\lambda\left(b + \sum_{i=1}^{n}{w_i\cdot x_i}\right)
$$

The function $\lambda$ is some arbitrary non-linear [[Activation Function|activation function]]. These are chosen arbitrarily, such that the output clustering on an $n$-dimensional graph may properly encapsulate the data from a statistical sense (without 'overfitting.')

The neuron is generally trained via [[Backpropagation|backpropagation]] in a [[Feedforward Neural Network (FNN)|feedforward neural network]].

## Mathematical Derivation

Suppose $w_{jk}^l$ refers to the *connection* from the $k$th neuron in the $(l-1)$th layer, pointing towards the $j$th neuron in the $l$th layer. The value $b_j^l$ refers to the bias of the $j$th neuron in the $l$th layer. Finally, $\hat{y}_j^l$ refers to the activation of the $j$th neuron in the $l$th layer. Then, we can compute the activations:

$$
\hat{y}_j^l = \lambda\left(\sum_{i=1}^{|(l-1)|}{\left(w_{ji}^l \cdot \hat{y}_j^{(l-1)}\right)} + b_j^l\right)
$$

The pure notation is far more cumbersome. However, this can be written in vectorized form:

$$
	\vec{\hat{Y}}^l = \lambda\left(\vec{W}^l \cdot \vec{\hat{Y}}^{(l-1)} + \vec{B}^l\right)
$$

