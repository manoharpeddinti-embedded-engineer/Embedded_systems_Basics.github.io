# Primary-Source Resource Index

Prefer documentation for the exact board, silicon revision and SDK release used in a project. Vendor APIs change; pin versions and record links in your repository.

## Architecture, firmware and RTOS

- [Arm embedded and microcontroller resources](https://developer.arm.com/embedded-and-microcontrollers) — Cortex-M tooling, CMSIS, DSP/ML and learning paths.
- [Arm CMSIS overview](https://developer.arm.com/Tools%20and%20Software/Keil%20MDK) — vendor-independent Cortex-M interfaces to core/peripherals, RTOS and middleware.
- [FreeRTOS documentation](https://docs.freertos.org/) — kernel, scheduling and supported architecture documentation.
- [Zephyr getting started](https://docs.zephyrproject.org/latest/develop/getting_started/index.html) — toolchain, build, flash and sample workflow.
- [Zephyr project documentation practices](https://docs.zephyrproject.org/latest/project/documentation.html) — useful example of API/test documentation and requirement traceability.
- [RISC-V ratified specifications](https://docs.riscv.org/) — official unprivileged and privileged ISA references.

## Vendor ecosystems and boards

- [STM32Cube documentation](https://dev.st.com/stm32cube-docs/stm32cubedocs-landing-page/en/index.html) and [STM32CubeIDE guide](https://www.st.com/resource/en/user_manual/um2609-stm32cubeide-user-guide-stmicroelectronics.pdf).
- [Espressif ESP-IDF get started](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html). Use a stable release for production-oriented work; the latest/master docs can change.
- [Nordic nRF Connect SDK](https://www.nordicsemi.com/Products/Development-software/nRF-Connect-SDK/GetStarted) and [installation/versioning](https://nrfconnectdocs.nordicsemi.com/ncs/latest/nrf/installation.html).
- [TI C2000 Academy overview](https://www.ti.com/document-viewer/lit/html/SPRT766/GUID-C750C29F-84F4-4C7F-8F6D-3A52B80932B7) — peripherals, motor control and digital power training.

## Linux and interfaces

- [Linux kernel GPIO documentation](https://docs.kernel.org/driver-api/gpio/index.html) and [GPIO-backed bus examples](https://docs.kernel.org/driver-api/gpio/drivers-on-gpio.html) — useful entry points to kernel driver conventions.
- Exact bus specs are often licensed standards. Use vendor datasheets/reference manuals and official standards bodies; do not rely on random code snippets for electrical requirements.

## Safety and security

- [ISO 26262 overview](https://www.iso.org/publication/PUB200262.html) — automotive functional safety standard family, including systems, hardware, software and supporting processes.
- [IEC 61508 functional-safety overview](https://assets.iec.ch/public/acos/IEC%2061508%20%26%20Functional%20Safety-2022.pdf) — generic E/E/PE functional-safety principles.
- [OWASP IoT project](https://owasp.org/projects/internet-of-things) — common IoT risks including weak credentials, insecure services, insecure interfaces and unsafe update mechanisms.
- [OWASP OT Top 10](https://ot.owasp.org/v/2025/the-top-10/) — operational-technology risk context.

## Essential companion references to obtain for each project

1. Board schematic and user guide.
2. MCU datasheet, reference manual, programming manual and errata.
3. SDK release notes and migration notes.
4. Debug-probe manual and toolchain/GDB documentation.
5. Device/sensor datasheet and protocol specification.
6. Organisation/domain standards required by the target employer.

## Research notes

This index was checked on 2026-11-21. It deliberately favors official vendors, standards bodies, kernel/RTOS projects and ISA owners over tutorial aggregators. Links support a learning plan; they do not replace the legally required standard edition or product documentation used by an employer.
