# 3-Wheel Balancing Robot

Self-balancing three-wheel robot — STM32F401 firmware, custom KiCad control board, and an
ESP8266 handheld remote. Built across several iterations; each is kept here rather than
overwritten so the progression is visible.

**MCU:** STM32F401RBT6 (Cortex-M4) · **IMU:** MPU6050 · **Toolchain:** STM32CubeIDE (HAL)

## Layout

| Folder | What it is |
|---|---|
| `firmware_main/` | Main firmware, plus `Kicad_Files/` for the v1 2-wheel board, `cad/` assembly model, and `Docs_Process/` build photos |
| `firmware_v2/` | Second-revision firmware and its own KiCad board (`V2_bot_embedded`) |
| `balance_noEncoder/` | Balance loop variant running without wheel encoders — IMU-only attitude estimate |
| `remote_esp8266/` | ESP8266 wireless remote (Arduino sketch) |
| `pcb/` | `Balancing_robot_ruth` KiCad project — schematic, layout, BOM, gerbers |

## Building

Firmware folders are STM32CubeIDE projects — *File → Open Projects from File System*, then
build. `Debug/` output is gitignored, so a clean checkout builds from source.

The KiCad projects open with KiCad 7+. `fp-info-cache` and `*-backups/` are gitignored and
regenerate on first open.

## Notes

- `Components/MPU6050/ITG-MPU.STEP` appears in more than one project folder because each
  KiCad project references its own footprint library copy.
