# EV ADAS Dashboard System

## Overview

This project is an Electric Vehicle (EV) Advanced Driver Assistance System (ADAS) developed using an STM32 microcontroller. The system combines EV control, ultrasonic-based obstacle detection, collision warning, blind-spot detection, vehicle fault monitoring, UART communication, and a Python-based dashboard.

The system is designed and tested using PICSimLab for hardware simulation and communicates with the Python dashboard through UART and a virtual serial COM-port connection.

## Features

- EV state and drive-mode control
- Accelerator and brake input monitoring
- Vehicle speed and motor torque monitoring
- Battery State of Charge (SOC) monitoring
- Motor temperature monitoring
- Front obstacle detection using HC-SR04
- Left and right blind-spot detection
- Forward Collision Warning (FCW)
- Time-to-Collision (TTC) calculation
- Overspeed detection
- Motor over-temperature fault detection
- Low battery/SOC fault detection
- Critical collision fault detection
- LED warning indications
- Buzzer/alarm indication
- UART-based system monitoring
- Python EV dashboard
- PICSimLab hardware simulation

## Hardware / Simulation

- STM32F103 microcontroller
- HC-SR04 ultrasonic sensors
- Potentiometers for analog parameter simulation
- LEDs for warning indications
- Buzzer
- PICSimLab
- Virtual Serial Port Emulator (VSPE)

## Software

- STM32CubeIDE
- STM32 HAL
- PICSimLab
- Python
- UART / Serial communication
- Tera Term / Virtual Terminal

## System Parameters

The system monitors:

| Parameter | Description |
|---|---|
| Accelerator | Controls vehicle acceleration |
| Brake | Controls braking and regenerative braking |
| Speed | Vehicle speed |
| SOC | Battery State of Charge |
| Motor Temperature | Motor thermal condition |
| Front Distance | Forward obstacle distance |
| Left Distance | Left blind-spot distance |
| Right Distance | Right blind-spot distance |
| TTC | Time to Collision |
| Collision Warning | Forward collision status |
| Blind Spot | Left/right blind-spot status |
| Fault Status | System fault condition |

## ADAS Warning Logic

### Forward Collision Warning

The front ultrasonic sensor measures the distance to an obstacle.

- Warning condition: front obstacle within the configured warning distance
- Critical condition: front obstacle within the configured critical distance
- TTC is also used to determine collision risk.

### Blind-Spot Detection

Left and right ultrasonic sensors monitor nearby objects.

Blind-spot warning is activated when the configured distance and vehicle-speed conditions are satisfied.

### Overspeed Detection

The system compares vehicle speed with the configured overspeed threshold and generates an advisory warning when the threshold is exceeded.

### Fault Detection

The system monitors:

- Motor over-temperature
- Critically low battery SOC
- Critical collision

When a critical fault occurs, the system enters the fault state and disables motor torque.

## UART Communication

The STM32 sends system information through UART, including:

- Vehicle speed
- SOC
- Motor temperature
- Front/left/right distance
- TTC
- Collision status
- Blind-spot status
- Alarm status
- Fault status

The UART data can be viewed using a serial terminal or received by the Python dashboard.

## Python Dashboard

The Python dashboard provides a graphical interface for monitoring the EV and ADAS parameters received through UART.

Example UART connection:

```text
PICSimLab
    |
    | UART
    v
Virtual COM Port
    |
    v
Python Dashboard
