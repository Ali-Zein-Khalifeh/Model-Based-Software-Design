# Automatic Transmission Control System (Simulink + Arduino)

This project implements an automatic transmission controller using
MATLAB/Simulink, Stateflow, and Arduino code generation. The controller
manages the vehicle’s transmission state based on the brake pedal,
throttle pedal, vehicle speed, CAN status, and the driver’s transmission
selector.

The system supports:
- Park (P)
- Reverse (R)
- Neutral (N)
- Drive (D)
- Brake mode
- Failure mode (CAN failure or inconsistent selector sensors)

Code is generated to an Arduino Uno and tested using SimulIDE.

---

## 📁 Repository Structure

