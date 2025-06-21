# Case Study: Stokes' Theorem (2022 Exam, Q4) / 斯托克斯定理解析

> [!question] Problem Statement
> Let the surface S be the elliptical paraboloid $z=x^2+4y^2$ lying beneath the plane $z=1$. If the orientation of S is defined by taking the inner normal vector n to the surface, which has a positive k-component.
> Find the flux of $\nabla\times F$ across S in the direction n for the vector field $F=yi-xzj+xz^{2}k$.
> In other words, calculate:
> $$ \iint_{S} (\nabla \times \vec{F}) \cdot \vec{n} \, dS $$

---

## 核心困惑解析 (Analysis of Core Confusion)

### 1. "Flux" 到底指什么？为什么不用高斯定理？

> [!faq]- 这道题的 "flux" 为什么指的是旋度的通量？
> 
> 你完全正确，这里的 "flux" 指的是 **flux of the curl** ($\nabla \times \vec{F}$)，即**旋度的通量**。
> 
> **这是一个关键的信号词**：
> * 当你看到求 **$\vec{F}$ 的通量**，并且曲面 $S$ 是**封闭**的，你应该首先想到**高斯散度定理**。
> * 当你看到求 **$\nabla \times \vec{F}$ 的通量**，你应该首先想到**斯托克斯定理**。
> 
> 本题要求计算 $\nabla \times \vec{F}$ 的通量，且曲面 $S$ (一个碗状的抛物面) **不是封闭的**，因此这道题是为斯托克斯定理量身定做的。

### 2. "Inner normal vector" 和 "positive k-component" 如何理解？

> [!faq]- “Inner normal” 和 “positive k-component” 这两个描述似乎是矛盾的？
> 
> 你的观察非常细致，这两个描述确实存在矛盾，这是题目出得不严谨的地方，但它也考察了你分辨主次信息的能力。
> 
> * 对于 $z=x^2+4y^2$ 这个“碗口朝上”的抛物面，通常我们认为指向碗内部（即z轴方向）的是**内法向量 (inner normal)**，它的k分量是**负的**。指向碗外部（远离z轴）的是**外法向量 (outer normal)**，它的k分量是**正的**。
> * 题目中同时给出了 "inner normal" 和 "positive k-component" 这两个条件。
> * **结论：** 在这种情况下，**我们必须以更具体、无歧义的指令为准**。"positive k-component" (k分量为正) 这个描述是明确的数学指令，它告诉我们法向量 $\vec{n}$ 的方向必须是**朝上的**。所以，我们忽略掉有歧义的 "inner normal" 文字，以法向量朝上为准。

---

## 解法一：斯托克斯定理 (Method 1: Stokes' Theorem) (推荐方法)

斯托克斯定理可以将一个（通常很复杂的）曲面积分，转化为一个（通常更简单的）环路积分。
$$ \iint_{S} (\nabla \times \vec{F}) \cdot \vec{n} \, dS = \oint_C \vec{F} \cdot d\vec{r} $$

**Step 1: Identify the Boundary Curve C (确定边界)**
边界曲线 $C$ 是曲面 $S$ (抛物面 $z=x^2+4y^2$) 和平面 $z=1$ 的交线。
$$ x^2+4y^2 = 1 $$
这是一条位于平面 $z=1$ 上的椭圆。

**Step 2: Determine the Orientation of C (确定环路方向)**
根据右手法则，当法向量 $\vec{n}$ 朝上时（大拇指朝上），环路 $C$ 的方向必须是**逆时针** (counter-clockwise)（从z轴正向往下看）。

**Step 3: Parameterize the Curve C (参数化曲线)**
对于椭圆 $x^2+(2y)^2=1$，我们可以进行如下参数化：
* $x = \cos t$
* $2y = \sin t \implies y = \frac{1}{2}\sin t$
* $z = 1$
所以，路径的参数方程为：
$$ \vec{r}(t) = (\cos t)\vec{i} + (\frac{1}{2}\sin t)\vec{j} + (1)\vec{k}, \quad t \in [0, 2\pi] $$

**Step 4: Calculate the Line Integral (计算线积分)**
* 计算 $d\vec{r}$:
    $$ d\vec{r} = \vec{r}'(t)dt = (-\sin t)\vec{i} + (\frac{1}{2}\cos t)\vec{j} + (0)\vec{k} \, dt $$
* 将 $\vec{F} = y\vec{i} - xz\vec{j} + xz^2\vec{k}$ 用参数 $t$ 表示：
    $$ \vec{F}(\vec{r}(t)) = (\frac{1}{2}\sin t)\vec{i} - ((\cos t)(1))\vec{j} + ((\cos t)(1)^2)\vec{k} $$
    $$ = \langle \frac{1}{2}\sin t, -\cos t, \cos t \rangle $$
* 计算点积 $\vec{F} \cdot d\vec{r}$:
    $$ \vec{F} \cdot \vec{r}'(t) = (\frac{1}{2}\sin t)(-\sin t) + (-\cos t)(\frac{1}{2}\cos t) + (\cos t)(0) $$
    $$ = -\frac{1}{2}\sin^2 t - \frac{1}{2}\cos^2 t = -\frac{1}{2}(\sin^2 t + \cos^2 t) = -\frac{1}{2} $$
* 计算最终积分：
    $$ \oint_C \vec{F} \cdot d\vec{r} = \int_{0}^{2\pi} \left(-\frac{1}{2}\right) dt = -\frac{1}{2} [t]_0^{2\pi} = -\pi $$

  

## 解法二：直接计算曲面积分 (Method 2: Direct Surface Integral)

之前我们已经推导出，直接计算需要求解以下二重积分：

$$ \iint_{D} (-3x^2 - 4y^2 - 1 + 8y(x^2+4y^2)^2) \, dA $$

其中积分区域 $D$ 是由椭圆 $x^2+4y^2 \le 1$ 定义的。

  

> [!tip]
> 
> 之前的分析在这里止步，并错误地认为计算会很繁琐。实际上，对于椭圆区域的积分，使用**变形极坐标 (modified polar coordinates)** 是标准且高效的方法。

  

**Step 1: 坐标变换 (Coordinate Transformation)**

为了将椭圆区域 $x^2 + 4y^2 \le 1$ 变为一个简单的圆形区域，我们进行如下替换：

* 令 $x = r\cos\theta$

* 令 $2y = r\sin\theta \implies y = \frac{1}{2}r\sin\theta$

通过这个变换，原区域 $x^2+(2y)^2 \le 1$ 就变成了 $r^2\cos^2\theta + r^2\sin^2\theta \le 1$，即 $r^2 \le 1$。

新的积分限为：

$$ 0 \le r \le 1 \quad \text{and} \quad 0 \le \theta \le 2\pi $$

  

**Step 2: 计算雅可比行列式 (Jacobian)**

面积微元 $dA = dx\,dy$ 需要转换为 $dr\,d\theta$。它们之间的换算关系由雅可比行列式 $|J|$ 决定。

$$ J = \begin{vmatrix} \frac{\partial x}{\partial r} & \frac{\partial x}{\partial \theta} \\ \frac{\partial y}{\partial r} & \frac{\partial y}{\partial \theta} \end{vmatrix} = \begin{vmatrix} \cos\theta & -r\sin\theta \\ \frac{1}{2}\sin\theta & \frac{1}{2}r\cos\theta \end{vmatrix} $$

$$ = (\cos\theta)(\frac{1}{2}r\cos\theta) - (-r\sin\theta)(\frac{1}{2}\sin\theta) = \frac{1}{2}r(\cos^2\theta + \sin^2\theta) = \frac{1}{2}r $$

所以，$dA = \frac{1}{2}r \, dr\,d\theta$。

  

**Step 3: 转换被积函数**

我们将被积函数 $(-3x^2 - 4y^2 - 1 + 8y(x^2+4y^2)^2)$ 中的 $x, y$ 全部用 $r, \theta$ 替换。

注意到 $x^2+4y^2 = r^2$。

$$ -3(r\cos\theta)^2 - 4(\frac{1}{2}r\sin\theta)^2 - 1 + 8(\frac{1}{2}r\sin\theta)(r^2)^2 $$

$$ = -3r^2\cos^2\theta - r^2\sin^2\theta - 1 + 4r^5\sin\theta $$

  

**Step 4: 建立并计算新积分**

$$ \int_{0}^{2\pi} \int_{0}^{1} (-3r^2\cos^2\theta - r^2\sin^2\theta - 1 + 4r^5\sin\theta) \cdot (\frac{1}{2}r) \, dr\,d\theta $$

$$ = \frac{1}{2} \int_{0}^{2\pi} \int_{0}^{1} (-3r^3\cos^2\theta - r^3\sin^2\theta - r + 4r^6\sin\theta) \, dr\,d\theta $$

先对 $r$ 积分：

$$ \frac{1}{2} \int_{0}^{2\pi} \left[ -\frac{3}{4}r^4\cos^2\theta - \frac{1}{4}r^4\sin^2\theta - \frac{1}{2}r^2 + \frac{4}{7}r^7\sin\theta \right]_{r=0}^{r=1} \,d\theta $$

$$ = \frac{1}{2} \int_{0}^{2\pi} \left( -\frac{3}{4}\cos^2\theta - \frac{1}{4}\sin^2\theta - \frac{1}{2} + \frac{4}{7}\sin\theta \right) \,d\theta $$

再对 $\theta$ 积分。我们知道在一个周期 $[0, 2\pi]$ 内：

* $\int_{0}^{2\pi}\cos^2\theta \, d\theta = \pi$

* $\int_{0}^{2\pi}\sin^2\theta \, d\theta = \pi$

* $\int_{0}^{2\pi}\sin\theta \, d\theta = 0$

所以，积分为：

$$ \frac{1}{2} \left[ -\frac{3}{4}(\pi) - \frac{1}{4}(\pi) - \frac{1}{2}(2\pi) + \frac{4}{7}(0) \right] $$

$$ = \frac{1}{2} \left[ -(\frac{3}{4}+\frac{1}{4})\pi - \pi \right] = \frac{1}{2} [-\pi - \pi] = \frac{1}{2}(-2\pi) = -\pi $$

  

### 结论

直接计算曲面积分的结果是 **$-\pi$**，与使用斯托克斯定理得到的结果完全一致。您的直觉是正确的，这种方法在掌握了正确的坐标变换后，是完全可行的。