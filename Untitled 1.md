# 通量 (Flux) vs. 旋度的通量 (Flux of the Curl)

#calculus #stokes-theorem #flux #curl #divergence-theorem #common-mistakes

---

## 一、 核心概念辨析：什么时候用高斯，什么时候用斯托克斯？

您觉得这道题的“flux”一词很有迷惑性，这一点非常敏锐。在多元微积分中，我们有两种主要的“通量”问题，它们对应着两个完全不同的重量级定理。

| 对比项 | **矢量场的通量 (Flux of a Vector Field)** | **旋度的通量 (Flux of the Curl)** |
| :--- | :--- | :--- |
| **计算对象** | $\iint_S \mathbf{F} \cdot \mathbf{n} \, d\sigma$ | $\iint_S (\nabla \times \mathbf{F}) \cdot \mathbf{n} \, d\sigma$ |
| **物理意义** | 矢量场 **F** 直接穿过曲面 S 的净流量。 | 矢量场 **F** 沿曲面 S **边界**的“环绕”或“旋转”趋势的总和。 |
| **相关定理** | **散度定理 (高斯定理)** | **斯托克斯定理 (Stokes' Theorem)** |
| **前提条件** | 曲面 S 必须是**封闭的 (closed)**，能包围一个三维实体。 | 曲面 S 必须是**有边界的 (open)**。 |

**如何为题目“诊断”？**

1.  **看计算对象：** 题目是要求 `flux of F` 还是 `flux of the curl of F`？ 
2.  **看曲面形状：** 曲面是像一个完整的球或盒子（封闭），还是像一个碗或降落伞（有边界）？ 

对于 `Assignment 10` 第四题，题目明确要求计算 **“flux of the curl”**，并且给出的曲面是一个**上半球面** ($0 \le \phi \le \pi/2$) ，这是一个有边界的开放曲面。两个条件都明确指向了**斯托克斯定理**。

---

## 二、题目解析 (Assignment 10, Q4)

> [!question] 问题
> 使用斯托克斯定理中的曲面积分，计算场 $\mathbf{F} = y^2\mathbf{i} + z^2\mathbf{j} + x\mathbf{k}$ [cite: 11] [cite_start]的旋度的通量，该通量穿过曲面 $S: \mathbf{r}(\phi, \theta) = (2\sin\phi\cos\theta)\mathbf{i} + (2\sin\phi\sin\theta)\mathbf{j} + (2\cos\phi)\mathbf{k}$ ($0 \le \phi \le \pi/2, 0 \le \theta \le 2\pi$) [cite: 13][cite_start]，方向为向外的单位法向量 。

### 方法选择：一个“善意的陷阱”

斯托克斯定理的伟大之处在于它建立了曲面积分和线积分的桥梁：
$$ \underbrace{\iint_S (\nabla \times \mathbf{F}) \cdot \mathbf{n} \, d\sigma}_{\text{旋度的通量 (Flux of the Curl)}} = \underbrace{\oint_C \mathbf{F} \cdot d\mathbf{r}}_{\text{环流量 (Circulation)}} $$
题目要求“使用斯托克斯定理中的曲面积分来计算”，这句话听起来是让我们硬算左边。但通常，这类问题的“潜台词”是：**请利用斯托克斯定理来计算这个旋度的通量**——而最简单的方法往往是计算等式右边的线积分。

下面我们用更简单的线积分方法来求解。

### 解法：利用斯托克斯定理转化为线积分

#### 步骤 1：确定边界曲线 C
-   [cite_start]曲面 S 是一个半径为2的上半球面。 
-   它的边界 C 就是赤道，即在 xy-平面 ($z=0$) 上的圆 $x^2+y^2=4$。

#### 步骤 2：参数化边界曲线 C
-   我们可以将边界 C 参数化为：
    $$ \mathbf{r}(t) = (2\cos t)\mathbf{i} + (2\sin t)\mathbf{j} + 0\mathbf{k}, \quad 0 \le t \le 2\pi $$
-   **确定方向：** 曲面的法向量是向外的（向上），根据右手定则，边界曲线 C 必须是**逆时针**方向。我们选择的参数化方向 `t` 从 0 到 $2\pi$ 正好是逆时针，方向正确。
-   求切向量：
    $$ \frac{d\mathbf{r}}{dt} = (-2\sin t)\mathbf{i} + (2\cos t)\mathbf{j} $$

#### 步骤 3：在边界 C 上表示矢量场 F
-   在边界 C 上，我们有 $x=2\cos t, y=2\sin t, z=0$。
-   [cite_start]将这些代入 $\mathbf{F} = y^2\mathbf{i} + z^2\mathbf{j} + x\mathbf{k}$ ：
    $$ \mathbf{F}(\mathbf{r}(t)) = (2\sin t)^2\mathbf{i} + (0)^2\mathbf{j} + (2\cos t)\mathbf{k} = (4\sin^2 t)\mathbf{i} + (2\cos t)\mathbf{k} $$

#### 步骤 4：计算线积分
-   计算点积 $\mathbf{F} \cdot \frac{d\mathbf{r}}{dt}$：
    $$ ((4\sin^2 t)\mathbf{i} + (2\cos t)\mathbf{k}) \cdot ((-2\sin t)\mathbf{i} + (2\cos t)\mathbf{j}) $$
    $$ = (4\sin^2 t)(-2\sin t) + (0)(2\cos t) + (2\cos t)(0) = -8\sin^3 t $$
-   计算定积分：
    $$ \oint_C \mathbf{F} \cdot d\mathbf{r} = \int_0^{2\pi} -8\sin^3 t \,dt $$
    这是一个周期函数在一个完整周期上的积分。我们可以利用 $\sin^3 t$ 是奇函数的性质，或者直接计算：
    $$ \int -8\sin^3 t \,dt = -8 \int (1-\cos^2 t)\sin t \,dt $$
    令 $u=\cos t, du = -\sin t \,dt$，积分变为 $8 \int (1-u^2)du = 8(u-\frac{u^3}{3}) = 8(\cos t - \frac{\cos^3 t}{3})$。
    $$ \left[ 8(\cos t - \frac{\cos^3 t}{3}) \right]_0^{2\pi} = 8(1-\frac{1}{3}) - 8(1-\frac{1}{3}) = 0 $$
    所以，旋度的通量为 **0**。

> [!success] 结论
> 这道题的旋度通量为 0。通过斯托克斯定理，我们避免了计算一个非常复杂的曲面积分，而是通过一个相对简单的线积分得到了答案。这正是该定理的威力所在，也是出题人希望考察的核心思想。