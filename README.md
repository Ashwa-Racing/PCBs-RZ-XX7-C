# RZ-XX7-C Electrical and PCB Designs

This repository contains the electrical design files for the Ashwa Racing
RZ-XX7-C, a 2027 combustion prototype. It covers the accelerator pedal position
sensor board (APPS), brake system plausibility device (BSPD), control unit,
interface control unit (ICU), and vehicle wiring harness.

The KiCad projects are the editable design sources. PDF drawings, PCB
manufacturing exports, and 3D models are included where available. Firmware
source and release binaries are not part of this repository.

## Design overview

| Design | Role |
| --- | --- |
| [APPS board](<./APPS-RZ-XX7-C/>) | Reads accelerator-pedal and throttle-position signals. Its schematic includes an STM32F4x1 module, analog signal conditioning, plausibility logic, relay control, and ETB-related signals. |
| [BSPD](<./BSPD-RZ-XX7-C/>) | Monitors brake-pressure, throttle-position, and brake-light-related signals. The schematic documents the plausibility, timing, reset, relay, and shutdown-circuit logic. |
| [Control Unit](<./Control Unit/>) | Provides power switching and control interfaces for the starter relay, fuel pump, electronic throttle body, radiator fan, water pump, and compressor. |
| [Interface Control Unit](<./Interface Control Unit/>) | Provides the vehicle interface electronics, including a Raspberry Pi Zero 2 W, CAN-FD controller and transceiver, IMU connections, and power/control circuitry for the display and auxiliary lighting. |
| [Harness](<./Harness-RZ-XX7-C/>) | Documents vehicle wiring and connectors between the engine-management system, boards, sensors, actuators, display, and vehicle systems. |

These descriptions summarize the design files; consult the schematics and
harness drawing for pin assignments, circuit details, and connector wiring.

## Repository contents

Each board folder contains a KiCad schematic (`.kicad_sch`), PCB layout
(`.kicad_pcb`), project settings (`.kicad_pro`), and a plotted schematic PDF.
The harness folder contains the corresponding wiring schematic, PCB document,
and PDF drawing.

| Folder | Design documents | Additional files |
| --- | --- | --- |
| [APPS-RZ-XX7-C](<./APPS-RZ-XX7-C/>) | [Schematic PDF](<./APPS-RZ-XX7-C/APPS-RZ-XX7-C%20Schematic%20PDF.pdf>) | [Gerbers and drill file](<./APPS-RZ-XX7-C/Gerbers/>), [3D model](<./APPS-RZ-XX7-C/APPS-RZ-XX7-C.step>) |
| [BSPD-RZ-XX7-C](<./BSPD-RZ-XX7-C/>) | [Schematic PDF](<./BSPD-RZ-XX7-C/BSPD-RZ-XX7-C%20Schematic%20PDF.pdf>) | [Gerbers and drill file](<./BSPD-RZ-XX7-C/Gerbers/>), [3D model](<./BSPD-RZ-XX7-C/BSPD-RZ-XX7-C.step>) |
| [Control Unit](<./Control Unit/>) | [Schematic PDF](<./Control%20Unit/Control%20Unit%20Schematic%20PDF.pdf>) | [Gerbers and drill file](<./Control%20Unit/Gerbers/>), [3D model](<./Control%20Unit/Control%20Unit.step>) |
| [Interface Control Unit](<./Interface Control Unit/>) | [Schematic PDF](<./Interface%20Control%20Unit/Interface%20Control%20Unit%20Schematic%20PDF.pdf>) | [Gerbers and drill file](<./Interface%20Control%20Unit/Gerbers/>), [ICU and display STEP archive](<./Interface%20Control%20Unit/ICU%20+%20Display%20V2%20STEP.zip>), [ICU STEP archive](<./Interface%20Control%20Unit/RZ-XX7-C%20ICU%20STEP.zip>) |
| [Harness-RZ-XX7-C](<./Harness-RZ-XX7-C/>) | [Harness PDF](<./Harness-RZ-XX7-C/Harness-RZ-XX7-C%20PDF.pdf>) | Reference manuals and wiring diagrams are in [Datasheets](<./Harness-RZ-XX7-C/Datasheets/>) |

The Gerber folders contain the copper, solder-mask, paste, silkscreen, and
board-outline layers, along with Excellon drill data. A Gerber set is currently
present for APPS, BSPD, Control Unit, and ICU; no harness Gerber export is
included.

The ICU folder also contains power-supply analysis documents in `Documents/`
and local KiCad symbol and footprint libraries alongside several projects.
Keep those libraries with their projects when moving or editing the designs;
KiCad may need their library paths configured on another machine.

## Opening and using the designs

1. Install KiCad and open a project's `.kicad_pro` file, or open its schematic
   or PCB file directly.
2. If KiCad reports missing symbols or footprints, configure the project's
   local libraries. Several custom libraries are stored in the relevant
   project folders.
3. Review the schematic and PCB together before making changes. Use the
   checked-in PDFs for quick reference; the KiCad files remain the editable
   source.
4. For fabrication, review the Gerber and drill files in a Gerber viewer and
   confirm the board revision and fabrication requirements before sending
   them to a manufacturer. Regenerate the exports from the KiCad source after
   changing a design.

The Gerber file headers identify KiCad 10.0.6 as the export version. KiCad
projects and generated manufacturing files should be checked together when
preparing a new release.

## Firmware status

- [ ] Upload the updated firmware to the target hardware.

Firmware source and binaries are not stored here, so this repository does not
provide firmware build or upload instructions.
