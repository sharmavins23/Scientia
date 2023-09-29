The Hodgkin-Huxley [[Neuron (Computer Science)|neuron]] is an implementation of a [[Neuron|biological neuron]] as an [[Analog Circuits|analog circuit]]:

![[Hodgkin-Huxley model of a neuron.png]]

This design implements the [[Action Potential|firing potential]] of the cell, only firing once that body potential reached a threshold. Mathematically, the current flowing through the lipid bilayer $C_m$ can be:

$$
I_c = C_m \frac{dV_m}{dt}
$$

The current through a given ion channel would be the product of the channel's conductance and the driving potential for the ion:

$$
I_i = g_i(V_m - V_i)
$$

With this, the total current through the membrane could be written as:

$$
I = C_m \frac{dV_m}{dt} + g_K(V_m-V_K) + g_{Na}(V_m-V_{Na}) + g_l(V_m-V_l)
$$

This is for a 'normal' cell with sodium and potassium channels.