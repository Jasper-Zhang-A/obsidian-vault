
# Solution for Exam Question 2023Q4(a)

### The Question

>Find the flux of the vector field $\vec{F}=yz\vec{j}+z^{2}\vec{k}$ outward through the surface S cut from the cylinder $y^{2}+z^{2}=1, z\ge0$, by the planes $x=0$ and $x=1$.

### Analysis and Strategy

The question asks for the outward flux of a vector field through a surface $S$. Let's analyze the surface $S$. It is described as being "cut from the cylinder $y^{2}+z^{2}=1, z\ge0$, by the planes $x=0$ and $x=1$". This surface is not just the curved wall of the half-cylinder; it also includes the flat end caps at $x=0$ and $x=1$. Therefore, $S$ is a **closed surface** that encloses a solid volume.

Since we need to find the outward flux through a closed surface, the **Divergence Theorem** is the most direct and efficient method. The theorem states:
$$
\iint_S \vec{F} \cdot \vec{n} \,d\sigma = \iiint_V (\nabla \cdot \vec{F}) \,dV
$$
This allows us to solve the problem by calculating a single volume integral instead of three separate surface integrals (one for the curved wall and one for each end cap).

---

### Step 1: Calculate the Divergence of F ($\nabla \cdot \vec{F}$)

The given vector field is $\vec{F} = 0\vec{i} + yz\vec{j} + z^2\vec{k}$. We find its divergence:
$$
\nabla \cdot \vec{F} = \frac{\partial P}{\partial x} + \frac{\partial Q}{\partial y} + \frac{\partial R}{\partial z}
$$
$$
\nabla \cdot \vec{F} = \frac{\partial}{\partial x}(0) + \frac{\partial}{\partial y}(yz) + \frac{\partial}{\partial z}(z^2) = 0 + z + 2z = 3z
$$

### Step 2: Set up the Volume Integral

Now we need to integrate the divergence, $3z$, over the volume $V$ enclosed by the surface $S$. The volume $V$ is the interior of the half-cylinder described by $y^2+z^2 \le 1$ with $z \ge 0$, between $x=0$ and $x=1$.

To evaluate this integral, it's easiest to use coordinates that match the geometry. We will use Cartesian coordinates for the $x$-axis and polar coordinates for the $yz$-plane.
Let:
* $x = x$
* $y = r \cos\phi$
* $z = r \sin\phi$

The bounds for these coordinates are:
* $0 \le x \le 1$ (from the planes)
* $0 \le r \le 1$ (from the cylinder equation $y^2+z^2 = r^2 \le 1$)
* $0 \le \phi \le \pi$ (since $z=r\sin\phi \ge 0$)

The differential volume element is $dV = dx \, r \, dr \, d\phi$. The integrand is $3z = 3r\sin\phi$.
The integral becomes:
$$
\iiint_V 3z \,dV = \int_0^1 \int_0^\pi \int_0^1 (3r\sin\phi) \, r \, dr \, d\phi \, dx
$$

### Step 3: Evaluate the Integral

We solve the integral iteratively, from the inside out.
$$
\int_0^1 \int_0^\pi \int_0^1 3r^2\sin\phi \, dr \, d\phi \, dx
$$
1.  **Integrate with respect to $r$:**
    $$
    \int_0^1 3r^2 \sin\phi \,dr = [r^3 \sin\phi]_0^1 = (1)^3\sin\phi - (0)^3\sin\phi = \sin\phi
    $$
2.  **Integrate with respect to $\phi$:**
    $$
    \int_0^\pi \sin\phi \,d\phi = [-\cos\phi]_0^\pi = (-\cos\pi) - (-\cos0) = -(-1) - (-1) = 1 + 1 = 2
    $$
3.  **Integrate with respect to $x$:**
    $$
    \int_0^1 2 \,dx = [2x]_0^1 = 2(1) - 2(0) = 2
    $$

### Step 4: Final Conclusion

By the Divergence Theorem, the total outward flux through the closed surface $S$ is equal to the value of the volume integral we just calculated.

The flux of the vector field $\vec{F}$ is 2.
