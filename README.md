---

# 📐 Parameter Definition for 2D Self-Balancing Bot in MATLAB

To simulate or control a 2D self-balancing robot (like a cart-pendulum model), you need to define several physical parameters. Here's how to calculate or estimate each one:

---

## 🔧 1. Mass of the Cart (`M`)

Represents the mass of the lower part of the robot (chassis, motors, etc.).

- **Real-world bot**: Weigh the chassis and components below the center of mass.
- **Simulation**: Estimate a typical value.

```matlab
M = 0.5; % kg
```

---

## 🔧 2. Mass of the Pendulum (`m`)

Represents the part of the bot that behaves like an inverted pendulum—typically the body above the wheel axis.

- **If simulating**: Use a fraction of total mass.
- **If real**: Weigh the mass above the wheel axis.

```matlab
m = 0.2; % kg
```

---

## 📏 3. Length to Center of Mass (`l`)

The distance from the pivot point (wheel axle) to the **center of mass** of the upper body (pendulum).

- **Estimate**: Assume halfway up the bot if uniform.
- For a robot of height `H`:  
  \[
  l = \frac{H}{2}
  \]

```matlab
l = 0.3; % meters (for a ~60 cm tall robot)
```

---

## 🌀 4. Moment of Inertia (`I`)

Inertia of the pendulum around the pivot point. For a rod or rectangular body pivoting at the bottom:

\[
I = \frac{1}{3} m \cdot l^2
\]

- Use CAD software (SolidWorks, Fusion360) for complex shapes.

```matlab
I = (1/3) * m * l^2; % kg·m²
```

---

## ⚙️ 5. Friction Coefficient (`b`)

Represents viscous damping from wheel and motor friction.

- **Difficult to measure** directly—use small value and tune.
- Increase if the system oscillates too much in simulation.

```matlab
b = 0.1; % N/m/sec
```

---

## 🌍 6. Gravity (`g`)

Standard gravitational acceleration on Earth:

```matlab
g = 9.81; % m/s^2
```

---

## ✅ Example Parameter Block

```matlab
M = 0.5;       % Mass of cart (kg)
m = 0.2;       % Mass of pendulum (kg)
b = 0.1;       % Coefficient of friction (N/m/sec)
l = 0.3;       % Length to pendulum center of mass (m)
I = (1/3)*m*l^2; % Moment of inertia (kg·m²)
g = 9.81;      % Gravity (m/s^2)
```

---

## 🛠 How to Measure for a Real Bot

| **Parameter** | **How to Obtain**                              |
|---------------|------------------------------------------------|
| `M`, `m`       | Weigh components separately using a scale      |
| `l`            | Measure vertical distance from axle to CoM     |
| `I`            | Estimate from shape or use CAD calculation     |
| `b`            | Estimate by observing slowing motion or tune   |

---

Let me know if you'd like this exported as a PDF, or embedded into a LaTeX report!