The LC tank (also known as resonant circuits, tank circuits, or tuned circuits) are simple designs of [[inductors]] and [[capacitors]] together.

## Design

![[Inductor-Capacitor (LC) Tank.png]]

The capacitor has the following time-dependent [[current]] relationship:

$$I(t)=-C \frac{dV(t)}{dt}$$

As a voltage changes across the capacitor, it influences a change in current. As such, a capacitor may be 'charged' up from an external source. When placed in the circuit, it sees the inductor as initially discharged as a [[steady-state]] [[short circuit]].

At this point the circuit can be modelled as a capacitor and a [[resistor]] in series, as the wire has a small non-zero [[resistance]]. The capacitor discharges energy, and as it reduces in stored [[voltage|potential]], it produces a positive current according to the aforementioned relation.

An inductor has the following time-dependent voltage relationship:

$$V(t)=-L \frac{dI(t)}{dt}$$

As the capacitor is now connected to the inductor, and a current is flowing through, the inductor 'charges', increasing in voltage. This change in voltage then feeds the capacitor's change in voltage to 'flip' the current (as now a negative current is produced due to the charging of the inductor).

The result of these two energy stores placed in series is a circuit that continuously swaps, generating a proper [[alternating current]] signal.

### Example

The following is the circuit in action on [Falstad](https://www.falstad.com/circuit/circuitjs.html?ctz=CQAgjCAMB0l3BWcAmaCBsyCclnq2AMzpgAsYSClICkNApgLRhgBQANiMqXeqVz3BZkUcCEYxkYbsjj4E0qcgDs6KKwDGIYgA4Qfbej1hhomPEgQwcaEazKdy0jgR4wa85dYB3AXRMiukIikD6GegbOagahvkEBIFHB6gDmiVhqCUmyenShAG7g0sksIjGigkh5UGisAM5FZfzcvPz+IABmAIbsdfSsAE5++vxB5WwADunR-EkJhGaDjcktyf6sAPYgWCMVkFjG6HnQEOtAA). A separate battery loop gives initial charge to the circuit; Afterwards, it acts as an (imperfect) A/C oscillator. Resistors are added to add negligible resistance for circuit computation.