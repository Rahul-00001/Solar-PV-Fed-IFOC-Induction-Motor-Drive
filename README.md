# Standalone Solar PV-Fed IFOC Induction Motor Drive

## Project Overview

This project presents the modeling, design, control, and simulation of a standalone solar PV-fed induction motor drive for a centrifugal water-pumping application using MATLAB/Simulink.

The system integrates a solar PV array, DC-DC boost converter, DC-link capacitor, three-phase voltage source inverter, induction motor, and centrifugal pump load.

Indirect Field-Oriented Control (IFOC) is implemented for motor speed control, while the source-side control incorporates Incremental Conductance MPPT and DC-link voltage regulation. A supervisory control strategy coordinates the two operating objectives by prioritizing the minimum DC-link voltage requirement of the motor drive when necessary and enabling MPPT operation when sufficient voltage margin is available.

The project also investigates the practical operating limit of the standalone system and analyzes the mechanism of PV source-side voltage collapse when the demanded motor-pump power exceeds the sustainable power capability of the PV source.

## Key Features

- Standalone solar PV-fed induction motor drive
- Indirect Field-Oriented Control (IFOC)
- Centrifugal pump load modeling
- Speed PI controller designed using frequency-domain loop shaping
- d-axis and q-axis current reference generation
- Slip and synchronous electrical speed calculation
- d-q voltage reference generation
- Direct d-q to three-phase voltage transformation
- SPWM-based three-phase VSI control
- DC-DC boost converter modeling and design
- Incremental Conductance MPPT
- Closed-loop PV voltage control
- Closed-loop DC-link voltage control
- Supervisory mode-selection strategy
- Dynamic minimum DC-link voltage calculation
- Source-side operating-limit investigation
- PV voltage-collapse analysis

## System Architecture

The complete power conversion system is

PV Array → Boost Converter → DC Link → Three-Phase VSI → Induction Motor → Centrifugal Pump

The control system consists of two major sections:

### Motor-Side Control

The induction motor is controlled using IFOC. The speed PI controller generates the electromagnetic torque reference. The flux-producing current reference is established from the rated flux requirement, while the torque reference is used to calculate the corresponding q-axis current reference.

The slip speed and synchronous electrical speed are then calculated, followed by generation of the d-q voltage references. These references are transformed directly into three-phase voltage references and applied to the SPWM-controlled voltage source inverter.

### Source-Side Control

The boost converter is controlled using two operating objectives:

- PV voltage regulation for MPPT operation
- DC-link voltage regulation when the minimum voltage required by the motor drive cannot be maintained

A supervisory controller selects the appropriate control mode according to the available DC-link voltage margin.

## Supervisory Control Strategy

The minimum DC-link voltage required by the inverter is calculated dynamically from the instantaneous three-phase voltage references.

The supervisory controller operates in two modes:

**Mode 0 – DC-Link Voltage Regulation**

The boost converter prioritizes maintaining the minimum DC-link voltage required for motor operation.

**Mode 1 – MPPT Operation**

When sufficient DC-link voltage margin is available, Incremental Conductance MPPT generates the PV voltage reference and the PV voltage controller determines the boost-converter duty ratio.

Hysteresis is incorporated into the mode-selection logic to prevent rapid switching between the two operating modes.

## Controller Design

The project uses frequency-domain modeling and loop-shaping techniques for controller design.

The motor speed controller was designed from the mechanical model of the induction motor.

The boost converter was modeled from both the input and output sides to design:

- PV voltage controller
- DC-link voltage controller

The final controller parameters were validated in the complete switching-model simulation.

## Simulation and Validation

The integrated system was evaluated under variations in:

- Solar irradiance
- PV temperature
- Motor speed reference

The simulations were used to examine motor speed tracking, DC-link voltage behaviour, source-side response, and overall system operation.

## Operating Limit and PV Source-Side Collapse

A distinct maximum sustainable operating region was observed during simulation.

The system remained stable at a motor speed reference of approximately 128 rad/s, while operation at 129 rad/s resulted in source-side voltage collapse.

Additional investigations were performed by increasing the DC-link capacitance and replacing the motor-drive system with an equivalent resistive load. These tests indicated that the collapse was fundamentally associated with the interaction between the finite power capability of the PV source and the boost converter rather than the IFOC system or insufficient DC-link capacitance.

The observed mechanism can be summarized as:

DC-link voltage reduction → increased converter loading → PV voltage reduction → reduction in available PV power → further DC-link voltage reduction

This investigation highlights an important practical limitation of directly coupled standalone PV-fed motor-drive systems.

## Tools and Technologies

- MATLAB
- Simulink
- Simscape Electrical
- Indirect Field-Oriented Control
- Power Electronics
- Frequency-Domain Loop Shaping
- PI Control
- Incremental Conductance MPPT
- SPWM

## Repository Structure

Solar-PV-Fed-IFOC-Induction-Motor-Drive

│

├── README.md

├── Project Report.pdf

└── Solar_Vector_Control.slx

## Project Report

The complete technical report covering system design, component sizing, IFOC development, boost-converter modeling, controller design, supervisory control, simulation results, and source-side collapse analysis is available in this repository.

📄 **Project Report.pdf**

## Simulink Model

The complete integrated MATLAB/Simulink model is included in the repository.

⚙️ **Solar_Vector_Control.slx**

## Author

Rahul Kumar Pandey

B.Tech Electrical Engineering

Areas of Interest:

- Control Systems
- Power Electronics
- Electric Drives
- Renewable Energy Systems
