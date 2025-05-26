import numpy as np
import matplotlib.pyplot as plt

# ==== IDEAL TRAJECTORY (No Drag) ====

def trajectory_no_drag(v0, theta_deg, g=9.81, resolution=100):
    theta = np.radians(theta_deg)
    T = 2 * v0 * np.sin(theta) / g
    t = np.linspace(0, T, resolution)
    x = v0 * np.cos(theta) * t
    y = v0 * np.sin(theta) * t - 0.5 * g * t**2
    return x, y

def plot_multiple_trajectories(v0, angle_list, g=9.81):
    plt.figure()
    for angle in angle_list:
        x, y = trajectory_no_drag(v0, angle, g)
        plt.plot(x, y, label=f"θ = {angle}°")
    plt.title(f"Ideal Trajectories (v0 = {v0} m/s)")
    plt.xlabel("Horizontal Distance (m)")
    plt.ylabel("Vertical Distance (m)")
    plt.grid(True)
    plt.legend()
    plt.savefig("ideal_trajectories.png")
    plt.show()

# ==== TRAJECTORY WITH AIR DRAG ====

def trajectory_with_drag(v0, theta_deg, drag_coeff=0.01, dt=0.01, g=9.81, t_max=10):
    theta = np.radians(theta_deg)
    vx = v0 * np.cos(theta)
    vy = v0 * np.sin(theta)
    x = y = 0
    x_list, y_list = [x], [y]
    t = 0

    while y >= 0 and t <= t_max:
        v = np.hypot(vx, vy)
        ax = -drag_coeff * v * vx
        ay = -g - drag_coeff * v * vy
        vx += ax * dt
        vy += ay * dt
        x += vx * dt
        y += vy * dt
        x_list.append(x)
        y_list.append(y)
        t += dt

    return x_list, y_list

def plot_drag_trajectories(v0, angle_list, drag_coeff=0.01):
    plt.figure()
    for angle in angle_list:
        x, y = trajectory_with_drag(v0, angle, drag_coeff)
        plt.plot(x, y, label=f"θ = {angle}°")
    plt.title(f"Trajectories with Air Drag (v0 = {v0} m/s, drag = {drag_coeff})")
    plt.xlabel("Horizontal Distance (m)")
    plt.ylabel("Vertical Distance (m)")
    plt.grid(True)
    plt.legend()
    plt.savefig("drag_trajectories.png")
    plt.show()

# ==== RANGE vs ANGLE (Ideal) ====

def range_vs_angle(v0, g=9.81):
    angles = np.linspace(0, 90, 300)
    ranges = (v0**2 / g) * np.sin(2 * np.radians(angles))
    plt.figure()
    plt.plot(angles, ranges, color='purple')
    plt.title(f"Range vs. Projection Angle (v0 = {v0} m/s)")
    plt.xlabel("Angle (degrees)")
    plt.ylabel("Range (meters)")
    plt.grid(True)
    plt.savefig("range_vs_angle.png")
    plt.show()

# ==== USAGE ====

v0 = 25
angles = [30, 45, 60]

# Plot ideal trajectories
plot_multiple_trajectories(v0, angles)

# Plot trajectories with air drag
plot_drag_trajectories(v0, angles, drag_coeff=0.02)

# Plot range vs. angle
range_vs_angle(v0)
