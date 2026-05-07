# Smart Thermal Table Control Model in MATLAB/Simulink

This project presents a MATLAB/Simulink-based closed-loop thermal control model for a smart heating surface. The system was designed to simulate spatial temperature monitoring, hotspot detection, matrix-based sensing, and distributed PID control across a heated table surface.

The main focus of this project is the modelling and design of the thermal plant, sensing architecture, analysis subsystem, and control strategy.

## Project Overview

The model represents the heating surface as a 6 × 8 thermal grid, producing 48 spatial temperature nodes. Each node represents a local area of the table surface, allowing the model to capture non-uniform heating, local disturbances, and spatial temperature gradients.

The complete Simulink architecture includes four main subsystems:

1. Thermal plant model
2. Matrix-based sensing layer
3. Thermal analysis and feature extraction
4. Distributed zonal PID control with heater mapping

## Key Features

- 6 × 8 discrete thermal surface model
- 48 spatial temperature measurement points
- Matrix-based sensing architecture
- Reduction of sensing interconnections from 48 to 14
- Approximate wiring reduction of 70%
- Four-zone thermal control strategy
- Local PID control for each thermal zone
- Adaptive gain scheduling based on error magnitude
- Hotspot detection and maximum temperature monitoring
- Discrete-time closed-loop simulation with 0.1 s time step

## System Architecture

The Simulink model is organised as a closed-loop control system. At each simulation step, the thermal plant updates the temperature field based on heater input, ambient heat loss, heat diffusion, and external disturbance. The sensing subsystem measures the temperature field, the analysis subsystem extracts zone-level information, and the controller adjusts the heater input accordingly.

![Overall Simulink Architecture](images/simulink_overview.png)

## Thermal Plant Modelling

The thermal plant is modelled using a discrete-time grid-based approach. Each node is affected by:

- Local heater input
- Heat diffusion from neighbouring nodes
- Ambient heat loss
- External thermal disturbances

This structure allows the model to represent realistic surface behaviour such as localised heating, cooling, and disturbance propagation.

## Matrix-Based Sensing

Instead of using individual wiring for all 48 temperature nodes, the model uses a matrix-addressed sensing structure with 6 row lines and 8 column lines. This reduces the number of sensing interconnections from 48 to 14.

This approach demonstrates how large-area smart surfaces can reduce wiring complexity while still maintaining spatial temperature awareness.

## Zonal PID Control

The surface is divided into four thermal zones. Each zone calculates an average temperature and compares it with the target setpoint. A local PID controller then generates a heating command for that zone.

This distributed control approach improves thermal uniformity and enables the system to respond more effectively to local disturbances than a single global controller.

## Adaptive Gain Scheduling

An adaptive gain scheduling mechanism is included to improve transient and steady-state behaviour. When the temperature error is large, the control effort is increased to speed up heating. As the temperature approaches the setpoint, the gain is reduced to limit overshoot and improve stability.

## Heater Mapping

The heater mapping subsystem converts the four zone-level control signals into a full 6 × 8 heater input matrix. Each zone applies uniform heating to its assigned grid area.

## Files Included

- `Thermal_Plant_model.slx` — main Simulink model
- `images/` — screenshots of the Simulink architecture and subsystems
- `results/` — simulation outputs and plots
