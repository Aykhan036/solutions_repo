import numpy as np
import matplotlib.pyplot as plt

def max_height(v0, theta_deg, g=9.81):
    theta_rad = np.radians(theta_deg)
    return (v0**2 * np.sin(theta_rad)**2) / (2 * g)

def plot_height_vs_angle(v0, g=9.81):
    angles = np.linspace(0, 90, 100)
    heights = max_height(v0, angles, g)

    plt.figure()
    plt.plot(angles, heights)
    plt.title(f"Max Height vs. Angle (v0 = {v0} m/s)")
    plt.xlabel("Angle of Projection (degrees)")
    plt.ylabel("Maximum Height (m)")
    plt.grid(True)
    plt.savefig("height_vs_angle.png")
    plt.show()

plot_height_vs_angle(v0=25)
def projectile_with_drag(v0, theta_deg, drag_coeff=0.05, g=9.81, dt=0.01, t_max=10):
    theta = np.radians(theta_deg)
    vx, vy = v0 * np.cos(theta), v0 * np.sin(theta)
    x, y = 0, 0
    x_vals, y_vals = [x], [y]
    t = 0
    while y >= 0 and t <= t_max:
        v = np.sqrt(vx**2 + vy**2)
        fx = -drag_coeff * v * vx
        fy = -drag_coeff * v * vy - g
        ax, ay = fx, fy
        vx += ax * dt
        vy += ay * dt
        x += vx * dt
        y += vy * dt
        x_vals.append(x)
        y_vals.append(y)
        t += dt
    return x_vals, y_vals

def plot_with_drag(v0, angles, drag=0.05):
    for angle in angles:
        x, y = projectile_with_drag(v0, angle, drag)
        plt.plot(x, y, label=f"{angle}°")
    plt.title(f"Projectile with Drag (v0 = {v0} m/s)")
    plt.xlabel("Horizontal Distance (m)")
    plt.ylabel("Vertical Distance (m)")
    plt.legend()
    plt.grid(True)
    plt.savefig("trajectories_drag_height.png")
    plt.show()

plot_with_drag(25, [30, 60, 90])