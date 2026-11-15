# Course: microelectronics from first circuits to advanced design

[Start page](README.md) · [Laboratory](LAB.md) · [Capstone](CAPSTONE.md) · [References](REFERENCES.md) · [Progress](PROGRESS.md)

## How to use the modules

Module hours include assigned reading, original derivations, exercises, the lab, and its report. The reading assignments select topics from the linked resources; completing every external course would substantially increase the workload. All required reading is freely accessible. Source IDs such as **R01** link to the annotated bibliography.

Each chapter's **External materials** section gives a suggested order: core written material, recommended viewing, then optional depth. The reading/viewing allowances are part of the existing module hours, not additional hours. Read only the specified sections and use videos to clarify the derivations; the full linked courses are optional. Historical lectures remain valuable for theory; current device manuals and the documentation for your pinned software govern implementation. Manufacturer videos may demonstrate proprietary tools: reproduce the concepts using KiCad/ngspice and the course's open-source programming tools.

**Jump to chapter materials:** [00](#materials-00) · [01](#materials-01) · [02](#materials-02) · [03](#materials-03) · [04](#materials-04) · [05](#materials-05) · [06](#materials-06) · [07](#materials-07) · [08](#materials-08) · [09](#materials-09) · [10](#materials-10) · [11](#materials-11) · [12](#materials-12) · [13](#materials-13) · [14](#materials-14) · [15](#materials-15) · [16](#materials-16) · [17](#materials-17) · [18](#materials-18).

Every module has four deliverables: an analysis, a simulation or numerical model, a physical experiment where specified, and an explanation of discrepancies. The **gate** is a concrete demonstration of readiness. Measurements need units, instrument settings, operating conditions, and uncertainty estimates. A justified discrepancy is more useful than a plot adjusted to match a prediction.

The default sequence is 00–18. Within it, device theory can proceed while equipment is being acquired. Module 16's early PCB exercises may follow Module 10; release the capstone PCB only after Module 17. Read the capstone brief early, but leave component values provisional until the relevant models have been tested.

## 00 — Laboratory orientation and the circuit abstraction

**8 hours · Prerequisites:** mathematics and programming · **Equipment:** computer; DMM and low-voltage source for the physical portion.

**Learn and derive.** Define charge, current, voltage, electromotive force, reference potential, and power with consistent signs. Relate KCL to charge conservation. Explain when a lumped model is appropriate, and why KVL needs care when time-varying magnetic flux links the measurement loop. Connect circuit energy flow to fields without replacing practical circuit analysis with a full field solution for every wire.

Learn resistor colour codes, component markings, schematic conventions, breadboard connectivity, split power rails, and datasheet pin diagrams. Distinguish a circuit reference node from protective earth and chassis. Learn the difference between a source setting and the actual voltage at its terminals under load.

**Exercises.** For a source feeding a resistor, assign reference directions and show that the algebraic sum of absorbed powers is zero. Explain why voltage is measured across a component and current through a branch. Draw the equivalent circuit of a voltmeter and then of an ammeter. Predict the consequence of placing each across a voltage source.

**Lab.** Inspect an unpowered breadboard with continuity mode. Map every connected strip and any rail breaks. Measure several resistors out of circuit. Identify the meter's input jacks, resistance-test limitations, fuse ratings, voltage range, and specified input impedance. Power a resistor from a protected low-voltage source; measure the source voltage and resistor drop. Infer current from resistance before attempting a series current measurement.

**Gate.** Draw the complete measurement circuit, including the meter. Explain the current path before energising it. Record your instruments and software versions. Follow [LAB.md](LAB.md) before starting any physical lab.

<a id="materials-00"></a>

### External materials

**Suggested order · about 2 hours of this module.**

1. **Core reading:** [MIT 6.002 — Lecture 1 written notes](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/resources/6002_l1/). Study the lumped-circuit assumptions, reference directions and circuit variables; connect them to charge conservation and your field-theory background.
2. **Core practical reading:** [KiCad 10 Getting Started](https://docs.kicad.org/10.0/en/getting_started_in_kicad/getting_started_in_kicad.html), “Basic concepts and workflow” and “Schematic editor basics.” Learn to express the physical connections unambiguously; defer PCB work.
3. **Watch — YouTube:** [MIT OCW, Lecture 1: Introduction and Lumped Abstraction](https://www.youtube.com/watch?v=AfQxyVuLeCs). Use it to check the abstraction and sign conventions before the first circuit.

**Optional depth:** [Fiore's open DC-circuits textbook](https://www.jimfiore.org/books/DCElectricalCircuitAnalysis.pdf), Chapter 2, for a continuous prose introduction to the electrical quantities; skim material already familiar from physics. Source notes: [R01](REFERENCES.md#r01), [R06](REFERENCES.md#r06), [R27](REFERENCES.md#r27).

## 01 — DC networks, loading, and equivalent circuits

**16 hours · Prerequisite:** 00 · **Equipment:** first purchase phase; scope not required.

**Learn and derive.** Ohm's law as a constitutive model, KCL/KVL, nodal analysis, dependent sources, superposition, Thévenin/Norton equivalence, source resistance, maximum power transfer, and resistor power ratings. Derive nodal equations as a linear system and interpret singular matrices as an electrical modelling problem. Include the source and meter in the network.

**Exercises.** Solve a three-node network by hand and with a matrix solver. Derive a loaded divider's output and sensitivity to each resistor. Prove Thévenin equivalence at the port. Show why maximum delivered power and maximum efficiency generally imply different operating points.

**Lab.** Complete [Lab 01](labs/01-dc-circuits.md): predict a divider; simulate it; load it; model the DMM; measure it; and propagate component uncertainty. Use its worked solutions only after making predictions. Extend it with a second load value selected to produce a specified voltage reduction.

**Gate.** Given a source network and a new load, predict terminal voltage, current, and dissipated power before wiring it. Explain discrepancies using measured component values, loading, source resistance, or uncertainty. Numerical agreement without an identified measurement model is insufficient.

**Capstone connection.** A photodiode, amplifier, ADC input, reference, and power rail all load one another. The ideal block diagram hides these interactions.

<a id="materials-01"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [MIT 6.002 lecture notes](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/pages/lecture-notes/), Lectures 2–3. Derive nodal analysis and source equivalents before applying them to the loaded divider.
2. **Watch — YouTube:** [MIT OCW, Lecture 2: Basic Circuit Analysis Method](https://www.youtube.com/watch?v=2vHGYdepKLw), then [Lecture 3: Superposition, Thévenin and Norton](https://www.youtube.com/watch?v=RsJ1eg7XNVs). Pause to solve each network before the lecturer does.
3. **Apply:** Work [Lab 01](labs/01-dc-circuits.md), particularly the equivalent-source and meter-loading calculations.

**Optional depth:** [Fiore's DC-circuits textbook](https://www.jimfiore.org/books/DCElectricalCircuitAnalysis.pdf), Chapters 3–7. Use the relevant worked examples for series/parallel networks, network theorems and nodal/dependent-source analysis; do not reread all elementary algebra. [Uncertainty reference: R05](REFERENCES.md#r05).

## 02 — Dynamic circuits, impedance, and frequency response

**24 hours · Prerequisite:** 01 · **Equipment:** RC parts; scope access for the physical transient gate.

**Learn and derive.** Capacitors and inductors from stored energy; initial conditions; first- and second-order differential equations; Laplace transforms; impedance; poles and zeros; phasors; complex power; resonance; Bode plots; and the relation between step and frequency response. Include capacitor ESR, inductor resistance, source impedance, and probe loading. Distinguish magnitude in dB, phase, group delay, and power ratios.

**Exercises.** Derive loaded RC low-pass and high-pass transfer functions. For an RC circuit with R = 10 kΩ and C = 100 nF, calculate the time constant and unloaded −3 dB frequency. Derive a series RLC response and identify its damping regimes. Predict how a finite probe resistance and capacitance change a measurement.

**Lab.** In KiCad, simulate an RC step and an AC sweep. Build the RC circuit and drive it using a low-frequency signal source or a correctly configured ESP32 GPIO square wave; use a series resistor and verify voltage limits. Observe input and output with the scope. Fit the time constant from waveform data. Add a resistive load and repeat. Use simulation for RLC exploration until suitable components and instrument access are available.

**Gate.** Recover an unknown RC time constant from a waveform and predict its frequency response. Explain why a bandwidth estimate changes when the circuit is loaded. Demonstrate both the physical trace and the model fit.

<a id="materials-02"></a>

### External materials

**Suggested order · about 4–5 hours of this module.**

1. **Core reading:** [MIT 6.002 lecture notes](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/pages/lecture-notes/), Lecture 12 and selected parts of 15–18. Follow the progression from stored energy and differential equations to second-order response, phasors, impedance and filters.
2. **Core simulation reading:** [ngspice manual](https://ngspice.sourceforge.io/docs.html), the introductory transient and AC-analysis sections. Reproduce one RC step and one frequency sweep using KiCad's simulator; read the manual matching its backend version.
3. **Watch — YouTube:** [MIT OCW, Lecture 12: Capacitors and First-Order Systems](https://www.youtube.com/watch?v=COdQmA9g9S8), then [Lecture 17: The Impedance Model](https://www.youtube.com/watch?v=Km9YIdkc2Oo). Relate the time- and frequency-domain descriptions of the same circuit.

**Optional depth:** [Fiore's open AC-circuits textbook](https://www.jimfiore.org/books/ACElectricalCircuitAnalysis.pdf), Chapter 1's reactance/impedance sections and Chapters 2–3 on series/parallel RLC circuits. Use this for additional worked circuits. [Tool references: R06–R07](REFERENCES.md#r06).

## 03 — Instruments, uncertainty, and experimental design

**16 hours · Prerequisites:** 01–02 · **Equipment:** DMM and scope access; low-voltage signal source.

**Learn and derive.** Instrument accuracy, resolution, bandwidth, input impedance, probe compensation, triggering, sampling, aliasing, and the effect of ground leads. Distinguish repeatability from bias and calibration. Develop uncertainty propagation using a Jacobian and covariance matrix; contrast worst-case bounds with probabilistic estimates. Plan measurements that distinguish competing explanations rather than merely collecting more data.

**Exercises.** Convert a DMM specification expressed as percent of reading plus counts into an uncertainty model. Propagate uncertainty through a voltage ratio and explain correlations when the same meter is reused. Estimate the rise-time limit imposed by finite bandwidth. Predict the error from a 1× probe on a high-impedance node.

**Lab.** Compensate a 10× probe using the instrument's reference output. Compare probe modes on the RC circuit. Measure the same waveform with a long ground lead and a short connection on this safe low-voltage circuit; account for any difference. Export raw data and fit a parameter with confidence bounds. Change the source amplitude or timebase as a controlled test of one suspected error.

**Gate.** Present a measurement with a stated measurand, bandwidth, uncertainty, and loading model. Show a case in which the probe or acquisition settings materially change the apparent result. Know where the scope ground is connected before attaching it.

<a id="materials-03"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [NIST Technical Note 1297](https://www.nist.gov/pml/nist-technical-note-1297), Sections 2–7 and [Appendix A: propagation of uncertainty](https://www.nist.gov/pml/nist-technical-note-1297/nist-tn-1297-appendix-law-propagation-uncertainty). Turn the compact treatment into a Jacobian/covariance calculation for your divider or RC measurement.
2. **Core practical reading:** [Tektronix, XYZs of Oscilloscopes](https://www.tek.com/en/documents/primer/xyzs-oscilloscopes-primer) ([university-hosted PDF](https://web.mst.edu/cottrell/ME240/Resources/Inst_manuals/XYZ%27s%20of%20oscilloscopes_2.pdf)). Select “The Complete Measurement System,” “Performance Terms and Considerations,” and “Operating the Oscilloscope.” Focus on probe loading, bandwidth, sample rate, grounding and compensation.
3. **Watch — YouTube:** [Keysight Labs, How to Use an Oscilloscope — Mega Guide](https://www.youtube.com/watch?v=t_UTV_9dpTc). Select the controls, triggering and probing material relevant to your lab; this is a bench companion, not an assignment to master every instrument feature.

**Optional depth:** [JCGM/GUM publications](https://www.bipm.org/en/committees/jc/jcgm/publications), JCGM 100 Sections 4–7 for measurement models, correlated inputs and reporting. Always consult your exact scope/probe/meter manuals before connecting them.

## 04 — Semiconductor physics, junctions, and photodiodes

**24 hours · Prerequisites:** 02–03 · **Equipment:** diodes, LED, photodiode, resistors; DMM; ADC or scope for data capture.

**Learn and derive.** Bands and carrier statistics; Fermi level; intrinsic and doped material; drift and diffusion; Poisson and continuity equations; recombination; depletion approximation; p–n junction equilibrium and bias; diode I–V behaviour; differential resistance; depletion/diffusion capacitance; generation of photocurrent; photovoltaic and photoconductive operation. State the nondegenerate, low-injection, temperature, and geometry assumptions behind simplified equations.

**Exercises.** Derive the built-in potential of a nondegenerate junction and its depletion-width scaling. Linearise the diode equation around a bias point. Explain why a photodiode is usefully modelled as a current source with capacitance and leakage, and why reverse bias changes more than its speed. Compare recombination and diffusion contributions to the observed ideality factor.

**Lab.** Measure a diode's I–V curve using a resistor-limited low-voltage source; infer current from the resistor drop. Plot linear and semilog axes and fit only a justified region. Repeat after a modest, measured ambient-temperature change. Measure a covered and illuminated photodiode through several load resistors. Observe when increased loading voltage invalidates a simple current-source model. Do not connect a bare junction directly across the source.

**Gate.** Fit an explicit physical/circuit model and identify a regime where it fails. Predict the qualitative tradeoff between detector area, capacitance, leakage, bandwidth, and sensitivity.

<a id="materials-04"></a>

### External materials

**Suggested order · about 4–5 hours of this module.**

1. **Core reading:** [MIT 6.012 lecture notes](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/resources/lecture-notes/), Lectures 1–6. Skim familiar statistics/transport physics, then derive the junction results in 4–6; [Lecture 4](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/resources/mit6_012f09_lec04/) starts the junction electrostatics sequence.
2. **Core device reading:** [Vishay BPW34 datasheet](https://www.vishay.com/docs/81521/bpw34.pdf), polarity/package, spectral response, capacitance and dark-current data, including their test conditions. Translate these into an equivalent circuit.
3. **Watch — YouTube:** [NPTEL/IIT Madras, S. Karmalkar — Solid State Devices, Lecture 19: PN Junction](https://www.youtube.com/watch?v=IMoJUqDlSQs). Use it as a second derivation of the junction model, then compare assumptions with MIT's notes.

**Optional depth:** Continue the university's [Solid State Devices course](https://nptel.ac.in/courses/117106091) only for topics where the physics-to-terminal-model connection remains unclear. MIT 6.012 is the core written course; a full NPTEL series is additional study.

## 05 — BJT and MOSFET circuits from physical models

**28 hours · Prerequisite:** 04 · **Equipment:** small-signal BJTs/MOSFETs, resistors, capacitors, DMM and scope.

**Learn and derive.** BJT operating regions, current gain limitations, Early effect, MOS electrostatics, threshold and body effect, strong/weak inversion, channel-length modulation, biasing, and load lines. Linearise at an operating point to obtain transconductance and output resistance. Study common-emitter/source, follower, current-source, differential-pair, and cascode circuits. Relate device capacitances and Miller effect to bandwidth. Treat square-law MOS behaviour as a model with a domain of validity.

**Exercises.** Derive g_m = I_C/V_T for the ideal forward-active BJT and the long-channel strong-inversion MOS relation g_m ≈ 2I_D/V_OV. Compare gain, input/output resistance, and headroom for three amplifier stages. Design a bias network whose operating point is less sensitive to current gain. Analyse a differential pair with a finite tail-source resistance.

**Lab.** Build a resistor-degenerated BJT amplifier with a measured DC operating point. Predict small-signal gain, apply a sufficiently small input, and sweep amplitude until clipping becomes visible. Measure its frequency response. Simulate a MOS amplifier, current mirror, differential pair, and cascode using documented models; physically build a simple MOS switching or follower circuit. Account for transistor package pinouts and available gate overdrive.

**Gate.** Select a bias point and defend gain, headroom, dissipation, and bandwidth. Explain a change caused by temperature or device substitution. A simulation with an unsuitable transistor model does not establish physical feasibility.

<a id="materials-05"></a>

### External materials

**Suggested order · about 5–6 hours of this module.**

1. **Core reading:** [MIT 6.012 lecture notes](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/resources/lecture-notes/), Lecture 7 on BJTs, 9–13 on MOS devices/linear models, and 17–19 on biasing, amplifier stages and differential pairs. Work from DC operating point to the local small-signal model; the notes are selected reading, not a second complete course.
2. **Watch — YouTube:** [MIT OCW 6.002, Lecture 9 part 1: MOSFET Amplifier Large-Signal Analysis](https://www.youtube.com/watch?v=Nijya-QJ45Y), then [Lecture 10: Amplifiers — Small-Signal Model](https://www.youtube.com/watch?v=9RqFFlZgf60). Check that the large- and small-signal models describe the same bias point.

**Optional depth:** MIT 6.012 Lectures 20–24 for multistage/differential/cascode behaviour and frequency limits; [MIT 6.002 Lecture 11: Small-Signal Circuits](https://www.youtube.com/watch?v=R4KxlqsuZ0A) for another circuit-analysis walkthrough. Keep the measured discrete amplifier and its device datasheet as the test of your model.

## 06 — Operational amplifiers, feedback, and stability

**28 hours · Prerequisites:** 02, 05 · **Equipment:** low-voltage op amps, passives, scope, low-voltage signal source.

**Learn and derive.** Differential and common-mode signals; finite open-loop gain; negative-feedback transfer A/(1 + Aβ); loop gain; sensitivity; Bode/Nyquist reasoning; phase/gain margins; noise gain; slew rate; saturation recovery; input bias/offset; common-mode range; output swing; and capacitive loading. Derive the virtual-short approximation from a stable, unsaturated closed loop rather than imposing it universally.

**Exercises.** Derive inverting and non-inverting transfer functions with finite open-loop gain. Separate noise gain from signal gain. Predict gain-bandwidth and slew-rate constraints for a sinusoid. Analyse a two-pole loop and choose a compensation strategy. Explain why a voltage follower can oscillate despite having an apparently simple signal transfer.

**Lab.** Build a non-inverting amplifier around a suitable low-voltage device. Measure DC errors, small-signal frequency response, and large-signal distortion. Introduce a controlled capacitive load within device limits and observe the step response; compare an appropriate isolation/compensation change. In simulation, obtain loop-gain evidence without disturbing DC bias. Relate this to measured ringing, acknowledging that step response alone is not a direct phase-margin measurement.

**Gate.** Produce a stable amplifier with documented input/output operating margins. Diagnose whether a faulty trace comes from saturation, slew limiting, loading, or an unstable loop. Explain which stability evidence is analytical, simulated, or measured.

<a id="materials-06"></a>

### External materials

**Suggested order · about 4–6 hours of this module.**

1. **Core reading:** [Roberge, Operational Amplifiers: Theory and Practice](https://ocw.mit.edu/courses/res-6-010-electronic-feedback-systems-spring-2013/resources/res6_010_s_13_coursetextbook_pdf/), Chapter 2 and the relevant stability/compensation sections of Chapters 4–5. Derive the loop equations and one two-pole example; defer unrelated applications.
2. **Core practical reading:** The same book's Sections 11.2–11.3 on specifications and precautions. Use the matching [MIT video-course manual](https://ocw.mit.edu/courses/res-6-010-electronic-feedback-systems-spring-2013/pages/video-course-manual/), Lectures 1, 4, 7–8, as a concise problem/derivation guide where needed.
3. **Watch — YouTube:** [MIT/Roberge, Lecture 1: Introduction and Basic Concepts](https://www.youtube.com/watch?v=ToEFkUxFURg), then [Lecture 7: Stability via Frequency Response](https://www.youtube.com/watch?v=KyO8jcUR254). Relate loop analysis to the amplifier you measure.

**Optional depth:** [Roberge, Lecture 8: Compensation](https://www.youtube.com/watch?v=akWLXjbYHK4), followed by [TI's TIA compensation note](https://www.ti.com/lit/an/sboa055a/sboa055a.pdf) as a bridge to Module 17. Historical circuit examples illustrate theory; use current specifications for your chosen op amp.

## 07 — Analog signal chains and filters

**22 hours · Prerequisites:** 05–06 · **Equipment:** op amps, RC parts, scope; matched resistors where needed.

**Learn and derive.** Buffers, instrumentation and differential amplifiers, level shifting, references, active/passive filters, Butterworth/Bessel responses, filter order and sensitivity, impedance interaction, CMRR, and rectification. Distinguish circuit poles from a complete system's useful passband. Include amplifier bandwidth, output loading, and reference impedance in a filter model.

**Exercises.** Design a second-order low-pass filter to a stated passband/stopband specification. Derive how resistor mismatch limits a difference amplifier's common-mode rejection. Budget output headroom across cascaded gain stages. Compare an active second-order filter with buffered cascaded RC stages, including their different pole placement.

**Lab.** Build a low-pass stage for a slow sensor signal. Measure gain and phase across at least one decade below and above its corner using a suitable source; fit the complete transfer function. Change one component deliberately and identify the resulting pole shift. Add a common-mode disturbance to a differential measurement within voltage limits and quantify rejection.

**Gate.** Meet a chosen bandwidth requirement and predict attenuation of an identified interference source. Demonstrate that the reference and ADC load have been included. Filter choice must follow a signal and interference specification.

<a id="materials-07"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [Roberge's open textbook](https://ocw.mit.edu/courses/res-6-010-electronic-feedback-systems-spring-2013/resources/res6_010_s_13_coursetextbook_pdf/), Section 11.4, “Representative Linear Connections.” Select the buffering, summing and differential connections relevant to your signal chain and derive their loading/error terms.
2. **Core filter reading:** [MIT 2.161, Lecture 8](https://ocw.mit.edu/courses/2-161-signal-processing-continuous-and-discrete-fall-2008/resources/lecture_08/), second-order sections and Section 3 on state-variable active filters. Use it to connect a pole specification to a realizable analog circuit.
3. **Watch — YouTube:** [MIT OCW 6.002, Lecture 18: Filters](https://www.youtube.com/watch?v=WT-qzgaKeGI). Use this as the passive-filter/frequency-response foundation, then extend it with the active-filter notes.

**Optional depth:** [TI, Active Filter Fundamentals](https://www.ti.com/video/6403725375112), a longer manufacturer-hosted lecture; focus on filter selection and implementation tradeoffs. Any WEBENCH workflow is optional—calculate and simulate your design in Python/KiCad. [SciPy's signal-processing tutorial](https://docs.scipy.org/doc/scipy/tutorial/signal.html) supports the numerical checks.

## 08 — Noise, precision, and statistical estimation

**26 hours · Prerequisites:** 03, 06–07; 04 for detector noise · **Equipment:** amplifier and shielded/covered sensor; scope and/or suitable ADC capture.

**Learn and derive.** Thermal and shot noise, 1/f noise, one-sided power spectral densities, input/output referring, equivalent noise bandwidth, correlated contributions, drift, interference, grounding, shielding, and the limits of averaging. Connect stochastic-process theory to a physical noise budget. Separate spectral density in V/√Hz from integrated RMS noise in volts.

For a resistor, use one-sided voltage PSD S_v = 4kTR; for ideal Poisson current, S_i = 2qI. Integrate each contribution through its own transfer function. Derive why a first-order low-pass has white-noise equivalent bandwidth πf_c/2. Include op-amp voltage/current noise, resistor noise, detector noise, and ADC effects with explicit assumptions.

**Exercises.** Calculate the noise density of a 100 kΩ resistor at 300 K. Integrate it through a 10 Hz first-order low-pass. Predict the benefit of averaging independent samples and explain why drift or autocorrelation violates that prediction. Estimate an input-referred noise spectrum from measured output data with a documented PSD normalisation.

**Lab.** Capture repeated dark/terminated-input records using the best available acquisition path. Compare histograms, spectra, RMS values, and averaging behaviour. Use a known gain to distinguish a measurement floor from front-end noise. If the instrument cannot resolve the predicted thermal floor, report an upper bound; do not interpret its own noise as detector noise. Repeat with wireless activity enabled and disabled.

**Gate.** Present a frequency-dependent noise budget and measured bound or result. Explain the dominant term, integrated bandwidth, and next worthwhile improvement. Verify that integrating the estimated PSD agrees reasonably with time-domain variance under matching processing.

<a id="materials-08"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [Analog Devices MT-047: Op Amp Noise](https://www.analog.com/media/en/training-seminars/tutorials/MT-047.pdf), the complete short tutorial. Build the equivalent voltage/current-noise model for your actual source impedance and feedback network.
2. **Core numerical reading:** [SciPy signal-processing tutorial](https://docs.scipy.org/doc/scipy/tutorial/signal.html), spectral-analysis and filtering sections. Check PSD units, normalisation, windowing and integration against a known synthetic signal before interpreting bench data.
3. **Watch — YouTube:** TI Precision Labs, [Spectral Density](https://www.youtube.com/watch?v=ewArZEGlLWw), then [Calculating RMS Noise](https://www.youtube.com/watch?v=ZhvdfHGORdQ). Reproduce the density-to-integrated-noise reasoning with your own transfer function. TINA-TI demonstrations are illustrative; use ngspice for the course work.

**Optional depth:** [MIT/Roberge, Effects of Feedback on Noise and Nonlinearities](https://www.youtube.com/watch?v=6HWeg0Q8VP4), or TI's [Measuring System Noise](https://www.youtube.com/watch?v=W2UUIUPmwdU) for a practical measurement follow-up. The [official TI op-amp course index](https://www.ti.com/en-us/design-development/educational-resources/video/series/precision-labs/ti-precision-labs-op-amps) provides companion resources.

## 09 — CMOS logic, timing, and digital integrity

**20 hours · Prerequisites:** 04–05 · **Equipment:** compatible logic ICs, buttons, RC parts, ESP32, scope and logic analyser.

**Learn and derive.** CMOS inverter transfer characteristics, switching thresholds, noise margins, static/dynamic power, propagation delay, fanout, pull resistors, open-drain versus push-pull outputs, Schmitt triggering, latches/flip-flops, setup/hold time, metastability, synchronisers, and state machines. Connect charging capacitance to switching energy and explain why logic correctness requires analog voltage and timing margins.

**Exercises.** Derive the approximate dynamic-power scaling αCV²f and define the activity convention used. Analyse a simple logic path against setup/hold constraints. Explain why a synchroniser reduces risk without eliminating metastability. Design a debouncer and compare hardware hysteresis with timed software sampling.

**Lab.** Observe button bounce. Build an RC/Schmitt input and compare it with a software debouncer. Capture a logic transition using the analog scope and logic analyser and explain why they reveal different information. Simulate a CMOS inverter's transfer curve and transient current; vary load capacitance and edge rate.

**Gate.** Turn an electrical input into a reliable logical event and justify its voltage and timing margins. Demonstrate a fault caused by a floating input or incompatible threshold without exceeding any absolute maximum ratings.

<a id="materials-09"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [MIT 6.012 lecture notes](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/resources/lecture-notes/), Lectures 14–16 on inverter behaviour, CMOS, delay and scaling. Derive the noise margins and capacitive switching model rather than treating a gate as an ideal Boolean operator.
2. **Core bench reading:** [PulseView manual](https://www.sigrok.org/doc/pulseview/0.4.2/manual.pdf), capture setup, trace navigation and decoding. Check your logic family's actual input thresholds and propagation specifications alongside this tool guide.
3. **Watch — YouTube:** [MIT OCW 6.002, Lecture 5: Inside the Digital Gate](https://www.youtube.com/watch?v=v6vqWasIHaw), then [Lecture 13: Digital Circuit Speed](https://www.youtube.com/watch?v=TXJIhDHtHSI). Connect the analog transition to its logical interpretation and timing consequences.

**Optional depth:** [MIT 6.002, Lecture 4: The Digital Abstraction](https://www.youtube.com/watch?v=4TCnYYpZxEc) if the interface between logical and electrical models needs a refresher. Use the scope and analyser together in the bounce/threshold experiment.

## 10 — Power, protection, and thermal design

**18 hours · Prerequisites:** 03, 05–06, 09 · **Equipment:** protected low-voltage source; current-limited supply access; suitable regulator/load parts and scope.

**Learn and derive.** Supply budgets, source resistance, decoupling, regulator dropout, PSRR, linear/switching-regulator principles, inrush, brownout, thermal resistance, reverse-polarity protection, fusing/current limiting, flyback paths, and connector ratings. Examine conducted noise and the impedance of a decoupling network. Keep switch-mode power-stage design simulation-led in the core.

**Exercises.** Estimate battery/runtime and regulator dissipation including peak loads and efficiency. Calculate the transient voltage drop for a load step with capacitive and resistive terms. Model thermal rise and explain the limitations of a single thermal-resistance number. Compare a buck regulator's ripple paths with a linear regulator's dissipation.

**Lab.** Measure the ESP32 supply during idle, peripheral activity, and radio operation. Use a short probe connection. Test a current-limited low-voltage regulator/load arrangement and compare input/output power and temperature. Simulate a simple buck converter and examine switch/inductor current; do not breadboard a high-current power stage as a substitute for layout design.

**Gate.** Produce a power tree with nominal, peak, startup, and fault currents, regulator headroom, thermal estimates, and decoupling locations. Explain a brownout or noise event with a measured trace. Use certified enclosed adapters; this course does not require mains construction or exposed mains measurements.

<a id="materials-10"></a>

### External materials

**Suggested order · about 3 hours of this module.**

1. **Core reading:** [MIT 6.334 Power Electronics notes](https://ocw.mit.edu/courses/6-334-power-electronics-spring-2007/pages/lecture-notes/), Chapter 5, “Introduction to DC/DC Converters,” and Chapter 13, “Thermal Modeling and Heat Sinking.” Select the converter operating principles and thermal-network calculations; the rest of this graduate course is optional.
2. **Core implementation reading:** [ESP32-DevKitC V4 hardware guide](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32/esp32-devkitc/user_guide.html), power connections and schematic, followed by your selected regulator's dropout, thermal and stability requirements. Substitute the exact board manual if using a different board.
3. **Watch — YouTube:** [TI, Power Supply Noise Mitigation Techniques](https://www.youtube.com/watch?v=fKGyVSKm2Dc). Use the explanation to decide where filtering, supply rejection and layout changes are likely to improve the measured rail.

**Optional depth:** MIT 6.334 Chapters 8 and 14 for converter control and EMI filtering. Keep these simulation-led until your low-voltage power tree and measurement technique are reliable.

## 11 — ESP32 as an acquisition and control subsystem

**20 hours · Prerequisites:** 09–10; existing programming fluency · **Equipment:** ESP32, signal source/button, scope and logic analyser.

**Learn and derive.** MCU architecture, memory-mapped peripherals, GPIO electrical limits, timers, interrupts, DMA concepts, RTOS scheduling, task ownership, queues, watchdogs, startup states, and debugging. Use the exact selected ESP32 variant's manuals. Connect timing uncertainty to measurement error; for a sinusoid, relate small sampling jitter to the signal derivative.

Use PlatformIO with the framework you already know. ESP-IDF is the reference for peripheral semantics and deeper work. Pin the platform/framework release after a working experiment; use documentation matching that release, not an unrelated latest example.

**Exercises.** Budget execution and buffering for acquisition independent of the host. Estimate allowable jitter for a stated signal. Compare polling, timer-driven, and converter-data-ready acquisition. Specify what happens when a consumer is slower than the producer.

**Lab.** Toggle a spare GPIO at acquisition boundaries and measure timing. Capture a periodic input or conversion-ready event while changing logging and wireless load. Move time-consuming work out of interrupt handlers; use a bounded queue. Induce and count a controlled buffer overrun, then implement a defined recovery path. Built-in ADC measurements are useful for exploring limitations, not a presumption of calibrated precision.

**Gate.** Demonstrate timed acquisition, monotonic sequence numbers, visible fault counters, and bounded memory use. Explain which clock produces the sample interval and which timestamp your firmware records.

<a id="materials-11"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [FreeRTOS Kernel Book, online contents](https://github.com/FreeRTOS/FreeRTOS-Kernel-Book/blob/main/toc.md), current Sections 4.2–4.7 on tasks and 5.2–5.3 on queues. Follow the linked chapter text and work out ownership, blocking and buffer limits for your acquisition path; older editions use different numbering.
2. **Core target-specific reading:** [ESP-IDF FreeRTOS](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/freertos_idf.html), task scheduling and critical sections, plus [ESP Timer](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/system/esp_timer.html), callback dispatch and timing limitations. Select your installed SDK version/target before implementing the examples.
3. **Watch — YouTube:** Shawn Hymel/DigiKey, [Introduction to RTOS, Part 3: Task Scheduling](https://www.youtube.com/watch?v=95yUbClyf3E), then [Part 5: FreeRTOS Queue Example](https://www.youtube.com/watch?v=pHJ3lxOoWeI). The ESP32/Arduino examples illustrate the concepts; adapt them to your pinned PlatformIO framework rather than changing frameworks solely to follow a video.

**Optional depth:** The book's interrupt-management sections, and Espressif's [FreeRTOS in ESP-IDF developer-conference talk](https://www.youtube.com/watch?v=03Q8oilo_2U). The 2022 talk is architectural background; current pinned documentation takes precedence for APIs.

## 12 — UART, I²C, and SPI from electrical layer to driver

**24 hours · Prerequisites:** 02, 09, 11 · **Equipment:** two ESP32 boards, logic analyser, scope access, ADS1115 breakout; SPI peripheral or loopback/shift-register alternative.

**Learn and derive.** UART framing and baud error; logic-level serial versus RS-232; SPI clock polarity/phase, chip select, setup/hold and full-duplex shifting; I²C open-drain signalling, addressing, START/STOP, ACK/NACK, repeated START, arbitration, clock stretching, bus capacitance, pull-ups, and recovery. Distinguish 7-bit device addresses from address bytes containing a direction bit. Learn register maps, endianness, signedness, and transaction boundaries before using a convenience library.

**Exercises.** Decode a UART frame by hand. For I²C, derive the first-order 30–70% rise time t_r ≈ 0.8473R_pC_b and combine it with the sink-current constraint R_p ≥ (V_DD − V_OL,max)/I_OL. Find a feasible pull-up range from the actual device and bus specification. Calculate payload throughput including framing and transaction overhead. Draw all four SPI modes and identify the sampling edge.

**Lab.** Exchange framed records between two UARTs. Capture a known byte pattern and a malformed frame. On I²C, read/write the ADC's documented configuration register, then read its conversion register; it has no generic WHO_AM_I requirement. Capture one complete transaction and decode it without software assistance. Measure SDA/SCL rise time and account for parallel breakout pull-ups. Exercise timeout/recovery after disconnecting an unpowered target. On SPI, capture a device transaction or a loopback pattern, then change a clock-mode setting and explain the observed fault. Never create output contention as a fault-injection technique.

**Gate.** Diagnose an unknown failure using both analog waveform evidence and decoded traffic. Deliver a transaction diagram, pull-up calculation, and minimal driver or clearly explained library calls with bounded error handling.

<a id="materials-12"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core reading:** [NXP UM10204 I²C specification, Rev. 7](https://www.nxp.com/docs/en/user-guide/UM10204.pdf), Sections 3.1.1–3.1.10, 3.1.16 and 7.1. Follow signalling/transactions, bus clear and pull-up sizing; use Section 6.1 as the electrical-timing reference.
2. **Core driver reading:** ESP-IDF's [UART](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/uart.html), [I²C](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/i2c.html), and [SPI](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/spi_master.html) guides. Read each overview and the transaction/configuration sections needed for your lab; defer the full API listings. Pair them with the target peripheral's register map.
3. **Watch — YouTube:** TI, [I2C Introduction: The Protocol](https://www.youtube.com/watch?v=j9yx8LOslng), then [SPI Communication Basics: Modes](https://www.youtube.com/watch?v=SvB9AWyyRNI). Draw the actual edges/bytes in your captured transactions and compare them with the explanations.

**Optional depth:** [PulseView's manual](https://www.sigrok.org/doc/pulseview/0.4.2/manual.pdf) for decoder operation and export, plus I²S/1-Wire documentation only if choosing those extensions. Use driver references matching your SDK, not a mixture of old and new I²C APIs.

## 13 — Sampling, ADCs, DACs, and mixed-signal error budgets

**26 hours · Prerequisites:** 07–08, 11–12 · **Equipment:** ADS1115, stable DC/low-frequency stimulus, scope; built-in or external DAC where available.

**Learn and derive.** Sampling theorem, aliasing, reconstruction, quantisation, dithering, oversampling, decimation, anti-alias filters, SAR and delta-sigma architectures, acquisition settling, reference quality, input common-mode limits, INL/DNL, offset/gain error, SNR, SINAD, and ENOB. Explain the assumptions behind q/√12 quantisation RMS and the ideal full-scale-sine SNR relation 6.02N + 1.76 dB. A converter's nominal word length is not its measured accuracy.

**Exercises.** Show where a tone at f_in folds for a chosen sample rate. Design an analog filter for a specified out-of-band interferer and error allowance. Calculate ADC-driver settling for a simplified switched-capacitor input. Build a current-to-code error budget using transimpedance, reference, gain, noise, and calibration terms. For a bipolar ±2.048 V, 16-bit transfer, calculate the ideal code step.

**Lab.** Characterise the external ADC at several safe DC levels and at least two data rates. Use conversion-ready events or a verified conversion schedule and prevent duplicate reads from being counted as new samples. Demonstrate aliasing with an injected low-voltage tone, then reduce it using an analog filter. Explore PWM plus an RC filter as a simple DAC and measure ripple/settling; use a true DAC if the chosen board has one. Compare the built-in ADC with the external converter after stating each calibration method.

**Gate.** Choose a converter from signal bandwidth and error requirements. Demonstrate code-to-unit conversion, measured noise, known timing, and an anti-alias argument. Respect individual input-pin limits even when the differential full-scale range is larger than the supply.

<a id="materials-13"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core theory reading:** Analog Devices [MT-001: Quantisation and Ideal ADC SNR](https://www.analog.com/media/en/training-seminars/tutorials/MT-001.pdf) and [MT-002: Sampling and the Nyquist Criterion](https://www.analog.com/media/en/training-seminars/tutorials/mt-002.pdf). Derive the formulae and their assumptions; use them to set an anti-alias/error budget.
2. **Core device reading:** [ADS1115 datasheet](https://www.ti.com/lit/ds/symlink/ads1115.pdf), Rev. E Section 6.1, Sections 7.3–7.5 and Section 8, selected for noise, operating modes, programming and conversion registers. Use section titles if a later revision changes the numbering.
3. **Watch — YouTube:** TI, [SAR and Delta-Sigma: Basic Operation](https://www.youtube.com/watch?v=U_Yv69IGAfQ), then [Hands-on Experiment: Aliasing and Anti-Aliasing Filters](https://www.youtube.com/watch?v=YskDE8PX5OI). The latter demonstrates TI hardware/TINA-TI; recreate the experiment with your course ADC, stimulus and ngspice.

**Optional depth:** The [official TI ADC course](https://www.ti.com/video/series/precision-labs/ti-precision-labs-analog-to-digital-converters-adcs.html), selected input-drive, reference and error topics; [ESP32 ADC calibration](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/adc_calibration.html) for the built-in/external comparison. Do not take the entire video series as additional core work.

## 14 — Raspberry Pi, Linux, and a reproducible data system

**16 hours · Prerequisites:** 11–13 · **Equipment:** Linux-capable Raspberry Pi, storage, proper supply, data cable; ESP32 acquisition system.

**Learn and derive.** Linux device interfaces, permissions, serial ports, I²C/SPI access, monotonic versus wall-clock time, buffering, process lifecycle, persistent logging, and host–device protocols. Distinguish an MCU from a Linux SBC, and a Raspberry Pi computer from a Pico microcontroller. Keep the converter's sampling clock distinct from host scheduling and packet arrival times.

**Exercises.** Design a record format carrying sample index, timing information, raw ADC code, range, status, and calibration identity. Calculate storage use and worst-case buffer duration. Specify reconnect, reboot, and partial-record behaviour. Explain what a UTC timestamp can and cannot establish about sample synchronisation.

**Lab.** Log ESP32 measurements to the Pi over its USB serial bridge or another verified serial path. Store raw records and metadata before plotting. Implement one simple acquisition process; a database or web dashboard is not required. Stop the host, restart it, and demonstrate explicit gaps or bounded recovery. Repeat a parameter fit from saved data without access to the hardware. Use GPIO Zero only for slow supervisory I/O if needed.

**Gate.** Run acquisition for 30 minutes, reconcile sample indices and fault counters, and regenerate plots from raw files. No unexplained loss or duplication is acceptable. Explain why host timestamps do not replace acquisition timing evidence.

<a id="materials-14"></a>

### External materials

**Suggested order · about 2–3 hours of this module.**

1. **Core hardware/OS reading:** [Raspberry Pi configuration documentation](https://www.raspberrypi.com/documentation/computers/configuration.html), relevant interface settings, UART device names and serial-console configuration. Header UART configuration applies only if you use that path; a USB serial bridge does not require repurposing the GPIO UART.
2. **Core acquisition reading:** [pySerial's Short Introduction](https://pyserial.readthedocs.io/en/latest/shortintro.html), opening/closing ports, reads/writes, timeouts and line framing. Define your record boundaries, reconnect behaviour and partial-read handling before writing the logger.
3. **Watch — YouTube:** [MIT Missing Semester: Command-Line Environment](https://www.youtube.com/watch?v=e8BO_dYxk5c), with its [written companion](https://missing.csail.mit.edu/2020/command-line/). Concentrate on jobs, signals, process control and remote access; skim material already familiar from programming.

**Optional depth:** [GPIO Zero](https://gpiozero.readthedocs.io/en/stable/) for slow supervisory I/O; [SciPy signal analysis](https://docs.scipy.org/doc/scipy/tutorial/signal.html) for saved-data processing. Keep acquisition timing evidence on the ADC/MCU side of the host link.

## 15 — Differential links, USB, networking, and wireless

**16 hours · Prerequisites:** 09–14 · **Equipment:** two ESP32 boards; compatible 3.3 V RS-485 and CAN transceivers, cable/termination; Pi/network access.

**Learn and derive.** Separate electrical signalling, framing, transport, and application protocols. RS-485 specifies an electrical interface; add a framed application protocol with addressing and checks. Study differential signalling, common-mode range, topology, termination, failsafe bias, half-duplex turnaround, CAN arbitration/error handling, USB roles/descriptors/endpoints, Ethernet framing, IP, TCP/UDP, Wi-Fi, and BLE services. Depth varies: UART/I²C/SPI receive register-level mastery; the wider interfaces receive architectural understanding and selected practical experiments.

**Exercises.** Predict the reflection coefficient for a mismatched line. Calculate a two-wire link's termination loading and check transmitter capability. Explain why two CAN nodes are needed for a normal acknowledged exchange. Calculate the data budget for a measurement stream and distinguish latency from throughput and sampling jitter.

**Lab.** Exchange records over a short, terminated RS-485 bench link with two transceivers; deliberately change termination while observing within safe operating limits. Bring up a classical CAN link between two compatible ESP32 controllers with external transceivers and document arbitration/ACK/error behaviour. Inspect the development board's USB descriptors and identify whether the USB endpoint is a UART bridge or native MCU USB. Send measurements over Wi-Fi using one simple transport, inspect traffic with Wireshark, and compare noise/timing against the wired baseline. Use BLE for a small status/configuration exchange if supported by the selected chip. Inspect Ethernet/IP traffic on an existing Ethernet interface or a capture from your own network; no dedicated Ethernet hardware purchase is required.

**Gate.** Select an interface for a stated distance, environment, bandwidth, timing, and recovery requirement. Explain each layer and identify which errors are detected where. Do not confuse UART with RS-232 or RS-485, or a CAN controller with its external electrical transceiver.

<a id="materials-15"></a>

### External materials

**Suggested order · about 2–3 hours of this module.**

1. **Core electrical-interface reading:** [TI's RS-485 Design Guide](https://www.ti.com/lit/an/slla272d/slla272d.pdf), Sections 2–8. Use its topology, termination, bias and loading discussion to draw the actual bench cable and transceiver circuit.
2. **Core CAN reading:** [TI, Introduction to CAN](https://www.ti.com/lit/an/sloa101b/sloa101b.pdf), Sections 3–5, then consult [ESP-IDF TWAI](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/twai.html) for your implementation. Separate frame/arbitration rules from electrical-transceiver requirements.
3. **Watch — YouTube:** [TI, CAN and CAN FD Overview](https://www.youtube.com/watch?v=AeSZ_3T1GCk) ([official TI-hosted alternative](https://www.ti.com/video/6078637459001)). Use the overview to compare classical CAN with CAN FD; only implement capabilities actually supported by your target.

**Optional depth/reference:** [Peter Dordal's open university networking textbook](https://intronetworks.cs.luc.edu/current2/html/index.html), Chapter 1's layers/Ethernet/IP/transport overview and selected later Wi-Fi/TCP/UDP chapters; [Wireshark's user documentation](https://www.wireshark.org/docs/) for the packet experiment. Use the exact board/stack's USB, Wi-Fi and BLE manuals for those comparisons. The goal here is interface selection and observation, not a second full networking course.

## 16 — PCB design, return paths, signal integrity, and power integrity

**28 hours · Prerequisites:** 07–10, 12–13 · **Equipment:** KiCad; scope; soldering tools for a small practice assembly.

**Learn and derive.** Hierarchical schematics, ERC, footprints, pin mapping, connector orientation, stackups, trace resistance/inductance, return currents, transmission lines, crosstalk, decoupling, ground-plane continuity, thermal paths, ESD entry points, testability, DRC, fabrication files, and assembly documentation. Relate electrically long interconnects to edge rise time rather than only clock frequency. Treat low-current detector inputs as leakage- and contamination-sensitive nodes.

**Exercises.** Estimate trace resistance and propagation time. Compare a continuous return plane with a slot under a fast signal. Draw the high-frequency current loops for a bypass capacitor, digital interface, and regulator. Explain why indiscriminate analog/digital ground splitting can worsen return paths. Check a footprint against the manufacturer's drawing independently of its library label.

**Lab.** Create a small KiCad practice board or adapter that you can inspect and solder. Run ERC/DRC, review footprints and connector pinouts, and inspect manufacturing outputs in a Gerber viewer. Capture edge/return-path behaviour on a safe bench example where instrument bandwidth permits; supplement with a transmission-line simulation. Begin the capstone schematic, placement, test points, and return-path plan, leaving front-end values conditional on Module 17.

**Gate.** Produce a reviewed design package: schematic, PCB, stackup/rules, BOM, fabrication/assembly outputs, and bring-up plan. Zero unexplained ERC/DRC errors; every waiver needs a reason. A clean DRC is necessary but does not verify a physical design.

<a id="materials-16"></a>

### External materials

**Suggested order · about 4–5 hours of this module.**

1. **Core design reading:** [KiCad 10 Getting Started](https://docs.kicad.org/10.0/en/getting_started_in_kicad/getting_started_in_kicad.html), schematic-to-PCB and manufacturing-output workflow. Use the [PCB Editor manual](https://docs.kicad.org/10.0/en/pcbnew/pcbnew.html) as a lookup for constraints, planes, inspection and export; skip familiar interface basics.
2. **Core field reading:** [MIT 6.013 lecture notes](https://ocw.mit.edu/courses/6-013-electromagnetics-and-applications-spring-2009/pages/lecture-notes/), Lectures 11–12 on device/interconnect delays, TEM lines, characteristic impedance and transients. Connect these to return currents and the edge rates on your own board.
3. **Watch — YouTube:** [Rick Hartley, How to Achieve Proper Grounding](https://www.youtube.com/watch?v=ySuUZEjARPY), hosted by Altium. This is a field/return-path lecture; apply the principles in KiCad. Draw your critical current loops while watching rather than copying a generic grounding rule.

**Optional depth:** [Phil's Lab #56: PCB Stack-Up and Build-Up](https://www.youtube.com/watch?v=QAOEtfvCaMw), theory at 00:27–07:49 and from 09:56 onward; the intervening Altium stack-manager demonstration is unnecessary. MIT 6.013 Lecture 13 extends the impedance-transformation theory.

## 17 — Photodiode transimpedance design

**26 hours · Prerequisites:** 04–08, 10, 13, 16 fundamentals · **Equipment:** detector, selected op amp, ADC, feedback components, short-wired prototype, covered enclosure, scope access, current-injection fixture.

**Learn and derive.** Current-to-voltage conversion, photovoltaic versus reverse-biased detection, detector capacitance, summing-node parasitics, leakage, input bias, feedback compensation, noise gain, loop stability, reference noise, overload recovery, dynamic range, and physical guarding. Separate the feedback capacitor's loop-compensation role from downstream anti-alias filtering.

**Exercises.** For current defined as entering the summing node, derive V_out − V_ref ≈ −I_in R_f in the low-frequency linear regime. Include finite loop gain and input capacitance to find the noise-gain shape. Build an input-referred noise model. Compare two feedback-resistor ranges and calculate output headroom, gain error, and ADC-referred current resolution. Explain why photocurrent cannot be converted to lux using one universal multiplier.

**Lab.** Start with an injected electrical current and a conservative feedback network; establish DC behaviour before relying on light. Add detector capacitance in simulation, then the physical detector, and examine stability across both ranges. Use short, clean wiring and progress to a suitable adapter/PCB when breadboard leakage/parasitics dominate. Measure transimpedance, frequency/step response, covered-detector noise, and the effect of radio/power activity. Repeat on both ranges and document any compensation changes.

**Gate.** Freeze a feasible capstone specification and release its PCB only after this front end has measured DC gain and stability evidence. Present the complete noise/error budget and an electrical calibration method. Clearly label prototype results, predictions, and quantities below your measurement floor.

<a id="materials-17"></a>

### External materials

**Suggested order · about 3–4 hours of this module.**

1. **Core theory reading:** [TI SBOA055A: Compensate Transimpedance Amplifiers Intuitively](https://www.ti.com/lit/an/sboa055a/sboa055a.pdf), technical pages 1–2. Derive the input-capacitance/noise-gain model and identify which assumptions apply to your detector and op amp.
2. **Core worked design:** [TI SBOA220B: Photodiode Amplifier Circuit](https://www.ti.com/lit/an/sboa220/sboa220.pdf), pages 1–3, design notes/steps and DC/AC results. Recalculate the design for the capstone's supply, sign convention, ranges and bandwidth. Rebuild the simulation in ngspice instead of depending on its TINA-TI/PSpice files.
3. **Watch — YouTube:** [TI, Photodiode Amplifier Circuit](https://www.youtube.com/watch?v=EdX1MBvPMOw) ([TI-hosted alternative](https://www.ti.com/video/6289331603001)). The older video uses a different op amp from the revised note; transfer the method, not its component values.

**Optional depth/reference:** Revisit [ADI MT-047 on noise](https://www.analog.com/media/en/training-seminars/tutorials/MT-047.pdf), the [BPW34 datasheet](https://www.vishay.com/docs/81521/bpw34.pdf) and your selected op-amp model. Use the [capstone brief](CAPSTONE.md) to connect compensation, electrical calibration, ADC limits and layout.

## 18 — Capstone integration, calibration, and defence

**64 hours · Prerequisites:** all core gates, especially 16–17 · **Equipment:** completed acquisition chain, custom PCB, enclosure, test fixtures, instrument access.

**Work packages.** Allocate approximately 8 hours to requirements/design review, 12 to layout/release, 12 to assembly/bring-up, 12 to firmware/Pi integration, 14 to characterisation, and 6 to the final report. Fabrication delivery time is additional. Keep allowance for rework or a second revision; take a narrower, well-measured result over an unverified feature list.

**Build and measure.** Implement the [capstone specification and acceptance plan](CAPSTONE.md). Power up in stages with a current limit; validate references and analog behaviour before adding continuous digital/radio traffic. Establish electrical gain/offset calibration and its uncertainty. Measure frequency response, noise, current range, overload behaviour, sample integrity, drift, and the effect of digital activity. Use controlled light changes for relative optical measurements.

**Transfer challenge.** Change one requirement after the baseline works: increase bandwidth, extend current range, or improve the noise floor. Predict which component, compensation, ADC, filter, layout, or firmware choices must change. Implement or simulate the change and explain the remaining evidence needed.

**Gate.** Another technically competent person can reproduce your main plots from the released design and raw records. Your report connects measured performance to semiconductor/circuit models, acquisition timing, calibration, and uncertainty. Demonstrate every mandatory requirement or document a failed target and the specific corrective experiment/design revision. Reading completion alone does not pass this module.

<a id="materials-18"></a>

### External materials

**Suggested order · about 2–3 hours of this module, followed by application throughout the project.**

1. **Core calibration reading:** [NIST Engineering Statistics Handbook, Section 2.3: Calibration](https://www.itl.nist.gov/div898/handbook/mpc/section3/mpc3.htm), especially “Instrument calibration over a regime”: model choice, data collection, analysis/validation and uncertainty. Plan independent validation points and a stated reference base before fitting your instrument.
2. **Core project reading:** [MIT 6.101 analog laboratory: Final Project](https://web.mit.edu/6.101/www/s2019/finalproject.html), the architecture/proposal, demonstration and report expectations. Adapt the engineering-review structure to this individual capstone; its historical class dates, team grading and deadlines do not apply.
3. **Watch — official TI-hosted video:** [Understanding and Calibrating the Offset and Gain for ADC Systems](https://www.ti.com/video/5466249277001), with [presentation and quiz](https://www.ti.com/content/dam/videos/external-videos/en-us/2/3816841626001/5466249277001.mp4/subassets/adcs-understanding-and-calibrating-the-offset-and-gain-for-adc-systems-presentation-quiz.pdf). Use the worked calibration as a starting model, then add reference uncertainty, residual nonlinearity and drift. This chapter uses the verified publisher-hosted video; a matching official YouTube upload was not established.

**Optional depth:** [JCGM/GUM publications](https://www.bipm.org/en/committees/jc/jcgm/publications), uncertainty reporting and Monte Carlo propagation where the linearised model is inadequate. The [capstone acceptance procedure](CAPSTONE.md) governs your actual tests and release package; the readings support it rather than replacing measurements.

## Milestone reviews

| Review | After | Required demonstration |
| --- | --- | --- |
| A — Circuit competence | 03 | Predict and measure an unfamiliar loaded RC network with a defensible measurement model |
| B — Analog competence | 08 | Design a biased, stable amplifier/filter and explain its noise floor or measured upper bound |
| C — Digital/power competence | 10 | Show input timing/threshold margins and a measured, current-budgeted power tree |
| D — Acquisition competence | 15 | Capture bus traffic and preserve correctly timed, unit-labelled data through a host/network fault |
| E — Design release | 17 | Review schematic, footprints, PCB, calibration plan, stability, and noise budget before fabrication |
| F — Instrument defence | 18 | Present raw-to-report reproducibility, performance evidence, and a justified redesign |

Each review includes one unfamiliar variation so that the result demonstrates transfer rather than memorised wiring. Revisit only the concepts exposed by a failed gate.

## Advanced track A — RF and distributed circuits

**50 additional hours · Prerequisites:** 02, 06, 08, 16 · **Equipment:** simulation initially; borrow a suitable VNA/RF source for physical calibration and measurement.

Study transmission-line equations, impedance transformations, Smith charts, S-parameters, matching, resonators, noise figure, gain/stability, mixers, oscillators, and the relation between fields and circuit ports. Derive reflection and power-wave relations with stated reference impedances. Distinguish a small-signal RF network model from nonlinear oscillator/mixer behaviour.

**Problems and lab.** Design a passive matching network and compare lumped/distributed models. Calibrate a VNA at a declared reference plane, then measure a passive network/cable and compare with simulation. Explore a modest-bandwidth detector front-end extension or an RF gain block in simulation. Use KiCad/ngspice plus an open-source RF analysis tool where appropriate; the instrument may have proprietary firmware. Do not purchase RF equipment until this track is chosen.

**Gate.** Defend calibration, reference plane, mismatch, and loss; distinguish DUT behaviour from fixture effects. A simulation-only completion must remain labelled simulation-only.

**Reading:** [R22, electromagnetics/transmission lines](REFERENCES.md#r22); [R23, Qucs-S and scikit-rf](REFERENCES.md#r23).

## Advanced track B — FPGA-based acquisition and digital design

**50 additional hours · Prerequisites:** 09, 11–13 · **Equipment:** HDL simulator first; an explicitly supported iCE40/ECP5 board and programmer for hardware work.

Study synchronous design, synthesizable RTL, finite-state machines, pipelining, fixed-point arithmetic, reset strategy, clock-domain crossing, timing constraints, static timing, and verification. Use Icarus Verilog or Verilator for simulation, Yosys for synthesis, and nextpnr for a supported FPGA family. Verify exact device/package/programmer support before buying; an open toolchain does not support every FPGA.

**Problems and lab.** Derive accumulator widths for a bounded signal. Write and verify a UART or SPI acquisition block, including reset and malformed-input cases. Build a timestamped capture FIFO and decimator. Compare latency, timing predictability, resource use, and power with the ESP32 implementation. Exercise overflow and clock-domain-crossing behaviour intentionally.

**Gate.** A passing behavioural simulation, explained timing constraints, a timing-closure report, and a physical capture all agree. State which analogue/metastability assumptions RTL simulation cannot verify.

**Reading:** [R24, simulator, synthesis, and place-and-route projects](REFERENCES.md#r24).

## Advanced track C — Integrated-circuit design and physical implementation

**80 additional hours · Prerequisites:** 04–09, 16; track B's RTL fundamentals for its digital option · **Equipment:** computer with adequate memory/disk; no fabrication required.

Study process steps, masks, design rules, compact device models, corners, mismatch, short-channel effects, body bias, standard cells, matching/common-centroid layout, parasitic extraction, DRC/LVS, reliability, and analog/digital physical-design tradeoffs. Extend core long-channel intuition using a documented PDK model rather than extrapolating it indefinitely.

**Problems and lab.** With a pinned open PDK/tool combination, simulate an inverter and current mirror across operating conditions. Lay out a small cell, run the available DRC/LVS flow, extract parasitics, and compare pre-/post-layout performance. For an analog emphasis, extend to a differential pair or compensated amplifier using Xschem/ngspice and a compatible layout/extraction flow. For a digital emphasis, take a tiny RTL block through synthesis, placement/routing, and timing analysis with an OpenROAD-based flow.

**Gate.** Deliver reproducible model/tool versions, pre-/post-layout comparisons, verification results, and a list of unverified manufacturing/sign-off assumptions. The open SKY130 release is documented as experimental; educational flow completion does not establish production readiness. Tapeout, shuttle availability, packaging, and fabrication cost are outside this course's core commitments.

**Reading:** [R25–R26, IC tools and PDK status](REFERENCES.md#r25).

## Working vocabulary

Use these terms precisely in reports. The relationships between them matter more than memorising the abbreviations.

| Term | Meaning in this course |
| --- | --- |
| KCL / KVL | Kirchhoff's current/voltage laws, applied within the stated lumped-circuit assumptions |
| Operating point | DC voltages/currents about which a device is linearised for small-signal analysis |
| Small signal | A perturbation small enough for the chosen local linearisation; its amplitude limit is circuit-dependent |
| Input/output impedance | The port's response to an applied test signal with other sources treated appropriately; generally frequency-dependent |
| Transconductance | Small-signal output-current change per input-voltage change, in siemens |
| Transimpedance / TIA | Voltage response per input current, in ohms / transimpedance amplifier |
| Loop gain / noise gain | Gain around a specified feedback loop / closed-loop gain seen by equivalent input-voltage noise; neither is automatically the signal gain |
| CMRR / PSRR | Common-mode rejection / power-supply rejection; specify frequency and the input/output convention |
| RMS | Root-mean-square amplitude; state the bandwidth and any removed mean/trend |
| PSD / amplitude density | Power spectral density, such as V²/Hz / its square root, such as V/√Hz |
| ENBW | Equivalent noise bandwidth: the bandwidth of an ideal rectangular filter passing the same white-noise power at the stated gain |
| ADC / DAC | Analog-to-digital / digital-to-analog converter |
| SNR / SINAD / ENOB | Signal-to-noise ratio / signal-to-noise-and-distortion ratio / effective number of bits under stated test conditions |
| I²C / SPI / UART | Inter-Integrated Circuit / Serial Peripheral Interface / Universal Asynchronous Receiver/Transmitter |
| MCU / SBC | Microcontroller / single-board computer; in the baseline these are the ESP32 and Linux Raspberry Pi respectively |
| ISR / DMA / RTOS | Interrupt service routine / direct memory access / real-time operating system; implementation tools whose timing still needs measurement |
| PCB / BOM | Printed circuit board / bill of materials |
| ERC / DRC | Electrical-rule / design-rule checking; automated checks with a defined and incomplete scope |
| PDK | Process design kit: process-specific models, rules and implementation data |
| LVS / extraction | Layout-versus-schematic connectivity comparison / recovery of device and parasitic information from layout |
| Calibration / validation | Establishing a measurement relationship using references / checking performance with independent evidence |
| Resolution / accuracy / uncertainty | Distinguishable increment / agreement with the quantity's value / quantified dispersion or limits associated with the result; these are different properties |
