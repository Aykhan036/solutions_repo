# Investigating the Dynamics of a Forced Damped Pendulum

## 1. Theoretical Foundation

### Governing Equation

The motion of a forced damped pendulum is governed by the second-order nonlinear differential equation:

$$
\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L} \sin\theta = A \cos(\omega t)
$$

Where:
- $\theta(t)$: angular displacement  
- $b$: damping coefficient  
- $g$: gravitational acceleration  
- $L$: pendulum length  
- $A$: driving amplitude  
- $\omega$: driving frequency

### Small-Angle Approximation

For small values of $\theta$, we use the approximation $\sin\theta \approx \theta$, so the equation becomes:

$$
\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
$$

This is a linear, second-order non-homogeneous differential equation and can be solved analytically using the method of undetermined coefficients or variation of parameters.

### Resonance Condition

Resonance occurs when the driving frequency matches the system's natural frequency:

$$
\omega \approx \sqrt{\frac{g}{L}}
$$

At resonance:
- The amplitude of oscillation is maximized.
- The energy input from the driving force balances the damping losses.

---

## 2. Analysis of Dynamics

### Parameters to Vary:
- Damping $b$: critical, underdamped, overdamped
- Driving amplitude $A$
- Driving frequency $\omega$

### Observable Behaviors:
- **Periodic motion**: Regular repeating oscillations.
- **Quasiperiodic motion**: Superposition of incommensurate frequencies.
- **Chaotic motion**: Sensitive dependence on initial conditions.

To observe transitions between these regimes, we analyze:
- **Phase portraits**
- **Poincaré sections**
- **Bifurcation diagrams**

---

## 3. Practical Applications

- **Energy harvesting**: Piezoelectric pendulum systems
- **Suspension bridges**: Driven by wind (e.g., Tacoma Narrows Bridge collapse)
- **Electronic analogs**: Driven RLC circuits
- **Biomechanics**: Human walking modeled as a forced oscillator

---

## 4. Implementation (Python) – Core Tasks

### Numerical Simulation:
Use `scipy.integrate.solve_ivp` to simulate the full nonlinear equation:

$$
\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L} \sin\theta = A \cos(\omega t)
$$

### Visualizations:
- Time evolution of $\theta(t)$
- Phase space: $(\theta, \dot{\theta})$
- Poincaré section (sample every period $T = \frac{2\pi}{\omega}$)
- Bifurcation diagram by sweeping a parameter (e.g., $A$)

