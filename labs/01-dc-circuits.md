# Lab 01 — DC circuits, loading, and uncertainty

[Course Module 01](../COURSE.md) · [Laboratory rules](../LAB.md) · [Worked solutions](../solutions/01-dc-circuits.md)

**Time:** approximately 6–8 hours within Module 01's 16-hour allocation. Sections 1–4 can be done before buying hardware. Complete Module 00's measurement and wiring preparation before the physical experiment.

**Question:** How accurately can an apparently simple voltage divider predict the voltage delivered to another circuit, and when does the act of measuring it change the answer?

**Outcomes:** use KCL and Ohm's law, construct a Thévenin equivalent, include a load and a meter, check power, simulate a network, and distinguish component uncertainty from a missing physical effect.

## 1. Circuit and conventions

Use an ideal 5.000 V source for the initial calculation. In the physical experiment use a protected low-voltage source; a different measured voltage is fine if every prediction is recomputed. Do not use a GPIO as a 5 V source.

```text
                 R1 = 10 kΩ
    Vs (+) o-----/\/\/\------o Vout
           |                 |
           |                 +-----[ RL ]-----+
        source               |                |
           |              R2 = 10 kΩ          |
           |                 |                |
    GND  o-+-----------------+----------------+

    The voltmeter, when attached, is another branch from Vout to GND.
    RL is absent initially, then 10 kΩ.
```

Define GND as 0 V and the source's positive node as Vs. Define the upper-resistor current from Vs toward Vout, and lower/load/meter currents from Vout toward GND. Voltage is always a difference between two named nodes. Use passive sign convention for the resistors.

Before using formulas, explain in words what prevents the current through R1 from necessarily equalling the current through R2 once a load is attached.

## 2. Derive before simulating

1. Apply KCL at Vout with no load or meter. Derive Vout and the resistor currents from Ohm's law.
2. Attach an arbitrary load R_L. Write the new nodal equation before simplifying it.
3. Find the open-circuit Thévenin voltage V_th at Vout. To find R_th, deactivate the ideal independent voltage source by replacing it with a short circuit. Do not interpret “deactivate” as physically shorting your powered source.
4. Derive the loaded output using the Thévenin equivalent. Check agreement with the full network.
5. Add the voltmeter as a resistance R_m. Derive an expression that covers all three lower branches. Treat missing branches as infinite resistance.
6. Calculate resistor and source powers and check energy balance. The source delivers power, so its absorbed power has the opposite sign.

You should obtain an equation of the form:

`(Vs − Vout)/R1 = Vout/R2 + Vout/RL + Vout/Rm`.

For your first numerical prediction, set R_m to infinity. Do not hide the meter's contribution by rounding early.

## 3. Predictions to record

Complete this table yourself. Use nominal values initially; repeat with measured values later.

| Case | R1 | R2 | RL | Assumed Rm | Predict Vout | Predict current through R1 |
| --- | ---: | ---: | ---: | ---: | --- | --- |
| A | 10 kΩ | 10 kΩ | Absent | Infinite | Calculate | Calculate |
| B | 10 kΩ | 10 kΩ | 10 kΩ | Infinite | Calculate | Calculate |
| C | 10 kΩ | 10 kΩ | 10 kΩ | 10 MΩ | Calculate | Calculate |
| D | 1 MΩ | 1 MΩ | Absent | Infinite | Calculate | Calculate |
| E | 1 MΩ | 1 MΩ | Absent | 10 MΩ | Calculate | Calculate |

Cases C/E use an illustrative 10 MΩ meter. Your actual meter may differ by model, range or function; use its manual for the physical prediction. If you lack 1 MΩ resistors, simulate D/E now and obtain or construct suitable resistance later.

Also predict:

- The ratio Vout/Vs in each case.
- The power in each resistor for B.
- The load that receives maximum power from the port and that maximum power.
- Whether increasing all resistors by a factor of 100 changes the ideal divider ratio, meter error, current and dissipation.

## 4. KiCad/ngspice experiment

Use the installed KiCad schematic editor and its simulator, following [the versioned manual](https://docs.kicad.org/). No external component model is needed for ideal sources and resistors.

1. Create a schematic containing a SPICE-compatible DC voltage source, R1, R2 and a ground reference. Enter 5 V and the resistor values. Label the input and output nets clearly.
2. Check the simulation properties/model mapping of the source and components. Ensure the reference node is defined; a floating network cannot establish an absolute node voltage.
3. Run an operating-point analysis. Record both node voltages and resistor currents, including sign conventions.
4. Add RL and repeat. Then add an explicit resistor for Rm and repeat.
5. Simulate the high-impedance cases. Change Rm to your actual meter's specified input resistance.
6. Sweep load resistance from roughly 1 kΩ to 1 MΩ, using available DC/parameter-sweep facilities or several saved operating points. Plot Vout and delivered load power. Compare with your Thévenin prediction.

The ideal model should agree with your algebra to within numerical/reporting precision. Investigate sign conventions, missing junctions, units and accidental loads if it does not. In SPICE value entry, check the simulator's suffix convention: a megaohm value should be entered unambiguously as `1Meg` or `1e6`, rather than assuming `M` means mega.

Record your KiCad/ngspice versions and save the schematic and simulation settings. A screenshot alone is not enough to recreate the experiment.

## 5. Physical preparation

Equipment: DMM; breadboard and leads; at least three 10 kΩ resistors; two 1 MΩ resistors for the high-impedance extension; protected low-voltage source; component and meter documentation. A scope is unnecessary here.

1. With the source disconnected, map the relevant breadboard strips/rails using continuity mode. Note any rail breaks.
2. Measure each resistor out of circuit, label it, and record the meter range/resolution. An in-circuit resistance reading may include parallel paths.
3. Record the DMM's DC-voltage input resistance and accuracy specification for the selected range. If the input resistance is unknown, keep that parameter explicitly uncertain rather than declaring it 10 MΩ.
4. Check the meter is in voltage mode with the lead in the voltage jack. This lab infers current from voltage drops; direct current-mode measurement is optional and must use a correctly wired series path.
5. Measure the unloaded source voltage. Disconnect power, wire case A, and inspect the connections. Use only the low-voltage portion of a certified enclosed adapter or another appropriately protected source.

## 6. Measure the loaded and unloaded divider

1. Power case A. Measure Vs at the circuit input and then Vout. Record the time/order; if the source drifts, bracket the output measurement with input readings. Your output reading includes the meter load.
2. Infer the current through R1 from its measured voltage drop and resistance. Account for the meter's input resistance when comparing the current balance. Avoid implying that sequential node measurements are perfectly simultaneous.
3. Power off. Add the measured load resistor and predict the new output using measured values. Power on, measure, and compare.
4. Power off and build the high-impedance case. Predict the meter-induced reduction before attaching the meter. Repeat the measurements while keeping leads and surfaces clean. Do not touch the high-impedance node during a reading.
5. Recompute predictions with measured source/resistor values and the actual meter model. Compare the fractional voltage ratios as well as raw volts.

If the source setting changes under load, use the measured input voltage or extend the model with source resistance. Do not “correct” the data to the nominal source setting.

## 7. Uncertainty and model selection

For the unloaded ideal divider, define y = Vs R2/(R1 + R2). Derive its partial derivatives with respect to Vs, R1 and R2. For independent standard uncertainties, apply:

`u_y² ≈ Σ (∂y/∂x_i)² u_i²`.

For correlated quantities, replace this sum by the Jacobian–covariance–Jacobian expression. If two measurements use the same meter, identify which calibration errors may be shared. Repeated measurements reveal repeatability; they do not remove a common gain error.

Tasks:

1. For equal resistors with independent ±1% tolerance, calculate a worst-case divider-ratio range.
2. Separately assume each tolerance interval has a uniform distribution and calculate the first-order standard uncertainty of the ratio. Explain why this differs from a worst-case bound.
3. Include the source and DMM specifications in your physical model, stating how their published limits were converted to uncertainties or retained as bounds.
4. Decide whether a disagreement is better explained by permitted component variation or a missing meter load. Use the high-impedance case as evidence.
5. Design one additional measurement that discriminates source resistance from a mistaken load value.

Do not assign a probability distribution to a manufacturer's tolerance merely because a convenient formula requires one. State it as an assumption and assess whether it matters to the conclusion.

## 8. Transfer problems

Attempt these before reading the [solutions](../solutions/01-dc-circuits.md).

1. Choose a load that reduces the open-circuit output to 80% of its value. Derive the result before choosing an available resistor.
2. For the 1 MΩ/1 MΩ divider, find the minimum meter resistance that keeps loading below 1% of the ideal output. Does a 10 MΩ meter meet it?
3. For the original source/divider, evaluate load power and source power at the maximum-power load. Is the original network's source-to-load efficiency 50%? Explain what the Thévenin equivalent preserves and what it does not.
4. Design a nominal 1.0 V output from 5.0 V with a 10 kΩ load. Choose R1/R2 to satisfy the loaded requirement and check powers. Explain why choosing the unloaded resistor ratio first can fail.

## 9. Report and completion gate

Submit one concise report containing the schematic/reference directions; derivations; prediction table; saved simulation; measured component/source/meter information; raw readings; power balance; uncertainty model; discrepancy explanation; and one transfer-problem solution.

Pass when you can predict a new load's effect before connecting it, reproduce the simulation, and explain the physical measurements within a defensible model and uncertainty/bound. Complete the bench portion before marking the module physically complete. If equipment is still unavailable, record the analytical/simulation progress and leave the measurement gate open.
