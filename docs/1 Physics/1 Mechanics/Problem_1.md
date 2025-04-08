# Projectile Motion: Range as a Function of the Angle of Projection

## 1. Theoretical Foundation

We begin with the basic equations of motion for a projectile launched at angle $\theta$ with speed $v_0$, assuming:

- No air resistance  
- Constant gravitational acceleration $g$  
- Launch height = 0  

### Decomposing Motion

- Horizontal velocity: $v_{0x} = v_0 \cos\theta$
- Vertical velocity: $v_{0y} = v_0 \sin\theta$

Time of flight ($T$) until it hits the ground:

$$
T = \frac{2v_0 \sin\theta}{g}
$$

Range $R$ is the horizontal distance traveled:

$$
R = v_{0x} \cdot T = v_0 \cos\theta \cdot \frac{2v_0 \sin\theta}{g} = \frac{v_0^2 \sin(2\theta)}{g}
$$

This is the governing equation for range as a function of angle.

---

## 2. Analysis of the Range

### Key Observations

- Maximum range occurs at $\theta = 45^\circ$ since $\sin(2\theta)$ reaches its peak at $\theta = 45^\circ$
- Symmetry: $R(\theta) = R(90^\circ - \theta)$

### Effect of Parameters

- Initial velocity $v_0$: Range increases quadratically with $v_0$
- Gravity $g$: Range is inversely proportional to $g$ (lower gravity = farther range)

---

## 3. Practical Applications

This model can apply to:

- Sports (e.g., soccer, basketball) – adjusting launch angles for maximum range  
- Engineering (e.g., missile trajectory, water jets)  
- Astrophysics – modeling orbits and interplanetary trajectories (with modifications)  

### Beyond Ideal Model

Real-world considerations:
- Air resistance (drag)
- Wind
- Non-zero launch height
- Uneven terrain

These factors require numerical integration and more complex models.

---

## 4. Implementation: Simulation in Python

```python
import numpy as np
import matplotlib.pyplot as plt

def compute_range(v0, g, angles_deg):
    angles_rad = np.radians(angles_deg)
    return (v0**2 * np.sin(2 * angles_rad)) / g

# Parameters
v0 = 50  # m/s
g_values = [9.81, 3.71, 1.62]  # Earth, Mars, Moon
angles = np.linspace(0, 90, 500)

# Plotting
plt.figure(figsize=(10, 6))
for g in g_values:
    R = compute_range(v0, g, angles)
    plt.plot(angles, R, label=f'g = {g} m/s²')

plt.title('Range vs Angle of Projection')
plt.xlabel('Angle (degrees)')
plt.ylabel('Range (meters)')
plt.legend()
plt.grid(True)
plt.show()
