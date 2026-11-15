# Lab 01 — Worked solutions and checks

[Lab](../labs/01-dc-circuits.md) · [Course](../COURSE.md)

These answers use ideal nominal components and Vs = 5.000 V unless stated otherwise. Replace them with your measured values for the physical comparison. Numerical answers below have been checked algebraically; they are not bench measurements.

## Nodal solution

For all three lower branches present,

`(Vs − Vout)/R1 = Vout(1/R2 + 1/RL + 1/Rm)`.

Therefore,

`Vout = Vs / (1 + R1/R2 + R1/RL + R1/Rm)`.

An absent branch contributes zero conductance. Equivalently, combine the lower resistors in parallel and use an ordinary divider. With no load or meter,

`Vout = Vs R2/(R1 + R2)`.

## Thévenin equivalent

For R1 = R2 = 10 kΩ,

`Vth = 2.5 V`, and `Rth = R1 || R2 = 5 kΩ`.

With load RL and no meter,

`Vout = Vth RL/(Rth + RL)`.

For a connected meter, replace RL by `RL || Rm`; for a meter alone, use Rm as the port load. The ideal source is shorted only in the mathematical equivalent-resistance calculation.

## Prediction table

| Case | Output voltage | Current through R1 |
| --- | ---: | ---: |
| A — 10 kΩ/10 kΩ, no load/meter | 2.500000 V | 250.0000 µA |
| B — additional 10 kΩ load, ideal meter | 1.666667 V | 333.3333 µA |
| C — case B plus 10 MΩ meter | 1.666111 V | 333.3889 µA |
| D — 1 MΩ/1 MΩ, no load/meter | 2.500000 V | 2.500000 µA |
| E — case D plus 10 MΩ meter | 2.380952 V | 2.619048 µA |

For B, R2 and RL each carry 166.6667 µA. For C, the meter current is approximately 0.1666 µA; the small extra branch explains the increased current through R1. For E, meter loading reduces the ideal output by about **4.762%**. The same nominal meter that was nearly negligible in B is consequential in E.

Scaling the divider resistances upward preserves its unloaded ideal ratio but increases port resistance. Current and power decrease while finite meter resistance has a greater effect. “High impedance” is relative to the connected instrument and load.

## Power balance for case B

The upper resistor drops 3.333333 V; the lower and load each drop 1.666667 V.

- R1 absorbs approximately **1.111111 mW**.
- R2 absorbs approximately **0.277778 mW**.
- RL absorbs approximately **0.277778 mW**.
- Their total is **1.666667 mW**, equal to the source's delivered power, 5 V × 333.3333 µA.

The source's absorbed power is negative under passive sign convention. Include the meter's dissipation if checking power for case C. These powers are comfortably small, but the method must be applied again when values or source voltage change.

## Sensitivity and uncertainty

For `y = Vs R2/(R1 + R2)`, the derivatives are:

`∂y/∂Vs = R2/(R1 + R2)`

`∂y/∂R1 = −Vs R2/(R1 + R2)²`

`∂y/∂R2 = Vs R1/(R1 + R2)²`.

For independent inputs, multiply the squared derivatives by the input variances and add. If inputs share errors, include the covariance terms. Source uncertainty enters with relative sensitivity 1. At equal resistances, the relative sensitivities to R1 and R2 are −1/2 and +1/2.

For independent resistor bounds of ±1%, the exact worst-case ratio is obtained with one high and the other low:

`Vout/Vs ∈ [0.495, 0.505]`.

At exact 5 V, that is **2.475–2.525 V**. This is a bound under the stated component limits, not a confidence interval.

If each resistor's relative error is additionally assumed uniform over ±1%, its relative standard uncertainty is 0.01/√3. The first-order relative standard uncertainty of the divider output due to the two resistors is:

`sqrt[(1/2)² + (1/2)²] × 0.01/sqrt(3) ≈ 0.004082`.

This is **0.4082%**, or about **10.21 mV standard uncertainty** at 2.5 V, before source/meter effects. The smaller number does not contradict the worst-case interval: it answers a different question with a distributional assumption.

A meter's loading is a deterministic model term when its input resistance is known. Uncertainty in that resistance is an additional uncertainty term. Repeating a loaded reading cannot remove the loading error or a shared calibration bias.

## Transfer problem 1 — 80% of open-circuit voltage

Set `RL/(Rth + RL) = 0.8`. Then `RL = 4Rth = 20 kΩ` for the original divider, and Vout = **2.0 V**. A finite meter would be in parallel with this load and lower the output slightly further.

## Transfer problem 2 — less than 1% meter loading

With only the meter attached, the fractional voltage reduction is:

`1 − Rm/(Rth + Rm) = Rth/(Rth + Rm)`.

For a reduction strictly below 1%, require `Rm > 99Rth`. The 1 MΩ/1 MΩ divider has Rth = 500 kΩ, so **Rm > 49.5 MΩ**. At exactly 49.5 MΩ the error is 1%; a 10 MΩ meter does not meet the requirement.

## Transfer problem 3 — maximum power and efficiency

Load power is `P_L = Vth² RL/(Rth + RL)²`. Differentiating gives a maximum at **RL = Rth = 5 kΩ**, where Vout = **1.25 V** and:

`P_L,max = Vth²/(4Rth) = 0.3125 mW`.

In the original divider, the 5 V source current is `(5 − 1.25)/10 kΩ = 375 µA`, so its delivered power is **1.875 mW**. Load power divided by original-source power is **1/6 ≈ 16.67%**, not 50%.

The Thévenin source and series resistance reproduce the external port's I–V relation. Their internal power distribution is not generally that of the original network. The familiar 50% maximum-power efficiency applies to the simple series-source-resistance equivalent's own power accounting, not automatically to the original source and internal divider dissipation.

## Transfer problem 4 — loaded 1.0 V output

There are many solutions. Choose R2 = 10 kΩ, so R2 || RL = 5 kΩ for RL = 10 kΩ. To obtain Vout/Vs = 1/5, choose **R1 = 20 kΩ**.

Then R1 current is 4 V / 20 kΩ = **200 µA**; R2 and RL each carry **100 µA**. R1 dissipates **0.8 mW**, each lower branch **0.1 mW**, and the source delivers **1.0 mW**. Component and meter effects require the same uncertainty/loading analysis as before.

Choosing R1 = 40 kΩ and R2 = 10 kΩ from the unloaded 1:5 ratio would produce only **0.555556 V** after adding the 10 kΩ load. Specifying the operating load is part of the design problem.

## A discriminating measurement

To distinguish source resistance from a wrong load, measure the source terminals under two known loads and compare their voltage change with total delivered current. Separately measure the disconnected load resistance. If the source terminal voltage stays fixed while the output disagrees, a source-resistance explanation becomes less plausible; if the terminal voltage sags consistently with current, include a source model. Account for the loading and uncertainty of the tests themselves.
