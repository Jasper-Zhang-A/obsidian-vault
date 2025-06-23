# 终极解析：二次型与对称矩阵对角化

> [!question] 核心问题
> “求二次型的标准形” 和 “求对称矩阵的正交对角化” 这两种题型之间到底有什么关联？

> [!abstract] 一句话总结
> **它们是同一个核心问题的两种不同问法**。求二次型标准形这个任务，其**核心解题步骤**，就是对这个二次型所对应的对称矩阵进行**正交对角化**。

---

### 从理论到实践的桥梁：变量替换原理

在我们开始完整计算前，先要理解为什么对角化能简化二次型。

> [!note] 核心原理：变量替换 $\mathbf{x} = P\mathbf{y}$
> 1. 任何一个二次型 $Q(\mathbf{x})$ 都可以写成矩阵形式 $\mathbf{x}^T A \mathbf{x}$，其中 $A$ 是对称矩阵。
> 2. 我们对矩阵 $A$ 进行正交对角化，找到一个**正交矩阵 $P$**，使得 $P^T A P = D$（一个对角矩阵，对角元是A的特征值）。
> 3. 进行变量替换 $\mathbf{x} = P\mathbf{y}$，二次型函数就发生了如下的代数演变：
>    $$
>    Q(\mathbf{x}) = (\mathbf{Py})^T A (\mathbf{Py}) = \mathbf{y}^T \mathbf{P}^T A \mathbf{Py} = \mathbf{y}^T (\mathbf{P}^T A \mathbf{P}) \mathbf{y} = \mathbf{y}^T \mathbf{D} \mathbf{y}
>    $$
> 4. 最终得到的 $\mathbf{y}^T \mathbf{D} \mathbf{y}$ 展开后就是不含交叉项的标准形 $\lambda_1 y_1^2 + \lambda_2 y_2^2 + \dots$。

---

> [!example] 完整解题流程：以一个综合例题为例
> **题目**: 已知二次型 $Q(\mathbf{x}) = 9x_1^2 + 7x_2^2 + 11x_3^2 - 8x_1x_2 + 8x_1x_3$。求正交矩阵 $P$，通过正交变换 $\mathbf{x}=P\mathbf{y}$ 将其化为标准形。

#### 第一步：从二次型写出对应的对称矩阵 A

> [!tip] 如何写出矩阵 A?
> - **对角线元素** $a_{ii}$：就是二次型中 $x_i^2$ 项的系数。
> - **非对角线元素** $a_{ij}$ ($i \neq j$)：就是二次型中交叉项 $x_ix_j$ 系数的**一半**。

根据此规则，我们得到矩阵 $A$：
$$
A = \begin{pmatrix} 9 & -4 & 4 \\ -4 & 7 & 0 \\ 4 & 0 & 11 \end{pmatrix}
$$

#### 第二步：计算矩阵 A 的特征值 (对角化的核心)

求解特征方程 $\det(A - \lambda I) = 0$，计算可得：
$$
\lambda^3 - 27\lambda^2 + 207\lambda - 405 = 0
$$
解得三个特征值为： $\lambda_1 = 3, \lambda_2 = 9, \lambda_3 = 15$。

#### 第三步：计算对应的标准正交特征向量

对于每一个特征值，求解线性方程组 $(A - \lambda I)\mathbf{x} = \mathbf{0}$，然后将解向量单位化。

1.  **对于 $\lambda_1 = 3$**:
    解得基础解系 $\mathbf{p}_1 = \begin{pmatrix} -2 \\ -2 \\ 1 \end{pmatrix}$。单位化后得到：
    $$ \mathbf{q}_1 = \frac{1}{3}\begin{pmatrix} -2 \\ -2 \\ 1 \end{pmatrix} $$

2.  **对于 $\lambda_2 = 9$**:
    解得基础解系 $\mathbf{p}_2 = \begin{pmatrix} 1 \\ -2 \\ -2 \end{pmatrix}$。单位化后得到：
    $$ \mathbf{q}_2 = \frac{1}{3}\begin{pmatrix} 1 \\ -2 \\ -2 \end{pmatrix} $$

3.  **对于 $\lambda_3 = 15$**:
    解得基础解系 $\mathbf{p}_3 = \begin{pmatrix} 2 \\ -1 \\ 2 \end{pmatrix}$。单位化后得到：
    $$ \mathbf{q}_3 = \frac{1}{3}\begin{pmatrix} 2 \\ -1 \\ 2 \end{pmatrix} $$

#### 第四步：构造正交矩阵 P 和写出标准形

将得到的标准正交特征向量作为列，构成正交矩阵 $P$。
$$
P = \begin{bmatrix} \mathbf{q}_1 & \mathbf{q}_2 & \mathbf{q}_3 \end{bmatrix} = \frac{1}{3}\begin{pmatrix} -2 & 1 & 2 \\ -2 & -2 & -1 \\ 1 & -2 & 2 \end{pmatrix}
$$
二次型的标准形由其特征值直接决定，系数就是矩阵A的特征值。
$$
Q(\mathbf{y}) = \lambda_1 y_1^2 + \lambda_2 y_2^2 + \lambda_3 y_3^2 = 3y_1^2 + 9y_2^2 + 15y_3^2
$$

> [!abstract] 最终答案
> - **进行变换的正交矩阵 P** 为：
>   $$
>   P = \frac{1}{3}\begin{pmatrix} -2 & 1 & 2 \\ -2 & -2 & -1 \\ 1 & -2 & 2 \end{pmatrix}
>   $$
> - **得到的标准形**为：
>   $$
>   3y_1^2 + 9y_2^2 + 15y_3^2
>   $$