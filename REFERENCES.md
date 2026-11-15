# References and assigned reading

[Course](COURSE.md) · [Start page](README.md)

Primary sources checked on **15 November 2026**. These materials are freely accessible; their licences remain separate from this repository. Read the assigned topics rather than taking every linked course end to end. University resources develop the theory; current component datasheets and framework manuals govern your actual implementation. Record the revision you used.

## Where to read the explanations

The teaching explanations are in the external lecture notes, textbooks and manuals below. The repository's [COURSE.md](COURSE.md) now gives **each chapter 00–18 its own External materials section**: core written readings, recommended videos, optional depth and a suggested order. Start there for chapter-specific assignments; this bibliography supplies the source catalogue and a shorter overview.

**Direct chapter materials:** [00](COURSE.md#materials-00) · [01](COURSE.md#materials-01) · [02](COURSE.md#materials-02) · [03](COURSE.md#materials-03) · [04](COURSE.md#materials-04) · [05](COURSE.md#materials-05) · [06](COURSE.md#materials-06) · [07](COURSE.md#materials-07) · [08](COURSE.md#materials-08) · [09](COURSE.md#materials-09) · [10](COURSE.md#materials-10) · [11](COURSE.md#materials-11) · [12](COURSE.md#materials-12) · [13](COURSE.md#materials-13) · [14](COURSE.md#materials-14) · [15](COURSE.md#materials-15) · [16](COURSE.md#materials-16) · [17](COURSE.md#materials-17) · [18](COURSE.md#materials-18).

**Selection and checks:** university open courses provide the theory backbone; NIST and manufacturer/instructor sources supply measurement and implementation detail. Linked materials are free to access; optional certificates, products and proprietary simulator demonstrations are not requirements. Video identities were checked against official publisher pages, channel metadata or embedded videos on the official course pages on 15 November 2026. Playback was not tested. The essential selections fit the existing module-hour estimates; full series are optional.

| Course modules | Written material to open | Reading assignment |
| --- | --- | --- |
| 00–01 — First circuits and DC analysis | [MIT 6.002 lecture notes](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/pages/lecture-notes/) | Lectures 1–3: circuit abstraction, circuit analysis and equivalent sources |
| 02 — Dynamic circuits | [MIT 6.002 lecture notes](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/pages/lecture-notes/) | Lectures 12 and 15–18: energy storage, dynamic systems, impedance and filters |
| 03 — Measurement and uncertainty | [JCGM/GUM publications](https://www.bipm.org/en/committees/jc/jcgm/publications) | Introductory measurement models and uncertainty propagation, plus your instruments' manuals |
| 04–05 and 09 — Devices, transistors and CMOS | [MIT 6.012 lecture notes](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/resources/lecture-notes/) | 1–6 for junctions; 7–13 and 17–24 for transistor models/amplifiers; 14–16 for digital circuits |
| 06–07 — Feedback and analog circuits | [Roberge's open textbook](https://ocw.mit.edu/courses/res-6-010-electronic-feedback-systems-spring-2013/resources/res6_010_s_13_coursetextbook_pdf/) | Feedback modelling, linear response, stability, compensation and active circuits |
| 08 and 13 — Noise and sampled data | [Op-amp noise](https://www.analog.com/media/en/training-seminars/tutorials/MT-047.pdf), [ADC quantisation](https://www.analog.com/media/en/training-seminars/tutorials/MT-001.pdf), [sampling](https://www.analog.com/media/en/training-seminars/tutorials/mt-002.pdf) | Read and derive the relevant tutorial results, then apply them to your signal chain |
| 10–12 — Power, ESP32 and peripheral buses | [ESP-IDF guide](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/), [I²C specification](https://www.nxp.com/docs/en/user-guide/UM10204.pdf) | Board/regulator datasheets for power; GPIO/timers/ADC/driver chapters; I²C transactions and electrical design |
| 14–15 — Pi and wider communications | [Pi hardware/manuals](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html), [RS-485 guide](https://www.ti.com/lit/an/slla272d/slla272d.pdf), [CAN introduction](https://www.ti.com/lit/an/sloa101b/sloa101b.pdf) | Device interfaces, signalling, termination and framing; use R18–R21 below for the remaining host/network reading |
| 16 — PCB design and return paths | [KiCad manuals](https://docs.kicad.org/), [MIT field/transmission-line notes](https://ocw.mit.edu/courses/6-013-electromagnetics-and-applications-spring-2009/pages/lecture-notes/) | Schematic/PCB workflow, then the field and interconnect topics relevant to your layout |
| 17–18 — Photodiode instrument | [TIA compensation note](https://www.ti.com/lit/an/sboa055a/sboa055a.pdf), [photodiode datasheet](https://www.vishay.com/docs/81521/bpw34.pdf), [ADC datasheet](https://www.ti.com/lit/ds/symlink/ads1115.pdf) | Front-end model, loop compensation and component constraints; use [CAPSTONE.md](CAPSTONE.md) for the integration/calibration procedure |

**First reading session:** [Lecture 1](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/resources/6002_l1/) → [Lecture 2](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/resources/6002_l2/) → [Lecture 3](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/resources/6002_l3/). Each page provides downloadable written notes. Then attempt the derivations in [Lab 01](labs/01-dc-circuits.md).

For a continuous introductory textbook alongside the compact MIT notes, use James Fiore's free [DC circuit text](https://www.jimfiore.org/books/DCElectricalCircuitAnalysis.pdf) and [AC circuit text](https://www.jimfiore.org/books/ACElectricalCircuitAnalysis.pdf). Start the DC book at Chapter 2; Chapters 3–7 develop resistive-network analysis. Skim familiar mathematical preliminaries. See R27 for their place in the course.

## Foundations and analysis

<a id="r01"></a>

### R01 — MIT 6.002: Circuits and Electronics

[Written lecture notes](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/pages/lecture-notes/) · [Course and videos](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/) · [Problem sets](https://ocw.mit.edu/courses/6-002-circuits-and-electronics-spring-2007/pages/assignments/)

Use for Modules 00–03: circuit abstraction, resistive networks, equivalent circuits, energy storage and dynamic response. Attempt relevant problems before watching solutions/explanations. Its freely available materials are sufficient for this course's assigned work; buying its commercial companion text is not required.

<a id="r02"></a>

### R02 — MIT 6.012: Microelectronic Devices and Circuits

[Course](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/) · [Lecture notes](https://ocw.mit.edu/courses/6-012-microelectronic-devices-and-circuits-fall-2009/resources/lecture-notes/)

Module 04 uses semiconductor transport and junction material, especially lectures 1–6. Module 05 uses BJT/MOS material and amplifier lectures; Module 09 uses inverter, delay and CMOS material. Read the complete relevant notes, derive the central equations, and state model assumptions. Supplement the physical experiments with appropriate original MIT problems. Modern process-specific conclusions still require current device/PDK models.

<a id="r03"></a>

### R03 — Roberge: Electronic Feedback Systems and Operational Amplifiers

[Lecture series and course manual](https://ocw.mit.edu/courses/res-6-010-electronic-feedback-systems-spring-2013/) · [Open textbook: Operational Amplifiers, Theory and Practice](https://ocw.mit.edu/courses/res-6-010-electronic-feedback-systems-spring-2013/resources/res6_010_s_13_coursetextbook_pdf/)

For Modules 06–07, work through feedback modelling, linear-system response, stability, compensation and active-circuit applications. Use its analytical depth freely. Historical devices illustrate principles; select your laboratory parts using their own supply, common-mode, output and stability specifications.

<a id="r04"></a>

### R04 — SciPy's signal-processing documentation

[Signal-processing tutorial](https://docs.scipy.org/doc/scipy/tutorial/signal.html)

For Modules 07–08 and 13–14, use the relevant filtering and spectral-analysis sections. When estimating a PSD, record sampling frequency, window, scaling, segment length, overlap and detrending. Numerical output needs a measurement model and a unit check. SciPy is an addition to the existing NumPy/Matplotlib environment when needed.

<a id="r05"></a>

### R05 — BIPM/JCGM: measurement uncertainty

[Official JCGM publications](https://www.bipm.org/en/committees/jc/jcgm/publications)

For Modules 01 and 03, read the introductory GUM material and measurement-model/uncertainty sections. Revisit covariance, distribution assumptions and propagation for the capstone. Use the Monte Carlo supplement for nonlinear or non-Gaussian cases. The entire standards suite is background reference, not a mandatory cover-to-cover assignment.

## Circuit tools and precision analog work

<a id="r06"></a>

### R06 — KiCad manuals and simulator

[Versioned manuals](https://docs.kicad.org/) · [Integrated SPICE overview](https://www.kicad.org/discover/spice/)

Start with Getting Started and the Schematic Editor's simulator sections. For Module 16, use the PCB Editor, Gerber Viewer and CLI documentation. Match the major version installed. Learn model/pin assignment and explicit SPICE grounding before assuming a visually correct schematic is a valid simulation.

<a id="r07"></a>

### R07 — ngspice documentation

[Official documentation and manual](https://ngspice.sourceforge.io/docs.html)

Read operating-point, DC, AC, transient and noise-analysis sections as they become relevant. Check support in the ngspice version used by KiCad. Model compatibility, numerical convergence and physical model validity are separate questions.

<a id="r08"></a>

### R08 — Analog Devices: converter fundamentals

[MT-001: ideal ADC SNR and quantisation](https://www.analog.com/media/en/training-seminars/tutorials/MT-001.pdf) · [MT-002: sampled-data system design](https://www.analog.com/media/en/training-seminars/tutorials/mt-002.pdf)

Read for Module 13. Derive the ideal results and write down the signal/statistical conditions behind them. Use them to interrogate converter specifications, not to turn nominal bit count into an accuracy claim.

<a id="r09"></a>

### R09 — Analog Devices MT-047: Op Amp Noise

[Tutorial](https://www.analog.com/media/en/training-seminars/tutorials/MT-047.pdf)

Use for Module 08 and the photodiode noise budget: equivalent voltage/current sources, resistor contributions and bandwidth-dependent results. Construct your own circuit's transfer functions rather than adding unrelated noise amplitudes directly.

<a id="r10"></a>

### R10 — TI SBOA055A: transimpedance compensation

[Compensate Transimpedance Amplifiers Intuitively](https://www.ti.com/lit/an/sboa055a/sboa055a.pdf) · [SBOA220B: worked photodiode-amplifier design](https://www.ti.com/lit/an/sboa220/sboa220.pdf)

For Modules 06 and 17, reproduce the equivalent input model and noise-gain reasoning. Check how capacitance and feedback change the loop. Confirm assumptions with the selected amplifier's model and physical measurements; an application-note formula is not a universal stability guarantee.

<a id="r11"></a>

### R11 — Vishay BPW34 photodiode

[Manufacturer datasheet](https://www.vishay.com/docs/81521/bpw34.pdf)

Read package/polarity, spectral response, capacitance, dark current and test conditions. Use it for Module 04's detector model and Module 17's front end. Typical spectral data supports design estimates; absolute optical calibration remains a separate measurement.

## Embedded tools and peripheral buses

<a id="r12"></a>

### R12 — ESP32 board and PlatformIO documentation

[ESP32-DevKitC V4 hardware guide](https://docs.espressif.com/projects/esp-dev-kits/en/latest/esp32/esp32-devkitc/user_guide.html) · [PlatformIO Espressif 32 platform](https://docs.platformio.org/en/stable/platforms/espressif32.html)

Record the exact module, board revision, pin map and permitted power connections. Use PlatformIO's supported board/framework combinations. The framework version bundled by a platform release may lag Espressif's current documentation; use matching API references.

<a id="r13"></a>

### R13 — ESP-IDF peripheral and ADC references

[ESP32 programming guide](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/) · [ADC calibration](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/adc_calibration.html) · [Continuous ADC acquisition](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/api-reference/peripherals/adc_continuous.html)

Modules 10–13 use GPIO, timers, interrupts, scheduling, ADC limitations and calibration. Consult the Wi-Fi/Bluetooth sections for Module 15. The last link illustrates the continuous driver in the current documentation; change its version/target selector to your installed SDK/chip before implementing it. Do not assume every ESP32 variant exposes the same peripherals or restrictions.

<a id="r14"></a>

### R14 — I²C specification and implementation

[NXP UM10204, Rev. 7](https://www.nxp.com/docs/en/user-guide/UM10204.pdf) · [ESP-IDF I²C driver](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/i2c.html)

For Module 12, read the bus transaction, timing and pull-up sizing material in UM10204, especially the electrical design discussion in Section 7. Work from the capabilities and limits of your actual target and devices. Separate a standards-level feature from what a selected controller/driver supports.

<a id="r15"></a>

### R15 — UART and SPI driver references

[ESP-IDF UART](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/uart.html) · [ESP-IDF SPI controller](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/spi_master.html)

Read transaction timing, framing, pin routing and resource constraints for Module 12. SPI peripherals define their own command/register protocols; the selected device datasheet is part of the assignment. UART framing does not by itself define cable voltage levels.

<a id="r16"></a>

### R16 — TI ADS1115 external ADC

[Product page](https://www.ti.com/product/ADS1115) · [Current datasheet](https://www.ti.com/lit/ds/symlink/ads1115.pdf)

For Modules 12–13 and the capstone, read the register map, signed conversion, PGA, data-rate, conversion-ready, settling and input-limit sections. Check the breakout schematic independently of the chip datasheet. A wider programmable differential range does not relax individual input-pin constraints.

<a id="r17"></a>

### R17 — sigrok and PulseView

[Logic-analyser introduction](https://sigrok.org/wiki/Getting_started_with_a_logic_analyzer) · [PulseView manual](https://www.sigrok.org/doc/pulseview/0.4.2/manual.pdf) · [fx2lafw firmware and hardware information](https://www.sigrok.org/wiki/Fx2lafw)

For Modules 09 and 12, learn capture setup, sampling, triggers where supported, decoders and export. Check actual hardware support and input ratings before purchase. Interpret a decoder's output against the captured edges rather than treating it as an independent truth source.

<a id="r18"></a>

### R18 — Raspberry Pi and GPIO Zero

[Hardware documentation](https://www.raspberrypi.com/documentation/computers/raspberry-pi.html) · [Software sources and firmware boundary](https://www.raspberrypi.com/documentation/computers/software-sources.html) · [GPIO Zero documentation](https://gpiozero.readthedocs.io/en/stable/)

For Module 14, confirm power, connectors, GPIO limitations and supported OS interfaces for your model. GPIO Zero is optional for slow supervisory functions; the core acquisition clock belongs to the ADC/MCU design. A general-purpose Linux process is not evidence of deterministic sample timing.

## Wider interfaces and fields

<a id="r19"></a>

### R19 — TI SLLA272D: RS-485

[The RS-485 Design Guide](https://www.ti.com/lit/an/slla272d/slla272d.pdf)

Read signalling, topology, common-mode, termination, bias and loading for Module 15. Build a short bench link before attempting long cables or isolated networks. Provide your own clearly specified framing/application protocol above this electrical layer.

<a id="r20"></a>

### R20 — CAN and ESP32 TWAI

[TI Introduction to CAN](https://www.ti.com/lit/an/sloa101b/sloa101b.pdf) · [Espressif TWAI controller documentation](https://docs.espressif.com/projects/esp-idf/en/stable/esp32/api-reference/peripherals/twai.html)

Use for arbitration, acknowledgement, error behaviour and the electrical interface. Select an external transceiver and check the exact chip/controller capability. Classical CAN and CAN FD require distinct capability checks.

<a id="r21"></a>

### R21 — Wireshark

[Official user documentation](https://www.wireshark.org/docs/)

For Module 15, capture and annotate traffic from your own measurement system. Identify where link frames, IP packets, transport and application records appear. Application throughput and packet arrival times should not be mistaken for ADC timing.

<a id="r22"></a>

### R22 — MIT 6.013: Electromagnetics and Applications

[Lecture notes](https://ocw.mit.edu/courses/6-013-electromagnetics-and-applications-spring-2009/pages/lecture-notes/)

Use selected field, energy-flow and transmission-line topics for Module 16 and the RF track. Your physics background makes this an opportunity to connect return paths and distributed effects to the field description. Revisit only the field mathematics you need for the design question.

## Optional advanced tools

<a id="r23"></a>

### R23 — Open-source RF analysis

[Qucs-S project](https://ra3xdh.github.io/) · [scikit-rf documentation](https://scikit-rf.readthedocs.io/en/latest/)

Use the appropriate Qucs-S backend for the circuit/network model; it is a frontend, not one universal simulation kernel. Use scikit-rf's network, calibration and de-embedding material for measured S-parameters. Record port/reference-plane assumptions.

<a id="r24"></a>

### R24 — FPGA simulation, synthesis and implementation

[Icarus Verilog](https://github.com/steveicarus/iverilog) · [Verilator guide](https://verilator.org/guide/latest/) · [Yosys](https://github.com/YosysHQ/yosys) · [nextpnr](https://github.com/YosysHQ/nextpnr)

Use the projects' own supported-language/device documentation. Choose the FPGA board only after verifying the complete synthesis, place-and-route, bitstream and programming route. Simulation, timing analysis and physical validation answer different questions.

<a id="r25"></a>

### R25 — Open IC design tools

[Xschem](https://xschem.sourceforge.io/stefan/index.html) · [KLayout](https://www.klayout.de/doc.html) · [Magic](https://opencircuitdesign.com/magic/) · [Netgen](https://opencircuitdesign.com/netgen/) · [OpenROAD](https://openroad.readthedocs.io/en/latest/)

For the IC track, select a documented PDK-compatible flow and pin its versions. A practical analog route combines schematic/SPICE work, a supported layout/extraction tool and LVS; the digital route adds synthesis and physical implementation. Check that the relevant DRC/LVS/extraction decks actually support the selected process and tool combination.

<a id="r26"></a>

### R26 — SKY130 process documentation and limitations

[PDK documentation and status](https://skywater-pdk.readthedocs.io/en/main/status.html)

Read device/model, design-rule and known-issue material for the chosen release. The project labels the open release experimental. Keep educational verification distinct from foundry sign-off, yield guarantees or fabrication availability.

## Reading strategy

Before each lab, read the exact device and instrument documentation needed to avoid guessing pinouts, voltage limits or timing. After the lab, use the theory sources to explain the largest discrepancy. When a source assumes an ideal device, explicitly restore the limitation that matters in your circuit. Keep a small reading log with the document revision, relevant sections and the question it answered.

<a id="r27"></a>

## R27 — Optional continuous textbooks for circuit fundamentals

[Author's open-textbook catalogue](https://www.jimfiore.org/Books.html) · [DC Electrical Circuit Analysis: A Practical Approach, PDF](https://www.jimfiore.org/books/DCElectricalCircuitAnalysis.pdf) · [AC Electrical Circuit Analysis: A Practical Approach, PDF](https://www.jimfiore.org/books/ACElectricalCircuitAnalysis.pdf)

These provide explanatory prose, worked examples and practice problems for the first circuit modules. The DC text covers basic quantities, resistive networks, analysis techniques, capacitors and inductors. The AC text develops sinusoidal circuits, impedance and RLC analysis. They are accessible starting points; retain the MIT and Roberge readings for the course's more theoretical development. Use KiCad/ngspice for simulator exercises, irrespective of a source's simulator illustrations.

## Additional open courses and teaching series

<a id="r28"></a>

### R28 — MIT 6.334: Power Electronics

[Lecture notes](https://ocw.mit.edu/courses/6-334-power-electronics-spring-2007/pages/lecture-notes/)

Chapter 5's DC/DC principles and Chapter 13's thermal models support Module 10. The full graduate course is optional. Later control and EMI-filtering chapters provide a deeper path after the basic power tree is working.

<a id="r29"></a>

### R29 — NIST and instrument-maker measurement teaching

[NIST TN1297](https://www.nist.gov/pml/nist-technical-note-1297) · [Covariance/propagation appendix](https://www.nist.gov/pml/nist-technical-note-1297/nist-tn-1297-appendix-law-propagation-uncertainty) · [Tektronix oscilloscope primer](https://www.tek.com/en/documents/primer/xyzs-oscilloscopes-primer) · [Keysight oscilloscope video](https://www.youtube.com/watch?v=t_UTV_9dpTc)

For Module 03, combine a precise uncertainty model with practical probe/scope operation. The chapter includes a university-hosted copy of the manufacturer primer if its main page is inaccessible. Substitute the actual instrument's manual for model-specific operating limits.

<a id="r30"></a>

### R30 — NPTEL/IIT Madras: Solid State Devices

[Open course](https://nptel.ac.in/courses/117106091) · [S. Karmalkar, Lecture 19: PN Junction](https://www.youtube.com/watch?v=IMoJUqDlSQs)

A university video complement to MIT 6.012's written device theory in Module 04. Use selected lectures where another derivation helps; the complete series is additional study.

<a id="r31"></a>

### R31 — TI Precision Labs and analog teaching videos

[Op-amp course](https://www.ti.com/en-us/design-development/educational-resources/video/series/precision-labs/ti-precision-labs-op-amps) · [ADC course](https://www.ti.com/video/series/precision-labs/ti-precision-labs-analog-to-digital-converters-adcs.html) · [CAN/LIN course](https://www.ti.com/video/series/precision-labs/ti-precision-labs-can-lin-sbc.html)

Short manufacturer lessons support Modules 08, 12–13, 15 and 17–18; the chapters link the selected videos directly. Use the associated slides/quiz to check understanding. TINA-TI, vendor calculators and training boards shown in demonstrations are not required; reproduce the appropriate circuits and experiments with the course tools and equipment.

<a id="r32"></a>

### R32 — FreeRTOS book and DigiKey/Shawn Hymel RTOS teaching

[Official FreeRTOS Kernel Book contents](https://github.com/FreeRTOS/FreeRTOS-Kernel-Book/blob/main/toc.md) · [DigiKey Part 3 companion: scheduling](https://www.digikey.com/en/maker/projects/introduction-to-rtos-solution-to-part-3-task-scheduling/8fbb9e0b0eed4279a2dd698f02ce125f) · [Part 5 companion: queues](https://www.digikey.com/en/maker/projects/introduction-to-rtos-solution-to-part-5-freertos-queue-example/72d2b361f7b94e0691d947c7c29a03c9)

Module 11 combines kernel concepts with concrete ESP32 experiments. Read task/queue management first, then the pinned ESP-IDF implementation notes. The companion articles carry the publisher's embedded videos and examples; transfer their logic into the framework you use.

<a id="r33"></a>

### R33 — MIT Missing Semester and pySerial

[Command-Line Environment: notes and video](https://missing.csail.mit.edu/2020/command-line/) · [pySerial introduction](https://pyserial.readthedocs.io/en/latest/shortintro.html)

For Module 14, select jobs, signals and process control, then serial reads/writes, timeouts and framing. Skip programming/shell basics you already know; preserve the distinction between host-process control and converter sampling timing.

<a id="r34"></a>

### R34 — MIT 2.161: continuous/discrete signal processing

[Lecture 8: second-order sections and active filters](https://ocw.mit.edu/courses/2-161-signal-processing-continuous-and-discrete-fall-2008/resources/lecture_08/)

Module 07 uses the analog realisation of a specified response, including state-variable filters. Derive one circuit and test its loading and component sensitivity rather than taking the entire signal-processing course.

<a id="r35"></a>

### R35 — Practical PCB field and stackup lectures

[Rick Hartley: How to Achieve Proper Grounding](https://www.youtube.com/watch?v=ySuUZEjARPY) · [Phil's Lab #56: PCB Stack-Up and Build-Up](https://www.youtube.com/watch?v=QAOEtfvCaMw)

Module 16 uses Hartley's field/return-path reasoning alongside university transmission-line notes. Phil's Lab is optional stackup depth. These are practitioner resources, with vendor hosting/sponsorship; their software demonstrations are not a requirement. Apply the transferable design principles in KiCad.

<a id="r36"></a>

### R36 — Calibration and an open university analog-project brief

[NIST calibration handbook](https://www.itl.nist.gov/div898/handbook/mpc/section3/mpc3.htm) · [MIT 6.101 Final Project](https://web.mit.edu/6.101/www/s2019/finalproject.html) · [TI gain/offset calibration video](https://www.ti.com/video/5466249277001)

Module 18 draws on calibration-model validation and engineering design/review/report practice. The historical MIT class's deadlines and grading do not apply. The capstone's own acceptance tests remain the requirements for your instrument; its electrical calibration does not establish absolute optical calibration.

<a id="r37"></a>

### R37 — Peter Dordal: An Introduction to Computer Networks

[Open university textbook](https://intronetworks.cs.luc.edu/current2/html/index.html)

Optional Module 15 context: start with Chapter 1's layers, rates, Ethernet/IP and transport overview, then consult the relevant Wi-Fi/TCP/UDP sections for your chosen transport. This supplies network theory beyond packet-inspection tool documentation.
