# Final Exam Analysis / 期末考试卷解析 (Corrected Version)

## Q1: Calculate Partial Derivatives (计算偏导数)

### Part (a) - Corrected

> [!question] Problem Statement
> Find $\frac{\partial^2 z}{\partial x^2}$ and $\frac{\partial^2 z}{\partial y^2}$ if $z = \frac{x^2+y^2}{xy}$.

**1. 分析与化简 (Analysis and Simplification)**
这道题要求二阶偏导数。直接对分式进行两次求导会非常繁琐。一个高效的技巧是先将函数 $z$ 化简。
$$ z = \frac{x^2+y^2}{xy} = \frac{x^2}{xy} + \frac{y^2}{xy} = \frac{x}{y} + \frac{y}{x} $$
将 $z$ 写为 $xy^{-1} + yx^{-1}$ 的形式，求导会变得非常简单。

**2. 求解一阶偏导数 (First Partial Derivatives)**
* **对 $x$ 求偏导**:
    $$ \frac{\partial z}{\partial x} = \frac{\partial}{\partial x} (xy^{-1} + yx^{-1}) = y^{-1} + y(-1x^{-2}) = \frac{1}{y} - \frac{y}{x^2} $$
* **对 $y$ 求偏导**:
    $$ \frac{\partial z}{\partial y} = \frac{\partial}{\partial y} (xy^{-1} + yx^{-1}) = x(-1y^{-2}) + x^{-1} = -\frac{x}{y^2} + \frac{1}{x} $$

**3. 求解二阶偏导数 (Second Partial Derivatives)**
* **求解 $\frac{\partial^2 z}{\partial x^2}$**:
    $$ \frac{\partial^2 z}{\partial x^2} = \frac{\partial}{\partial x}\left(\frac{\partial z}{\partial x}\right) = \frac{\partial}{\partial x}\left(\frac{1}{y} - yx^{-2}\right) $$
    $$ = 0 - y(-2x^{-3}) = \frac{2y}{x^3} $$
* **求解 $\frac{\partial^2 z}{\partial y^2}$**:
    $$ \frac{\partial^2 z}{\partial y^2} = \frac{\partial}{\partial y}\left(\frac{\partial z}{\partial y}\right) = \frac{\partial}{\partial y}\left(-\frac{x}{y^2} + \frac{1}{x}\right) $$
    $$ = \frac{\partial}{\partial y}(-xy^{-2} + \frac{1}{x}) = -x(-2y^{-3}) + 0 = \frac{2x}{y^3} $$

**最终答案 (Part a):**
$$ \frac{\partial^2 z}{\partial x^2} = \frac{2y}{x^3} \quad \text{and} \quad \frac{\partial^2 z}{\partial y^2} = \frac{2x}{y^3} $$

### Part (b) - Corrected

> [!question] Problem Statement
> Find $\frac{\partial f}{\partial y}(x(y,z),y,z)\bigg|_{(1,1,1)}$, where $f(x,y,z)=x^3y^2z$ and the function $x=x(y,z)$ is determined by the equation $x+y+z-3+e^{-3} = e^{-(x+y+z)}$.

**1. 分析 (Analysis)**
这依然是一个**链式法则 (Chain Rule)** 问题，因为 $f$ 的变量 $x$ 又是 $y$ 和 $z$ 的函数。我们要求 $f$ 对 $y$ 的全偏导。

**2. 链式法则公式**
当我们将 $z$ 视为常数，对 $y$ 求偏导时，链式法则的公式为：
$$ \frac{\partial f}{\partial y} = \frac{\partial f}{\partial x}\frac{\partial x}{\partial y} + \frac{\partial f}{\partial y} $$
> [!warning]
> 请注意，公式右边的 $\frac{\partial f}{\partial x}$ 和 $\frac{\partial f}{\partial y}$ 指的是将 $x,y,z$ 均看作独立变量时的“显式”偏导数。

**3. 计算各个部分**
* **计算 $f$ 的显式偏导数**:
    * $$ \frac{\partial f}{\partial x} = 3x^2y^2z $$
    * $$ \frac{\partial f}{\partial y} = 2x^3yz $$
* **使用隐函数求导计算 $\frac{\partial x}{\partial y}$**:
    我们从约束方程 $x+y+z-3+e^{-3} - e^{-(x+y+z)} = 0$ 中求解。
    令 $F(x,y,z) = x+y+z-3+e^{-3} - e^{-(x+y+z)}$。
    根据公式 $\frac{\partial x}{\partial y} = - \frac{F_y}{F_x}$。
    * $$ F_y = \frac{\partial F}{\partial y} = 1 - e^{-(x+y+z)} \cdot (-1) = 1 + e^{-(x+y+z)} $$
    * $$ F_x = \frac{\partial F}{\partial x} = 1 - e^{-(x+y+z)} \cdot (-1) = 1 + e^{-(x+y+z)} $$
    * 因此：
        $$ \frac{\partial x}{\partial y} = - \frac{1 + e^{-(x+y+z)}}{1 + e^{-(x+y+z)}} = -1 $$
        这是一个常数！

**4. 在点 $(1,1,1)$ 求值**
* $$ \frac{\partial f}{\partial x}\bigg|_{(1,1,1)} = 3(1)^2(1)^2(1) = 3 $$
* $$ \frac{\partial f}{\partial y}\bigg|_{(1,1,1)} = 2(1)^3(1)(1) = 2 $$
* $$ \frac{\partial x}{\partial y}\bigg|_{(1,1,1)} = -1 $$

**5. 代入链式法则公式**
$$ \frac{\partial f}{\partial y}\bigg|_{(1,1,1)} = \left(\frac{\partial f}{\partial x}\bigg|_{(1,1,1)}\right) \cdot \left(\frac{\partial x}{\partial y}\bigg|_{(1,1,1)}\right) + \left(\frac{\partial f}{\partial y}\bigg|_{(1,1,1)}\right) $$
$$ = (3) \cdot (-1) + (2) = -3 + 2 = -1 $$

**最终答案 (Part b):**
$$ \frac{\partial f}{\partial y}\bigg|_{(1,1,1)} = -1 $$



## Q2: Application of Partial Derivatives (偏导数的应用)

### Part (a): Largest Box in an Ellipsoid

> [!question] Problem Statement
> Find the volume of the largest rectangular box that can be included in the ellipsoid $\frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1$, where $a,b,c > 0$ are given constants.

**1. 分析 (Analysis)**
这是一个在约束条件下求函数最大值的经典问题，我们使用**拉格朗日乘数法 (Lagrange Multipliers)**。

**2. 建立数学模型 (Modeling the Problem)**
* **目标函数 (Objective Function):** 我们最大化函数 $f(x,y,z) = xyz$ (代表了八分之一的体积)。
* **约束条件 (Constraint):** $g(x,y,z) = \frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} - 1 = 0$。

**3. 求解 (Solving)**
通过建立方程组 $\nabla f = \lambda \nabla g$ 并结合约束条件，可以解出：
$$ x = \frac{a}{\sqrt{3}}, \quad y = \frac{b}{\sqrt{3}}, \quad z = \frac{c}{\sqrt{3}} $$

**4. 计算最大体积 (Calculate Maximum Volume)**
长方体的总体积是 $V = 8xyz$。
$$ V_{max} = 8 \left(\frac{a}{\sqrt{3}}\right) \left(\frac{b}{\sqrt{3}}\right) \left(\frac{c}{\sqrt{3}}\right) = \frac{8abc}{3\sqrt{3}} $$

### Part (b): Tangent Plane Containing a Line

> [!question] Problem Statement
> Find the points on the surface $3x^2 + y^2 - z^2 = 27$ where the tangent planes there contain the line given by the intersection of $10x + 2y - 2z = 27$ and $x + y - z = 0$. Then write out the equations of the tangent planes.

#### **核心逻辑：如何锁定满足条件的点 $P_0(x_0,y_0,z_0)$**

我们需要找到一个点 $P_0$，这个点必须同时满足三个几何条件：
1.  **点在曲面上**：$P_0$ 的坐标满足曲面方程。
2.  **法向量垂直方向向量**：在 $P_0$ 点的切平面的法向量 $\vec{n}$，必须与给定直线的方向向量 $\vec{d}$ 垂直。
3.  **平面包含直线上一点**：切平面必须穿过给定直线上的任意一个点。

#### **Step 1: 提取关键向量和点**
* **曲面函数**: $f(x,y,z) = 3x^2 + y^2 - z^2 - 27$
* **切平面法向量 $\vec{n}$**: $\vec{n} = \nabla f(P_0) = \langle 6x_0, 2y_0, -2z_0 \rangle$
* **直线的方向向量 $\vec{d}$**:
    $$ \vec{d} = \langle 10, 2, -2 \rangle \times \langle 1, 1, -1 \rangle = \langle 0, 8, 8 \rangle $$
    我们可以取其平行向量简化计算：$\vec{d}_{simple} = \langle 0, 1, 1 \rangle$。
* **直线上的一点 $P_L$**:
    令 $z=0$，解方程组 $10x+2y=27$ 和 $x+y=0$，得到 $P_L = (27/8, -27/8, 0)$。

#### **Step 2: 利用“向量垂直”条件简化问题**
我们应用条件2：$\vec{n} \cdot \vec{d}_{simple} = 0$。
$$ \langle 6x_0, 2y_0, -2z_0 \rangle \cdot \langle 0, 1, 1 \rangle = 0 $$
$$ (6x_0)(0) + (2y_0)(1) + (-2z_0)(1) = 0 $$
$$ 2y_0 - 2z_0 = 0 \implies y_0 = z_0 $$
> [!tip]
> 这是一个关键的简化！我们现在知道，我们要找的点的 $y$ 坐标和 $z$ 坐标是相等的。

#### **Step 3: 利用“点在曲面”条件进一步简化**
我们应用条件1，并将 $y_0 = z_0$ 代入曲面方程：
$$ 3x_0^2 + y_0^2 - z_0^2 = 27 $$
$$ 3x_0^2 + y_0^2 - (y_0)^2 = 27 $$
$$ 3x_0^2 = 27 \implies x_0^2 = 9 \implies x_0 = \pm 3 $$
> [!success]
> 重大突破！我们已经确定了满足条件的点的 $x$ 坐标只有两种可能：$3$ 或 $-3$。

#### **Step 4: 利用“平面过点”条件求解最终坐标**
现在我们只剩下 $y_0$ (以及等于它的 $z_0$) 未知。我们应用条件3来建立 $x_0$ 和 $y_0$ 之间的关系。
切平面方程是：
$$ 6x_0(x-x_0) + 2y_0(y-y_0) - 2z_0(z-z_0) = 0 $$
因为 $y_0=z_0$，方程变为：
$$ 3x_0(x-x_0) + y_0(y-y_0) - y_0(z-y_0) = 0 $$
把直线上的点 $P_L(27/8, -27/8, 0)$ 代入 $(x,y,z)$:
$$ 3x_0(\frac{27}{8}-x_0) + y_0(-\frac{27}{8}-y_0) - y_0(0-y_0) = 0 $$
$$ \frac{81x_0}{8} - 3x_0^2 - \frac{27y_0}{8} - y_0^2 + y_0^2 = 0 $$
$$ \frac{81x_0}{8} - \frac{27y_0}{8} = 3x_0^2 $$
两边同乘以8，再除以3：
$$ 27x_0 - 9y_0 = 8x_0^2 \implies 9y_0 = 27x_0 - 8x_0^2 $$

#### **Step 5: 求解点的具体坐标**
我们现在将 $x_0 = \pm 3$ 代入上面的关系式。
* **当 $x_0 = 3$**:
    $$ 9y_0 = 27(3) - 8(3)^2 = 81 - 72 = 9 \implies y_0 = 1 $$
    因为 $z_0=y_0$，所以 $z_0=1$。
    **第一个点是 $P_1 = (3,1,1)$**。
* **当 $x_0 = -3$**:
    $$ 9y_0 = 27(-3) - 8(-3)^2 = -81 - 72 = -153 \implies y_0 = -17 $$
    因为 $z_0=y_0$，所以 $z_0=-17$。
    **第二个点是 $P_2 = (-3,-17,-17)$**。

#### **Step 6: 写出切平面方程 (作为收尾)**
* **在点 $P_1(3,1,1)$**:
    法向量 $\vec{n} = \langle 18, 2, -2 \rangle$。
    平面方程：$18(x-3)+2(y-1)-2(z-1)=0 \implies 9x+y-z=27$。
* **在点 $P_2(-3,-17,-17)$**:
    法向量 $\vec{n} = \langle -18, -34, 34 \rangle$。
    平面方程：$-18(x+3)-34(y+17)+34(z+17)=0 \implies 9x+17y-17z=-27$。



## Q3: Calculate Multiple Integrals (计算多重积分)

### Part (a)

> [!question] Problem Statement
> Calculate the integral $I = \iint_D \sin\left(\frac{\pi x}{2y}\right) dx dy$, where D is the plane region bounded by the curve $y=\sqrt{x}$ and the lines $y=x$ and $y=2$.

**1. 分析与画图 (Analysis and Sketch)**
* **边界**:
    1.  $y=\sqrt{x} \implies x=y^2$ (开口向右的抛物线)
    2.  $y=x$ (过原点的直线)
    3.  $y=2$ (水平直线)
* **交点**:
    * $y=x$ 和 $y=\sqrt{x}$ 的交点是 $(0,0)$ 和 $(1,1)$。
    * $y=2$ 和 $y=x$ 的交点是 $(2,2)$。
    * $y=2$ 和 $y=\sqrt{x}$ 的交点是 $(4,2)$。
* **积分区域 D**: 这三条线围成的区域是一个在第一象限的图形，其 $y$ 坐标范围是 $1 \le y \le 2$。在此范围内，$y^2 > y$ (例如当 $y=2$ 时，$x=4 > x=2$)，所以抛物线 $x=y^2$ 在直线 $x=y$ 的右侧。
    * **上边界**: $y=2$
    * **下边界**: 点 $(1,1)$
    * **左边界**: $x=y$
    * **右边界**: $x=y^2$

**2. 选择积分顺序 (Choose Order of Integration)**
被积函数是 $\sin(\frac{\pi x}{2y})$。如果先对 $y$ 积分，会非常困难。因此，我们选择先对 $x$ 积分 (将 $y$ 视为常数)，即采用 $dx\,dy$ 的顺序。

**3. 建立并计算积分 (Set up and Evaluate)**
根据我们对区域的分析，积分限为：
$$ I = \int_{1}^{2} \int_{y}^{y^2} \sin\left(\frac{\pi x}{2y}\right) \,dx \,dy $$
* **计算内层积分 (对 $x$)**:
    $$ \int_{y}^{y^2} \sin\left(\frac{\pi x}{2y}\right) \,dx = \left[ -\frac{2y}{\pi} \cos\left(\frac{\pi x}{2y}\right) \right]_{x=y}^{x=y^2} $$
    $$ = \left(-\frac{2y}{\pi}\cos\left(\frac{\pi y^2}{2y}\right)\right) - \left(-\frac{2y}{\pi}\cos\left(\frac{\pi y}{2y}\right)\right) $$
    $$ = -\frac{2y}{\pi}\cos\left(\frac{\pi y}{2}\right) + \frac{2y}{\pi}\cos\left(\frac{\pi}{2}\right) $$
    $$ = -\frac{2y}{\pi}\cos\left(\frac{\pi y}{2}\right) + 0 = -\frac{2y}{\pi}\cos\left(\frac{\pi y}{2}\right) $$
* **计算外层积分 (对 $y$)**:
    $$ I = \int_{1}^{2} -\frac{2y}{\pi}\cos\left(\frac{\pi y}{2}\right) \,dy $$
    这需要使用**分部积分法 (Integration by Parts)**: $\int u\,dv = uv - \int v\,du$。
    * 令 $u = -\frac{2y}{\pi}$, $dv = \cos(\frac{\pi y}{2})dy$
    * 则 $du = -\frac{2}{\pi}dy$, $v = \frac{2}{\pi}\sin(\frac{\pi y}{2})$
    $$ I = \left[ \left(-\frac{2y}{\pi}\right)\left(\frac{2}{\pi}\sin\frac{\pi y}{2}\right) \right]_{1}^{2} - \int_{1}^{2} \left(\frac{2}{\pi}\sin\frac{\pi y}{2}\right) \left(-\frac{2}{\pi}\right) dy $$
    $$ = \left[ -\frac{4y}{\pi^2}\sin\left(\frac{\pi y}{2}\right) \right]_{1}^{2} + \frac{4}{\pi^2} \int_{1}^{2} \sin\left(\frac{\pi y}{2}\right) dy $$
    $$ = \left[ -\frac{4y}{\pi^2}\sin\left(\frac{\pi y}{2}\right) \right]_{1}^{2} + \frac{4}{\pi^2} \left[ -\frac{2}{\pi}\cos\left(\frac{\pi y}{2}\right) \right]_{1}^{2} $$
    $$ = \left[ -\frac{4y}{\pi^2}\sin\left(\frac{\pi y}{2}\right) - \frac{8}{\pi^3}\cos\left(\frac{\pi y}{2}\right) \right]_{1}^{2} $$
    代入上限 $y=2$: $(-\frac{8}{\pi^2}\sin(\pi) - \frac{8}{\pi^3}\cos(\pi)) = (0 - \frac{8}{\pi^3}(-1)) = \frac{8}{\pi^3}$
    代入下限 $y=1$: $(-\frac{4}{\pi^2}\sin(\frac{\pi}{2}) - \frac{8}{\pi^3}\cos(\frac{\pi}{2})) = (-\frac{4}{\pi^2}(1) - 0) = -\frac{4}{\pi^2}$
    $$ I = \left(\frac{8}{\pi^3}\right) - \left(-\frac{4}{\pi^2}\right) = \frac{8}{\pi^3} + \frac{4}{\pi^2} $$

### Part (b)

> [!question] Problem Statement
> Calculate the integral $I = \iint_D \text{sgn}(y-x^2) \,dx\,dy$, where $D = \{(x,y) | x^2+y^2 \le 2\}$ and sgn is the sign function.

**1. 分析 (Analysis)**
* **符号函数 (Sign function)**:
    $$ \text{sgn}(u) = \begin{cases} 1, & u>0 \\ 0, & u=0 \\ -1, & u<0 \end{cases} $$
* **被积函数**: $\text{sgn}(y-x^2)$ 的值取决于点 $(x,y)$ 是在抛物线 $y=x^2$ 的上方、上方还是下方。
* **积分区域 D**: 是一个以原点为中心，半径为 $\sqrt{2}$ 的圆盘。
* **积分的几何意义**:
    $$ I = \iint_D \text{sgn}(y-x^2) dA = \iint_{D_1} (1) \,dA + \iint_{D_2} (-1) \,dA + \iint_{D_3} (0) \,dA $$
    其中 $D_1$ 是 $y>x^2$ 的区域，$D_2$ 是 $y<x^2$ 的区域，$D_3$ 是 $y=x^2$ 的曲线。
    $$ I = \text{Area}(D_1) - \text{Area}(D_2) $$

**2. 寻找交点并建立积分**
我们需要计算抛物线 $y=x^2$ 和圆 $x^2+y^2=2$ 的交点。
$$ y + y^2 = 2 \implies y^2+y-2=0 \implies (y+2)(y-1)=0 $$
因为 $y=x^2 \ge 0$，所以我们取 $y=1$。当 $y=1$ 时，$x^2=1 \implies x=\pm 1$。
交点为 $(-1,1)$ 和 $(1,1)$。

**3. 计算区域面积**
我们计算区域 $D_1$ (圆内且在抛物线上方) 的面积。
$$ \text{Area}(D_1) = \int_{-1}^{1} (y_{\text{upper}} - y_{\text{lower}}) \,dx = \int_{-1}^{1} (\sqrt{2-x^2} - x^2) \,dx $$
* $\int_{-1}^{1} (-x^2) dx = \left[-\frac{x^3}{3}\right]_{-1}^{1} = -\frac{1}{3} - \frac{1}{3} = -\frac{2}{3}$。
* $\int_{-1}^{1} \sqrt{2-x^2} dx$ 是一个半径为 $\sqrt{2}$ 的圆被弦 $y=1$ 截下的上方弓形的面积，加上一个 $2 \times 1$ 的矩形面积。这个积分也可以用三角代换求解，结果为 $\frac{\pi}{2}+1$。
* $\text{Area}(D_1) = (\frac{\pi}{2}+1) - \frac{2}{3} = \frac{\pi}{2} + \frac{1}{3}$。

**4. 计算最终结果**
* 圆的总面积是 $\pi(\sqrt{2})^2 = 2\pi$。
* $\text{Area}(D_2) = \text{Total Area} - \text{Area}(D_1) = 2\pi - (\frac{\pi}{2}+\frac{1}{3}) = \frac{3\pi}{2} - \frac{1}{3}$。
* $I = \text{Area}(D_1) - \text{Area}(D_2) = (\frac{\pi}{2}+\frac{1}{3}) - (\frac{3\pi}{2}-\frac{1}{3}) = -\pi + \frac{2}{3}$。


> [!tip] My Original Idea / 我的想法：用对称性来做
> 
> 我的思路是利用对称性。我知道 `sgn` 函数会把积分区域分成三块：$y>x^2$（值为+1），$y<x^2$（值为-1），以及 $y=x^2$（值为0）。
> 
> 所以，整个积分就等于 **(上方区域的面积) 减去 (下方区域的面积)**。
> 
> 这个思路是完全正确的！这道题的本质就是一个几何问题，而不是一个复杂的函数积分问题。如果在计算中出错了，问题一定出在计算面积的环节。

---

## Correct Solution: The Area Subtraction Method / 正确解法：面积相减法

### Step 1: Deconstruct the Integral (解构积分)

根据符号函数 `sgn` 的定义，我们可以把原积分拆解为：
$$ I = \iint_{y>x^2, D} (1) \,dA + \iint_{y<x^2, D} (-1) \,dA + \iint_{y=x^2, D} (0) \,dA $$
其中 $D$ 是半径为 $\sqrt{2}$ 的圆盘。
由于在一条线上积分为0，上式可以简化为：
$$ I = \text{Area}(D_1) - \text{Area}(D_2) $$
* $D_1$: 圆盘内，且在抛物线 $y=x^2$ **上方**的区域。
* $D_2$: 圆盘内，且在抛物线 $y=x^2$ **下方**的区域。

### Step 2: Find the Intersection Points (寻找交点)

为了计算面积，我们首先需要找到抛物线 $y=x^2$ 和圆 $x^2+y^2=2$ 的交点。
将 $x^2=y$ 代入圆的方程：
$$ y + y^2 = 2 \implies y^2+y-2=0 $$
因式分解得到：
$$ (y+2)(y-1)=0 $$
因为 $y=x^2 \ge 0$，所以我们只取 $y=1$。
当 $y=1$ 时，$x^2=1 \implies x=\pm 1$。
所以，交点是 **$(-1,1)$** 和 **$(1,1)$**。

### Step 3: Calculate the Area of the Upper Region $D_1$ (计算上方区域面积)

区域 $D_1$ 的面积可以通过定积分计算，其上边界是圆 $y=\sqrt{2-x^2}$，下边界是抛物线 $y=x^2$。
$$ \text{Area}(D_1) = \int_{-1}^{1} (y_{\text{upper}} - y_{\text{lower}}) \,dx = \int_{-1}^{1} (\sqrt{2-x^2} - x^2) \,dx $$
我们将这个积分拆成两部分来计算：
$$ \text{Area}(D_1) = \int_{-1}^{1} \sqrt{2-x^2} \,dx - \int_{-1}^{1} x^2 \,dx $$

* **计算第二部分 (抛物线下的面积)**:
    $$ \int_{-1}^{1} x^2 \,dx = \left[ \frac{x^3}{3} \right]_{-1}^{1} = \frac{1}{3} - (-\frac{1}{3}) = \frac{2}{3} $$

* **计算第一部分 (圆弧下的面积)**:
> [!faq]- 如何计算 $\int_{-1}^{1} \sqrt{2-x^2} \,dx$ ？
    > 
    > 这个积分需要使用**三角代换 (Trigonometric Substitution)**。
    > 令 $x = \sqrt{2}\sin\theta$，则 $dx = \sqrt{2}\cos\theta \,d\theta$。
    > 变换积分限：
    > * 当 $x=1$ 时, $\sin\theta = 1/\sqrt{2} \implies \theta = \pi/4$。
    > * 当 $x=-1$ 时, $\sin\theta = -1/\sqrt{2} \implies \theta = -\pi/4$。
    > 
    > $$ \int_{-\pi/4}^{\pi/4} \sqrt{2 - 2\sin^2\theta} \cdot (\sqrt{2}\cos\theta) \,d\theta $$
    > $$ = \int_{-\pi/4}^{\pi/4} \sqrt{2\cos^2\theta} \cdot (\sqrt{2}\cos\theta) \,d\theta = \int_{-\pi/4}^{\pi/4} 2\cos^2\theta \,d\theta $$
    > 使用半角公式 $2\cos^2\theta = 1+\cos(2\theta)$:
    > $$ = \int_{-\pi/4}^{\pi/4} (1+\cos(2\theta)) \,d\theta = \left[ \theta + \frac{1}{2}\sin(2\theta) \right]_{-\pi/4}^{\pi/4} $$
    > $$ = \left(\frac{\pi}{4} + \frac{1}{2}\sin(\frac{\pi}{2})\right) - \left(-\frac{\pi}{4} + \frac{1}{2}\sin(-\frac{\pi}{2})\right) $$
    > $$ = \left(\frac{\pi}{4} + \frac{1}{2}\right) - \left(-\frac{\pi}{4} - \frac{1}{2}\right) = \frac{\pi}{2} + 1 $$
* **组合得到 $\text{Area}(D_1)$**:
    $$ \text{Area}(D_1) = \left(\frac{\pi}{2} + 1\right) - \frac{2}{3} = \frac{\pi}{2} + \frac{1}{3} $$

### Step 4: Calculate the Final Integral Value (计算最终结果)

* **圆盘总面积**: $A_{total} = \pi r^2 = \pi (\sqrt{2})^2 = 2\pi$。
* **下方区域面积**: $\text{Area}(D_2) = A_{total} - \text{Area}(D_1) = 2\pi - \left(\frac{\pi}{2} + \frac{1}{3}\right) = \frac{3\pi}{2} - \frac{1}{3}$。
* **最终积分值**:
    $$ I = \text{Area}(D_1) - \text{Area}(D_2) = \left(\frac{\pi}{2} + \frac{1}{3}\right) - \left(\frac{3\pi}{2} - \frac{1}{3}\right) $$
    $$ = \frac{\pi}{2} - \frac{3\pi}{2} + \frac{1}{3} + \frac{1}{3} = -\pi + \frac{2}{3} $$




## Q4: Integration in Vector Fields (Corrected Analysis)

### Part (a): Surface Integral of a Scalar Function

> [!question] Problem Statement
> Compute the surface integral $\iint_S y \, d\sigma$, where $S$ is the portion of the cylindrical surface $x^2+y^2=4$ in the first octant ($x>0, y>0, z>0$) and bounded by the planes $z=0$, $z=x$, and $x=1$.

> [!faq]- 关于积分区域的重新讨论 (Re-discussion on the Integration Region)
> 
> **您的观点是对的**。题目中“bounded by the plane $x=1$”的表述存在歧义。
> * 我之前的理解是 $x \ge 1$ 的部分，这不太符合一般出题习惯。
> * 您的理解是 $x \le 1$ 的部分，即由 $x=0$ (y-z平面) 和 $x=1$ 所围住的区域，这是更标准、更合理的解释。
> 
> 我们现在按照您提出的、更标准的理解，即 **$0 \le x \le 1$** 的区域，来重新确定积分限并计算。

**1. 参数化曲面 $S$ (Parameterize the Surface)**
我们依然使用柱面坐标参数化曲面：
$$ \vec{r}(\theta, z) = (2\cos\theta)\vec{i} + (2\sin\theta)\vec{j} + z\vec{k} $$
面积元经计算仍为 $d\sigma = 2 \,d\theta\,dz$。

**2. 重新确定参数范围 (Re-determine the Limits)**
* **$\theta$的范围**: 根据我们新的理解，区域在第一象限，且 $0 \le x \le 1$。
    * 当 $x=0$ 时，$0=2\cos\theta \implies \theta = \pi/2$。
    * 当 $x=1$ 时，$1=2\cos\theta \implies \cos\theta=1/2 \implies \theta=\pi/3$。
    * 因此，角度 $\theta$ 的范围是 **$\pi/3 \le \theta \le \pi/2$**。
* **$z$的范围**: 保持不变，$0 \le z \le x = 2\cos\theta$。

**3. 重新计算积分 (Re-evaluate the Integral)**
$$ \iint_S y \, d\sigma = \int_{\pi/3}^{\pi/2} \int_{0}^{2\cos\theta} (2\sin\theta) \cdot (2 \,dz\,d\theta) $$
$$ = \int_{\pi/3}^{\pi/2} \int_{0}^{2\cos\theta} 4\sin\theta \,dz\,d\theta $$
* **先对 $z$ 积分**:
    $$ \int_{0}^{2\cos\theta} 4\sin\theta \,dz = 4\sin\theta [z]_{z=0}^{z=2\cos\theta} = 8\sin\theta\cos\theta = 4\sin(2\theta) $$
* **再对 $\theta$ 积分**:
    $$ \int_{\pi/3}^{\pi/2} 4\sin(2\theta) \,d\theta = [-2\cos(2\theta)]_{\pi/3}^{\pi/2} $$
    $$ = (-2\cos(\pi)) - (-2\cos(2\pi/3)) $$
    $$ = (-2)(-1) - (-2)(-\frac{1}{2}) = 2 - 1 = 1 $$

### Part (b): Line Integral Minimization (Corrected)

> [!question] Problem Statement
> Find the value of $a > 0$ such that the integral $\int_L (1+y^3)dx + (2x+y)dy$ takes its minimum value, where $L$ is the curve $y = a\sin x$ from the point O(0,0) to the point A($\pi$,0).

> [!warning]
> 我之前的回答中看错了题目中的 $y$ 的幂次，这里根据正确的 $1+y^3$ 和 $2x+y$ 进行重新计算。

**1. 参数化路径 $L$**
令 $x=t$，则 $y=a\sin t$。
$$ \vec{r}(t) = \langle t, a\sin t \rangle, \quad t \in [0, \pi] $$

**2. 计算线积分**
线积分 $\int_L M\,dx + N\,dy$。
* $M = 1+y^3 = 1+a^3\sin^3t$
* $N = 2x+y = 2t+a\sin t$
* $dx = dt$
* $dy = a\cos t \,dt$
代入积分，得到积分值 $I(a)$：
$$ I(a) = \int_{0}^{\pi} \left[ (1+a^3\sin^3t)dt + (2t+a\sin t)(a\cos t \,dt) \right] $$
$$ = \int_{0}^{\pi} (1 + a^3\sin^3t + 2at\cos t + a^2\sin t\cos t) \,dt $$
我们分项积分：
* $\int_0^\pi 1 \,dt = \pi$
* $\int_0^\pi 2at\cos t \,dt = -4a$  (此项与上次计算相同)
* $\int_0^\pi a^2\sin t\cos t \,dt = \frac{a^2}{2} \int_0^\pi \sin(2t) \,dt = 0$
* **计算新的一项**: $\int_0^\pi a^3\sin^3t \,dt$。
    我们知道 $\sin^3t = \sin t(1-\cos^2t) = \sin t - \sin t\cos^2t$。
    $$ \int (\sin t - \sin t\cos^2t) dt = -\cos t + \frac{\cos^3t}{3} $$
    $$ a^3 \left[ -\cos t + \frac{\cos^3t}{3} \right]_0^\pi = a^3 \left[ \left(-(-1) + \frac{(-1)^3}{3}\right) - \left(-1 + \frac{1^3}{3}\right) \right] $$
    $$ = a^3 \left[ \left(1 - \frac{1}{3}\right) - \left(- \frac{2}{3}\right) \right] = a^3 \left( \frac{2}{3} + \frac{2}{3} \right) = \frac{4}{3}a^3 $$

将各项结果相加，得到积分值 $I(a)$：
$$ I(a) = \frac{4}{3}a^3 - 4a + \pi $$

**3. 求 $I(a)$ 的最小值**
对 $I(a)$ 关于 $a$ 求导，并令其为0。
$$ I'(a) = \frac{d}{da}\left(\frac{4}{3}a^3 - 4a + \pi\right) = 4a^2 - 4 $$
令 $I'(a) = 0$：
$$ 4a^2 - 4 = 0 \implies a^2 = 1 $$
因为题目要求 $a>0$，所以 $a=1$。
(二阶导数 $I''(a) = 8a$，当 $a=1$ 时为正，确认是最小值点。)

**最终答案 (Corrected):**
(a) 1
(b) $a = 1$