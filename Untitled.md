# Case Study: Flux & The Divergence Theorem (Assignment-10, Q2)

> [!question] Problem Statement
> Find the flux of the field $F(x,y,z)=z^{2}i+xj-3zk$ outward through the surface cut from the parabolic cylinder $z=4-y^{2}$ by the planes $x=0$, $x=1$, and $z=0$.
> $$ \text{Flux} = \iint_{S} \vec{F} \cdot \vec{n} \, dS $$

---

> [!warning] My Mistake / 我的错误分析
> 
> **我的思路**: 我第一遍做的时候，只考虑了顶部的抛物面 $S_{top}: z=4-y^2$，忽略了其他几个面。我当时想把这个曲面投影到 $xy$ 平面上，然后用公式 $\iint_R \frac{\vec{F} \cdot \nabla f}{|\nabla f \cdot \vec{k}|} dA$ 来计算。
> 
> **错误原因 (Root Cause):**
> 这个思路有两个核心问题：
> 
> 1.  **曲面不完整 (Incomplete Surface):** 题目要求计算“**outward flux**”（向外的通量）。“向外”这个词暗示着我们考虑的是一个**封闭实体**的**整个外表面**。题目描述的 “surface” 是由抛物柱面 $z=4-y^2$、底面 $z=0$、前平面 $x=1$ 和后平面 $x=0$ 共同围成的一个**封闭立体**的**所有外表面**。只计算顶部抛物面的通量，相当于只计算了“屋顶”的通量，而忽略了“地板”和“墙壁”的通量，所以得到的答案是不完整的。
> 2.  **方法不适用 (Incorrect Method Choice):** 你想用的投影法，是计算**单个、开放曲面**通量的标准方法之一。但当问题涉及到一个**封闭曲面**的**总通量**时，有一个强大得多的工具——**高斯散度定理 (Divergence Theorem)**。

---

## Correct Solution: Using the Divergence Theorem / 正确解法：使用高斯散度定理

### Step 1: Justify the Method (判断使用条件)
由于我们需要计算一个向量场穿过一个**封闭曲面 S** 的**向外总通量**，这完全符合高斯散度定理的应用条件。该定理可以将一个复杂的、需要对多个面分别计算的曲面积分，转化为一个相对简单的三重积分。
$$ \iint_{S} \vec{F} \cdot \vec{n} \, dS = \iiint_{D} (\nabla \cdot \vec{F}) \, dV $$
其中，$D$ 是由曲面 $S$ 包围的实体区域。

### Step 2: Calculate the Divergence of $\vec{F}$ (计算散度)
给定向量场 $\vec{F} = \langle z^2, x, -3z \rangle$。
$$ \nabla \cdot \vec{F} = \frac{\partial}{\partial x}(z^2) + \frac{\partial}{\partial y}(x) + \frac{\partial}{\partial z}(-3z) $$
$$ = 0 + 0 - 3 = -3 $$
> [!tip]
> 散度是一个常数，这是问题变得简单的关键信号！

### Step 3: Set up the Triple Integral (建立三重积分)
根据高斯散度定理，原积分变为：
$$ \text{Flux} = \iiint_{D} (-3) \, dV = -3 \iiint_{D} dV $$
这个式子告诉我们，总通量就等于 **-3 乘以区域 D 的体积**。

### Step 4: Determine the Limits of Integration to Find the Volume (确定积分限)
我们需要描述区域 $D$ 的边界：
* **$z$ 的范围**: 从底面 $z=0$ 到顶面 $z=4-y^2$。
    $$ 0 \le z \le 4-y^2 $$
* **$y$ 的范围**: 区域的底面在 $z=0$ 处，此时 $0 = 4-y^2 \implies y = \pm 2$。
    $$ -2 \le y \le 2 $$
* **$x$ 的范围**: 题目直接给出，从后平面 $x=0$ 到前平面 $x=1$。
    $$ 0 \le x \le 1 $$

### Step 5: Evaluate the Integral to Find the Volume (计算体积)
$$ \text{Volume} = \iiint_D dV = \int_{0}^{1} \int_{-2}^{2} \int_{0}^{4-y^2} dz \, dy \, dx $$
* **对 $z$ 积分**:
    $$ \int_{0}^{4-y^2} dz = 4-y^2 $$
* **对 $y$ 积分**:
    $$ \int_{-2}^{2} (4-y^2) \, dy = \left[ 4y - \frac{y^3}{3} \right]_{-2}^{2} $$
    $$ = \left(8 - \frac{8}{3}\right) - \left(-8 - \frac{-8}{3}\right) = \left(\frac{16}{3}\right) - \left(-\frac{16}{3}\right) = \frac{32}{3} $$
* **对 $x$ 积分**:
    $$ \int_{0}^{1} \frac{32}{3} \, dx = \frac{32}{3} [x]_0^1 = \frac{32}{3} $$

### Step 6: Calculate the Final Flux (计算总通量)
$$ \text{Flux} = -3 \times \text{Volume} = -3 \times \frac{32}{3} = -32 $$