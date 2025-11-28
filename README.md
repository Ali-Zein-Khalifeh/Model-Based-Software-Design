# Automatic Transmission Control System (Simulink + Arduino)

This project implements an **Automatic Transmission Controller** using  
**MATLAB/Simulink**, **Stateflow**, and **Arduino code generation**.  
The controller reads driver inputs (brake, throttle, selector position, vehicle speed)  
and determines the correct transmission state while generating a torque request signal.  
The controller was tested in Simulink and in SimulIDE using a virtual Arduino Uno.

---

## 📁 Repository Structure

```

Transmission_Control_Project/  
├── controller_arduino.slx  
├── controller_lab4.slx  
├── TransmissionState.m  
├── controller_arduino.hex  
└── Results/  
  ├── park_state.jpg  
  ├── drive_state.jpg  
  ├── reverse_state.jpg  
  ├── neutral_state.jpg  
  ├── brake_state.jpg  
  ├── failure_mode.jpg  
  ├── stateflow_chart_1.jpg  
  └── stateflow_chart_2.jpg  
```
---

## Project Overview

The controller operates as a **state machine** with the following modes:

- Park (P)  
- Reverse (R)  
- Neutral (N)  
- Drive (D)  
- Brake Mode  
- Failure Mode (selector inconsistency or CAN failure)

The system computes:

- Transmission state  
- Torque request  
- Error/failure conditions  

---

## How It Works

### Input Processing
The controller reads:
- Brake pedal position  
- Throttle pedal position  
- Selector lever (P / R / N / D)  
- Vehicle speed  
- CAN failure flag  

### Stateflow Controller
Implements:
- State transitions  
- Safety conditions (no Park while moving)  
- Brake/throttle interlocks  
- Failure detection (selector mismatch or CAN error)  
- Torque request output  

### Arduino Deployment
Simulink generates:
- controller_arduino.hex  
- controller_arduino.elf  

These can be flashed to an Arduino Uno.  
SimulIDE is used for hardware-in-the-loop validation.

---

## Validation in SimulIDE

Testing confirmed:
- Correct state transitions  
- Valid safety conditions  
- Proper failure mode behavior  
- Matching results between Simulink and Arduino execution  

---

## Tools & Technologies

- MATLAB / Simulink  
- Stateflow  
- Arduino Uno  
- SimulIDE  
- C/C++ Automatic Code Generation  
- Simulink Support Package for Arduino Hardware  

---

## 👤 Author

**Ali Zein Khalifeh**  
Politecnico di Torino  
Model-Based Software Design
