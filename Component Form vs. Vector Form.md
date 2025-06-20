## Problem: Circulation of a Vector Field (2024Q4b)

### The Question

>Find the circulation of the vector field $\vec{F}=(x^{2}+y)\vec{i}+(x+y)\vec{j}+(4y^{2}-z)\vec{k}$ around the circle C in which the plane $z=-y$ meets the sphere $x^{2}+y^{2}+z^{2}=4$, counterclockwise as viewed from above. 

---

### Method 1: Using the Vector Form of Stokes' Theorem

This method uses the vector form of Stokes' Theorem, which states that the circulation of a vector field along a closed loop is equal to the flux of its curl through any surface bounded by that loop.

$$\oint_C \vec{F} \cdot d\vec{r} = \iint_S (\nabla \times \vec{F}) \cdot \vec{n} \, d\sigma$$

#### Step 1: Calculate the Curl ($\nabla \times \vec{F}$)
First, we calculate the curl of the given vector field $\vec{F}=(x^{2}+y)\vec{i}+(x+y)\vec{j}+(4y^{2}-z)\vec{k}$.
$$
\nabla \times \vec{F} = 
\begin{vmatrix} 
\vec{i} & \vec{j} & \vec{k} \\
\frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\
x^2+y & x+y & 4y^2-z
\end{vmatrix}
$$
The components are:
* **i-component**: $\frac{\partial}{\partial y}(4y^2-z) - \frac{\partial}{\partial z}(x+y) = 8y - 0 = 8y$
* **j-component**: $\frac{\partial}{\partial z}(x^2+y) - \frac{\partial}{\partial x}(4y^2-z) = 0 - 0 = 0$
* **k-component**: $\frac{\partial}{\partial x}(x+y) - \frac{\partial}{\partial y}(x^2+y) = 1 - 1 = 0$

The resulting curl is:
$$\nabla \times \vec{F} = 8y\vec{i}$$

#### Step 2: Determine the Surface $S$ and its Normal Vector $\vec{n}$
The simplest surface $S$ bounded by the curve $C$ is the portion of the plane $z=-y$ that lies inside the sphere. We can write the plane's equation as $y+z=0$. A normal vector $\vec{n}$ to this plane is given by the gradient of $y+z$, which is $\vec{n}' = \vec{j}+\vec{k}$.

The problem specifies the curve is oriented "counterclockwise as viewed from above". By the right-hand rule, this implies the normal vector must have a positive $\vec{k}$ component. Our vector $\vec{n}' = \vec{j}+\vec{k}$ satisfies this condition, so we can use it to determine the orientation.

#### Step 3: Calculate the Dot Product $(\nabla \times \vec{F}) \cdot \vec{n}$
We now compute the dot product of the curl and the normal vector.
$$(\nabla \times \vec{F}) \cdot \vec{n} = (8y\vec{i}) \cdot (\vec{j}+\vec{k}) = (8y)(0) + (0)(1) + (0)(1) = 0$$

#### Step 4: Evaluate the Integral and Conclude
Since the integrand $(\nabla \times \vec{F}) \cdot \vec{n}$ is 0, the entire surface integral is 0.
$$\iint_S 0 \, d\sigma = 0$$
By Stokes' Theorem, the circulation is equal to this integral. Therefore, the circulation of $\vec{F}$ around the curve $C$ is 0.

---

### Method 2: Using the Component Form of Stokes' Theorem

This method uses the component form of the surface integral in Stokes' Theorem, which is mathematically equivalent to the vector form.

$$\oint_C \vec{F} \cdot d\vec{r} = \iint_S \left[ \left( \frac{\partial R}{\partial y} - \frac{\partial Q}{\partial z} \right) dy\,dz + \left( \frac{\partial P}{\partial z} - \frac{\partial R}{\partial x} \right) dz\,dx + \left( \frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} \right) dx\,dy \right]$$

#### Step 1: Calculate the Curl Components
Given $\vec{F}=(x^{2}+y)\vec{i}+(x+y)\vec{j}+(4y^{2}-z)\vec{k}$, we identify $P = x^2+y$, $Q = x+y$, and $R = 4y^2-z$. We calculate each coefficient in the formula:
* **Coefficient of $dy\,dz$**: $\frac{\partial R}{\partial y} - \frac{\partial Q}{\partial z} = 8y - 0 = 8y$
* **Coefficient of $dz\,dx$**: $\frac{\partial P}{\partial z} - \frac{\partial R}{\partial x} = 0 - 0 = 0$
* **Coefficient of $dx\,dy$**: $\frac{\partial Q}{\partial x} - \frac{\partial P}{\partial y} = 1 - 1 = 0$

#### Step 2: Simplify the Surface Integral
Substituting these components back into the formula simplifies the integral significantly:
$$\iint_S \left[ (8y) dy\,dz + (0) dz\,dx + (0) dx\,dy \right] = \iint_S 8y \, dy\,dz$$

#### Step 3: Evaluate the Integral(imporant!)
To evaluate $\iint_S 8y \, dy\,dz$, we consider the geometric meaning of the differential $dy\,dz$. It represents the area element of the surface $S$ projected onto the $yz$-plane.

Our surface $S$ is the plane $y+z=0$. This plane is parallel to the $x$-axis. When a surface that is parallel to the $x$-axis is projected onto the $yz$-plane, it collapses into a line segment. A line segment has **zero area**.

Alternatively, using the formal definition, $dy\,dz = (\vec{n} \cdot \vec{i})d\sigma$. From Method 1, we know the normal vector $\vec{n}$ is parallel to $\vec{j}+\vec{k}$. Therefore, $\vec{n} \cdot \vec{i} = 0$. This makes the integrand zero.

Since we are integrating over a region of zero area (the projection), the value of the integral is zero.
$$\iint_S 8y \, dy\,dz = 0$$

#### Step 4: Conclude
The result of the surface integral is 0. By Stokes' Theorem, the circulation is also 0.

***

