Energy and power signals are [[Continuous-Time Signals|continuous-time signals]] that express energy and power. More formally, the formula for an energy signal is:

$$
\begin{align}
&E_x =\int_{-\infty}^{\infty}{|x(t)|^2}dt \\
0 < &E_x < +\infty \\
&P_x = 0
\end{align}
$$

An energy signal, by definition, has finite energy. When averaged over an infinite amount of time, this results in zero power.

The formula for a power signal is:

$$
\begin{align}
&P_x = \lim_{T\to\infty}{\frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}}}{|x(t)|^2}dt \\
0 < &P_x < +\infty \\
&E_x=+\infty
\end{align}
$$

A power signal has finite power. When accumulated over an infinite amount of time, this results in infinite energy.