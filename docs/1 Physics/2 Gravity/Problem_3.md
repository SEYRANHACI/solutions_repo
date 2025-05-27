Here’s a **clean, simplified, and fully English version** of the material you provided on **Gravitational Motion and Trajectories**, ideal for a project, study guide, or explanation:

---

## 🌍 Problem 3 — Gravitational Motion and Space Trajectories

### 3.1 Newton’s Law of Gravitation

The gravitational force acting between Earth and a payload (e.g., a spacecraft or satellite) is:

$$
F = \frac{GMm}{r^2}
$$

* **$G$** – Gravitational constant: $6.67430 \times 10^{-11} \ \mathrm{m^3 \cdot kg^{-1} \cdot s^{-2}}$
* **$M$** – Mass of Earth: $5.972 \times 10^{24} \ \mathrm{kg}$
* **$m$** – Mass of the object/payload
* **$r$** – Distance from the center of the Earth

---

### 3.1.1 Conservation of Mechanical Energy

The total mechanical energy $E$ (kinetic + potential) of a payload in motion is:

$$
E = \frac{1}{2}mv^2 - \frac{GMm}{r}
$$

* $v$: Speed of the object
* $r$: Distance from Earth’s center

---

### 🚀 Trajectory Types Based on Energy

#### 1. **Parabolic Trajectory** – Escape velocity

* Total Energy $E = 0$
* Condition:

  $$
  \frac{1}{2}mv^2 = \frac{GMm}{r}
  $$
* Follows a parabolic path; just escapes Earth’s gravity.

#### 2. **Elliptical Orbit**

* Total Energy $E < 0$
* Equation:

  $$
  E = -\frac{GMm}{2a}
  $$
* $a$: Semi-major axis of the elliptical orbit

#### 3. **Hyperbolic Trajectory**

* Total Energy $E > 0$
* Object escapes Earth’s gravity at high speed.

---

### 3.1.2 Mathematical Model (Force and Acceleration)

Using **Newton’s Second Law** and **Universal Gravitation**:

$$
\vec{a} = -\frac{GM}{r^3} \vec{r}
$$

Where:

* $\vec{a}$: Acceleration vector
* $\vec{r}$: Position vector
* $r = \sqrt{x^2 + y^2}$

This is a **central force problem**, often solved using numerical methods like Euler or Runge-Kutta.

---

### 3.1.3 🚀 Real-World Trajectories

| Trajectory Type         | Required Speed (from LEO) | Real-World Example                        |
| ----------------------- | ------------------------- | ----------------------------------------- |
| **Suborbital**          | < 7.8 km/s                | Blue Origin space tourism                 |
| **Orbital (Circular)**  | ≈ 7.8 km/s                | Satellites, ISS                           |
| **Elliptical Orbit**    | 7.8 – 11.2 km/s           | Geostationary satellites, transfer orbits |
| **Escape (Hyperbolic)** | > 11.2 km/s               | Voyager, Mars rovers                      |

* **LEO**: Low Earth Orbit
* **ISS**: International Space Station

---

### 3.1.4 ✅ Key Equations

#### Newton’s Law of Gravitation (Vector Form):

$$
\vec{F}_g = -\frac{GMm}{r^2} \hat{r}
$$

* $\hat{r}$: Unit vector in radial direction
* Negative sign means the force is attractive (toward Earth)

#### Newton’s Second Law:

$$
\vec{a} = \frac{\vec{F}}{m} = -\frac{GM}{r^3} \vec{r}
$$

#### Equations of Motion (2D Form):

$$
\frac{d^2x}{dt^2} = -\frac{GMx}{(x^2 + y^2)^{3/2}}, \quad \frac{d^2y}{dt^2} = -\frac{GMy}{(x^2 + y^2)^{3/2}}
$$

These are solved using numerical methods (e.g., Euler integration) in Python simulations.

---

### 📈 Visualization:

Numerical simulations can visualize trajectories like:

* Arcs (suborbital)
* Circles and ellipses (orbital)
* Hyperbolas (escape)

---

Would you like this formatted into a **PDF** or **PowerPoint presentation**?
