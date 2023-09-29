Backpropagation is a method in [[Machine Learning|machine learning]] of 'training' a [[Artificial Neural Network (ANN)|neural network]]. The idea is simple:

1. Propagate training data through the model from the input to the predicted output, $\hat{y}$. This is the [[Feedforward Neural Network (FNN)|feedforward step]].
2. Adjust model weights to reduce error ([[Mean Squared Error|MSE]]) relative to the weights.
	1. The derivative of the error is found, and the weight is adjusted by a negative multiple of this derivative in a process known as [[gradient descent]].
3. Repeatedly update the weights until they converge, or the model has undergone enough iterations.
