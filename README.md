# Anycubic i3 Mega Klipper Configuration

This repository contains the Klipper configuration for an Anycubic i3 Mega with Ultrabase 3D printer.

## Overview

This configuration is specifically tailored for the Anycubic i3 Mega (2017 model) with Ultrabase. The printer uses dual Z-axis stepper motors and is configured for Klipper firmware running on a host computer (typically a Raspberry Pi).

## Hardware Specifications

- **Printer Model**: Anycubic i3 Mega with Ultrabase
- **Build Volume**: 210 x 210 x 205 mm
- **Kinematics**: Cartesian
- **Microcontroller**: AVR atmega2560
- **Stepper Drivers**: 
  - X, Y, Z (dual motors), and E axes
  - 16 microsteps configured for all axes

## Features

- **Dual Z-axis motors** for improved bed leveling stability
- **Input shaper** configured to reduce print artifacts and vibrations
- **PID tuning** values included for both hotend and heated bed
- **Custom G-code macros**:
  - `PAUSE` / `RESUME` - Pause and resume print functionality
  - `CANCEL_PRINT` - Cancel the current print
  - `LOAD_FILAMENT` / `UNLOAD_FILAMENT` - Automated filament change procedures

## Installation

1. Install Klipper on your host computer (Raspberry Pi recommended)
2. Copy the `config/printer.cfg` file to your Klipper configuration directory
3. Update the MCU serial path if necessary:
   ```
   serial: /dev/serial/by-id/usb-Silicon_Labs_CP2102_USB_to_UART_Bridge_Controller_0001-if00-port0
   ```
4. Restart Klipper service

## Configuration Details

### Motion Settings
- **Max Velocity**: 300 mm/s
- **Max Acceleration**: 3000 mm/s²
- **Max Z Velocity**: 10 mm/s
- **Max Z Acceleration**: 60 mm/s²

### Temperature Limits
- **Hotend**: 0-245°C
- **Heated Bed**: 0-110°C

### Input Shaper
- **X-axis frequency**: 49.535 Hz
- **Y-axis frequency**: 31.22 Hz
- **Shaper type**: EI (Equal Impulse)

## Usage

### Basic Commands

- **Home All Axes**: `G28`
- **Heat Hotend**: `M104 S[temp]` or `M109 S[temp]` (wait for temperature)
- **Heat Bed**: `M140 S[temp]` or `M190 S[temp]` (wait for temperature)
- **Load Filament**: `LOAD_FILAMENT TEMP=[temperature]`
- **Unload Filament**: `UNLOAD_FILAMENT TEMP=[temperature]`

### Pause/Resume Printing

During a print, you can use:
- `PAUSE` - Pauses the print and parks the toolhead
- `RESUME` - Resumes the print from where it was paused
- `CANCEL_PRINT` - Cancels the print and turns off heaters

## Calibration

Before first use, ensure to:
1. Verify all endstops are working correctly
2. Calibrate E-steps for your specific extruder
3. Run PID tuning for both hotend and bed if temperatures are unstable
4. Perform bed leveling

## Safety Notes

- The firmware is configured for an AVR atmega2560 - ensure this matches your board
- Always verify endstop functionality before homing
- The configuration includes min/max temperature limits for safety
- Test all movements at low speeds initially

## Contributing

Feel free to submit issues or pull requests if you have improvements or fixes for this configuration.

## License

This configuration is provided as-is for use with Anycubic i3 Mega printers running Klipper firmware.