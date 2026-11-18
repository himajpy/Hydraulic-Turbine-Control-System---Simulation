# Hydraulic Turbine & DC-Bus Control Simulation

Multi-domain simulation of a small-scale hydroelectric power system built in **MATLAB/Simulink** and **Simscape Electrical** (FHNW School of Engineering, FS2025).

## Overview
The model simulates the complete energy conversion chain from water flow control to electrical DC-bus stabilization:
* **Hydraulic Domain:** *Hydraulic Turbine & Governor (HTG)* block modeling water column inertia ($T_w = 2.7\,\text{s}$), servomotor actuation, and guide vane limits ($g_{\min} = 0.01$, $g_{\max} = 0.975$).
* **Mechanical Domain:** Rotational shaft dynamics with flywheel inertia ($J = 2 \times 10^5\,\text{kg}\cdot\text{m}^2$) and lossless electromechanical conversion ($K_v \approx 2.13\,\text{V}\cdot\text{s}/\text{rad}$).
* **Electrical Domain:** $400\,\text{V}$ DC-link bus with capacitive filtering ($1\,\mu\text{F}$), resistive load ($1\,\Omega$), and ideal voltage buffering.

## Control Architecture
A two-stage hierarchical control scheme regulates both frequency/speed and bus voltage:
1. **Outer Voltage Loop:** Discrete PID controller ($K_p = 2$, $K_i = 50$) with back-calculation anti-windup regulating the $400\,\text{V}$ DC bus.
2. **Primary Speed/Power Loop:** Integrated governor with $5\%$ droop ($R_p = 0.05$) tracking nominal angular velocity ($\omega \approx 188\,\text{rad/s}$ at $\approx 160\,\text{kW}$ nominal power).

## Repository Contents
* `Glal4_Simulink_Bericht.pdf` — Full technical documentation, parameter derivation, and transient analysis (German).
* `*.slx` — MATLAB/Simulink & Simscape model files.
