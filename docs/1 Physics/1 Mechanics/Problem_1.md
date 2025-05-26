# 📘 Investigating the Range as a Function of the Angle of Projection

## 1. Theoretical Foundation

### Equations of Motion

Assume a projectile is launched from ground level with:
- Initial speed $v_0$
- Angle of projection $\theta$
- Acceleration due to gravity $g$

Decomposing the motion:

- Horizontal component: $v_{0x} = v_0 \cos(\theta)$
- Vertical component: $v_{0y} = v_0 \sin(\theta)$

Time of flight (until projectile returns to same vertical level):

\[
T = \frac{2v_0 \sin(\theta)}{g}
\]

Horizontal range:

\[
R = v_{0x} \cdot T = v_0 \cos(\theta) \cdot \frac{2v_0 \sin(\theta)}{g}
\]

Simplified:

\[
\boxed{R = \frac{v_0^2 \sin(2\theta)}{g}}
\]

### Family of Solutions

- For a fixed $v_0$ and $g$, the range depends solely on $\sin(2\theta)$.
- Maximum range occurs at $\theta = 45^\circ$ because $\sin(2\theta) = 1$.
- Complementary angles (e.g., $30^\circ$ and $60^\circ$) yield the same range.

---

## 2. Analysis of the Range

### Parameter Effects

- **Initial Velocity ($v_0$)**: Since $R \propto v_0^2$, doubling $v_0$ quadruples the range.
- **Gravitational Acceleration ($g$)**: Since $R \propto \frac{1}{g}$, the range is greater on the Moon than on Earth.
- **Angle ($\theta$)**: Range is symmetric about $45^\circ$.

---

## 3. Practical Applications

- **Sports**: Optimal kicking/throwing angles for maximum range.
- **Engineering**: Designing ballistic trajectories.
- **Astrophysics**: Orbital injection angles and escape trajectories.

**Extensions**:
- Launch from a height: Changes total time of flight.
- Air resistance: Reduces range, shifts optimal angle below $45^\circ$.
- Uneven terrain: Requires numerical methods to solve.

---

## 4. Implementation in Python

### Python Code

```python
import numpy as np
import matplotlib.pyplot as plt

def range_of_projectile(v0, g, theta_deg):
    theta_rad = np.radians(theta_deg)
    return (v0 ** 2) * np.sin(2 * theta_rad) / g

# Parameters
v0_values = [10, 20, 30]
g = 9.81
angles = np.linspace(0, 90, 500)

# Plotting
plt.figure(figsize=(10, 6))
for v0 in v0_values:
    ranges = range_of_projectile(v0, g, angles)
    plt.plot(angles, ranges, label=f'v0 = {v0} m/s')

plt.title("Range vs Angle of Projection")
plt.xlabel("Angle (degrees)")
plt.ylabel("Range (meters)")
plt.legend()
plt.grid(True)
plt.show()
