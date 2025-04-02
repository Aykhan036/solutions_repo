# Problem 1
\documentclass{article}
\usepackage{amsmath, amssymb, graphicx}

\title{Investigating the Range as a Function of the Angle of Projection}
\author{}
\date{}

\begin{document}

\maketitle

\section{Introduction}
Projectile motion is a fundamental topic in physics that provides insights into motion under gravity. The range of a projectile, which depends on the angle of projection, follows a well-defined mathematical relationship. This document explores the theoretical and computational aspects of projectile motion.

\section{Theoretical Foundation}
The equations of motion for a projectile launched with an initial velocity $ v_0 $ at an angle $ \theta $ from the horizontal are derived from kinematics.

The horizontal and vertical components of velocity are:
\begin{align}
    v_{0x} &= v_0 \cos \theta, \\
    v_{0y} &= v_0 \sin \theta.
\end{align}

The equations of motion under constant gravitational acceleration $ g $ are:
\begin{align}
    x(t) &= v_{0x} t, \\
    y(t) &= v_{0y} t - \frac{1}{2} g t^2.
\end{align}

To find the time of flight, we solve for $ t $ when $ y = 0 $:
\begin{align}
    0 &= v_0 \sin \theta \cdot t - \frac{1}{2} g t^2.
\end{align}

Factoring out $ t $:
\begin{align}
    t (v_0 \sin \theta - \frac{1}{2} g t) &= 0.
\end{align}

This gives two solutions: $ t = 0 $ (initial launch) and $ t = \frac{2 v_0 \sin \theta}{g} $ (landing time).

The range $ R $ is found by substituting the total flight time into $ x(t) $:
\begin{align}
    R = v_{0x} t = v_0 \cos \theta \cdot \frac{2 v_0 \sin \theta}{g}.
\end{align}

Using the trigonometric identity $ 2 \sin \theta \cos \theta = \sin 2\theta $, we get:
\begin{align}
    R = \frac{v_0^2}{g} \sin 2\theta.
\end{align}

\section{Analysis of the Range}
The range depends on the angle $ \theta $, initial velocity $ v_0 $, and gravitational acceleration $ g $. The maximum range occurs at $ \theta = 45^\circ $, where $ \sin 2\theta = 1 $. 

For different values of $ v_0 $ and $ g $, the range varies as:
\begin{align}
    R_{\max} = \frac{v_0^2}{g}.
\end{align}

\section{Practical Applications}
This model can be extended to real-world scenarios such as:
\begin{itemize}
    \item Sports physics (e.g., optimizing the angle for maximum shot put distance).
    \item Ballistics and military applications.
    \item Spacecraft and rocket launch trajectories.
\end{itemize}

Incorporating factors like air resistance leads to more complex models that require numerical simulations.

\section{Implementation in Python}
A Python script can simulate projectile motion and visualize the range vs. angle of projection:

```python
import numpy as np
import matplotlib.pyplot as plt

def projectile_range(v0, g):
    angles = np.linspace(0, 90, 100)
    ranges = (v0**2 / g) * np.sin(2 * np.radians(angles))
    plt.plot(angles, ranges)
    plt.xlabel("Angle (degrees)")
    plt.ylabel("Range (meters)")
    plt.title("Projectile Range as a Function of Launch Angle")
    plt.show()

projectile_range(20, 9.81)
```

\section{Conclusion}
Projectile motion demonstrates the interplay between initial conditions and motion outcomes. The derived equations provide insights into real-world applications, and computational tools help visualize complex scenarios.

\end{document}