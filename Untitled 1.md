# Stokes定理应用：旋度通量与法向量方向解析

#stokes-theorem #flux-of-curl #orientation #vector-calculus

---

## 一、 概念辨析：“通量” vs. “旋度的通量”

您感觉到的“迷惑性”是完全正常的，因为 "Flux" 这个词在不同定理中指代的对象不同。

> [!question] "Flux" 到底指什么？
> -   **情况一：标准的“通量” (Flux)**
>     -   **公式:** $\text{Flux} = \iint_S \mathbf{F} \cdot \mathbf{n} \,d\sigma$
>     -   **物理意义:** 计算的是矢量场 **F 本身** 穿过曲面 S 的净流量。
>     -   **相关定理:** 如果 S 是一个**封闭曲面**，这个通量可以用**高斯散度定理** (Divergence Theorem) 转化为对散度 $\nabla \cdot \mathbf{F}$ 的体积分。
>
> -   **情况二：“旋度的通量” (Flux of the Curl)**
>     -   **公式:** $\text{Flux of Curl} = \iint_S (\nabla \times \mathbf{F}) \cdot \mathbf{n} \,d\sigma$
>     -   **物理意义:** 计算的是矢量场 **F 的旋度（Curl）** 这个新矢量场穿过曲面 S 的净流量。它衡量了场 F 沿着 S 边界的“净环绕程度”。
>     -   **相关定理:** 这个通量可以用**斯托克斯定理** (Stokes' Theorem) 转化为场 **F** 沿着曲面 S 的**边界曲线 C** 的环流量（线积分）$\oint_C \mathbf{F} \cdot d\mathbf{r}$。

**考试技巧：** 当题目中出现 **"flux of the curl"** 或者要求计算**环流量(circulation)** $\oint_C \mathbf{F} \cdot d\mathbf{r}$ 时，这几乎是明确的信号，告诉你应该使用**斯托克斯定理**，而不是高斯散度定理。

---

## 二、难点解析：法向量方向的确定

> [!help] “taking the inner normal vector n to the surface” 和 “a positive k-component” 如何理解？

这是理解题目的关键。我们来拆解这两个描述。

#### 1. "a positive k-component" (k分量为正)
这是一个**绝对清晰、没有歧义**的数学指令。它告诉你，无论你用什么方法计算法向量，最终用在积分里的那个法向量 $\mathbf{n}$，它的 $\mathbf{k}$ 分量必须是正数。这通常意味着法向量是**指向上方**的。

**快速求解技巧:** 对于任何形如 $z=g(x,y)$ 的曲面，我们可以令 $f(x,y,z) = z - g(x,y) = 0$。
它的梯度是：
$$ \nabla f = -\frac{\partial g}{\partial x}\mathbf{i} - \frac{\partial g}{\partial y}\mathbf{j} + 1\mathbf{k} $$
你会发现，这样定义的 $\nabla f$，其 **k-分量永远是 +1**。因此，它自动满足 "a positive k-component" 的要求。

#### 2. "inner normal vector" (内法向量)
这个词的含义是**依赖于上下文的**，有时会模糊不清。
-   对于一个**封闭曲面**（如球面），“内法向量”明确指向封闭体内部。
-   对于一个**开放曲面**（如一个碗状的抛物面），“内法向量”没有一个统一的定义。它可能指凹进去的一侧，也可能只是出题人为了增加难度而使用的非标准术语。

**结论：** 当这两个描述同时出现时，**必须以最明确的那个为准**。题目说“... a normal vector ... which has a positive k-component”，这等于是在说：“**请使用 k 分量为正的那个法向量，我们在这个题目里把它叫做 inner normal**”。你只需要执行“k分量为正”这个指令即可，无需纠结它是否符合你对“内法向量”的直观理解。

---

## 三、典型题目完整解析

> [!question] 2023年第四大题 (典型例题)
>
> （由于无法获取原题，我们以此为例）
> 设 S 为抛物面 $z = x^2 + y^2$ 被平面 $z=4$ 所截下的部分。设矢量场 $\mathbf{F} = yz\mathbf{i} - xz\mathbf{j} + xy\mathbf{k}$。计算旋度的通量 $\iint_S (\nabla \times \mathbf{F}) \cdot \mathbf{n} \,d\sigma$，其中 **n** 是指向 S 上方的单位法向量（即 k 分量为正）。

#### **步骤一：计算旋度 `∇ × F`**
$$ \nabla \times \mathbf{F} = \begin{vmatrix} \mathbf{i} & \mathbf{j} & \mathbf{k} \\ \frac{\partial}{\partial x} & \frac{\partial}{\partial y} & \frac{\partial}{\partial z} \\ yz & -xz & xy \end{vmatrix} $$
$$ = \mathbf{i}(\frac{\partial(xy)}{\partial y} - \frac{\partial(-xz)}{\partial z}) - \mathbf{j}(\frac{\partial(xy)}{\partial x} - \frac{\partial(yz)}{\partial z}) + \mathbf{k}(\frac{\partial(-xz)}{\partial x} - \frac{\partial(yz)}{\partial y}) $$
$$ = \mathbf{i}(x - (-x)) - \mathbf{j}(y - y) + \mathbf{k}(-z - z) = 2x\mathbf{i} - 0\mathbf{j} - 2z\mathbf{k} = \langle 2x, 0, -2z \rangle $$

#### **步骤二：确定法向量 `n` 及 `dσ`**
-   曲面为 $z = x^2+y^2$。我们使用梯度法，令 $f(x,y,z) = z - x^2 - y^2 = 0$。
-   计算梯度：$\nabla f = -2x\mathbf{i} - 2y\mathbf{j} + \mathbf{k}$。
-   这个向量的 k-分量为+1，满足题目“k分量为正”的要求。所以我们直接用它。
-   我们将曲面投影到 xy-平面，投影区域 $R$ 是圆盘 $x^2+y^2 \le 4$。
-   对于投影，我们有 $\mathbf{n}\,d\sigma = \nabla f \,dA = (-2x\mathbf{i} - 2y\mathbf{j} + \mathbf{k}) \,dx\,dy$。

#### **步骤三：计算点积 `(∇ × F) · n`**
$$ (\nabla \times \mathbf{F}) \cdot \nabla f = \langle 2x, 0, -2z \rangle \cdot \langle -2x, -2y, 1 \rangle $$
$$ = (2x)(-2x) + (0)(-2y) + (-2z)(1) = -4x^2 - 2z $$
-   **变量替换：** 在积分前，必须把 $z$ 替换掉。在曲面上 $z=x^2+y^2$。
    $$ -4x^2 - 2(x^2+y^2) = -4x^2 - 2x^2 - 2y^2 = -6x^2 - 2y^2 $$

#### **步骤四：建立并求解积分**
$$ \iint_S (\nabla \times \mathbf{F}) \cdot \mathbf{n} \,d\sigma = \iint_R (-6x^2 - 2y^2) \,dA $$
-   投影区域 $R$ 是一个半径为2的圆，使用**极坐标**计算最方便。
-   $x = r\cos\theta, y=r\sin\theta, dA = r\,dr\,d\theta$。范围是 $0 \le r \le 2, 0 \le \theta \le 2\pi$。
-   被积函数变为：$-6(r\cos\theta)^2 - 2(r\sin\theta)^2 = -6r^2\cos^2\theta - 2r^2\sin^2\theta$。
-   积分式：
    $$ \int_0^{2\pi} \int_0^2 (-6r^2\cos^2\theta - 2r^2\sin^2\theta) \,r\,dr\,d\theta $$
    $$ = \int_0^{2\pi} \int_0^2 -r^3(6\cos^2\theta + 2\sin^2\theta) \,dr\,d\theta $$
    $$ = \int_0^{2\pi} -(6\cos^2\theta + 2\sin^2\theta) \left[ \frac{r^4}{4} \right]_0^2 d\theta $$
    $$ = \int_0^{2\pi} -(6\cos^2\theta + 2\sin^2\theta) (4) d\theta = -4 \int_0^{2\pi} (6\cos^2\theta + 2\sin^2\theta) d\theta $$
-   利用公式 $\cos^2\theta = \frac{1+\cos(2\theta)}{2}$ 和 $\sin^2\theta = \frac{1-\cos(2\theta)}{2}$：
    $$ -4 \int_0^{2\pi} \left( 6\frac{1+\cos(2\theta)}{2} + 2\frac{1-\cos(2\theta)}{2} \right) d\theta $$
    $$ = -4 \int_0^{2\pi} (3(1+\cos(2\theta)) + (1-\cos(2\theta))) d\theta $$
    $$ = -4 \int_0^{2\pi} (4 + 2\cos(2\theta)) d\theta = -4 \left[ 4\theta + \sin(2\theta) \right]_0^{2\pi} $$
    $$ = -4 ( (4(2\pi)+0) - (0+0) ) = -32\pi $$