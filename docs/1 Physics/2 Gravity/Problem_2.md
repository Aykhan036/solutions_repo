# 🚀 Problem 2: Escape Velocities and Cosmic Velocities

## Theoretical Background

**First Cosmic Velocity ($v_1$):**

$$
v_1 = \sqrt{ \frac{G M}{r} }
$$

**Second Cosmic Velocity ($v_2$):**

$$
v_2 = \sqrt{2} \cdot v_1 = \sqrt{ \frac{2 G M}{r} }
$$

**Third Cosmic Velocity ($v_3$):**

$$
v_{\text{orbit}} = \sqrt{ \frac{G M_{\odot}}{r_{\text{orbit}}} }
$$

$$
v_3 = \sqrt{ v_2^2 + v_{\text{orbit}}^2 }
$$

Where:

- $G$: Gravitational constant.
- $M$: Mass of the planet.
- $r$: Radius of the planet.
- $M_{\odot}$: Mass of the Sun.
- $r_{\text{orbit}}$: Distance of the planet's orbit around the Sun.

---

## Python Simulation

```python
import numpy as np
import matplotlib.pyplot as plt

# Gravitational constant
G = 6.67430e-11  # m^3 kg^-1 s^-2
M_sun = 1.989e30  # kg (mass of the Sun)

# Celestial body data: Mass (kg), Radius (m), Orbit radius (m)
bodies = {
    'Earth':   [5.972e24, 6.371e6, 1.496e11],
    'Mars':    [6.417e23, 3.3895e6, 2.279e11],
    'Jupiter': [1.898e27, 6.9911e7, 7.785e11]
}

names = []
v1_list = []
v2_list = []
v3_list = []

for name, (M, r, r_orbit) in bodies.items():
    # First Cosmic Velocity (v₁)
    v1 = np.sqrt(G * M / r)
    
    # Second Cosmic Velocity (v₂)
    v2 = np.sqrt(2) * v1
    
    # Orbital velocity around the Sun
    v_orbit = np.sqrt(G * M_sun / r_orbit)
    
    # Third Cosmic Velocity (v₃)
    v3 = np.sqrt(v2**2 + v_orbit**2)
    
    # Store values (convert to km/s)
    names.append(name)
    v1_list.append(v1 / 1000)
    v2_list.append(v2 / 1000)
    v3_list.append(v3 / 1000)

# Plotting
x = np.arange(len(names))
width = 0.25

plt.figure(figsize=(10, 6))
plt.bar(x - width, v1_list, width, label='First Cosmic Velocity (v₁)')
plt.bar(x, v2_list, width, label='Second Cosmic Velocity (v₂)')
plt.bar(x + width, v3_list, width, label='Third Cosmic Velocity (v₃)')

plt.xticks(x, names)
plt.ylabel('Velocity (km/s)')
plt.title('Cosmic Velocities for Earth, Mars, and Jupiter')
plt.legend()
plt.grid(True, axis='y')
plt.show()
