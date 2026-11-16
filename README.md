# Microelectronics: circuits to scientific instruments

A self-paced course for a physicist who knows mathematics and programming and is beginning practical electronics. Start with charge, voltage, current, and real measurements; finish by designing and characterising a photodiode instrument with a custom PCB, ESP32 acquisition, and Raspberry Pi analysis.

The central habit is **derive → simulate → build → measure → explain discrepancies**. Mathematical fluency lets you explore the models deeply. Practical competence comes from checking where those models stop describing your hardware.

**Read online:** [Microelectronics course website](https://guimarais.github.io/microelectronics/), with chapter navigation, search, reading/video links and browser-saved progress. The reader automatically checks this repository's published Markdown for updates; its implementation lives in the [portfolio repository](https://github.com/guimarais/guimarais.github.io/tree/master/microelectronics).

## Course handbook

| Document | Use it for |
| --- | --- |
| [Course](COURSE.md) | All chapters 00–18, each with direct core readings, recommended videos/YouTube links, optional depth, exercises and labs |
| [Laboratory](LAB.md) | Equipment tiers, phased purchases, software, measurement practice, and instrument access |
| [Capstone](CAPSTONE.md) | Instrument architecture, design targets, calibration, and acceptance measurements |
| [Read the teaching material](REFERENCES.md) | Direct links to written notes/textbooks, mapped to the modules; annotated sources below |
| [First lab](labs/01-dc-circuits.md) | A fully worked learning sequence for DC circuits, loading, and uncertainty |
| [First-lab solutions](solutions/01-dc-circuits.md) | Numerical checks and derivations; open after attempting the problems |
| [Progress](PROGRESS.md) | Your completion record and links to evidence |

## Scope and workload

The core contains **19 modules and approximately 450 hours**, including its capstone. At 5–7 hours weekly, allow **65–90 working weeks**, approximately **15–21 months before breaks**. These are planning estimates, not deadlines; equipment delivery, debugging, and PCB revisions can add time. Optional tracks add their own hours.

| Phase | Modules | Hours | Cumulative hours | Outcome |
| --- | --- | ---: | ---: | --- |
| Circuits and measurement | 00–03 | 64 | 64 | Analyse and measure loaded DC and dynamic circuits |
| Devices and analog design | 04–08 | 128 | 192 | Connect device physics to amplifiers, stability, and noise |
| Digital circuits and power | 09–10 | 38 | 230 | Design logic interfaces and a reliable power budget |
| Embedded acquisition and communications | 11–15 | 102 | 332 | Build a timed, observable measurement system |
| PCB and photodiode front end | 16–17 | 54 | 386 | Produce a reviewed mixed-signal design |
| Integrated scientific instrument | 18 | 64 | 450 | Assemble, calibrate, and defend the complete instrument |

RF, FPGA design, and integrated-circuit design are separate advanced tracks. The core includes semiconductor physics and transistor-level design; the IC track extends this to process-specific models, layout, extraction, and physical verification.

## Your platforms

- **KiCad + ngspice:** schematic capture, circuit simulation, PCB layout, and manufacturing outputs. KiCad integrates ngspice; no proprietary simulator is required. See [KiCad's simulator overview](https://www.kicad.org/discover/spice/).
- **ESP32:** timers, interrupts, peripheral buses, acquisition, buffering, and wireless experiments. Start from the PlatformIO workflow you know; record the exact chip, board, and framework versions.
- **Raspberry Pi running Linux:** supervision, logging, analysis, networking, and a persistent laboratory instrument. Keep acquisition timing near the ADC and MCU.
- **Python:** numerical models, fits, uncertainty propagation, spectral analysis, and plots. There is no introductory programming or calculus sequence.

Required development and analysis tools are open source. Disclosed vendor firmware, instrument firmware, and component models may be proprietary. The lab guide identifies this boundary and gives an open-source route for the work you author.

## How to study

Use a typical six-hour week as two hours of theory and derivation, one hour of problems/simulation, two hours at the bench, and one hour of analysis and notes. Some weeks will be entirely theoretical or experimental.

For each module, preserve the schematic, assumptions, calculations, simulation settings, raw data, instrument settings, analysis, and a short explanation of model–measurement disagreement. A neat plot without its acquisition conditions is incomplete evidence.

Use the **External materials** section within each chapter as your reading/viewing path. It selects specific notes, book sections and lectures, including official YouTube uploads where available. The stated resource-work allowance is included in the module's hours; optional courses and deeper videos are additional study.

Advance when you can pass the module's gate, including its unfamiliar transfer problem. Familiar mathematics can be accelerated. Instrument operation and circuit debugging still require direct practice. Keep simulation-only work marked as such until the physical measurement has been completed.

## Start here

1. Read Module 00 and the laboratory guide's operating rules.
2. Open the [reading path](REFERENCES.md). Read MIT 6.002's written notes for Lectures 1–3, then start [Lab 01](labs/01-dc-circuits.md), Sections 1–4, using paper and KiCad. No hardware purchase is needed for this part.
3. Acquire only the first equipment phase in [LAB.md](LAB.md). Measure the same circuits and compare with your predictions.
4. Record evidence in [PROGRESS.md](PROGRESS.md). Continue with Module 02 when the DC-circuit gate is complete.

Do not buy the entire laboratory immediately. The minimum-cost path uses borrowed instruments at specified gates; the fuller path equips your own bench. Neither a simulation nor a digital logic analyser substitutes for an analog stability measurement.

## What completion means

You can translate a physical measurement into electrical requirements; derive and assess circuit models; choose devices from datasheets; simulate and build the signal chain; diagnose analog, digital, and timing faults; design its PCB; and report performance with a defensible uncertainty budget.

The capstone measures photocurrent and relative optical changes. Absolute optical power or illuminance requires additional optical calibration; a photodiode datasheet alone does not establish that calibration.

Course designed on **15 November 2026**. Prices and software interfaces should be rechecked when needed. External resources retain their own licences; links do not incorporate their content into this repository's licence.
