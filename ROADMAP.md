# Phased Roadmap

The durations are planning ranges for part-time study. Advance only when the exit criteria are met. Keep a lab notebook from Day 1: board, toolchain/SDK version, schematic/datasheet links, hypothesis, measurements, failure, fix, test result and commit.

## Phase 0 — Orientation and lab safety (1 week)

**Learn:** the difference between MCU firmware, RTOS, Linux, PCB, FPGA and validation roles; electrical safety; ESD; voltage/current/power; common ground; probe grounding; datasheet navigation.

**Do:** install Git, a compiler/toolchain, vendor IDE/CLI and serial terminal. Configure editor formatting, warnings, Git identity and a repository. Read the board schematic, pinout, MCU data sheet and reference manual table of contents.

**Evidence / exit:** a `lab-notes` repository containing environment setup, a photographed/diagrammed safe LED circuit, measured voltage/current, and a one-page target-role decision.

## Phase 1 — Circuits, logic and measurement (4–8 weeks)

**Theory:** DC and AC basics; passive parts and tolerances; dividers; pull resistors; RC filters; diodes/transistors; op-amp boundaries; switching regulators; digital thresholds; Boolean algebra; combinational/sequential logic; clocks and timing; ADC/DAC sampling basics.

**Practical labs:**

- Calculate then measure LED current and resistor dissipation; explain error from nominal values.
- Build button pull-up/pull-down and RC debounce circuits; compare physical bounce with firmware debounce.
- Measure PWM duty/frequency and RC-filter output.
- Read sensor supply and logic-level constraints; demonstrate why a 5 V-to-3.3 V interface can fail.

**Problems to solve:** divider loading; capacitor tolerance; RC time constant; logic-level compatibility; aliasing; ground-loop/probe mistakes; heat/power dissipation.

**Exit:** explain every component and net in a small schematic; use multimeter and logic analyzer safely; publish calculations, waveform captures and a short error analysis.

## Phase 2 — Programming foundations for constrained systems (6–10 weeks)

**C in depth:** integer widths and signedness, casting, bitwise operations, masks, shifts, endian conversions, pointer arithmetic, array decay, structure packing/alignment, storage duration, header/API design, `volatile`, `const`, `restrict`, error handling, dynamic-memory avoidance, stack budgeting, preprocessor risks and undefined behavior.

**Computer science:** complexity; ring buffer; queue; finite-state machine; binary search; CRC; debouncing; parser design; testable modular architecture.

**Practice without hardware:** implement a fixed-capacity ring buffer, non-blocking button debouncer, CRC-16/32, byte-stream packet parser and event-driven state machine. Add host unit tests, invalid-input tests, formatting, static analysis and CI.

**Exit:** defend each `volatile` use; explain a data race vs an interrupt-safe design; read compiler warnings; interpret a stack trace/map-file symbol; submit a clean PR-style README and test report.

## Phase 3 — One MCU from reset to peripherals (8–12 weeks)

**Architecture:** reset/startup, vector table, memory map, flash/SRAM, clock tree, bus/peripheral clock gating, NVIC, SysTick, exceptions, stack frames, linker script, sections, boot modes, MMIO and barriers.

**Peripherals, in this order:** GPIO → timer/PWM → UART → interrupt-driven UART/ring buffer → I2C/SPI sensor → ADC/DMA → low-power sleep/wake → watchdog/reset-cause. Use vendor HAL initially, then implement at least two small drivers from register-level documentation.

**Debug drills:** intentionally create an incorrect clock setup, missing peripheral clock, wrong alternate-function pin, baud-rate mismatch, I2C pull-up problem, ISR storm, stack overflow and hard fault. Capture symptoms, hypothesis and resolution.

**Portfolio project 1 — Instrumented sensor node:** periodic sensor acquisition over I2C/SPI; timestamped UART command/telemetry protocol; DMA or interrupt path; button/UI; watchdog; configuration CRC; fault counters. Include architecture diagram, pin table, protocol spec, timing/memory budget, test procedure and scope/logic traces.

**Exit:** build/flash/debug from command line; use SWD/JTAG and GDB; explain interrupt latency trade-offs; derive clock/baud/timer settings; diagnose a peripheral with datasheet + measurement.

## Phase 4 — Real-time design and RTOS (6–10 weeks)

**Theory:** latency, jitter, deadlines, rate-monotonic intuition, cooperative vs preemptive scheduling, priority inversion, critical sections, lock ordering, ISR-to-task handoff, queues/semaphores/mutexes/event flags, memory fragmentation, stack high-water marks and timeouts.

**Do:** recreate part of Project 1 using FreeRTOS or Zephyr. Model tasks and data ownership. Use queues/event flags rather than shared writable globals. Measure timing and stack use; induce and fix a priority-inversion case. Study the project’s configuration and build system.

**Exit:** choose between polling, IRQ, DMA and task context with a written justification; explain why a mutex normally differs from a semaphore; prove no blocking call is made in an ISR; show timing traces and stress-test results.

## Phase 5 — Hardware/software integration and production quality (6–12 weeks)

**Integrate:** nonvolatile storage/wear concerns; bootloader/image layout; firmware update and rollback; device identity; versioning; reset/power-fail behavior; logging; health metrics; manufacturing test hooks.

**Quality workflow:** requirements → design → implementation → review → verification → traceability. Write testable requirements, a FMEA-style risk table, test matrix and release checklist. Add CMake/Make build, unit tests, static analysis, formatting, CI and a reproducible release artifact.

**Portfolio project 2 — Reliable controller:** implement a framed protocol with CRC and timeout/retry; persistent configuration with version/migration and CRC; watchdog/recovery policy; host test harness/fuzzer for parser; update simulator or dual-bank update design (only on hardware you can safely recover).

**Exit:** a stranger can clone, build, flash, test and understand limitations. Demonstrate error injection: corrupt frame, sensor disconnect, brownout/reset simulation, full configuration storage, invalid command and stalled task.

## Phase 6 — Select a specialization (8–20+ weeks)

Pick one pathway; retain the universal core.

### A. IoT / wireless

Learn Wi-Fi/BLE/Thread/Zigbee/Matter/cellular only according to target market; RF coexistence and power profiling; IPv4/IPv6, TCP/UDP, DNS, TLS, MQTT/CoAP; provisioning; OTA; credential lifecycle; secure storage. Build an ESP-IDF or Nordic/Zephyr device with measured sleep current, authenticated update concept and outage-tolerant telemetry.

### B. Embedded Linux / drivers

Learn Linux process/thread/IPC/memory model; shell and Python; cross-toolchains; U-Boot/boot flow; root filesystem; device tree; kernel modules, driver model, GPIO/I2C/SPI/UART; Buildroot or Yocto; systemd; tracing (`dmesg`, `ftrace`, `perf` as relevant). Build a custom image and a simple kernel or userspace driver; document boot logs and device-tree changes.

### C. Hardware / PCB

Learn schematic capture and PCB CAD; component selection and datasheets; power-tree design; analogue front end; protection; layout/return paths/decoupling; SI/PI/EMI basics; DFM/DFT; fabrication/assembly files; board bring-up. Design a low-risk sensor/peripheral board, peer review it, manufacture only after checks, then run a bring-up plan with measurements.

### D. FPGA / digital

Learn synchronous RTL, Verilog/SystemVerilog or VHDL, resets/CDC, simulation/testbench, assertions, synthesis, constraints, static timing analysis, BRAM/FIFO, AXI/Avalon basics and embedded firmware interface. Deliver a simulated and board-demonstrated peripheral with self-checking tests and timing report.

### E. Automotive / safety

Learn CAN/CAN FD, LIN, UDS concepts, boot/update, AUTOSAR awareness, diagnostics, functional safety vocabulary, requirements traceability, static analysis and configuration management. Study ISO 26262 scope before using safety terminology. Deliver a CAN node with fault handling, documented requirements, test traceability and a safety-oriented design rationale.

### F. Controls, motor and power

Learn sensors, PWM/dead time, ADC synchronization, Clarke/Park transforms, fixed-point, PID/control stability, protection paths, gate drivers, current/voltage measurement and power-stage safety. Begin with low-voltage demonstrations; never improvise mains/high-energy work. Deliver a simulated controller plus a safely constrained hardware lab with recorded response and fault behavior.

## Phase 7 — Security and lifecycle competence (continuous; 4–8 focused weeks)

Threat-model one portfolio device. Define assets, attacker capabilities, attack surfaces, trust boundaries and mitigations. Implement appropriate measures: secure boot/verified image concept, signed update verification, per-device secrets, debug policy, TLS/credential validation, least privilege/MPU, input validation, rollback/version policy and vulnerability response. Create an SBOM if dependencies are used. Document what the project does *not* protect against.

## Phase 8 — Interview and application readiness (4–6 weeks)

**Portfolio minimum:** two deep repos rather than many copied tutorials. Each must include problem statement; requirements; architecture; hardware; build/flash; tests; measurement; known defects/trade-offs; demo; concise commit history.

**Prepare explanations:** `volatile` vs atomic; ISR vs thread safety; UART/I2C/SPI/CAN trade-offs; stack/heap; linker/map; watchdog; DMA/cache; mutex priority inversion; endian/alignment; reset/boot; debugging a bus; power; secure update; a failure you found systematically.

**Practice:** timed C/bit manipulation exercises; code review; draw a sensor-to-cloud or sensor-to-actuator system; read a datasheet section aloud and propose a driver; perform a mock bug triage based on logs and waveforms. Tailor résumé keywords and project emphasis to the job description; do not list technologies without evidence.

## Ongoing growth after the first role

Read reference manuals, errata and postmortems; contribute a small documentation/test/driver fix upstream; learn the company’s domain and quality process; become reliable at reproducing and communicating defects. Deepen one subsystem while preserving system-level literacy.
