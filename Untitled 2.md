# Case Study: Lagrange Multipliers with Two Constraints (2022 Exam, Q2)

> [!question] Problem Statement
> Find the points on the curve defined by the intersection of $x^2 + y^2 = z$ and $x + y + z = 1$ that lie closest and farthest from the origin.

---

## 1. 建立数学模型 (Modeling the Problem)

* **目标函数 (Objective Function):** 我们要寻找离原点 $(0,0,0)$ 最近和最远的点。一个点 $(x,y,z)$ 到原点的距离是 $d = \sqrt{x^2+y^2+z^2}$。为了简化计算，我们通常优化距离的平方 $d^2$，这与优化 $d$ 的结果是等价的。所以，我们的目标函数是：
    $$ f(x,y,z) = x^2+y^2+z^2 $$
* **约束条件 (Constraints):** 点 $(x,y,z)$ 必须同时满足两个方程：
    1.  $g_1(x,y,z) = x^2+y^2-z = 0$  (点在抛物面上)
    2.  $g_2(x,y,z) = x+y+z-1 = 0$  (点在平面上)

## 2. 应用拉格朗日乘数法 (Applying the Method)

对于带两个约束条件的拉格朗日乘数法，其核心方程是：
$$ \nabla f = \lambda \nabla g_1 + \mu \nabla g_2 $$
其中 $\lambda$ 和 $\mu$ 是拉格朗日乘子。

**Step 1: 计算所有梯度 (Calculate Gradients)**
$$ \nabla f = \langle 2x, 2y, 2z \rangle $$
$$ \nabla g_1 = \langle 2x, 2y, -1 \rangle $$
$$ \nabla g_2 = \langle 1, 1, 1 \rangle $$

**Step 2: 建立方程组 (Set up the System of Equations)**
将梯度代入核心方程，我们得到一个包含5个方程和5个未知数 ($x,y,z,\lambda,\mu$) 的方程组：
1.  $$ 2x = \lambda(2x) + \mu(1) $$
2.  $$ 2y = \lambda(2y) + \mu(1) $$
3.  $$ 2z = \lambda(-1) + \mu(1) $$
4.  $$ x^2+y^2-z = 0 $$
5.  $$ x+y+z = 1 $$

## 3. 解方程组 (Solving the System)

这是本题计算的关键和难点。

* **从方程 (1) 和 (2) 入手**:
    $$ 2x(1-\lambda) = \mu $$
    $$ 2y(1-\lambda) = \mu $$
    这告诉我们 $2x(1-\lambda) = 2y(1-\lambda)$，即 $(2x-2y)(1-\lambda)=0$。
    这就引出了两种可能性：

* **Case A: $1-\lambda = 0 \implies \lambda=1$**
    如果 $\lambda=1$，那么 $\mu = 2x(1-1) = 0$。
    将 $\lambda=1, \mu=0$ 代入方程 (3)：
    $$ 2z = (1)(-1) + 0 \implies z = -1/2 $$
    将 $z=-1/2$ 代入方程 (4)：
    $$ x^2+y^2 = -1/2 $$
    这是一个矛盾的结论，因为实数的平方和不可能是负数。所以，这种情况被排除。

* **Case B: $2x-2y = 0 \implies x=y$**
    这是唯一的可能性。现在我们将这个结论代入约束方程中：
    * 代入方程 (4): $x^2+x^2-z=0 \implies z=2x^2$
    * 代入方程 (5): $x+x+z=1 \implies 2x+z=1$
    我们得到了一个关于 $x$ 和 $z$ 的简单方程组。将 $z=2x^2$ 代入 $2x+z=1$：
    $$ 2x + 2x^2 = 1 $$
    整理成标准二次方程形式：
    $$ 2x^2+2x-1=0 $$
    使用求根公式 $x = \frac{-b \pm \sqrt{b^2-4ac}}{2a}$：
    $$ x = \frac{-2 \pm \sqrt{2^2 - 4(2)(-1)}}{2(2)} = \frac{-2 \pm \sqrt{12}}{4} = \frac{-2 \pm 2\sqrt{3}}{4} = \frac{-1 \pm \sqrt{3}}{2} $$

**Step 3: 找到候选点 (Find the Candidate Points)**
我们找到了两个可能的 $x$ 值，因为 $y=x$ 且 $z=2x^2$，我们可以得到两个候选点：

* **Point 1**: $x_1 = \frac{-1+\sqrt{3}}{2}$
    $$ y_1 = \frac{-1+\sqrt{3}}{2} $$
    $$ z_1 = 2x_1^2 = 2\left(\frac{-1+\sqrt{3}}{2}\right)^2 = 2\left(\frac{1-2\sqrt{3}+3}{4}\right) = 2 - \sqrt{3} $$
    所以 $P_1 = \left( \frac{-1+\sqrt{3}}{2}, \frac{-1+\sqrt{3}}{2}, 2-\sqrt{3} \right)$

* **Point 2**: $x_2 = \frac{-1-\sqrt{3}}{2}$
    $$ y_2 = \frac{-1-\sqrt{3}}{2} $$
    $$ z_2 = 2x_2^2 = 2\left(\frac{-1-\sqrt{3}}{2}\right)^2 = 2\left(\frac{1+2\sqrt{3}+3}{4}\right) = 2 + \sqrt{3} $$
    所以 $P_2 = \left( \frac{-1-\sqrt{3}}{2}, \frac{-1-\sqrt{3}}{2}, 2+\sqrt{3} \right)$

## 4. 比较距离并得出结论 (Compare Distances and Conclude)

我们现在需要判断哪个点最近，哪个点最远。我们只需比较目标函数 $f=x^2+y^2+z^2$ 的值。利用约束条件 $z=x^2+y^2$，我们可以简化目标函数为 $f = z+z^2$。

* **对于 $P_1$**: $z_1 = 2-\sqrt{3} \approx 2-1.732 = 0.268$。这是一个较小的 $z$ 值。
* **对于 $P_2$**: $z_2 = 2+\sqrt{3} \approx 2+1.732 = 3.732$。这是一个较大的 $z$ 值。

由于函数 $f(z)=z+z^2$ 在 $z>0$ 时是增函数，所以 $z$ 值较小的 $P_1$ 对应的 $f$ 值较小，距离近；$z$ 值较大的 $P_2$ 对应的 $f$ 值较大，距离远。

> [!success] 最终答案
> * **最近点 (Closest Point)**: $$P_1 = \left( \frac{\sqrt{3}-1}{2}, \frac{\sqrt{3}-1}{2}, 2-\sqrt{3} \right)$$
> * **最远点 (Farthest Point)**: $$P_2 = \left( -\frac{\sqrt{3}+1}{2}, -\frac{\sqrt{3}+1}{2}, 2+\sqrt{3} \right)$$