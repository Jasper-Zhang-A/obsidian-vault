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