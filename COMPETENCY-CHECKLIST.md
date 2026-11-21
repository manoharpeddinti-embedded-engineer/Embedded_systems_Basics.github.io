# Competency Checklist and Evidence Log

Mark a topic only when you can explain it, apply it, and show evidence. Suggested scale: **0** = unseen, **1** = recognize, **2** = explain, **3** = implement with guidance, **4** = independently implement/debug, **5** = review/teach/optimize. Link each score to a commit, lab note, test or measurement.

## 1. Electrical and analogue fundamentals

| Competency | Evidence expected |
|---|---|
| Voltage, current, resistance, power, energy; passive sign convention | Hand calculation and multimeter verification |
| KCL/KVL; divider loading; Thévenin/Norton | Solve and measure a loaded divider |
| Capacitors/inductors; RC/RL transients; filters | Plot predicted vs measured time/frequency response |
| AC: impedance, phase, RMS, dB, resonance | Explain measurement and limitations |
| Diode/BJT/MOSFET operation; low-/high-side switching | Safe LED/load switching design |
| Linear vs switching regulation; efficiency, ripple, thermal derating | Power budget and regulator-selection rationale |
| Op-amp limits: common mode, rail-to-rail, offset, bandwidth | Review an analogue front-end circuit |
| ADC input conditioning, reference, sampling and quantization | Sensor calibration/error analysis |
| ESD/EMI basics, TVS/fuse/reverse polarity | Identify protection components in a schematic |

## 2. Digital hardware and board literacy

| Competency | Evidence expected |
|---|---|
| Logic families, thresholds, fanout, 3.3/5 V compatibility | Diagnose a level mismatch |
| Pull-up/down, open-drain, push-pull, tri-state | Configure and measure each GPIO mode |
| Debounce, metastability, synchronization | Hardware/software debounce comparison |
| Clock, reset, boot straps, decoupling | Annotated board schematic |
| I2C: open drain, pull-up sizing, address/NACK/arbitration | Decode capture and recover a stuck bus |
| SPI: modes, chip select, timing, MISO contention | Decode capture and configure correct mode |
| UART: framing, baud error, flow control | Debug a corrupted serial link |
| CAN/LIN/RS-485: differential signalling, termination, faults | Explain intended use and physical-layer needs |
| USB/Ethernet basics | Identify when specialized hardware/stack is necessary |
| PCB: return paths, decoupling, grounding, DFM/DFT | Perform a basic design review |

## 3. C and low-level software

| Competency | Evidence expected |
|---|---|
| Integer width/signedness/promotion/conversion | Tests for edge values and compiler warnings |
| Bit manipulation and register field APIs | Driver code with named masks and review notes |
| Pointer/array/struct/union behavior, alignment, packing | Explain portability and inspect memory layout |
| `const`, `volatile`, static storage, linkage, headers | Correct minimal multi-file module |
| Undefined behavior, strict aliasing, shift/overflow hazards | Find and repair intentionally flawed code |
| Ring buffers, finite-state machines, parsers, CRC | Tested bounded-memory implementation |
| Error contracts, assertions, defensive validation | Error-path tests |
| Memory map, sections, startup and linker script | Linker-map annotation |
| Assembly/disassembly and calling convention basics | Debug a fault to source/instruction |

## 4. MCU peripherals and real time

| Competency | Evidence expected |
|---|---|
| Clock tree, peripheral clocking, pin mux | Compute settings and validate signal |
| IRQ vectoring, priorities, nesting, latency | Trace/timing measurement |
| Timer, input capture, output compare, PWM | Measured frequency/duty and edge cases |
| DMA configuration/lifetime/cache interactions | Transfer test with faults/timeouts |
| ADC/DAC/triggering/calibration | Sampling and error report |
| Low-power modes, wake sources, power profiling | Sleep-current measurement |
| Watchdog/reset cause/brownout behavior | Test plan and recovery demonstration |
| Fault handlers and post-mortem capture | Intentional fault exercise |
| RTOS task model, queues, event flags, mutexes | Concurrency diagram and stress test |
| Priority inversion, race/deadlock prevention | Reproduced problem and fix |

## 5. Tools, debugging, testing and delivery

| Competency | Evidence expected |
|---|---|
| Git/reviewable commits/tags | Inspectable history and release tag |
| Cross toolchain, CMake/Make, reproducible build | Clean build on another machine/CI |
| GDB/SWD/JTAG breakpoint/watchpoint/register inspection | Debug session note |
| Logic analyzer/oscilloscope/multimeter use | Annotated captures/readings |
| Compiler warnings, map/ELF size analysis | Flash/RAM/stack budget |
| Unit/integration/HIL test strategy | Test matrix and automated tests |
| Mocking and host-side testing | Independent tests for protocol/business logic |
| Static analysis/formatting/code review | Tool output and review checklist |
| CI artifact/release notes/versioning | Passing pipeline + immutable artifact |
| Requirements/design/test traceability | Small traceability table |

## 6. Reliability, security and professional practice

| Competency | Evidence expected |
|---|---|
| Failure modes, timeout/retry, safe state | Fault-injection result |
| Checksums/CRC, persistence/version migration | Corrupt-data recovery test |
| Boot/update/rollback lifecycle | Diagram and testable strategy |
| Threat model and trust boundaries | Written threat model |
| Secure boot/signatures/keys/debug policy | Correct conceptual design; no hard-coded secret |
| TLS/authentication/input validation | Negative-path and expiry/error tests |
| SBOM/dependency/vulnerability process | Generated or documented inventory |
| Requirements/change control/risk communication | Concise design decision record |

## Portfolio evidence template

For every project include:

```text
Problem and constraints:
Target hardware and exact revision:
Toolchain / SDK / build command:
Interfaces and electrical assumptions:
Architecture and task/interrupt model:
Timing, flash, RAM, stack, power budgets:
Test strategy and result summary:
Faults injected and observed recovery:
Security and safety boundaries:
Trade-offs / known limitations / next work:
Demo and reproduction instructions:
```

## Interview drill bank

- A UART occasionally drops bytes. Enumerate the evidence you request, then test clock, baud, ISR/DMA buffering, flow control, electrical levels and framing.
- An I2C bus is held low. Explain pull-ups, open drain, clock stretching, reset/recovery and measurement precautions.
- A task hangs only under load. Separate deadlock, priority inversion, stack overflow, allocation failure and ISR misuse; name the evidence for each.
- A field update bricks a device after power loss. Design an image/boot-state strategy and recovery path.
- A sensor is noisy. Distinguish source noise, aliasing, grounding/layout, ADC reference, filtering and software smoothing.
- A watchdog resets intermittently. Avoid merely increasing timeout; identify blocking paths, deadlines, heartbeats, reset-cause capture and safe recovery.
