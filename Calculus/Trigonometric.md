
# **A Summary of Integrating Pure Trigonometric Functions**

---
## Contents
1. Basic Forms
2. Integrals of the Form $\int \sin^n x \,dx$ and $\int \cos^n x \,dx$
3. Integrals of the Form $\int \sin^m x \cos^n x \,dx$
4. Integrals of the Form $\int \tan^n x \,dx$ and $\int \sec^n x \,dx$
5. Application of Product-to-Sum Formulas
6. Wallis' Formula
7. Advanced Example: A Mixed-Function Integral

---

## 1. Basic Forms
These are the most fundamental integrals, derived directly from differentiation rules.
$$\int \sin x \,dx = -\cos x + C$$
$$\int \cos x \,dx = \sin x + C$$
$$\int \tan x \,dx = \int \frac{\sin x}{\cos x} \,dx = -\ln|\cos x| + C = \ln|\sec x| + C$$
$$\int \cot x \,dx = \int \frac{\cos x}{\sin x} \,dx = \ln|\sin x| + C = -\ln|\csc x| + C$$
$$\int \sec x \,dx = \ln|\sec x + \tan x| + C$$
$$\int \csc x \,dx = \ln|\csc x - \cot x| + C$$
$$\int \sec^2 x \,dx = \tan x + C$$
$$\int \csc^2 x \,dx = -\cot x + C$$
$$\int \sec x \tan x \,dx = \sec x + C$$
$$\int \csc x \cot x \,dx = -\csc x + C$$

---

## 2. Integrals of the Form $\int \sin^n x \,dx$ and $\int \cos^n x \,dx$
The method for these integrals depends on whether $n$ is odd or even.

### When $n$ is a positive odd integer
For $\int \sin^n x \,dx$, rewrite $\sin^n x = \sin^{n-1}x \sin x$. Since $n-1$ is even, use $\sin^2 x = 1 - \cos^2 x$ to convert $\sin^{n-1}x$ into a polynomial of $\cos x$. Then, let $u = \cos x$, which gives $du = -\sin x \,dx$. The method is similar for $\int \cos^n x \,dx$ by letting $u = \sin x$.

**Example**:
$$\int \sin^3 x \,dx = \int \sin^2 x \sin x \,dx = \int (1 - \cos^2 x) \sin x \,dx$$
Let $u = \cos x$, so $du = -\sin x \,dx$. The integral becomes:
$$-\int (1 - u^2) \,du = -u + \frac{u^3}{3} + C = -\cos x + \frac{\cos^3 x}{3} + C$$

### When $n$ is a positive even integer
Use the power-reduction formulas (half-angle formulas):
$$\sin^2 x = \frac{1 - \cos(2x)}{2} \quad \text{and} \quad \cos^2 x = \frac{1 + \cos(2x)}{2}$$
Apply these formulas repeatedly until the powers are reduced to a point where direct integration is possible.

### Reduction Formulas
Alternatively, one can derive reduction formulas using integration by parts:
$$\int \sin^n x \,dx = -\frac{1}{n}\sin^{n-1}x \cos x + \frac{n-1}{n}\int \sin^{n-2}x \,dx$$
$$\int \cos^n x \,dx = \frac{1}{n}\cos^{n-1}x \sin x + \frac{n-1}{n}\int \cos^{n-2}x \,dx$$

---

## 3. Integrals of the Form $\int \sin^m x \cos^n x \,dx$
The strategy depends on the parity of the exponents $m$ and $n$.

### When at least one exponent is a positive odd integer
* If $m$ is odd, save one $\sin x$ factor and convert the rest to cosines using $\sin^2 x = 1 - \cos^2 x$. Then, substitute $u = \cos x$.
* If $n$ is odd, save one $\cos x$ factor and convert the rest to sines using $\cos^2 x = 1 - \sin^2 x$. Then, substitute $u = \sin x$.
* If both are odd, either method works.

### When both $m$ and $n$ are positive even integers
Use the power-reduction formulas repeatedly. Using $\sin x \cos x = \frac{1}{2}\sin(2x)$ can also be helpful.

**Example**:
$$\int \sin^2 x \cos^2 x \,dx = \int (\sin x \cos x)^2 \,dx = \int \left(\frac{\sin(2x)}{2}\right)^2 \,dx = \frac{1}{4}\int \sin^2(2x) \,dx$$
Then apply the power-reduction formula to $\sin^2(2x)$.

---

## 4. Integrals of the Form $\int \tan^n x \,dx$ and $\int \sec^n x \,dx$

### $\int \tan^n x \,dx$
Rewrite $\tan^n x = \tan^{n-2} x \tan^2 x = \tan^{n-2} x (\sec^2 x - 1)$.
$$\int \tan^n x \,dx = \int \tan^{n-2} x \sec^2 x \,dx - \int \tan^{n-2} x \,dx$$
The first part, $\int \tan^{n-2} x \sec^2 x \,dx$, can be solved by letting $u = \tan x$, which yields a reduction formula.

### $\int \sec^n x \,dx$
* **When $n$ is a positive even integer**: Let $n=2k$.
  $$\sec^n x = \sec^{2k-2} x \sec^2 x = (\tan^2 x + 1)^{k-1} \sec^2 x$$
  Then, substitute $u = \tan x$, so $du = \sec^2 x \,dx$.
* **When $n$ is a positive odd integer**: Use integration by parts to derive the reduction formula:
  $$\int \sec^n x \,dx = \frac{\sec^{n-2} x \tan x}{n-1} + \frac{n-2}{n-1}\int \sec^{n-2} x \,dx$$

**Special Cases**:
$$\int \sec x \,dx = \ln|\sec x + \tan x| + C$$
$$\int \sec^3 x \,dx = \frac{1}{2}(\sec x \tan x + \ln|\sec x + \tan x|) + C$$

---

## 5. Application of Product-to-Sum Formulas
For integrals like $\int \sin(ax)\cos(bx) \,dx$, use the product-to-sum identities to simplify the integrand:
$$\sin A \cos B = \frac{1}{2}[\sin(A+B) + \sin(A-B)]$$
$$\cos A \sin B = \frac{1}{2}[\sin(A+B) - \sin(A-B)]$$
$$\cos A \cos B = \frac{1}{2}[\cos(A+B) + \cos(A-B)]$$
$$\sin A \sin B = -\frac{1}{2}[\cos(A+B) - \cos(A-B)]$$

---

## 6. Wallis' Formula
Wallis' formula provides a quick method for evaluating definite integrals of $\sin^n x$ and $\cos^n x$ over the interval $[0, \frac{\pi}{2}]$.

### Formula Definition
Let $I_n = \int_{0}^{\frac{\pi}{2}} \sin^n x \,dx = \int_{0}^{\frac{\pi}{2}} \cos^n x \,dx$.
* **When $n$ is a positive even integer** ($n=2k, k \ge 1$):
  $$I_n = \frac{n-1}{n} \cdot \frac{n-3}{n-2} \cdot \dots \cdot \frac{3}{4} \cdot \frac{1}{2} \cdot \frac{\pi}{2} = \frac{(n-1)!!}{n!!} \cdot \frac{\pi}{2}$$
* **When $n$ is a positive odd integer** ($n=2k+1, k \ge 0$):
  $$I_n = \frac{n-1}{n} \cdot \frac{n-3}{n-2} \cdot \dots \cdot \frac{4}{5} \cdot \frac{2}{3} = \frac{(n-1)!!}{n!!}$$

### Application and Extension
* **Base Interval**: The formula is defined for the interval $[0, \frac{\pi}{2}]$.
* **Extension to $[0, \pi]$**: By symmetry,
    * $\int_{0}^{\pi} \sin^n x \,dx = 2 \int_{0}^{\frac{\pi}{2}} \sin^n x \,dx$ (for any $n \ge 0$)
    * $$ \int_{0}^{\pi} \cos^n x \,dx = 
        \begin{cases}
            2 \int_{0}^{\frac{\pi}{2}} \cos^n x \,dx, & \text{if } n \text{ is even} \\
            0, & \text{if } n \text{ is odd}
        \end{cases} $$

---

## 7. Advanced Example: A Mixed-Function Integral
This section details the solution for the integral $\int \frac{1}{\cos\theta (\cos\theta + \sin\theta)} \,d\theta$.

**Step 1: Rewrite the integrand**
Divide the numerator and denominator by $\cos^2\theta$ (assuming $\cos\theta \neq 0$):
$$\frac{1}{\cos\theta(\cos\theta+\sin\theta)} = \frac{\frac{1}{\cos^2\theta}}{\frac{\cos\theta(\cos\theta+\sin\theta)}{\cos^2\theta}} = \frac{\sec^2\theta}{\frac{\cos\theta+\sin\theta}{\cos\theta}} = \frac{\sec^2\theta}{1+\frac{\sin\theta}{\cos\theta}} = \frac{\sec^2\theta}{1+\tan\theta}$$
So the integral becomes:
$$I = \int \frac{\sec^2\theta}{1+\tan\theta} \,d\theta$$

**Step 2: Perform a substitution**
Let $u = 1 + \tan\theta$. Differentiating with respect to $\theta$, we get:
$$\frac{du}{d\theta} = \frac{d}{d\theta}(1+\tan\theta) = \sec^2\theta$$
Therefore, $du = \sec^2\theta \,d\theta$.

**Step 3: Substitute and integrate**
Substitute $u$ and $du$ into the integral:
$$I = \int \frac{1}{u} \,du$$
This is a standard integral, and its result is:
$$I = \ln|u| + C$$
where $C$ is the constant of integration.

**Step 4: Substitute back**
Substitute $u = 1 + \tan\theta$ back into the result:
$$I = \ln|1 + \tan\theta| + C$$

**Alternative Forms of the Result**
The answer can be written in other equivalent forms:
$$\ln|1 + \tan\theta| + C = \ln\left|1 + \frac{\sin\theta}{\cos\theta}\right| + C = \ln\left|\frac{\cos\theta + \sin\theta}{\cos\theta}\right| + C$$
Using the logarithm property $\ln|\frac{a}{b}| = \ln|a| - \ln|b|$, this can be written as:
$$I = \ln|\cos\theta + \sin\theta| - \ln|\cos\theta| + C$$

**Final Answer**:
$$\int \frac{1}{\cos\theta(\cos\theta + \sin\theta)} \,d\theta = \ln|1 + \tan\theta| + C$$

# 学习笔记：反三角函数求导的深度解析

## 一、基本反三角函数的导数公式

以下是六个基本反三角函数的导数公式，这是微积分中的基础，需要牢记。

* **反正弦 (Arcsine)**
    $$\frac{d}{dx}(\arcsin u) = \frac{1}{\sqrt{1-u^2}} \cdot \frac{du}{dx}$$

* **反余弦 (Arccosine)**
    $$\frac{d}{dx}(\arccos u) = -\frac{1}{\sqrt{1-u^2}} \cdot \frac{du}{dx}$$

* **反正切 (Arctangent)**
    $$\frac{d}{dx}(\arctan u) = \frac{1}{1+u^2} \cdot \frac{du}{dx}$$

* **反余切 (Arccotangent)**
    $$\frac{d}{dx}(\text{arccot } u) = -\frac{1}{1+u^2} \cdot \frac{du}{dx}$$

* **反正割 (Arcsecant)**
    $$\frac{d}{dx}(\text{arcsec } u) = \frac{1}{|u|\sqrt{u^2-1}} \cdot \frac{du}{dx}$$

* **反余割 (Arccosecant)**
    $$\frac{d}{dx}(\text{arccsc } u) = -\frac{1}{|u|\sqrt{u^2-1}} \cdot \frac{du}{dx}$$

---

## 二、核心问题：为什么 `arcsin(x)` 的导数没有正负号？

> [!question] 用户提问
> 在推导反正弦函数导数时，我们用到 $cos(y) = ±sqrt(1-sin²(y))$，为什么最后公式里只有正号，没有 `±` 呢？

这是一个非常深刻的问题！答案在于**反函数**的定义。

#### 1. 反函数存在的前提

一个函数必须是**一一对应**的（即通过“水平线测试”）才能拥有反函数。但我们知道，像 `sin(x)` 这样的周期函数，一个 y 值（如 0.5）会对应无数个 x 值，它并不是一一对应的。

![Sine Wave](https://i.imgur.com/uN8E7z1.png)

#### 2. “主值区间”的引入

为了解决这个问题，数学家们“强制”让 `sin(x)` 变成一一对应函数。方法是**限制其定义域**。

* 我们只取 `sin(x)` 函数上的一段单调递增的部分，国际上公认的选取标准是 `[-π/2, π/2]`。
* 在这个**主值区间 (Principal Value Range)** `[-π/2, π/2]` 内，`sin(x)` 函数就是一一对应的了，因此可以定义其反函数 `arcsin(x)`。

#### 3. 对导数推导的影响

现在我们来看这个限制如何影响导数的推导：

1.  我们设 $y = \arcsin(x)$。根据反函数的定义，这意味着：
    * $x = \sin(y)$
    * 并且 $y$ 的取值范围被限制在了 $[-\pi/2, \pi/2]$。

2.  我们对 $x = \sin(y)$ 进行隐函数求导：
    $$\frac{d}{dx}(x) = \frac{d}{dx}(\sin(y))$$
    $$1 = \cos(y) \cdot \frac{dy}{dx}$$
    $$\frac{dy}{dx} = \frac{1}{\cos(y)}$$

3.  **决定正负号的关键时刻**
    * 我们知道 $\cos^2(y) + \sin^2(y) = 1$，所以 $\cos(y) = \pm\sqrt{1-\sin^2(y)}$。
    * 但是，我们已经规定了 $y$ 的范围是 $[-\pi/2, \pi/2]$。
    * 在这个区间（即直角坐标系的第四和第一象限）内，$\cos(y)$ 的值**永远是非负的** ($\cos(y) \ge 0$)。
    * 因此，我们没有选择的余地，**必须取正号**！即 $\cos(y) = +\sqrt{1-\sin^2(y)}$。

4.  **代入并得出最终结论**
    将 $\cos(y) = \sqrt{1-\sin^2(y)}$ 和 $\sin(y)=x$ 代入第2步的结果：
    $$\frac{dy}{dx} = \frac{1}{\sqrt{1-x^2}}$$

> [!tip] 结论总结
> 反三角函数导数公式中正负号的取舍，完全取决于为了让原函数可逆而人为选择的**主值区间 (Principal Value Range)**。对于 `y = arcsin(x)`，其值域 `[-π/2, π/2]` 决定了 `cos(y)` 必须为正，从而导数也为正。同理，`y = arccos(x)` 的值域是 `[0, π]`，在这个区间内 `sin(y)` 为正，但其导数公式是 `-1/sin(y)`，所以最终为负。