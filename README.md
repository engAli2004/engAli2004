

# Ali Naserddine
**Mechanical Engineer | Robotics & Autonomous Systems | Digital Twin Simulation**

[![ROS 2 Humble](https://img.shields.io/badge/ROS_2-Humble-22314E?logo=ros&logoColor=white)](https://ros.org)
[![C++17](https://img.shields.io/badge/C++-00599C?logo=c%2B%2B&logoColor=white)](https://isocpp.org)
[![Python 3](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://python.org)
[![CasADi](https://img.shields.io/badge/CasADi-Nonlinear_Optimization-FF6B6B)](https://web.casadi.org)
[![SolidWorks](https://img.shields.io/badge/SolidWorks-Mechanical_Design-DA291C?logo=dassaultsystemes&logoColor=white)](https://solidworks.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Saint Joseph University of Beirut** | B.Eng. Mechanical Engineering (Expected 2027) | GPA: 3.2/4.0  
**Location:** Beirut, Lebanon | **Open to:** Remote internships worldwide

  [Email](mailto:eng.naserddine2004@gmail.com) · [LinkedIn](https://linkedin.com/in/ali-naserddine)



---

## Professional Summary

Mechanical engineering specialist in robotics, autonomous systems, and digital twin simulation. Proven end-to-end ownership across the full autonomy stack — from SolidWorks mechanical design and ESP32 embedded firmware to ROS 2/Gazebo simulation, sensor fusion, model predictive control, and physics-informed machine learning. Demonstrated through an end-to-end UAV digital twin, a self-built vision-guided UGV, motor-drive projects, and industrial cryogenic plant automation.

**Core Competency:** Vertical integration of mechanical design, state estimation, optimal control, and real-time embedded systems.

---

## Technical Competencies

| Domain | Technologies & Methods |
|--------|----------------------|
| **Robotics & Autonomy** | ROS 2, Gazebo Classic, Digital Twin & Sim-to-Real, Visual Servoing, YOLOv8, SLAM, ESKF/EKF Sensor Fusion, Kalman Filtering, Motion Planning, Minimum-Snap Trajectory Generation, Coverage Planning, Inverse Kinematics, Mobile Manipulation |
| **Control & Drives** | Model Predictive Control (MPC, CasADi/ipopt), PID, State-Space Control, Sliding-Mode Control, Lyapunov Stability, Luenberger Observers, Sensorless FOC, PWM, PLC/HMI Automation (Siemens Simatic), Industrial Instrumentation (4–20 mA Loops) |
| **Programming & Simulation** | Python, C++, Embedded C, MATLAB/Simulink, OpenCV, TensorFlow, NumPy, CoppeliaSim, Git/GitHub |
| **Embedded & Hardware** | ESP32, Raspberry Pi, ARM/AVR, Arduino, UART/I2C/SPI, SolidWorks, FDM 3D Printing |
| **Languages** | Arabic (Native), English (IELTS 7.0), French (Fluent), German (Basic) |

---

## Selected Engineering Projects

### [UR5 Pick-and-Place Digital Twin](https://github.com/engAli2004/ur5-digital-twin-mpc)
**`ROS 2 Humble` `Gazebo Classic` `Python/NumPy` `CasADi` `Foxglove Studio`**

Complete mechanical-digital-twin pipeline for a 6-DOF UR5 collaborative robot. The system derives Denavit-Hartenberg forward kinematics from first principles, solves geometric inverse kinematics via Damped Least Squares (Levenberg-Marquardt), and validates all trajectories against static torque limits with a safety factor ≥ 2.5 prior to execution. A two-layer multilayer perceptron implemented from scratch in NumPy estimates unknown payload mass from joint torque residuals and adapts the gravity compensation model in real time.

- **Kinematics:** DH-parameter forward kinematics verified against UR5 manufacturer specifications; DLS-IK converges in ≤ 20 iterations with position error &lt; 1×10⁻⁵ m and rotation error &lt; 1×10⁻⁴ rad
- **Workspace Analysis:** Monte Carlo sampling of 5,000 configurations mapping reachable envelope; Jacobian determinant tracked along all trajectories for singularity avoidance
- **Mechanical Validation:** Static torque analysis at 3.0 kg payload; all joints pass with FoS = 2.5 against UR5 manufacturer torque limits (Base: 150 Nm, Shoulder: 150 Nm, Elbow: 100 Nm, Wrist: 28 Nm)
- **Control:** Minimum-snap quintic spline trajectory generation in joint space; PD + gravity compensation controller with CasADi-ready MPC architecture
- **Neural Estimator:** 32→16→1 MLP trained on 200 synthetic samples (MSE &lt; 0.03); validates at ±0.5 kg on unseen payloads
- **Deployment:** Single-command launch via `ros2 launch ur5_control ur5_digital_twin.launch.py`; Foxglove telemetry bridge at 10 Hz

### [VTOL UAV Digital Twin](https://github.com/engAli2004/vtol-digital-twin)
**`ROS 2` `Gazebo Classic` `C++/Eigen` `Python/CasADi` `ESKF` `MPC`**

Full digital twin of a hybrid VTOL UAV (4 lift rotors, pusher propeller, fixed wing) in ROS 2/Gazebo with a custom aerodynamics engine modeling wing stall, drag polars, and rotor thrust. The flight controller operates entirely on estimated state from simulated noisy sensors.

- **State Estimation:** 9-state Error-State Kalman Filter in C++ (Eigen) fusing IMU (100 Hz) and GPS (10 Hz, σ = 0.5 m); achieves 0.15–0.30 m position error versus 0.5 m raw GPS noise
- **Control:** Cascaded PID attitude controller + receding-horizon MPC (CasADi/ipopt, RK4 dynamics, 10 Hz) with automatic PD fallback and minimum-snap trajectory generation for oscillation-free waypoint tracking
- **Aerodynamics:** Custom physics node modeling rotor thrust, body drag (linear + quadratic), wing lift/drag polars with stall model, and pusher propeller
- **Flight Test:** Demonstrated hover-to-cruise transition at 14.1 m/s with wings carrying 88% of vehicle weight at α = 3.9°; diagnosed 5 controller failures from flight telemetry including mixer saturation and phugoid-stall oscillations

### [4WD Vision-Guided UGV](https://github.com/engAli2004/ugv-4wd-vision)
**`ESP32` `YOLOv8` `OpenCV` `SolidWorks` `3D Printing` `Embedded C`**

End-to-end design, fabrication, and deployment of a 4WD skid-steer unmanned ground vehicle. Custom SolidWorks chassis, 12V geared motors with encoders, dual H-bridge drivers, and a 2-axis pan-tilt camera mechanism. Closed the perception-action loop on hardware.

- **Perception:** YOLOv8 person detection → normalized pixel error → proportional control with deadband and static-friction PWM floor; demonstrated real-time person following and pan-tilt tracking
- **Embedded:** ESP32 real-time firmware with encoder-based PID wheel-speed control, serial command protocol, safety watchdog, and slew-rate current limiting
- **Reliability:** Diagnosed hardware failures via systematic root-cause analysis — supply brownout (resolved via bulk capacitance + supply isolation), H-bridge voltage-drop torque limits, serial-line faults

### [Autonomous Guided Vehicle with Scissor Lift](https://github.com/engAli2004/agv-scissor-lift-mechanical)
**`SolidWorks` `MATLAB/Simulink` `Team Project — Mechanical Lead`**

Led mechanical design of a 6-member differential-drive AGV project. Responsible for chassis design, MATLAB kinematic modeling, and fabrication.

- **Mechanism:** Engineered a cable-actuated scissor lift for 4–5 kg payloads with 100 mm stroke; corrected a shaft failure via shear analysis and verified FoS ≥ 2.5 at maximum extension
- **Drive:** Modeled nonlinear PMSM dynamics and implemented state-feedback with integral action to eliminate steady-state speed error; designed a Luenberger observer to estimate rotor speed from electrical signals, removing the need for a physical encoder

---

## Professional Experience

**Mechanical Engineering Intern** | Chehab Industrial & Medical Gases (CIMG) | Jun 2026 – Aug 2026
- Analyzed end-to-end operation of an industrial cryogenic air separation unit (650 Nm³/hr LOX at ≥ 99.6% purity), covering Siemens Simatic PLC/HMI automation, 4–20 mA instrumentation loops, and fail-safe pneumatic valve logic
- Audited the 1,750 HP multi-stage centrifugal compression train: verified cooling network capacity (~1,848 kW rejection vs. 1,247 kW plant load) and safety trip set-points (72,000 RPM overspeed, 0.8 mil vibration limits)
- Performed real-gas (compressibility factor) calculations for high-pressure cylinder filling and evaluated rotating-equipment reliability practices: laser shaft alignment, vibration monitoring, and dry gas seal systems
- Supported HVAC psychrometric analysis and VFD tuning for large climate-control units; assisted commissioning of pumps and NFPA 20 fire-safety systems

**Robotics & Coding Instructor** | J-Tech Academy | 2022 – 2025
- Taught 100+ students robotics, Python, and C++ over 3 years
- Developed curriculum from programming fundamentals to autonomous robot deployment and digital twin simulation

---

## Education & Certifications

**B.Eng. Mechanical Engineering** | Saint Joseph University of Beirut (USJ) | Expected 2027
- GPA: 3.2/4.0
- Relevant Coursework: Linear Control Systems, Mechatronics, Embedded C, Systems Analysis, Robotics

**Certifications**
- Modern Robotics: Mechanics, Planning and Control | Northwestern University (Coursera)
- AI for Mechanical Engineers | Coursera

---

## Engineering Philosophy

**1. Validate Before Actuating**
Every motion command is preceded by workspace verification, Jacobian singularity checks, and static torque validation against manufacturer limits with an appropriate factor of safety.

**2. First-Principles Implementation**
DH kinematics, Jacobian matrices, and neural network backpropagation are implemented from scratch rather than imported from black-box libraries. This ensures debuggability, real-time performance, and deep system understanding.

**3. Systems Integration Over Scripts**
A standalone Python script that actuates a joint is a demonstration. A ROS 2 package with validated kinematics, constrained trajectory optimization, state estimation, and live telemetry logging is engineering.

---




---

## Contact

**Email:** [eng.naserddine2004@gmail.com](mailto:eng.naserddine2004@gmail.com)  
**LinkedIn:** [linkedin.com/in/ali-naserddine](https://linkedin.com/in/ali-naserddine)  
**GitHub:** [github.com/engAli2004](https://github.com/engAli2004)  
**Location:** Beirut, Lebanon (UTC+3) — Available for remote roles globally
