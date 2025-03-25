### **Mathematical Formulation of Projectile Motion**

#### **1. Governing Equations of Motion**  
Using **Newton’s Second Law**, considering only gravitational force (neglecting air resistance):

\[
F = ma = -mg \hat{y}
\]

This results in two differential equations:

- **Horizontal motion**:  
  \[
  \frac{d^2x}{dt^2} = 0
  \]

- **Vertical motion**:  
  \[
  \frac{d^2y}{dt^2} = -g
  \]

#### **2. Solving the Equations**  
Given initial conditions:  

- **Initial position**: \((x_0, y_0) = (0, y_0)\)  
- **Initial velocity**: \( v_0 \) at an angle \( \theta \)  
- **Velocity components**:  

  \[
  v_{0x} = v_0 \cos\theta, \quad v_{0y} = v_0 \sin\theta
  \]

The general solutions are:

\[
x(t) = v_0 \cos\theta \cdot t
\]

\[
y(t) = y_0 + v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
\]

#### **3. Time of Flight**  
The time of flight is found by solving \( y(t) = 0 \) (when the projectile returns to its initial height \( y_0 \)).

For **\( y_0 = 0 \)**:

\[
0 = v_0 \sin\theta \cdot t - \frac{1}{2} g t^2
\]

Solving for \( t \):

\[
t = \frac{2 v_0 \sin\theta}{g}
\]

For **\( y_0 \neq 0 \)**, solving the quadratic equation \( y(t) = 0 \):

\[
t = \frac{v_0 \sin\theta + \sqrt{(v_0 \sin\theta)^2 + 2g y_0}}{g}
\]

#### **4. Range Calculation**  
The **horizontal range \( R \)** is:

For **\( y_0 = 0 \)**:

\[
R = v_0 \cos\theta \cdot \frac{2 v_0 \sin\theta}{g} = \frac{v_0^2 \sin 2\theta}{g}
\]

For **\( y_0 \neq 0 \)**:

\[
R = v_0 \cos\theta \cdot t
\]

where \( t \) is given by the quadratic formula above.

#### **5. Maximum Height**  
The maximum height occurs when vertical velocity becomes zero (\( v_y = 0 \)):

\[
H = \frac{v_0^2 \sin^2\theta}{2g}
\]

For **\( y_0 \neq 0 \)**:

\[
H = y_0 + \frac{v_0^2 \sin^2\theta}{2g}
\]

#### **6. Optimal Launch Angle**  
The launch angle that maximizes the range for **\( y_0 = 0 \)** is:

\[
\theta_{\text{optimal}} = 45^\circ
\]

For **\( y_0 > 0 \)**, the optimal angle is slightly less than \( 45^\circ \), given by:

\[
\theta_{\text{optimal}} \approx 45^\circ - \frac{y_0}{v_0^2} \cdot k
\]

where \( k \) is a proportionality constant.

---

These equations provide a complete theoretical framework for projectile motion analysis. Would you like further modifications or additional explanations?
![alt text](image.png)