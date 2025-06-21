---
share_link: https://share.note.sx/0an5q8vo#YccF3JRgBF+bIVgPieEdZvhGoB62m0tf32sAkPGULOI
share_updated: 2025-06-21T17:59:24+08:00
---
# Case Study: Stokes' Theorem (2022 Exam, Q4) / 斯托克斯定理解析 (最终完整版)

> [!question] Problem Statement
> Let the surface S be the elliptical paraboloid $z=x^2+4y^2$ lying beneath the plane $z=1$. If the orientation of S is defined by taking the inner normal vector n to the surface, which has a positive k-component.
> Find the flux of $\nabla\times F$ across S in the direction n for the vector field $F=yi-xzj+xz^{2}k$.
> In other words, calculate:
> $$ \iint_{S} (\nabla \times \vec{F}) \cdot \vec{n} \, dS $$

---

## 核心困惑解析 (Analysis of Core Confusion)

### 1. "Flux of Curl" vs. "Flux"
> [!faq]- 这道题的 "flux" 为什么指的是旋度的通量？
> 
> 这里的关键词是 **flux of $\nabla \times \vec{F}$**。
> * 当看到求 **$\nabla \times \vec{F}$ 的通量**，应首先想到**斯托克斯定理**。
> * 当看到求 **$\vec{F}$ 的通量**，且曲面是**封闭**的，应首先想到**高斯散度定理**。
> 本题曲面不封闭，且求的是旋度的通量，是典型的斯托克斯定理应用场景。

### 2. "Inner normal vector" vs. "positive k-component"
> [!faq]- “Inner normal” 和 “positive k-component” 这两个描述似乎是矛盾的？
> 
> 这里的描述确实不严谨。对于碗口朝上的抛物面，内法向量的k分量应为负。在这种情况下，我们必须以更具体的数学指令为准：**"positive k-component" (k分量为正)**，这明确定义了法向量 $\vec{n}$ 的方向是**朝上的**。

---

## 解法一：斯托克斯定理 (Method 1: Stokes' Theorem) (推荐方法)

此方法将曲面积分转化为边界的环路积分：$\iint_S (\nabla \times \vec{F}) \cdot \vec{n} \, dS = \oint_C \vec{F} \cdot d\vec{r}$。

**Step 1: 确定边界曲线 $C$**
边界是椭圆 $x^2+4y^2 = 1$，位于平面 $z=1$上。

**Step 2: 确定环路方向**
法向量 $\vec{n}$ 朝上，根据右手法则，环路 $C$ 的方向为**逆时针**。

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
$$ \nabla \times \vec{F} = \langle x, -z^2, -z-1 \rangle $$

**Step 2: 参数化曲面 $S$ 并求法向量**
$$ \vec{r}(x,y) = \langle x, y, x^2+4y^2 \rangle $$
$$ \vec{n}\,dS = (\vec{r}_x \times \vec{r}_y) \,dA = \langle -2x, -8y, 1 \rangle \,dA $$

**Step 3: 计算点积 $(\nabla \times \vec{F}) \cdot (\vec{r}_x \times \vec{r}_y)$**
$$ = \langle x, -z^2, -z-1 \rangle \cdot \langle -2x, -8y, 1 \rangle $$
$$ = -2x^2 + 8yz^2 - z - 1 $$

**Step 4: 将 $z$ 替换为 $x,y$ 的表达式**
代入 $z=x^2+4y^2$：
$$ \text{Integrand} = -2x^2 + 8y(x^2+4y^2)^2 - (x^2+4y^2) - 1 $$
$$ = -3x^2 - 4y^2 - 1 + 8y(x^2+4y^2)^2 $$
所以，我们要计算的二重积分是：
$$ I = \iint_{D} (-3x^2 - 4y^2 - 1 + 8y(x^2+4y^2)^2) \, dA $$
其中积分区域 $D$ 是椭圆 $x^2+4y^2 \le 1$。

**Step 5: 使用椭圆坐标变换计算积分**
引入变换：$x = r\cos\theta$, $y = \frac{1}{2}r\sin\theta$。
此时，积分区域变为 $0 \le r \le 1, \quad 0 \le \theta \le 2\pi$。

> [!faq]- 雅可比行列式 (Jacobian) 是什么？
> 
> 在进行多重积分的坐标变换时（例如从直角坐标 $(x,y)$ 换到极坐标 $(r,\theta)$），面积微元 $dA$ 的关系并**不是**简单的 $dx\,dy = dr\,d\theta$。因为坐标系的“拉伸”或“扭曲”程度在不同点是不同的。
> 
> **雅可比行列式 $J$ 就是这个变换的“面积缩放因子”**。它告诉我们在某一点附近，新坐标系下的一个微小矩形区域，在旧坐标系下对应的面积是多少。
> 
> $$ dA = dx\,dy = |J| \,dr\,d\theta $$
> 对于二维变换 $x=g(r,\theta), y=h(r,\theta)$，雅可比行列式定义为：
> $$ J = \det \begin{pmatrix} \frac{\partial x}{\partial r} & \frac{\partial x}{\partial \theta} \\ \frac{\partial y}{\partial r} & \frac{\partial y}{\partial \theta} \end{pmatrix} $$
> **在本题中**，我们的变换是 $x=r\cos\theta, y=\frac{1}{2}r\sin\theta$，计算它的雅可比行列式：
> $$ J = \det \begin{pmatrix} \cos\theta & -r\sin\theta \\ \frac{1}{2}\sin\theta & \frac{1}{2}r\cos\theta \end{pmatrix} = \frac{1}{2}r\cos^2\theta - (-\frac{1}{2}r\sin^2\theta) = \frac{1}{2}r $$
> 所以，面积元 $dA = \frac{1}{2}r \,dr\,d\theta$。

**Step 6: 建立并计算新积分**
将被积函数用新坐标表示：
$$ -r^2(3\cos^2\theta + \sin^2\theta) - 1 + 4r^5\sin\theta $$
建立新积分：
$$ I = \int_{0}^{2\pi} \int_{0}^{1} [-r^2(3\cos^2\theta + \sin^2\theta) - 1 + 4r^5\sin\theta] \cdot (\frac{1}{2}r) \,dr\,d\theta $$
$$ = \frac{1}{2} \int_{0}^{2\pi} \left[ -\frac{r^4}{4}(3\cos^2\theta + \sin^2\theta) - \frac{r^2}{2} + \frac{4r^7}{7}\sin\theta \right]_{r=0}^{r=1} \,d\theta $$
$$ = \frac{1}{2} \int_{0}^{2\pi} \left( -\frac{1}{4}(3\cos^2\theta + \sin^2\theta) - \frac{1}{2} + \frac{4}{7}\sin\theta \right) \,d\theta $$
利用定积分性质 $\int_0^{2\pi}\sin\theta d\theta=0$, $\int_0^{2\pi}\cos^2\theta d\theta=\pi$, $\int_0^{2\pi}\sin^2\theta d\theta=\pi$：
$$ = \frac{1}{2} \left[ -\frac{1}{4}(3\pi + \pi) - \frac{1}{2}(2\pi) + 0 \right] = \frac{1}{2} [-\pi - \pi] = -\pi $$

**最终结论**:
两种方法都得到了相同的结果 $-\pi$。

---

## Part 2: How to Determine the Orientation? (如何判断方向正负？)

“正”和“负”方向是相对的，它取决于我们如何定义曲面。在考试中，主要有两种情况。

### 1. 曲面由函数 $z=f(x,y)$ 定义 (如此题)

这种情况最常见。我们通常将这个方程改写为 $G(x,y,z) = z - f(x,y) = 0$。

* **法向量的计算**: 法向量总是与梯度 $\nabla G$ 平行。
    $$ \nabla G = \langle -\frac{\partial f}{\partial x}, -\frac{\partial f}{\partial y}, 1 \rangle $$
* **判断正负方向**:
    * `✅` **向上 / 正向 (Upward / Positive Orientation)**:
        就是梯度 $\nabla G$ 本身的方向，因为它的k分量恒为 `+1`。
        对于本题 $f(x,y)=x^2+4y^2$，向上的法向量是 $\vec{n}_{up} = \langle -2x, -8y, 1 \rangle$。
    * `❌` **向下 / 负向 (Downward / Negative Orientation)**:
        就是梯度 $\nabla G$ 的反方向 $-\nabla G$。
        $$ -\nabla G = \langle \frac{\partial f}{\partial x}, \frac{\partial f}{\partial y}, -1 \rangle $$
        它的k分量恒为 `-1`。对于本题，向下的法向量是 $\vec{n}_{down} = \langle 2x, 8y, -1 \rangle$。

> [!faq]- 如何应对题目指令？
> 你只需要严格遵守题目的文字描述：
> * 如果题目说 **"positive k-component"** 或 **"upward"**，你就选择 $\vec{n}_{up}$。
> * 如果题目说 **"negative k-component"** 或 **"downward"**，你就选择 $\vec{n}_{down}$。
> * (本题中的 "inner normal" 是一个不严谨的描述，我们应以更精确的 "positive k-component" 为准。)

### 2. 曲面是一个封闭面 (Closed Surface)

对于像球面、立方体这样的封闭曲面，方向的定义更直观。

* `✅` **正向 (Positive Orientation)**: 指的是**向外 (outward)** 的法向量，即从实体区域内部指向外部。
* `❌` **负向 (Negative Orientation)**: 指的是**向内 (inward)** 的法向量。

在解题时，除非题目特别说明，我们默认的“通量”都是指**正向（向外）通量**。
[[取正还是取负]]