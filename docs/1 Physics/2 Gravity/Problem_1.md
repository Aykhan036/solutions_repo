# Kepler's Third Law - Orbital Period vs Orbital Radius (Circular Orbits)

```python
import numpy as np
import matplotlib.pyplot as plt

# Gravitational constant (m^3 kg^-1 s^-2)
G = 6.67430e-11
# Mass of the Earth (kg)
M_earth = 5.972e24

# Function to calculate orbital period for circular orbit
def orbital_period(radius, M=M_earth):
    return 2 * np.pi * np.sqrt(radius**3 / (G * M))

# Generate orbital radii from 7e6 m to 4e8 m
radii = np.linspace(7e6, 4e8, 500)
periods = orbital_period(radii)

# Plotting T^2 vs R^3
T_squared = periods**2
R_cubed = radii**3

plt.figure(figsize=(10, 6))
plt.plot(R_cubed, T_squared, label="$T^2$ vs $R^3$")
plt.xlabel("$R^3$ (m^3)")
plt.ylabel("$T^2$ (s^2)")
plt.title("Verification of Kepler's Third Law (Circular Orbits)")
plt.grid(True)
plt.legend()
plt.show()

# Example: Moon's orbit around Earth
R_moon = 3.844e8  # in meters
T_moon = orbital_period(R_moon)
print(f"Orbital period of the Moon around Earth: {T_moon / (60 * 60 * 24):.2f} days")
