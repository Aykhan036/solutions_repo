# Problem 1
# Pendulum Experiment to Measure Gravitational Acceleration

## 1. Experimental Setup

- **Pendulum length ($L$)**: Measured from suspension point to center of mass of the weight.
- **Measuring tool resolution**: 1 mm = 0.001 m

Uncertainty in $L$:

\[
\Delta L = \frac{0.001}{2} = 0.0005 \text{ m}
\]

Measured value:

\[
L = 1.000 \text{ m}, \quad \Delta L = 0.0005 \text{ m}
\]

## 2. Timing Data Collection

**Measured time for 10 oscillations (in seconds):**

| Trial | $T_{10}$ (s) |
|-------|--------------|
| 1     | 20.10        |
| 2     | 20.15        |
| 3     | 20.08        |
| 4     | 20.12        |
| 5     | 20.14        |
| 6     | 20.09        |
| 7     | 20.11        |
| 8     | 20.13        |
| 9     | 20.16        |
| 10    | 20.10        |

Mean time for 10 oscillations:

\[
\bar{T}_{10} = \frac{1}{10} \sum T_{10} = 20.118 \text{ s}
\]

Standard deviation:

\[
\sigma_T \approx 0.026 \text{ s}
\]

Uncertainty in the mean:

\[
\Delta T_{10} = \frac{\sigma_T}{\sqrt{n}} = \frac{0.026}{\sqrt{10}} \approx 0.008 \text{ s}
\]

## 3. Calculations

### (a) Period of 1 oscillation:

\[
T = \frac{\bar{T}_{10}}{10} = \frac{20.118}{10} = 2.0118 \text{ s}
\]

\[
\Delta T = \frac{0.008}{10} = 0.0008 \text{ s}
\]

### (b) Acceleration due to gravity:

\[
g = \frac{4\pi^2 L}{T^2} = \frac{4\pi^2 \cdot 1.000}{(2.0118)^2} \approx 9.766 \text{ m/s}^2
\]

### (c) Uncertainty in $g$:

\[
\Delta g = g \sqrt{\left( \frac{\Delta L}{L} \right)^2 + \left( 2 \cdot \frac{\Delta T}{T} \right)^2}
\]

\[
\Delta g = 9.766 \cdot \sqrt{\left( \frac{0.0005}{1.000} \right)^2 + \left( 2 \cdot \frac{0.0008}{2.0118} \right)^2}
\]

\[
\Delta g \approx 9.766 \cdot \sqrt{2.5 \times 10^{-7} + 6.3 \times 10^{-7}} \approx 0.010 \text{ m/s}^2
\]

## 4. Final Results Summary

```markdown
| Quantity                 | Value         |
|--------------------------|---------------|
| $L$                      | 1.000 m       |
| $\Delta L$               | 0.0005 m      |
| Mean $T_{10}$ ($\bar{T}_{10}$) | 20.118 s      |
| $\sigma_T$               | 0.026 s       |
| $\Delta T_{10}$          | 0.008 s       |
| Period $T$               | 2.0118 s      |
| $\Delta T$               | 0.0008 s      |
| $g$                      | 9.766 m/s²    |
| $\Delta g$               | 0.010 m/s²    |
