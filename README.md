Automatic Transmission Control System (Simulink + Arduino)

This project implements an Automatic Transmission Controller using
MATLAB/Simulink, Stateflow, and Arduino code generation.
The controller evaluates driver inputs (brake pedal, throttle, selector position)
and vehicle speed to determine the correct transmission state, while outputting
a torque request signal for each mode. The system was tested both in Simulink
and in SimulIDE using a virtual Arduino Uno.

Project Overview

The controller operates as a state machine with the following modes:

Park (P)

Reverse (R)

Neutral (N)

Drive (D)

Brake Mode

Failure Mode (when selector sensors are inconsistent or CAN failure signal is high)

The system reads multiple inputs, processes them, and computes:

Transmission state

Requested torque

Error/failure conditions

Code is automatically generated and uploaded to an Arduino Uno, which can be tested
using SimulIDE.

How It Works
1. Input Processing

Inputs include:

Brake pedal position

Throttle pedal position

Transmission selector (P, R, N, D)

Vehicle speed

CAN failure flag

Signals are scaled and converted before feeding into the Stateflow controller.

2. Stateflow Controller

The Stateflow chart implements the transmission logic:

Manages transitions between all states

Checks speed conditions (e.g., cannot shift to “Park” while moving)

Handles brake/throttle interlocks

Detects inconsistent selector readings and enters Failure Mode

Computes torque request for each mode

3. Arduino Deployment

Simulink generates:

controller_arduino.hex

controller_arduino.elf

These binaries can be flashed directly to the Arduino Uno.

SimulIDE allows hardware-in-the-loop validation, simulating:

The Arduino board

Digital/analog inputs

Outputs representing transmission LEDs or actuators

📁 Repository Structure
Transmission_Control_Project/
│
├── controller_arduino.slx        # Main Simulink model
├── controller_lab4.slx           # Alternative/initial model
├── TransmissionState.m           # MATLAB enumeration / helper file
├── controller_arduino.hex        # Compiled firmware for Arduino
│
└── Results/                      # Simulation & SimulIDE screenshots
      ├── park_state.jpg
      ├── drive_state.jpg
      ├── reverse_state.jpg
      ├── neutral_state.jpg
      ├── brake_state.jpg
      ├── failure_mode.jpg
      ├── stateflow_chart_1.jpg
      └── stateflow_chart_2.jpg

Validation in SimulIDE

The system was tested using:

Virtual Arduino Uno

Potentiometers / buttons as inputs

LEDs/motors to visualize outputs

Real-time behavior matches Simulink simulation

This step verifies that:

State transitions behave as expected

Failure conditions trigger correctly

Torque request output changes according to state

Tools & Technologies

MATLAB / Simulink

Stateflow

Simulink Support Package for Arduino Hardware

SimulIDE simulator

Arduino Uno

Automatic code generation (C/C++)

Author

Ali Zein Khalifeh
Politecnico di Torino
Model-Based Software Design / Embedded Systems
