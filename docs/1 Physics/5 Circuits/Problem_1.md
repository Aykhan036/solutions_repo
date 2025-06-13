# Problem 1
# Equivalent Resistance Using Graph Theory – Step-by-Step Explanation

## 1. Model the Circuit as a Graph

- Each **junction** in the circuit becomes a **node**.
- Each **resistor** becomes an **edge** between two nodes.
- The **resistance value** becomes the **weight** of the edge.
- The graph is **undirected**, since current flows in both directions through a resistor.

## 2. Identify Series Connections

- A node (excluding the starting and ending terminals) that connects to **exactly two** other nodes is a **series node**.

- If three nodes are connected like:

  ```
  A —[R₁]— B —[R₂]— C
  ```

  and node $B$ connects only to $A$ and $C$, then resistors $R_1$ and $R_2$ are in **series**.

- Replace this part with a single resistor from $A$ to $C$ with total resistance:

  $$
  R = R_1 + R_2
  $$

- Remove node $B$ and its two edges. Add a new edge directly between $A$ and $C$ with resistance $R$.

## 3. Identify Parallel Connections

- If two or more resistors connect the **same pair of nodes**, they are in **parallel**.

- For resistors $R_1, R_2, \dots, R_n$ between the same two nodes, calculate the total resistance using:

  $$
  \frac{1}{R} = \frac{1}{R_1} + \frac{1}{R_2} + \dots + \frac{1}{R_n}
  $$

- Remove all parallel edges and replace them with **one edge** representing the **equivalent resistance**.

## 4. Repeat the Process

- After each series or parallel simplification, the structure of the graph changes.

- Repeat the checks:

  - Are there new series nodes?
  - Are there new parallel edges?

- Keep simplifying until you're left with just **two nodes**: the starting node and the ending node (the ones across which you want the equivalent resistance).

- The remaining resistor between these two nodes is the **equivalent resistance**.

## 5. Handling Complex and Nested Circuits

- **Nested combinations** (e.g., a series containing parallel branches, or vice versa) are handled the same way:
  - Simplify **inner parts first**, then continue outward.

- Always look for the **smallest series or parallel patterns**, reduce them, and repeat.

- In **cyclic graphs** (loops), simplifications expose more series or parallel connections step by step.

## Examples

### Simple Series

```
A —[5Ω]— B —[10Ω]— C
```

- Combine to get:

  ```
  A —[15Ω]— C
  ```

  $$
  R = 5\,\Omega + 10\,\Omega = 15\,\Omega
  $$

### Simple Parallel

- Two resistors of $10\,\Omega$ and $20\,\Omega$ between $A$ and $B$:

  $$
  \frac{1}{R} = \frac{1}{10} + \frac{1}{20} = \frac{3}{20} \Rightarrow R = \frac{20}{3} \approx 6.67\,\Omega
  $$

### Nested Example

```
A —[10Ω]— B
B —[20Ω]— C
B —[10Ω]— C
C —[5Ω]— D
```

- First combine $B \to C$ in parallel:

  $$
  \frac{1}{R_{BC}} = \frac{1}{20} + \frac{1}{10} = \frac{3}{20} \Rightarrow R_{BC} = \frac{20}{3} \approx 6.67\,\Omega
  $$

- Then total path $A \to B \to C \to D$:

  $$
  R = 10 + \frac{20}{3} + 5 = \frac{95}{3} \approx 31.67\,\Omega
  $$

## Final Result

- After applying the above steps, you end up with a **single edge** between your two main terminals.
- The resistance of that final edge is the **equivalent resistance** of the entire circuit.

