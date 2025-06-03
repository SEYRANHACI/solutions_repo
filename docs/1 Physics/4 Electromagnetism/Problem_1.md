Great! Here's your complete solution, *with the headings updated* to match the four sections from your image:

---

# 🌟 *Complete Solution: Lorentz Force Simulation and Applications*

---

## ✅ *1. Exploration of Applications*

### 🔸 Mathematical Basis:

The Lorentz force governs the motion of a charged particle in electromagnetic fields:

$$
\vec{F} = q(\vec{E} + \vec{v} \times \vec{B})
$$

Using Newton’s second law:

$$
m \frac{d\vec{v}}{dt} = q(\vec{E} + \vec{v} \times \vec{B})
$$

This leads to circular, helical, or drift motion based on the field and velocity configuration.

---

### 🔸 Real-World Applications:

| System                 | Role of Lorentz Force                                           |
| ---------------------- | --------------------------------------------------------------- |
| *Cyclotron*          | Circular acceleration of charged particles in \$\vec{B}\$ field |
| *Mass Spectrometer*  | Deflection reveals mass-to-charge ratio                         |
| *Plasma Confinement* | Magnetic fields trap charged particles in devices like Tokamaks |
| *Space Physics*      | Earth's magnetic field deflects solar wind, cosmic rays         |

---

## ✅ *2. Simulated Particle Motion*

### 🔸 Mathematical Model:

Assume a uniform magnetic field and zero electric field:

$$
\vec{E} = 0, \quad \vec{F} = q (\vec{v} \times \vec{B})
$$

This results in:

* *Circular motion* if \$\vec{v} \perp \vec{B}\$
* *Helical motion* if \$\vec{v}\$ has a component along \$\vec{B}\$

---

## ✅ *3. Parameter Exploration*

We vary the following parameters to observe their effects:

* Electric and Magnetic Fields: \$\vec{E}\$, \$\vec{B}\$
* Charge and Mass: \$q\$, \$m\$
* Initial Velocity: \$\vec{v}\_0\$

Useful formula:

* *Larmor radius*:

  $$
  r_L = \frac{m v_\perp}{|q| B}
  $$

* *Drift velocity* in crossed fields:

  $$
  \vec{v}_{\text{drift}} = \frac{\vec{E} \times \vec{B}}{B^2}
  $$

---

## ✅ *4. Visualization*

The simulation generates:

* *2D trajectory plots* (e.g., x–y spiral paths)
* *3D visualizations* of particle motion
* *Insights into drift, Larmor radius, and motion behavior*

---

## ✅ *💻 Python Simulation Code (Tasks 2–4)*

python
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
r0 = np.array([0.0, 0.0, 0.0])   # Position
v0 = np.array([1.0, 1.0, 1.0])   # Velocity

T = 20.0     # Total time (s)
dt = 0.01    # Time step
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


---

## ✅ *Try These Parameter Variations*

| Case                         | Settings                       | Expected Behavior      |
| ---------------------------- | ------------------------------ | ---------------------- |
| Pure Magnetic Field          | E = [0, 0, 0]                | Circular/spiral motion |
| Crossed Fields (E × B Drift) | E = [1, 0, 0], B = [0, 0, 1] | Drift + spiral motion  |
| Opposite Charge              | q = -1.0                     | Opposite trajectory    |
| Heavier Particle             | m = 2.0                      | Slower, larger radius  |

---

## ✅ *Conclusion*

This project covered all four key tasks:

1. *Identified key applications* of the Lorentz force.
2. *Simulated* particle motion in electromagnetic fields.
3. *Explored parameter changes* and their effect on motion.
4. *Visualized trajectories* in both 2D and 3D.

