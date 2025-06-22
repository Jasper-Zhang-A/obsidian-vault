# 曲面积分综合学习笔记：梯度法 vs. 参数法

> [!abstract] 核心思想
> 本笔记旨在对比求解曲面积分的两种核心方法：**梯度法**和**参数法**。
> 
> * **梯度法 (Gradient Method)**：适用于曲面可以被隐函数 $f(x,y,z)=c$ 或显函数 $z=g(x,y)$ 清晰描述的情况。其核心是**梯度向量 $\nabla f$** 和向特定坐标平面的**投影**。
> * **参数法 (Parametric Method)**：适用于任何可以用参数方程 $\vec{r}(u,v)$ 描述的曲面。其核心是**切向量的叉乘 $\vec{r}_u \times \vec{r}_v$**。
> 
> 我们将证明，**参数法是更通用、更根本的方法**。梯度法可以看作是参数法在特定情况（用x,y等作为参数）下的一个特例。

---

## 一、核心方法回顾：参数方程法

当一个曲面 $S$ 是由参数方程 $\vec{r}(u,v)$ 给出时，所有计算的基础都源于叉乘向量 $\vec{r}_u \times \vec{r}_v$。

### 1.1 关键：面积元 $d\sigma$
1.  **计算关键向量：** 计算偏导数向量 $\vec{r}_u$ 和 $\vec{r}_v$，然后计算它们的叉乘 $\vec{r}_u \times \vec{r}_v$。这个向量是曲面的法向量。
2.  **定义面积元：** 面积元 $d\sigma$ 就是上述叉乘向量的模长。
    $$ d\sigma = |\vec{r}_u \times \vec{r}_v| \,du\,dv $$

### 1.2 应用：计算曲面面积、标量积分和通量
* **曲面面积 (Area):**
    $$ A = \iint_S d\sigma = \iint_D |\vec{r}_u \times \vec{r}_v| \,du\,dv $$
* **标量函数的曲面积分 (Scalar Surface Integral):**
    $$ \iint_S G(x,y,z) \,d\sigma = \iint_D G(\vec{r}(u,v)) |\vec{r}_u \times \vec{r}_v| \,du\,dv $$
* **矢量场的通量 (Flux of a Vector Field):**
    $$ \text{Flux} = \iint_S \vec{F} \cdot \vec{n} \,d\sigma = \iint_D \vec{F}(\vec{r}(u,v)) \cdot (\pm \vec{r}_u \times \vec{r}_v) \,du\,dv $$
    ($\pm$ 取决于法向量方向要求)

---

## 二、方法对比：用参数法重解“梯度法”问题

现在，我们用更通用的**参数法**来解决之前用梯度法求解的两个经典问题，以展示两种方法之间的联系和参数法的普适性。

### Case Study 1: 曲面面积计算 (半球面被柱面所截)

> [!question] 原题目
> 求半球面 $S: x^2 + y^2 + z^2 = 2, z \ge 0$ 被柱面 $x^2 + y^2 = 1$ 所截下的帽形部分的曲面面积。

#### **参数法解题步骤**

1.  **参数化曲面 $S$ (使用球坐标)**
    这个半球面是半径为 $\sqrt{2}$ 的球面的一部分。因此，最自然的参数化是球坐标：
    $$ \vec{r}(\phi, \theta) = (\sqrt{2}\sin\phi\cos\theta)\vec{i} + (\sqrt{2}\sin\phi\sin\theta)\vec{j} + (\sqrt{2}\cos\phi)\vec{k} $$
2.  **确定参数范围 (关键步骤)**
    * $\theta$ 显然是 $0 \le \theta \le 2\pi$。
    * $\phi$ 的范围不是完整的 $0 \le \phi \le \pi/2$。我们需要找到边界，即 $x^2+y^2=1$ 所在的纬度。
    * 在曲面上，$x^2+y^2 = (\sqrt{2}\sin\phi)^2 = 2\sin^2\phi$。
    * 令 $2\sin^2\phi = 1 \implies \sin^2\phi = 1/2 \implies \sin\phi = 1/\sqrt{2}$。
    * 由于是上半球面，我们取 $\phi = \pi/4$。
    * 所以，帽形部分的参数范围是 $0 \le \phi \le \pi/4$ 和 $0 \le \theta \le 2\pi$。
3.  **计算面积元 $d\sigma$**
    对于半径为 $a$ 的球面，我们知道其面积元为 $d\sigma = a^2\sin\phi \,d\phi\,d\theta$。
    在本题中，$a=\sqrt{2}$，所以：
    $$ d\sigma = (\sqrt{2})^2\sin\phi \,d\phi\,d\theta = 2\sin\phi \,d\phi\,d\theta $$
4.  **建立并计算面积积分**
    $$ A = \iint_S d\sigma = \int_0^{2\pi} \int_0^{\pi/4} 2\sin\phi \,d\phi\,d\theta $$
    $$ = 2 \int_0^{2\pi} [-\cos\phi]_0^{\pi/4} d\theta = 2 \int_0^{2\pi} (-\cos(\pi/4) - (-\cos(0))) d\theta $$
    $$ = 2 \int_0^{2\pi} (1 - \frac{\sqrt{2}}{2}) d\theta = 2(1 - \frac{\sqrt{2}}{2}) [\theta]_0^{2\pi} = 2(1 - \frac{\sqrt{2}}{2}) (2\pi) = 4\pi - 2\pi\sqrt{2} = 2\pi(2-\sqrt{2}) $$

> [!success] 对比结论
> 这个结果与我们用梯度法算出的 $2\pi(2-\sqrt{2})$ 完全一致。这说明两种方法是相通的。梯度法本质上是选择了 $x,y$ 作为参数，而参数法可以选择更贴合几何形状的参数（如 $\phi, \theta$），有时能让积分限更简单。

### Case Study 2: 标量函数的曲面积分 (立方体表面)

> [!question] 原题目
> 对函数 $G(x,y,z) = xyz$ 在第一卦限内，由平面 $x=1, y=1, z=1$ 和三个坐标平面所围成的正方体表面上进行曲面积分。

#### **参数法解题步骤 (以面 A: z=1 为例)**

1.  **参数化曲面 $S_A$ (使用 $x,y$ 作参数)**
    对于平面 $z=1$ 上的区域，最自然的参数就是 $x$ 和 $y$。
    $$ \vec{r}(x, y) = x\vec{i} + y\vec{j} + 1\vec{k} $$
    参数范围是 $0 \le x \le 1, 0 \le y \le 1$。
2.  **计算面积元 $d\sigma$**
    $$ \vec{r}_x = \langle 1, 0, 0 \rangle $$
    $$ \vec{r}_y = \langle 0, 1, 0 \rangle $$
    $$ \vec{r}_x \times \vec{r}_y = \langle 0, 0, 1 \rangle = \vec{k} $$
    $$ d\sigma = |\vec{r}_x \times \vec{r}_y| \,dx\,dy = |\vec{k}| \,dx\,dy = 1 \,dx\,dy $$
3.  **建立并计算积分**
    在曲面上，$z=1$, $G(x,y,z)=xy$。
    $$ \iint_{S_A} G \,d\sigma = \iint_{R_{xy}} xy (1 \,dx\,dy) = \int_0^1 \int_0^1 xy \,dx\,dy = \frac{1}{4} $$

> [!success] 对比结论
> 这次参数法的结果与梯度法完全一致。实际上，当我们选择 $x,y$ 作为参数来参数化显函数 $z=f(x,y)$ 时，参数法中的叉乘向量 $|\vec{r}_x \times \vec{r}_y|$ 正好等于梯度法中面积元公式的分子部分 $|\nabla F|$ (当 $F=z-f(x,y)$)，所以说梯度法是参数法的一种特例。

---

## 三、参数法的“专属优势”：处理复杂或无明确函数关系的曲面

梯度法要求曲面能被 $f(x,y,z)=c$ 描述。但有些曲面（如莫比乌斯带）或参数化更方便的曲面，只能用参数法解决。

### Case Study 3: 薄锥形平截面质心的计算

> [!question] 题目
> 求密度为常数 $\delta$ 的薄锥形平面 $z = \sqrt{x^2+y^2}$ 被平面 $z=1$ 和 $z=2$ 截下的部分的质心。

这个问题用梯度法会比较麻烦，因为 $z = \sqrt{x^2+y^2}$ 在原点不可导。但用参数法（圆柱坐标）则非常自然。

#### **参数法解题步骤**
1.  **参数化曲面 (使用圆柱坐标)**
    在圆锥上，$z=r$。
    $$ \vec{r}(r, \theta) = (r\cos\theta)\vec{i} + (r\sin\theta)\vec{j} + r\vec{k} $$
    参数范围: $1 \le r \le 2$ (因 $1 \le z \le 2$), $0 \le \theta \le 2\pi$。
2.  **计算面积元 $d\sigma$**
    $$ \vec{r}_r = \langle \cos\theta, \sin\theta, 1 \rangle $$
    $$ \vec{r}_\theta = \langle -r\sin\theta, r\cos\theta, 0 \rangle $$
    $$ |\vec{r}_r \times \vec{r}_\theta| = |\langle -r\cos\theta, -r\sin\theta, r \rangle| = \sqrt{r^2\cos^2\theta + r^2\sin^2\theta + r^2} = \sqrt{2r^2} = r\sqrt{2} $$
    所以 $d\sigma = r\sqrt{2} \,dr\,d\theta$。
3.  **计算质量和一阶矩**
    * **总质量 M**:
        $$ M = \iint_S \delta \,d\sigma = \int_0^{2\pi}\int_1^2 \delta (r\sqrt{2}) \,dr\,d\theta = 3\pi\delta\sqrt{2} $$
    * **一阶矩 $M_{xy}$**:
        $$ M_{xy} = \iint_S z\delta \,d\sigma = \int_0^{2\pi}\int_1^2 (r)\delta (r\sqrt{2}) \,dr\,d\theta = \int_0^{2\pi}\int_1^2 \delta\sqrt{2} r^2 \,dr\,d\theta = \frac{14\pi\delta\sqrt{2}}{3} $$
4.  **计算质心**
    $$ \bar{z} = \frac{M_{xy}}{M} = \frac{14/3}{3} = \frac{14}{9} $$
    质心为 $(0, 0, \frac{14}{9})$。

---

> [!summary] 最终总结
> 1.  **参数法是“万能钥匙”**：理论上，所有能用梯度法解决的问题都能用参数法解决，反之则不成立。参数法是更根本、更通用的方法。
> 2.  **梯度法是“快捷方式”**：当曲面能方便地写成 $z=f(x,y)$ 或 $f(x,y,z)=c$ 的形式时，梯度法通常公式更简洁，心算更快。
> 3.  **选择的智慧**：解题时，应根据曲面的几何形状来选择最适合的方法。对于球面、锥面、旋转面等，参数法（使用球坐标或柱面坐标）往往更具优势。对于简单的平面或显函数曲面，梯度法可能更直接。