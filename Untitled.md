# 学习笔记：曲面面积的计算与参数化

> [!question] 核心问题
> 有没有一个例子，是只能用“曲面面积积分”计算，而不能用“参数化”计算的？

这是一个概念辨析问题。实际上，“曲面面积积分”和“参数化”不是两种对立的方法。关系如下：
* **曲面面积的定义**: $A = \iint_S d\sigma$。这是一个抽象的定义。
* **计算方法**: 为了求解这个积分，我们**必须**对曲面 $S$ 进行**参数化**，从而将抽象的 $d\sigma$ 转换成我们可以积分的具体表达式。

参数化主要有两种形式：
1.  **显式参数化 (Explicit Parametrization)**: 当曲面可以被表示为 $z=f(x,y)$ 时，我们实际上是用 $x$ 和 $y$ 作为参数。此时面积微元 $d\sigma = \sqrt{1 + (\frac{\partial f}{\partial x})^2 + (\frac{\partial f}{\partial y})^2} \,dA$。这本质上是 $\vec{r}(x,y)$ 参数化的一种特例。
2.  **通用参数化 (General Parametrization)**: 对于更复杂的曲面，我们使用两个独立的参数 $u,v$ 来描述，即 $\vec{r}(u,v) = \langle x(u,v), y(u,v), z(u,v) \rangle$。此时面积微元 $d\sigma = |\vec{r}_u \times \vec{r}_v| \,du\,dv$。

---

> [!tip] 问题的重新诠释
> 一个更有意义的问题是：**有没有一个例子，是不能用简单的 $z=f(x,y)$ 投影法，而必须使用更通用的 $\vec{r}(u,v)$ 参数化的？**
> 
> 答案是：有。一个经典的例子就是圆柱的侧面。

### 案例分析：计算圆柱侧面积

**题目**: 求圆柱面 $x^2+y^2=a^2$ 在 $z=0$ 和 $z=h$ 之间的部分的面积。

#### 1. 为什么 $z=f(x,y)$ 方法行不通？

这个圆柱的侧面是**垂直于 xy 平面**的。你无法把它写成一个单一的函数 $z=f(x,y)$。对于圆周上任意一个点 $(x,y)$，$z$ 的值可以是从 $0$ 到 $h$ 的任何数，这不满足函数的定义。同样，你也不能简单地用 $x=f(y,z)$ 或 $y=f(x,z)$ 来描述整个圆柱面（最多只能描述一半）。

#### 2. 正确方法：使用柱面坐标进行通用参数化

这个时候，我们就必须使用更通用的参数化方法。对于圆柱面，最自然的参数就是**角度 $\theta$** 和**高度 $z$**。

**Step 1: 参数化曲面 $S$**
我们用参数 $\theta$ 和 $z$ 来定义曲面上的点 $(x,y,z)$：
* $x = a\cos\theta$
* $y = a\sin\theta$
* $z = z$
参数方程为：
$$ \vec{r}(\theta, z) = \langle a\cos\theta, a\sin\theta, z \rangle $$
参数的取值范围是：$0 \le \theta \le 2\pi$，$0 \le z \le h$。

**Step 2: 计算切向量 $\vec{r}_\theta$ 和 $\vec{r}_z$**
$$ \vec{r}_\theta = \frac{\partial \vec{r}}{\partial \theta} = \langle -a\sin\theta, a\cos\theta, 0 \rangle $$
$$ \vec{r}_z = \frac{\partial \vec{r}}{\partial z} = \langle 0, 0, 1 \rangle $$

**Step 3: 计算叉积并求其模长**
$$ \vec{r}_\theta \times \vec{r}_z = \begin{vmatrix} \vec{i} & \vec{j} & \vec{k} \\ -a\sin\theta & a\cos\theta & 0 \\ 0 & 0 & 1 \end{vmatrix} = \langle a\cos\theta, a\sin\theta, 0 \rangle $$
$$ |\vec{r}_\theta \times \vec{r}_z| = \sqrt{(a\cos\theta)^2 + (a\sin\theta)^2 + 0^2} = \sqrt{a^2(\cos^2\theta+\sin^2\theta)} = a $$

**Step 4: 建立并计算积分**
面积微元 $d\sigma = |\vec{r}_\theta \times \vec{r}_z| \,d\theta\,dz = a\,d\theta\,dz$。
$$ \text{Area} = \iint_S d\sigma = \int_0^h \int_0^{2\pi} a \,d\theta\,dz $$
$$ = a \cdot \int_0^h [\theta]_0^{2\pi} \,dz = a \cdot \int_0^h 2\pi \,dz = 2\pi a [z]_0^h = 2\pi ah $$

**结论**: 圆柱的侧面积是 $2\pi ah$ (周长 $\times$ 高)，这与我们的几何常识完全相符，也证明了参数化方法的正确性和必要性。