# Problem 2

gravity 2.1.1

 Problem 2 – Task 1: Define the First, Second, and Third Cosmic Velocities
📌 Definitions and Physical Meaning
First Cosmic Velocity (
𝑣
1
v 
1
​
 ) — Orbital Velocity
The minimum horizontal speed needed for an object to enter stable circular orbit near the surface of a planet (without propulsion).

𝑣
1
=
𝐺
𝑀
𝑟
v 
1
​
 = 
r
GM
​
 
​
 
Second Cosmic Velocity (
𝑣
2
v 
2
​
 ) — Escape Velocity
The minimum speed required to break free from a planet’s gravitational field without further propulsion.

𝑣
2
=
2
𝐺
𝑀
𝑟
v 
2
​
 = 
r
2GM
​
 
​
 
Third Cosmic Velocity (
𝑣
3
v 
3
​
 ) — Interstellar Escape Velocity
The minimum speed needed to escape the gravitational pull of the Sun from Earth’s orbit (i.e., to leave the solar system).

𝑣
3
=
𝑣
Earth orbit
2
+
𝑣
2
2
v 
3
​
 = 
v 
Earth orbit
2
​
 +v 
2
2
​
 
​
 
Where:

𝑣
Earth orbit
≈
29.78
 
km/s
v 
Earth orbit
​
 ≈29.78km/s (orbital velocity of Earth around Sun),

𝑣
2
≈
11.2
 
km/s
v 
2
​
 ≈11.2km/s (escape velocity from E


 import numpy as np

# Gravitational constant
G = 6.67430e-11  # m^3 kg^-1 s^-2

# Define planets with mass (kg) and radius (m)
planets = {
    "Earth":   {"mass": 5.972e24, "radius": 6.371e6},
    "Mars":    {"mass": 6.417e23, "radius": 3.390e6},
    "Jupiter": {"mass": 1.898e27, "radius": 6.991e7}
}

# Function to compute v1 and v2
def compute_cosmic_velocities(mass, radius):
    v1 = np.sqrt(G * mass / radius)        # First cosmic velocity
    v2 = np.sqrt(2 * G * mass / radius)    # Second cosmic velocity
    return v1, v2

# Calculate and print
for planet, data in planets.items():
    v1, v2 = compute_cosmic_velocities(data["mass"], data["radius"])
    print(f"{planet}:\n  First Cosmic Velocity (v1): {v1/1000:.2f} km/s\n  Second Cosmic Velocity (v2): {v2/1000:.2f} km/s\n")

output 

Earth:
  First Cosmic Velocity (v1): 7.91 km/s
  Second Cosmic Velocity (v2): 11.19 km/s

Mars:
  First Cosmic Velocity (v1): 3.55 km/s
  Second Cosmic Velocity (v2): 5.03 km/s

Jupiter:
  First Cosmic Velocity (v1): 42.06 km/s
  Second Cosmic Velocity (v2): 59.54 km/s
