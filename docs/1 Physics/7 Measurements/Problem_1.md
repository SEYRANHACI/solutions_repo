
---

# **TASK**

**MEASURE THE ACCELERATION DUE TO GRAVITY USING A PENDULUM AND IN DETAILS ANALYZE THE UNCERTAINTIES IN THE MEASUREMENTS.**

This experiment emphasizes rigorous measurement practices, uncertainty analysis, and their role in experimental physics.

---

# **PROCEDURE**

---

## **1. MATERIALS**

Prepare the following materials:

* A string (1 or 1.5 meters long)
* A small weight (e.g., bag of coins, sugar packet, or key chain)
* Stopwatch or smartphone timer
* Ruler or measuring tape

No calculation is needed in this step.

---

## **2. SETUP**

**Step-by-step:**

* Attach the weight to the string and fix the other end to a sturdy support.
* Measure the length of the pendulum $L$ from the suspension point to the center of the mass.
* Record the resolution $r$ of the ruler or tape. Calculate uncertainty in length:

$$
\Delta L = \frac{r}{2}
$$

> **Example:** If ruler resolution is 1 mm = 0.001 m:

$$
\Delta L = \frac{0.001}{2} = 0.0005 \, \text{m}
$$

**Python Code:**

```python
ruler_resolution = 0.001  # in meters
Delta_L = ruler_resolution / 2
```

---

## **3. DATA COLLECTION**

**Step-by-step:**

1. Displace the pendulum slightly (less than 15°) and release it.
2. Measure the time for 10 full oscillations $T_{10,i}$.
3. Repeat this process 10 times to collect 10 values.
4. Calculate the **mean** time for 10 oscillations:

$$
\bar{T}_{10} = \frac{1}{n} \sum_{i=1}^{n} T_{10,i}
$$

5. Compute the **standard deviation** of those 10 times:

$$
\sigma_T = \sqrt{ \frac{1}{n - 1} \sum_{i=1}^{n} \left( T_{10,i} - \bar{T}_{10} \right)^2 }
$$

6. Determine the **uncertainty in mean time**:

$$
\Delta T_{10} = \frac{\sigma_T}{\sqrt{n}}
$$

> Where $n = 10$

**Python Code:**

```python
import numpy as np

# Example data
T10_measurements = np.array([12.5, 12.4, 12.6, 12.5, 12.7, 12.6, 12.4, 12.5, 12.6, 12.5])

# Mean time for 10 oscillations
T10_mean = np.mean(T10_measurements)

# Standard deviation
sigma_T = np.std(T10_measurements, ddof=1)

# Uncertainty in the mean
n = len(T10_measurements)
Delta_T10 = sigma_T / np.sqrt(n)
```

---

