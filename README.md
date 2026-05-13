# Semi-Active Quarter-Car Suspension Simulation

A Simulink implementation of a 2-DOF quarter-car suspension model featuring a variable proportional solenoid valve damper optimized for off-road terrain.

## System Architecture & Signal Flow

<img width="1600" height="1090" alt="image" src="https://github.com/user-attachments/assets/110f1c41-0739-4027-a3c9-7445289d674f" />

The model consists of a two-degree-of-freedom (2-DOF) system tracking both sprung (body) and unsprung (wheel) masses:
*   **Road Input:** Feeds terrain profiles into the tire deflection summing junction.
*   **Mass Trackers:** Dual cascaded integrators tracking `Accel -> Velocity -> Position` for both masses.
*   **Semi-Active Damper Block:** A custom MATLAB function routing `rel_vel` and `sprung_vel` to calculate dynamic real-time damping forces.

## Plotting Characteristics

Run the following script to generate the asymmetric force-velocity characteristic curve of your proportional valve:

```matlab
figure
plot(out.rel_vel, out.damping_force, 'LineWidth', 2) 
xlabel('Relative Velocity (m/s)') 
ylabel('Damping Force (N)') 
title('Semi-Active Damper Characteristic (Proportional Solenoid Profile)') 
grid on 
axis tight 
```
