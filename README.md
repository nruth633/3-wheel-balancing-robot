# 3-Wheel Robot

A three-wheel robot on an STM32F401 control board I designed in KiCad and soldered by hand.
An ESP8266 runs its own WiFi access point and serves a control page, so you can drive it from
a phone browser. Button presses go over a WebSocket to the ESP8266, which passes them to the
STM32 over UART. Roll and pitch from the MPU6050 are sent back to the page.

I started this as a self-balancing robot, but I didn't get as far as a working balance
controller, so for now it only drives. The wheel encoder code is also switched off, so the
speed readout on the control page stays at 0.

Write-up: https://nruth633.github.io/projects/balancing-robot.html

## What's in here

- `balance_noEncoder/`: the STM32 firmware (STM32CubeIDE, HAL). Reads the MPU6050 through a
  complementary filter at 100 Hz, drives the motors through a TB6612FNG, and talks to the
  ESP8266 over UART.
- `remote_esp8266/`: the ESP8266 sketch (access point, web page, WebSocket server).
- `pcb/`: KiCad project for the control board.
- `firmware_v2/`: KiCad project for a later board revision.
- `firmware_main/`: the first board, a two-wheel version: KiCad files, gerbers, an
  interactive BOM, a CAD model of the assembly, and build photos. No firmware, despite
  the name.

The board files were saved in KiCad 9 and 10, so open them in KiCad 10.
