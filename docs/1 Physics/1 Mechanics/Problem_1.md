```latex
\documentclass{article}
\usepackage{amsmath, amssymb}
\usepackage{graphicx}

\begin{document}

\title{Investigating the Range as a Function of the Angle of Projection}
\author{}
\date{}
\maketitle

\section{Theoretical Foundation}
Projectile motion follows Newton's laws of motion. We consider a projectile launched with initial velocity $v_0$ at an angle $\theta$ above the horizontal. The motion can be analyzed in two perpendicular components: horizontal and vertical.

\subsection{Equations of Motion}
\begin{itemize}
    \item \textbf{Horizontal motion:}
    \begin{equation}
    x(t) = v_0 \cos(\theta) t
    \end{equation}
    The horizontal acceleration is zero (ignoring air resistance), so the velocity remains constant.

    \item \textbf{Vertical motion:}
    \begin{equation}
    y(t) = v_0 \sin(\theta) t - \frac{1}{2} g t^2
    \end{equation}
    The acceleration due to gravity, $g$, acts downward.
\end{itemize}

The time of flight (when the projectile returns to the ground, $y = 0$) is obtained by solving:
\begin{equation}
    v_0 \sin(\theta) t - \frac{1}{2} g t^2 = 0
\end{equation}
Factoring out $t$, we get:
\begin{equation}
    t (v_0 \sin(\theta) - \frac{1}{2} g t) = 0
\end{equation}
This gives two solutions: $t = 0$ (initial position) and $t = \frac{2 v_0 \sin(\theta)}{g}$ (when it hits the ground).

\subsection{Range Equation}
The range $R$ is the horizontal displacement when $t = \frac{2 v_0 \sin(\theta)}{g}$:
\begin{equation}
    R = v_0 \cos(\theta) \times \frac{2 v_0 \sin(\theta)}{g}
\end{equation}
Using the trigonometric identity $2 \sin(\theta) \cos(\theta) = \sin(2\theta)$, we obtain:
\begin{equation}
    R = \frac{v_0^2 \sin(2\theta)}{g}
\end{equation}

\section{Analysis of the Range}
\begin{itemize}
    \item The range is maximized when $\sin(2\theta)$ is maximized, which occurs at $2\theta = 90^\circ$ or $\theta = 45^\circ$.
    \item Increasing $v_0$ increases the range quadratically.
    \item Increasing $g$ reduces the range, as gravity pulls the projectile down more quickly.
\end{itemize}

\section{Practical Applications}
\begin{itemize}
    \item \textbf{Sports:} The trajectory of a soccer ball, golf ball, or javelin throw follows projectile motion.
    \item \textbf{Engineering:} Ballistic missile trajectory prediction.
    \item \textbf{Space Science:} Rockets launched at different angles optimize range.
\end{itemize}

\section{Implementation}
A Python script to simulate projectile motion and visualize range vs. angle:

\begin{verbatim}
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g=9.81):
    angles = np.linspace(0, 90, 100)  # Angles in degrees
    angles_rad = np.radians(angles)  # Convert to radians
    ranges = (v0**2 * np.sin(2 * angles_rad)) / g
    
    plt.figure(figsize=(8,5))
    plt.plot(angles, ranges, label=f'v0 = {v0} m/s')
    plt.xlabel('Angle of Projection (degrees)')
    plt.ylabel('Range (m)')
    plt.title('Projectile Range vs. Angle of Projection')
    plt.legend()
    plt.grid()
    plt.show()

projectile_range(20)  # Example with v0 = 20 m/s
\end{verbatim}

\section{Limitations and Extensions}
\begin{itemize}
    \item \textbf{Ignoring Air Resistance:} In reality, drag affects range.
    \item \textbf{Uneven Terrain:} Modifies landing conditions.
    \item \textbf{Variable Gravity:} Different gravitational fields alter trajectories.
\end{itemize}

\subsection{Suggested Extensions}
\begin{itemize}
    \item Implement air resistance using numerical methods.
    \item Simulate projectile motion on inclined planes.
    \item Extend analysis to three-dimensional motion.
\end{itemize}

This study demonstrates the power of fundamental physics principles in explaining and predicting real-world motion.

\end{document}
```

