Reservoir computing is a new form of [[Machine Learning|machine learning]] largely based on [[Recurrent Neural Network (RNN)|RNN]] theory. It (ideally) maps input signals into potentially higher dimensional computational spaces through dynamics of a fixed non-linear system called a reservoir.

After the input signal is fed into the reservoir, which is treated like a [[black box]], a simple readout mechanism is trained to read the state of the reservoir and map it to the desired output. This has two benefits:

1. Since training only occurs on the output stage, and reservoir dynamics are (relatively) fixed, training is 'easier'.
2. Computational power of naturally available systems (potentially [[quantum mechanics|quantum]] or [[Mechanical Engineering|mechanical]]) may be leveraged to reduce computational cost.
