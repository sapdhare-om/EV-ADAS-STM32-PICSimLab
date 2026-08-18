# EV ADAS - STM32 Based Advanced Driver Assistance System

## Overview

This project implements a simulation-oriented Advanced Driver Assistance System (ADAS) for an Electric Vehicle using an STM32 microcontroller.

The system combines EV control, ultrasonic obstacle detection, collision warning, blind-spot detection, overspeed detection, fault management, UART communication, and a Python-based dashboard.

The STM32 firmware is tested using PICSimLab, while UART data is transferred to a Python dashboard for real-time monitoring.

---

## Features

- Electric vehicle control
- Accelerator and brake input processing
- Vehicle speed simulation
- Motor torque calculation
- Regenerative braking
- Battery State of Charge (SOC) monitoring
- Motor temperature monitoring
- Front obstacle detection
- Forward Collision Warning (FCW)
- Time to Collision (TTC) calculation
- Left blind-spot detection
- Right blind-spot detection
- Overspeed detection
- Fault detection
- Fault state management
- LED indications
- Buzzer indication
- UART communication
- Python-based EV dashboard
- PICSimLab hardware simulation

---

## System Architecture

```text
             Analog Inputs
                  |
        +---------+---------+
        |                   |
   Accelerator           Brake
        |                   |
        +---------+---------+
                  |
              STM32 MCU
                  |
       +----------+----------+
       |          |          |
      EV         ADAS      Fault
   Control      System     Manager
       |          |          |
       |     Ultrasonic     |
       |      Sensors       |
       |          |          |
       +----------+----------+
                  |
          UART Communication
                  |
            Python Dashboard
                  |
             PC / Laptop
