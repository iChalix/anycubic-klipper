# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Klipper 3D printer configuration repository for an Anycubic i3 Mega with Ultrabase. Klipper is an open-source 3D printer firmware that runs on a Raspberry Pi (or similar host) and controls the printer's MCU (microcontroller).

## Key Configuration

The main configuration file is `config/printer.cfg` which contains:
- Stepper motor configurations for X, Y, Z axes (dual Z motors)
- Extruder and hotend settings
- Heated bed configuration
- Fan controls
- MCU serial connection settings
- Input shaper configuration for reducing print artifacts
- Custom G-code macros for pause/resume and filament management

## Architecture

The repository follows Klipper's standard configuration structure:
- Configuration files are stored in the `config/` directory
- The printer uses an AVR atmega2560 microcontroller
- Communication happens via USB serial connection
- Virtual SD card support is configured for G-code file management

## Important Configuration Details

- **Printer Type**: Cartesian kinematics
- **Build Volume**: 210x210x205mm
- **MCU**: AVR atmega2560
- **Serial Port**: `/dev/serial/by-id/usb-Silicon_Labs_CP2102_USB_to_UART_Bridge_Controller_0001-if00-port0`
- **Input Shaper**: Configured with EI shaper type for vibration compensation

## Common Tasks

When modifying printer configuration:
1. Edit `config/printer.cfg` directly
2. Changes take effect after restarting Klipper service
3. Always verify pin mappings match the physical hardware
4. Test changes incrementally, especially for motion-related settings

## G-code Macros

The configuration includes several useful macros:
- `PAUSE` / `RESUME`: Print pause and resume functionality
- `CANCEL_PRINT`: Cancel current print
- `LOAD_FILAMENT` / `UNLOAD_FILAMENT`: Filament change procedures with temperature control