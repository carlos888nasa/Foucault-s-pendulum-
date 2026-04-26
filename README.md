# 🌀 Foucault's Pendulum Simulator — Wolfram Language

An interactive simulation of the **Foucault pendulum** built in Wolfram Mathematica, combining classical pendulum dynamics with the **Coriolis effect** due to Earth's rotation.

> Code and labels are in Spanish — working on gradually migrating to English.

---

## 📌 What it does

The notebook includes a unified interactive interface (`Manipulate`) with **four panels**:

| Panel | Description |
|---|---|
| Top-left | Classical pendulum animation (rope + mass + velocity vector) |
| Top-right | Angular displacement vs. time plot |
| Bottom-left | Top-down view of the pendulum trajectory under Coriolis effect |
| Bottom-right | X and Y coordinate evolution over time |

---

## ⚙️ Physics

### Classical pendulum (nonlinear)
Solves the exact equation of motion numerically using `NDSolve`:

$$\ddot{\Theta} = -\frac{g}{L} \sin(\Theta), \quad \Theta(0) = \theta_0, \quad \dot{\Theta}(0) = 0$$

with `g = 10 m/s²`.

### Coriolis effect (linearized)
Models the horizontal plane motion of the pendulum bob under Earth's rotation at a given latitude φ:

$$\ddot{x} = -\frac{g}{L}x + 2\Omega\sin\phi\,\dot{y}$$
$$\ddot{y} = -\frac{g}{L}y - 2\Omega\sin\phi\,\dot{x}$$

with Earth's angular velocity Ω = 7.2921 × 10⁻⁵ rad/s.

---

## 🎛️ Interactive Parameters

| Parameter | Range | Default | Description |
|---|---|---|---|
| `θ₀` | 1° – 80° | 20° | Initial angle |
| `L` | 10 – 100 m | 10 m | Pendulum length |
| `φ` | 0° – 90° | 45° | Geographic latitude |
| `x₀`, `y₀` | −1 – 1 | 0.5, 0 | Initial Coriolis position |
| `vx₀`, `vy₀` | −1 – 1 | 0, 0.5 | Initial Coriolis velocity |
| `t` | 0 – 10 s | — | Simulation time slider |

---

## 🗂️ Files

```
Foucault-s-pendulum-/
├── pendulo con efecto coriolis unificado.nb   # Main Wolfram notebook
└── README.md
```

---

## 🚀 How to run

1. Open the `.nb` file in **Wolfram Mathematica** (tested on version 14.2).
2. Run all cells (`Evaluation → Evaluate Notebook`).
3. Use the sliders in the `Manipulate` output to explore different configurations.

> ⚠️ Requires Wolfram Mathematica. Not compatible with Wolfram Player alone (uses `NDSolve` and dynamic modules).

---

## 🧠 Implementation notes

- The classical pendulum uses **memoization** (`θ₀tmp`, `Ltmp`) to avoid recomputing the ODE solution when parameters haven't changed, reducing recalculation overhead during animation.
- The Coriolis simulation solves a coupled ODE system over `t ∈ [0, 100]` seconds.
- The velocity arrow in the classical panel is scaled by `L/5` for visual clarity.

---

## 📚 Context

The **Foucault pendulum** (1851) demonstrates Earth's rotation through the slow precession of the pendulum's oscillation plane. The precession rate at latitude φ is:

$$\Omega_{\text{precession}} = \Omega \sin\phi$$

At the poles (φ = 90°), one full rotation takes ~24 hours. At the equator (φ = 0°), there is no precession.

---

## 🏷️ Topics

`physics` · `simulation` · `wolfram-language` · `mathematica` · `differential-equations` · `coriolis-effect` · `education` · `mechanics`
