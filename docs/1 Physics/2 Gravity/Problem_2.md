Sure! Here's your simplified and clean version of the **Cosmic Velocities** topic in **English**:

---

### 🚀 Cosmic Velocities — Simple Explanation

#### 1️⃣ First Cosmic Velocity (v₁) — To Enter Orbit

* The minimum horizontal speed needed for a body to enter a stable circular orbit around a planet.
* **Formula:**

  $$
  v₁ = \sqrt{\frac{GM}{r}}
  $$

#### 2️⃣ Second Cosmic Velocity (v₂) — To Escape Gravity

* The speed required to completely escape a planet’s gravitational pull.
* **Formula:**

  $$
  v₂ = \sqrt{\frac{2GM}{r}} = \sqrt{2} \cdot v₁
  $$

#### 3️⃣ Third Cosmic Velocity (v₃) — To Leave the Solar System

* The speed required to escape the Sun's gravity from Earth’s orbit.
* **Approximate Formula:**

  $$
  v₃ = \sqrt{v₂^2 + v_{\text{earth orbit}}^2}
  $$

---

### 🌍 Example Calculations (Python Code)

```python
import numpy as np

G = 6.67430e-11  # Gravitational constant
v_earth_orbit = 29.78e3  # Earth's orbital speed (m/s)

planets = {
    "Earth":   {"mass": 5.972e24, "radius": 6.371e6},
    "Mars":    {"mass": 6.417e23, "radius": 3.390e6},
    "Jupiter": {"mass": 1.898e27, "radius": 6.991e7}
}

for name, data in planets.items():
    M = data["mass"]
    r = data["radius"]
    
    v1 = np.sqrt(G * M / r)
    v2 = np.sqrt(2 * G * M / r)

    if name == "Earth":
        v3 = np.sqrt(v2**2 + v_earth_orbit**2)
        print(f"{name}: v₁={v1/1000:.2f} km/s, v₂={v2/1000:.2f} km/s, v₃={v3/1000:.2f} km/s")
    else:
        print(f"{name}: v₁={v1/1000:.2f} km/s, v₂={v2/1000:.2f} km/s")
```

---

### 📌 What These Velocities Mean

| Velocity | Use Case                                          |
| -------- | ------------------------------------------------- |
| v₁       | Placing satellites into orbit (e.g., GPS, ISS)    |
| v₂       | Interplanetary missions (e.g., Mars rovers)       |
| v₃       | Escaping the solar system (e.g., Voyager 1 probe) |

---

### 🔍 Test Example: Classify a Given Launch Speed

```python
def classify_velocity(v_launch):
    if v_launch < 7910:
        return "Not enough to orbit — falls back to Earth"
    elif 7910 <= v_launch < 11190:
        return "Achieves Earth orbit"
    elif 11190 <= v_launch < 42100:
        return "Escapes Earth's gravity"
    else:
        return "Exits the Solar System"

for v in [3000, 7900, 11200, 45000]:
    print(f"{v/1000:.1f} km/s → {classify_velocity(v)}")
```

---

Would you like me to format this as a downloadable **PDF** or **Word document**?
