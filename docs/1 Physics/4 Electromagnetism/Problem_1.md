Əla iş! Sənin paylaşdığın sənəd məzmun olaraq çox yaxşıdır, sadəcə **GitHub və Visual Studio Code** kimi platformalarda daha yaxşı görünməsi üçün formatı bir az optimallaşdırmaq lazımdır.

Aşağıda sənə oxunaqlılığı artırılmış və **Markdown sintaksisinə uyğunlaşdırılmış** versiyasını təqdim edirəm — bu versiya GitHub, Jupyter Notebook və VS Code-da daha gözəl görünəcək:

---

# 🌟 **Complete Solution: Lorentz Force Simulation and Applications**

---

## ✅ 1. EXPLORATION OF APPLICATIONS

### 🔸 **Mathematical Basis**

The Lorentz force determines the motion of a charged particle in electromagnetic fields:

$$
\vec{F} = q(\vec{E} + \vec{v} \times \vec{B})
$$

From Newton’s second law:

$$
m \frac{d\vec{v}}{dt} = q(\vec{E} + \vec{v} \times \vec{B})
$$

This leads to:

* Circular motion
* Helical motion
* Drift motion (depending on field & velocity)

---

### 🔸 **Real-World Applications**

| System                 | Role of Lorentz Force                                              |
| ---------------------- | ------------------------------------------------------------------ |
| **Cyclotron**          | Circular acceleration of charged particles using magnetic fields   |
| **Mass Spectrometer**  | Particle deflection reveals mass-to-charge ratio                   |
| **Plasma Confinement** | Magnetic fields trap particles (e.g., in Tokamaks)                 |
| **Space Physics**      | Deflects solar wind and cosmic rays near planetary magnetic fields |

---

## ✅ 2. SIMULATED PARTICLE MOTION

### 🔸 **Model**

Assume:

* Uniform magnetic field: $\vec{B}$
* No electric field: $\vec{E} = 0$

Then:

* If $\vec{v} \perp \vec{B}$: Circular motion
* If $\vec{v} \parallel \vec{B}$: Linear motion
* If mixed: Helical motion

---

## ✅ 3. PARAMETER EXPLORATION

### 🔸 **Key Quantities**

* **Larmor radius**:

  $$
  r_L = \frac{m v_\perp}{|q| B}
  $$

* **Drift velocity** in crossed fields:

  $$
  \vec{v}_{\text{drift}} = \frac{\vec{E} \times \vec{B}}{B^2}
  $$

### 🔸 **Effect of Parameter Changes**

| Parameter        | Effect                           |
| ---------------- | -------------------------------- |
| Higher velocity  | Larger radius                    |
| Heavier particle | Slower rotation                  |
| Negative charge  | Opposite trajectory direction    |
| $\vec{E} \neq 0$ | Adds drift to helical trajectory |

---

## ✅ 4. VISUALIZATION

Python simulation plots:

* 2D spiral in the x–y plane
* 3D helix in x–y–z space
* Changes based on initial velocity and field values

---

## ✅ 💻 PYTHON SIMULATION CODE (TASKS 2–4)

```python
import numpy as np
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D

# --- Parameters ---
q = 1.0                          # Charge (C)
m = 1.0                          # Mass (kg)

# Fields
E = np.array([1.0, 0.0, 0.0])    # Electric field (V/m)
B = np.array([0.0, 0.0, 1.0])    # Magnetic field (T)

# Initial conditions
r0 = np.array([0.0, 0.0, 0.0])
v0 = np.array([1.0, 1.0, 1.0])

T = 20.0
dt = 0.01
steps = int(T / dt)

# Arrays
r = np.zeros((steps, 3))
v = np.zeros((steps, 3))
t = np.zeros(steps)

r[0], v[0] = r0, v0

def acceleration(v):
    return (q / m) * (E + np.cross(v, B))

def rk4(r, v, dt):
    k1v = acceleration(v)
    k1r = v

    k2v = acceleration(v + 0.5 * dt * k1v)
    k2r = v + 0.5 * dt * k1v

    k3v = acceleration(v + 0.5 * dt * k2v)
    k3r = v + 0.5 * dt * k2v

    k4v = acceleration(v + dt * k3v)
    k4r = v + dt * k3v

    v_new = v + (dt / 6.0) * (k1v + 2*k2v + 2*k3v + k4v)
    r_new = r + (dt / 6.0) * (k1r + 2*k2r + 2*k3r + k4r)

    return r_new, v_new

for i in range(1, steps):
    r[i], v[i] = rk4(r[i-1], v[i-1], dt)
    t[i] = t[i-1] + dt

# --- Visualization ---
fig = plt.figure(figsize=(12, 5))

# 2D Trajectory
plt.subplot(1, 2, 1)
plt.plot(r[:,0], r[:,1])
plt.title("2D Trajectory (x-y)")
plt.xlabel("x [m]")
plt.ylabel("y [m]")
plt.axis('equal')
plt.grid(True)

# 3D Trajectory
ax = fig.add_subplot(1, 2, 2, projection='3d')
ax.plot3D(r[:,0], r[:,1], r[:,2])
ax.set_title("3D Trajectory")
ax.set_xlabel("x [m]")
ax.set_ylabel("y [m]")
ax.set_zlabel("z [m]")

plt.tight_layout()
plt.show()
```

---

## ✅ PARAMETER TEST CASES

| Scenario               | Settings                       | Behavior                |
| ---------------------- | ------------------------------ | ----------------------- |
| Pure Magnetic Field    | `E = [0, 0, 0]`                | Circular/spiral motion  |
| Crossed Fields (E × B) | `E = [1, 0, 0], B = [0, 0, 1]` | Drift + spiral motion   |
| Opposite Charge        | `q = -1.0`                     | Opposite rotation       |
| Heavier Particle       | `m = 2.0`                      | Slower motion, larger r |

---

## ✅ CONCLUSION

This project covered all four tasks:

1. **Exploration of Applications**
2. **Simulated Particle Motion**
3. **Parameter Exploration**
4. **Visualization**

This simulation builds intuition for motion under Lorentz force — crucial in fields like **accelerator physics**, **space research**, and **plasma engineering**.

---

