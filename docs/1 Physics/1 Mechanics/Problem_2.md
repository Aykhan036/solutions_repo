# 📘 Investigating the Dynamics of a Forced Damped Pendulum

## 1. Theoretical Foundation

### Governing Equation

The forced damped pendulum is described by the second-order nonlinear differential equation:

$$
\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L} \sin(\theta) = A \cos(\omega t)
$$

Where:

- $\theta$: Angular displacement  
- $b$: Damping coefficient  
- $g$: Acceleration due to gravity  
- $L$: Length of the pendulum  
- $A$: Amplitude of the external driving force  
- $\omega$: Frequency of the driving force  

---

### Small-Angle Approximation

For small angles ($\theta \ll 1$), $\sin(\theta) \approx \theta$, reducing the equation to a linear form:

$$
\frac{d^2\theta}{dt^2} + b\frac{d\theta}{dt} + \frac{g}{L} \theta = A \cos(\omega t)
$$

This is a linear second-order nonhomogeneous ODE with solutions that show:

- Damped oscillations  
- Steady-state response  
- Resonance at $\omega \approx \sqrt{g/L}$

---

### Resonance and Energy

Resonance occurs when the driving frequency $\omega$ matches the natural frequency of the system, leading to large amplitude oscillations and maximum energy transfer.

---

## 📊 2. Analysis of Dynamics

We investigate how varying the parameters affects the motion of the pendulum:

- **Low $b$**: Less energy loss, more pronounced resonance  
- **High $A$**: May push the system into nonlinear chaotic motion  
- **Varying $\omega$**: Shows resonance and off-resonance behavior  

Chaotic behavior arises when the system becomes sensitive to initial conditions and exhibits aperiodic, non-repeating behavior.

---

## 🛠️ 3. Practical Applications

- **Energy Harvesting**: Nonlinear oscillations help capture ambient energy  
- **Suspension Bridges**: Models external periodic forces like wind or traffic  
- **Electrical Circuits**: Analogous to driven RLC circuits  
- **Biomechanics**: Human walking (gait) under damping and periodic forcing  

---

## 💻 4. Implementation (Python Simulation & Visualizations)

Below is a Python script using the 4th-order Runge-Kutta method to simulate the forced damped pendulum:

```python
import numpy as np
import matplotlib.pyplot as plt

# Parameters
g = 9.81        # gravity
L = 1.0         # pendulum length
b = 0.2         # damping coefficient
A = 1.2         # amplitude of driving force
omega = 2/3     # frequency of driving force

# Time settings
dt = 0.01
T = 100
steps = int(T/dt)
t = np.linspace(0, T, steps)

# Arrays
theta = np.zeros(steps)
omega_dot = np.zeros(steps)
theta[0] = 0.2   # initial angle
omega_dot[0] = 0 # initial angular velocity

# Equation of motion
def d2theta_dt2(theta, omega_dot, t):
    return -b*omega_dot - (g/L)*np.sin(theta) + A*np.cos(omega*t)

# Runge-Kutta 4
for i in range(steps-1):
    k1_omega = dt * d2theta_dt2(theta[i], omega_dot[i], t[i])
    k1_theta = dt * omega_dot[i]

    k2_omega = dt * d2theta_dt2(theta[i] + 0.5*k1_theta, omega_dot[i] + 0.5*k1_omega, t[i] + 0.5*dt)
    k2_theta = dt * (omega_dot[i] + 0.5*k1_omega)

    k3_omega = dt * d2theta_dt2(theta[i] + 0.5*k2_theta, omega_dot[i] + 0.5*k2_omega, t[i] + 0.5*dt)
    k3_theta = dt * (omega_dot[i] + 0.5*k2_omega)

    k4_omega = dt * d2theta_dt2(theta[i] + k3_theta, omega_dot[i] + k3_omega, t[i] + dt)
    k4_theta = dt * (omega_dot[i] + k3_omega)

    omega_dot[i+1] = omega_dot[i] + (1/6)*(k1_omega + 2*k2_omega + 2*k3_omega + k4_omega)
    theta[i+1] = theta[i] + (1/6)*(k1_theta + 2*k2_theta + 2*k3_theta + k4_theta)

# Plot
plt.figure(figsize=(10,4))
plt.plot(t, theta, label="Theta(t)")
plt.xlabel("Time (s)")
plt.ylabel("Angle (rad)")
plt.title("Forced Damped Pendulum Motion")
plt.grid(True)
plt.legend()
plt.show()
