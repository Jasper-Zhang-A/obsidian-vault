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


# Final Exam Analysis / 期末考试卷解析

## Q2: Application of Partial Derivatives (偏导数的应用)

### Part (a): Largest Box in an Ellipsoid

> [!question] Problem Statement
> Find the volume of the largest rectangular box that can be included in the ellipsoid $\frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1$, where $a,b,c > 0$ are given constants.

**1. 分析 (Analysis)**
这是一个在约束条件下求函数最大值的经典问题，我们使用**拉格朗日乘数法 (Lagrange Multipliers)**。

**2. 建立数学模型 (Modeling the Problem)**
* **目标函数 (Objective Function):** 我们要最大化一个内接长方体的体积。假设长方体的顶点在第一卦限是 $(x,y,z)$，那么它的长、宽、高分别是 $2x, 2y, 2z$。体积为 $V = 8xyz$。为简化计算，我们最大化函数：
    $$ f(x,y,z) = xyz $$
* **约束条件 (Constraint):** 长方体的顶点必须在椭球面上。
    $$ g(x,y,z) = \frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} - 1 = 0 $$

**3. 应用拉格朗日乘数法 (Applying the Method)**
核心方程是 $\nabla f = \lambda \nabla g$。
* **计算梯度**:
    * $$ \nabla f = \langle yz, xz, xy \rangle $$
    * $$ \nabla g = \langle \frac{2x}{a^2}, \frac{2y}{b^2}, \frac{2z}{c^2} \rangle $$
* **建立方程组**:
    1.  $$ yz = \lambda \frac{2x}{a^2} $$
    2.  $$ xz = \lambda \frac{2y}{b^2} $$
    3.  $$ xy = \lambda \frac{2z}{c^2} $$
    4.  $$ \frac{x^2}{a^2} + \frac{y^2}{b^2} + \frac{z^2}{c^2} = 1 $$

**4. 解方程组 (Solving the System)**
将方程 (1), (2), (3) 分别乘以 $x, y, z$：
$$ xyz = \lambda \frac{2x^2}{a^2} \quad \implies \quad \frac{x^2}{a^2} = \frac{xyz}{2\lambda} $$
$$ xyz = \lambda \frac{2y^2}{b^2} \quad \implies \quad \frac{y^2}{b^2} = \frac{xyz}{2\lambda} $$
$$ xyz = \lambda \frac{2z^2}{c^2} \quad \implies \quad \frac{z^2}{c^2} = \frac{xyz}{2\lambda} $$
由此可知：
$$ \frac{x^2}{a^2} = \frac{y^2}{b^2} = \frac{z^2}{c^2} $$
将这个关系代入约束方程 (4)：
$$ \frac{x^2}{a^2} + \frac{x^2}{a^2} + \frac{x^2}{a^2} = 1 \implies 3\frac{x^2}{a^2} = 1 \implies x^2 = \frac{a^2}{3} \implies x = \frac{a}{\sqrt{3}} $$
同理可得：
$$ y = \frac{b}{\sqrt{3}}, \quad z = \frac{c}{\sqrt{3}} $$

**5. 计算最大体积 (Calculate Maximum Volume)**
$$ V_{max} = 8xyz = 8 \left(\frac{a}{\sqrt{3}}\right) \left(\frac{b}{\sqrt{3}}\right) \left(\frac{c}{\sqrt{3}}\right) = \frac{8abc}{3\sqrt{3}} $$

### Part (b): Tangent Plane Containing a Line

> [!question] Problem Statement
> Find the points on the surface $3x^2 + y^2 - z^2 = 27$ where the tangent planes there contain the line given by the intersection of $10x + 2y - 2z = 27$ and $x + y - z = 0$. Then write out the equations of the tangent planes.

**1. 分析 (Analysis)**
一个平面包含一条直线，必须满足两个条件：
1.  平面通过直线上的任意一个点。
2.  平面的法向量垂直于直线的方向向量。

**2. 提取关键向量和点**
* **曲面函数**: $f(x,y,z) = 3x^2 + y^2 - z^2 - 27$
* **切平面法向量 $\vec{n}$**: 是曲面在点 $P_0(x_0,y_0,z_0)$ 的梯度。
    $$ \vec{n} = \nabla f = \langle 6x_0, 2y_0, -2z_0 \rangle $$
* **直线的方向向量 $\vec{d}$**: 是定义直线的两个平面法向量的叉乘。
    $$ \vec{n}_1 = \langle 10, 2, -2 \rangle, \quad \vec{n}_2 = \langle 1, 1, -1 \rangle $$
    $$ \vec{d} = \vec{n}_1 \times \vec{n}_2 = \langle (2)(-1)-(-2)(1), (-2)(1)-(10)(-1), (10)(1)-(2)(1) \rangle = \langle 0, 8, 8 \rangle $$
    我们可以取其平行向量简化计算：$\vec{d} = \langle 0, 1, 1 \rangle$。
* **直线上的一点 $P_L$**: 我们令 $z=0$ 来求解。
    $$ 10x+2y=27 \quad \text{and} \quad x+y=0 \implies y=-x $$
    代入得 $10x - 2x = 27 \implies 8x=27 \implies x=27/8$。所以 $y=-27/8$。
    直线上的一点是 $P_L = (27/8, -27/8, 0)$。

**3. 建立方程组**
* **条件1**: 点 $P_0(x_0,y_0,z_0)$ 在曲面上。
    $$ 3x_0^2 + y_0^2 - z_0^2 = 27 $$
* **条件2**: 法向量与方向向量垂直，$\vec{n} \cdot \vec{d} = 0$。
    $$ \langle 6x_0, 2y_0, -2z_0 \rangle \cdot \langle 0, 1, 1 \rangle = 0 \implies 2y_0 - 2z_0 = 0 \implies y_0 = z_0 $$
* **条件3**: 直线上的点 $P_L$ 在切平面上。切平面方程为：$6x_0(x-x_0) + 2y_0(y-y_0) - 2z_0(z-z_0) = 0$。代入 $P_L$ 的坐标：
    $$ 6x_0(\frac{27}{8}-x_0) + 2y_0(-\frac{27}{8}-y_0) - 2z_0(0-z_0) = 0 $$
    结合 $y_0 = z_0$ 简化：
    $$ 6x_0(\frac{27}{8}-x_0) + 2y_0(-\frac{27}{8}-y_0) + 2y_0^2 = 0 $$
    $$ \frac{162x_0}{8} - 6x_0^2 - \frac{54y_0}{8} - 2y_0^2 + 2y_0^2 = 0 $$
    $$ \frac{81x_0}{4} - \frac{27y_0}{4} - 6x_0^2 = 0 \implies 81x_0 - 27y_0 -