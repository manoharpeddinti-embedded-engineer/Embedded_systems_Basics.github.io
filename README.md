# Embedded-Systems Career Roadmap

A research-backed, role-aware learning plan for candidates targeting embedded-systems companies. It is designed as a living GitHub knowledge base, not a claim that one person must master every specialization.

## Start here

1. Read [the role map](ROLE-AND-SKILL-MAP.md) and choose a primary track by Phase 4.
2. Follow [the phased roadmap](ROADMAP.md), completing its evidence-based exit criteria rather than studying only by calendar.
3. Record projects, bugs, measurements, test evidence, schematics, and design decisions in a public portfolio repository.
4. Use [the primary-source resource index](RESOURCES.md), pinning exact tool/SDK versions in every project.

## Repository structure

| File | Purpose |
|---|---|
| `ROADMAP.md` | Detailed phases from prerequisites through job readiness and ongoing growth. |
| `ROLE-AND-SKILL-MAP.md` | Universal skills, depth expectations, and track-specific requirements. |
| `RESOURCES.md` | Curated official documentation, standards, and learning resources. |

## Guiding principle

Embedded work is a system discipline: hardware constraints, firmware behavior, verification, and lifecycle concerns interact. Learn broadly enough to communicate across those boundaries, then develop demonstrable depth in one target role.

## Suggested first hardware

- STM32 Nucleo or similar Cortex-M board + ST-Link/J-Link debugger.
- Breadboard, regulated supply, jumper wires, resistors, LEDs, switches, and a logic analyzer.
- Multimeter; add an oscilloscope when working on timing, analogue signals, or fast buses.
- Optional: ESP32 for connected products, Nordic board for BLE/low power, Raspberry Pi/Linux SBC for embedded Linux.

Do not connect unknown circuits directly to a computer or power source. Confirm voltage levels, grounding, current limits, and probe ground placement first.
