# Case Study: Stokes' Theorem (2022 Exam, Q4) / 斯托克斯定理解析

> [!question] Problem Statement
> Let the surface S be the elliptical paraboloid $z=x^2+4y^2$ lying beneath the plane $z=1$. If the orientation of S is defined by taking the inner normal vector n to the surface, which has a positive k-component.
> Find the flux of $\nabla\times F$ across S in the direction n for the vector field $F=yi-xzj+xz^{2}k$.
> In other words, calculate:
> $$ \iint_{S} (\nabla \times \vec{F}) \cdot \vec{n} \, dS $$

---

## 解法一：斯托克斯定理 (Method 1: Stokes' Theorem) (推荐方法)

此方法将曲面积分转化为边界的环路积分：$\iint_S (\nabla \times \vec{F}) \cdot \vec{n} \, dS = \oint_C \vec{F} \cdot d\vec{r}$。

**Step 1: 确定边界曲线 $C$**
边界是抛物面 $z=x^2+4y^2$ 和平面 $z=1$ 的交线，即位于 $z=1$ 平面上的椭圆：
$$ x^2+4y^2 = 1 $$

**Step 2: 确定环路方向**
法向量 $\vec{n}$ 要求k分量为正（朝上），根据右手法则，环路 $C$ 的方向为**逆时针**。

**Step 3: 参数化曲线 $C$**
$$ \vec{r}(t) = \langle \cos t, \frac{1}{2}\sin t, 1 \rangle, \quad t \in [0, 2\pi] $$

**Step 4: 计算线积分**
* $d\vec{r} = \langle -\sin t, \frac{1}{2}\cos t, 0 \rangle dt$
* $\vec{F}(\vec{r}(t)) = \langle y, -xz, xz^2 \rangle = \langle \frac{1}{2}\sin t, -\cos t, \cos t \rangle$
* 点积 $\vec{F} \cdot d\vec{r} = (-\frac{1}{2}\sin^2 t - \frac{1}{2}\cos^2 t)dt = -\frac{1}{2}dt$
* 积分：
    $$ \oint_C \vec{F} \cdot d\vec{r} = \int_{0}^{2\pi} \left(-\frac{1}{2}\right) dt = -\pi $$

---

## 解法二：直接计算曲面积分 (Method 2: Direct Surface Integral) (完整推导过程)

此方法直接计算 $\iint_S (\nabla \times \vec{F}) \cdot \vec{n} \, dS$，计算量较大，但能得到相同结果。

**Step 1: 计算旋度 $\nabla \times \vec{F}$**
$$ \nabla \times \vec{F} = \nabla \times \langle y, -xz, xz^2 \rangle $$
$$ = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ y & -xz & xz^2 \end{vmatrix} $$
$$ = \vec{i}(\frac{\partial}{\partial y}(xz^2) - \frac{\partial}{\partial z}(-xz)) - \vec{j}(\frac{\partial}{\partial x}(xz^2) - \frac{\partial}{\partial z}(y)) + \vec{k}(\frac{\partial}{\partial x}(-xz) - \frac{\partial}{\partial y}(y)) $$
$$ = \langle x, -z^2, -z-1 \rangle $$

**Step 2: 参数化曲面 $S$ 并求法向量**
曲面为 $z=x^2+4y^2$，我们可以用 $x, y$ 作为参数：
$$ \vec{r}(x,y) = \langle x, y, x^2+4y^2 \rangle $$
其中参数 $(x,y)$ 的范围是椭圆区域 $D: x^2+4y^2 \le 1$。
求切向量并计算法向量：
$$ \vec{r}_x = \langle 1, 0, 2x \rangle $$
$$ \vec{r}_y = \langle 0, 1, 8y \rangle $$
$$ \vec{n}\,dS = (\vec{r}_x \times \vec{r}_y) \,dA = \langle -2x, -8y, 1 \rangle \,dA $$
该法向量的k分量为+1，朝上，符合题目要求。

**Step 3: 计算点积 $(\nabla \times \vec{F}) \cdot (\vec{r}_x \times \vec{r}_y)$**
这是将被积函数转换为 $x,y$ 的关键一步。
$$ (\nabla \times \vec{F}) \cdot (\vec{r}_x \times \vec{r}_y) = \langle x, -z^2, -z-1 \rangle \cdot \langle -2x, -8y, 1 \rangle $$
$$ = (x)(-2x) + (-z^2)(-8y) + (-z-1)(1) $$
$$ = -2x^2 + 8yz^2 - z - 1 $$

**Step 4: 将 $z$ 替换为 $x,y$ 的表达式**
为了能在 $xy$ 平面上积分，我们将曲面方程 $z=x^2+4y^2$ 代入上式：
$$ \text{Integrand} = -2x^2 + 8y(x^2+4y^2)^2 - (x^2+4y^2) - 1 $$
$$ = -3x^2 - 4y^2 - 1 + 8y(x^2+4y^2)^2 $$
至此，我们才推导出曲面积分等价于下面的二重积分：
$$ I = \iint_{D} (-3x^2 - 4y^2 - 1 + 8y(x^2+4y^2)^2) \, dA $$

**Step 5: 使用椭圆坐标变换计算积分**
引入变换：$x = r\cos\theta$, $y = \frac{1}{2}r\sin\theta$。
此时，积分区域变为 $0 \le r \le 1, \quad 0 \le \theta \le 2\pi$。
面积元 $dA = |J| \,dr\,d\theta = \frac{1}{2}r \,dr\,d\theta$。
将被积函数用新坐标表示：
$$ -r^2(3\cos^2\theta + \sin^2\theta) - 1 + 4r^5\sin\theta $$
建立新积分：
$$ I = \int_{0}^{2\pi} \int_{0}^{1} [-r^2(3\cos^2\theta + \sin^2\theta) - 1 + 4r^5\sin\theta] \cdot (\frac{1}{2}r) \,dr\,d\theta $$
$$ = \frac{1}{2} \int_{0}^{2\pi} \left[ -\frac{r^4}{4}(3\cos^2\theta + \sin^2\theta) - \frac{r^2}{2} + \frac{4r^7}{7}\sin\theta \right]_{r=0}^{r=1} \,d\theta $$
$$ = \frac{1}{2} \int_{0}^{2\pi} \left( -\frac{1}{4}(3\cos^2\theta + \sin^2\theta) - \frac{1}{2} + \frac{4}{7}\sin\theta \right) \,d\theta $$
利用定积分性质 $\int_0^{2\pi}\sin\theta d\theta=0$, $\int_0^{2\pi}\cos^2\theta d\theta=\pi$, $\int_0^{2\pi}\sin^2\theta d\theta=\pi$：
$$ = \frac{1}{2} \left[ -\frac{1}{4}(3\pi + \pi) - \frac{1}{2}(2\pi) + 0 \right] = \frac{1}{2} [-\pi - \pi] = -\pi $$

**最终结论**: 两种方法都得到了相同的结果 $-\pi$。