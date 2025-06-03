## 🚀 GRAVITY – PROBLEM 2

## ESCAPE VELOCITIES AND COSMIC VELOCITIES

---

### ✅ 1. DEFINE THE FIRST, SECOND, AND THIRD COSMIC VELOCITIES, EXPLAINING THEIR PHYSICAL MEANING

---

### 📐 Definitions:

* **First Cosmic Velocity (Orbital Velocity):**
  Minimum velocity to enter stable circular orbit near a celestial body’s surface.

  $$
  v_1 = \sqrt{\frac{G M}{r}}
  $$

* **Second Cosmic Velocity (Escape Velocity):**
  Velocity needed to break free from a planet’s gravity (no further propulsion).

  $$
  v_2 = \sqrt{2} \cdot v_1 = \sqrt{\frac{2GM}{r}}
  $$

* **Third Cosmic Velocity:**
  Velocity required to escape the gravitational influence of the **entire solar system**.
  Depends on Sun’s gravity and spacecraft's distance from it.

---

### ✅ 2. ANALYZE THE MATHEMATICAL DERIVATIONS AND PARAMETERS AFFECTING THESE VELOCITIES

---

### 📐 Derivations:

From conservation of energy:

$$
\text{Kinetic Energy} = \text{Gravitational Potential Energy}
$$

* Escape condition:

$$
\frac{1}{2}mv^2 = \frac{GMm}{r}
\Rightarrow v = \sqrt{\frac{2GM}{r}}
$$

**Parameters affecting velocity:**

* $M$ → mass of planet/star
* $r$ → distance from center
* $G$ → universal constant (fixed)

Heavier or denser bodies → higher escape velocities.

---

### ✅ 3. CALCULATE AND VISUALIZE THESE VELOCITIES FOR DIFFERENT CELESTIAL BODIES LIKE EARTH, MARS AND JUPYTER

---

### 💻 Python Code:

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11

# Planetary data: name, mass (kg), radius (m)
bodies = {
    "Earth": [5.972e24, 6.371e6],
    "Mars": [6.39e23, 3.39e6],
    "Jupiter": [1.898e27, 6.9911e7]
}

v1, v2 = {}, {}

for body, (mass, radius) in bodies.items():
    v1[body] = np.sqrt(G * mass / radius)
    v2[body] = np.sqrt(2 * G * mass / radius)

# Plotting
labels = list(bodies.keys())
v1_vals = [v1[b] for b in labels]
v2_vals = [v2[b] for b in labels]

x = np.arange(len(labels))
width = 0.35

plt.bar(x - width/2, v1_vals, width, label='v1 (Orbital)')
plt.bar(x + width/2, v2_vals, width, label='v2 (Escape)')
plt.xticks(x, labels)
plt.ylabel("Velocity (m/s)")
plt.title("Cosmic Velocities for Different Planets")
plt.legend()
plt.grid(True, linestyle='--', alpha=0.5)
plt.show()
```

---

### ✅ 4. DISCUSS THEIR IMPORTANCE IN SPACE EXPLORATION, INCLUDING LAUNCHING SATELLITES, MISSIONS TO OTHER PLANETS, AND POTENTIAL INTERSTELLAR TRAVEL

---

### 🚀 Application Discussion:

* **v1** → Used to launch satellites into **low Earth orbit (LEO)**.
* **v2** → Needed to send probes to **Moon, Mars**, or deep space.
* **v3** → Relevant for escaping solar system; e.g., **Voyager 1** used gravity assist to exceed v3.

Knowing these velocities helps:

* Optimize fuel and payload
* Plan gravity assists
* Design interplanetary and interstellar missions

Əla, Problem 3 də sənin istədiyin kimi əvvəl **riyazi izah**, sonra **Python simulyasiyası** ilə hazırlanıb. Hər bir hissənin başlığı **verilən kimi və böyük hərflərlə** qeyd olunub. Qrafiklər, nümunələr və kod daxil edilib.

---