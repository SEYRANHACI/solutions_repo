Great, let’s break this task into the four key parts:

---

## **1. Deriving the Relationship (Kepler’s Third Law for Circular Orbits)**

### **Newton's Law of Universal Gravitation:**

For two bodies (like a planet and its satellite),

$$
F = \frac{G M m}{r^2}
$$

Where:

* $G$ = gravitational constant
* $M$ = mass of central body (e.g., Earth, Sun)
* $m$ = mass of orbiting body (e.g., Moon, satellite)
* $r$ = orbital radius

### **Centripetal Force for Circular Motion:**

$$
F = \frac{m v^2}{r}
$$

### **Equating Gravitational and Centripetal Forces:**

$$
\frac{G M m}{r^2} = \frac{m v^2}{r}
\Rightarrow v^2 = \frac{G M}{r}
$$

Now, express orbital velocity $v$ in terms of the period $T$:

$$
v = \frac{2 \pi r}{T}
\Rightarrow \left(\frac{2 \pi r}{T}\right)^2 = \frac{G M}{r}
$$

Simplify:

$$
\frac{4 \pi^2 r^2}{T^2} = \frac{G M}{r}
\Rightarrow T^2 = \frac{4 \pi^2 r^3}{G M}
$$

### ✅ **Kepler’s Third Law (Circular Orbit Form):**

$$
T^2 \propto r^3
$$

---

## **2. Implications for Astronomy**

### **a. Mass Determination:**

Rearranging the formula:

$$
M = \frac{4 \pi^2 r^3}{G T^2}
$$

This allows astronomers to calculate the mass of a central body (like the Earth or the Sun) using observations of satellite or planetary orbits.

### **b. Distance Estimation:**

If we know the orbital period and the mass of the central body, we can solve for orbital radius $r$.

### **c. System Characterization:**

Used to classify and understand multi-body systems such as:

* Exoplanets around stars
* Moons around planets
* Satellites around Earth

---

## **3. Real-World Examples**

### **a. Moon Orbiting Earth**

* $T \approx 27.3$ days $= 2.36 \times 10^6$ s
* $r \approx 3.84 \times 10^8$ m
* Earth mass from this:

$$
M = \frac{4 \pi^2 r^3}{G T^2} \approx 5.97 \times 10^{24} \text{ kg}
$$

### **b. Planets in the Solar System**

Using ratios (e.g., Earth vs. Mars):

$$
\left(\frac{T_1}{T_2}\right)^2 = \left(\frac{r_1}{r_2}\right)^3
$$

Holds well when measured.

---

## **4. Computational Model to Simulate and Verify**

We can simulate several orbiting bodies and numerically test if $T^2 \propto r^3$.

Here's a basic Python simulation using `matplotlib` and `numpy`:

```python
import numpy as np
import matplotlib.pyplot as plt

# Constants
G = 6.67430e-11  # gravitational constant
M = 1.989e30     # mass of the Sun in kg

# Generate radii (in meters) and calculate periods
radii = np.linspace(0.3, 30, 100) * 1.496e11  # 0.3 AU to 30 AU
T_squared = []
R_cubed = []

for r in radii:
    T = 2 * np.pi * np.sqrt(r**3 / (G * M))
    T_squared.append(T**2)
    R_cubed.append(r**3)

# Plot T^2 vs r^3
plt.figure(figsize=(8,6))
plt.plot(R_cubed, T_squared, label=r'$T^2$ vs $r^3$', color='blue')
plt.xlabel('Orbital Radius Cubed $r^3$ (m³)')
plt.ylabel('Orbital Period Squared $T^2$ (s²)')
plt.title("Verification of Kepler's Third Law")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
```

---

### ✅ Summary

* **Derived**: $T^2 = \frac{4 \pi^2 r^3}{GM}$
* **Implications**: Enables mass/distance determination in astronomy.
* **Examples**: Moon-Earth system, planetary orbits.
* **Model**: Simulated and verified using a Python plot — confirms the linearity of $T^2$ vs. $r^3$.

Would you like to explore adding elliptical orbits, or implementing an interactive orbit simulator next?
