# Role and Skill Map

## The roles are different

| Track | Typical deliverables | Must develop deeply | Helpful adjacent knowledge |
|---|---|---|---|
| MCU firmware / bare metal | drivers, application firmware, board bring-up | C, registers, interrupts, timers, DMA, debugging | RTOS, PCB reading, protocols |
| RTOS / connected IoT | concurrent firmware, networking, OTA | scheduling, synchronization, memory, TCP/IP, security | cloud APIs, RF/power measurement |
| Embedded Linux / BSP | boot flow, device tree, kernel drivers, images | Linux, C, build systems, kernel/device model | Yocto/Buildroot, scripting, hardware debug |
| Hardware / PCB | schematics, PCB, bring-up, test | analogue/digital design, power, SI/EMI, layout | firmware interfaces, DFM/DFT |
| FPGA / digital design | RTL, constraints, verification, firmware interface | digital logic, Verilog/VHDL, simulation, timing closure | SoC buses, Linux, board design |
| Automotive / safety-critical | safety artifacts, verified production firmware | CAN/LIN, diagnostics, traceability, static analysis | ISO 26262, AUTOSAR, security |
| Controls / motor / power | real-time control firmware and power electronics | PWM/ADC, control theory, fixed point, sensing | FOC, gate drive, EMC, safety |
| Test / validation / manufacturing | test rigs, reports, automation, failure analysis | test design, instrumentation, scripting, debug | requirements and quality systems |

Choose one primary track and one adjacent track. A junior candidate is not expected to be expert in all rows; claiming that often signals a shallow portfolio.

## Universal foundation: what every candidate should be able to explain and demonstrate

### Engineering mathematics and physics

- SI units; dimensional analysis; algebra, complex numbers, logarithms and decibels.
- DC/AC circuit analysis: Ohm/Kirchhoff laws, Thévenin/Norton, RC/RL/RLC response, impedance, filters, resonance, power and efficiency.
- Semiconductor basics: diode, BJT, MOSFET, op-amp; regulation, switching losses, thermal limits and derating.
- Boolean algebra, state machines, timing diagrams, setup/hold intuition, sampling/aliasing, quantization and noise.
- Numerical methods used in firmware: overflow, fixed-point scaling, saturation, rounding, error propagation; basic probability/statistics for measurement and test.
- Control basics where relevant: transfer functions, feedback, stability, PID, discrete sampling.

### Digital hardware and boards

- Read a schematic: rails, decoupling, reset/boot straps, clock source, level shifting, pull-up/down, protection, connectors and test points.
- Explain GPIO electrical modes; input thresholds; open-drain vs push-pull; voltage/current limits; debouncing; metastability.
- Select and use I2C, SPI, UART/USART, CAN/CAN FD, LIN, USB, Ethernet, RS-485, PWM, ADC, DAC, I2S/PCM as appropriate. Know framing, addressing, termination, pull-ups, clocks, fault modes and how to inspect a waveform.
- Basic PCB awareness: stackup, return current, decoupling placement, ground strategy, trace impedance, creepage/clearance, EMI/EMC, ESD, thermal paths, manufacturability and testability.

### Software and computer architecture

- C: types and integer promotion; `const`/`volatile`/`static`; pointers; arrays; structs/unions/bit-fields (and portability limits); function pointers; lifetime; undefined behavior; linkage; preprocessors; headers; memory layout; atomics; MISRA-style defensive patterns.
- C++ when a target company uses it: RAII, value/reference semantics, templates, compile-time costs, exception policy, allocation strategy and interoperability with C.
- Data structures/algorithms: arrays, ring buffers, queues, lists, heaps, hash tables; complexity; bounded-memory alternatives; sorting/searching; state machines.
- CPU: registers, stack/heap, ABI/calling convention, instruction execution, endianness, alignment, cache, MMIO, linker sections, startup code, vector table, exceptions/interrupts, MPU/MMU and privilege.
- Architectures: at least one Cortex-M family deeply; awareness of Cortex-A/R and RISC-V. Read a reference manual rather than relying solely on HAL.

### Firmware construction and quality

- Cross compilation, linker scripts/maps, ELF/BIN/HEX, Make/CMake, compiler/linker flags, warnings-as-errors, size/speed analysis.
- Git: branches, clean commits, pull requests, rebasing/merging, tags, submodules; issue tracking and release notes.
- Debug: SWD/JTAG, GDB, breakpoints/watchpoints, register/peripheral views, serial logs, core dumps, fault handlers, disassembly, map files, logic analyzer and oscilloscope.
- Verification: unit, integration, hardware-in-the-loop, regression, boundary/error-injection tests; mocks/fakes; coverage limits; code review; static analysis; sanitizers where host tests permit; CI.
- Documentation: requirements, interface contracts, block diagrams, timing diagrams, state machines, pin maps, bring-up notes, test reports, known limitations and reproducible build instructions.

### System engineering, reliability and security

- Convert stakeholder needs to measurable requirements; identify interfaces, assumptions, hazards, failure modes, timing/power/memory budgets and acceptance tests.
- Watchdog, brownout/reset cause, clock failure, safe state, fault containment, retries/backoff, wear leveling, CRC/checksums, redundant data, logging/telemetry, calibration and field diagnostics.
- Threat model assets, entry points and trust boundaries. Know secure boot chain, signed firmware, key provisioning/storage, debug-lock lifecycle, least privilege, secure communication, rollback/anti-rollback, vulnerability and SBOM processes.
- Understand that certification standards are role/domain specific. For automotive, ISO 26262 separates system, hardware, software and supporting processes; do not represent familiarity as certification competence without real process experience.

## Skills employers assess in interviews

1. Can you reason from a schematic/datasheet to working code and then prove behavior on hardware?
2. Can you write correct C under memory, latency, power and reliability constraints?
3. Can you isolate a fault using evidence rather than trial-and-error?
4. Can you explain interrupt/context safety, race conditions, volatile vs atomic operations, and lifetime?
5. Can you communicate trade-offs and leave a reproducible engineering record?
6. Have you shipped—or simulated convincingly—features such as a driver, bootloader/OTA flow, protocol stack, test harness or board bring-up?
