# 例题精解：对称矩阵的正交对角化

**题目**：设矩阵 $A = \begin{pmatrix} 3 & 0 & 1 \\ 0 & 4 & 0 \\ 1 & 0 & 3 \end{pmatrix}$，求一个正交矩阵 $Q$，使得 $Q^{-1}AQ = \Lambda$ 为对角矩阵。

**核心思路**：
由于 $A$ 是对称矩阵，它必然可以被正交对角化。我们需要的正交矩阵 $Q$ 是由 $A$ 的标准正交特征向量构成的，而对角矩阵 $\Lambda$ 是由对应的特征值构成的。

---

### 第一步：求矩阵 A 的特征值

我们通过求解特征方程 $\det(A - \lambda I) = 0$ 来得到特征值 $\lambda$。
$$
\det(A - \lambda I) = \begin{vmatrix} 3-\lambda & 0 & 1 \\ 0 & 4-\lambda & 0 \\ 1 & 0 & 3-\lambda \end{vmatrix} = 0
$$
沿第二行展开，计算行列式：
$$
(4-\lambda) \begin{vmatrix} 3-\lambda & 1 \\ 1 & 3-\lambda \end{vmatrix} = (4-\lambda) \left[ (3-\lambda)^2 - 1 \right] = 0
$$
$$
(4-\lambda) (\lambda^2 - 6\lambda + 9 - 1) = (4-\lambda) (\lambda^2 - 6\lambda + 8) = 0
$$
$$
(4-\lambda)(\lambda-2)(\lambda-4) = 0
$$
解得特征值为：$\lambda_1 = 2$，$\lambda_2 = 4$（二重根）。

---

### 第二步：求每个特征值对应的特征向量

#### 1. 当 $\lambda_1 = 2$ 时
求解线性方程组 $(A - 2I)\mathbf{x} = \mathbf{0}$：
$$
\begin{pmatrix} 1 & 0 & 1 \\ 0 & 2 & 0 \\ 1 & 0 & 1 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \implies \begin{cases} x_1 + x_3 = 0 \\ 2x_2 = 0 \end{cases} \implies \begin{cases} x_1 = -x_3 \\ x_2 = 0 \end{cases}
$$
取一个基础解系（基向量），令 $x_3=1$，得到特征向量：
$$
\mathbf{p}_1 = \begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix}
$$

#### 2. 当 $\lambda_2 = 4$ 时
求解线性方程组 $(A - 4I)\mathbf{x} = \mathbf{0}$：
$$
\begin{pmatrix} -1 & 0 & 1 \\ 0 & 0 & 0 \\ 1 & 0 & -1 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix} \implies x_1 - x_3 = 0 \implies x_1 = x_3
$$
这里的 $x_2$ 是自由变量。我们可以取两个线性无关的向量作为这个特征空间的基础解系：
- 令 $x_3=1, x_2=0$，得到 $\mathbf{p}_2 = \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}$
- 令 $x_3=0, x_2=1$，得到 $\mathbf{p}_3 = \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}$

---

### 第三步：将特征向量正交单位化，构造 Q 和 Λ

#### 1. 施密特正交化
- 不同特征空间的特征向量（如 $\mathbf{p}_1$ 与 $\mathbf{p}_2, \mathbf{p}_3$）对于**对称矩阵一定是正交的**。
- 我们需要检查同一特征空间（$\lambda=4$）中的基向量 $\mathbf{p}_2$ 和 $\mathbf{p}_3$ 是否正交：
  $$
  \mathbf{p}_2 \cdot \mathbf{p}_3 = (1)(0) + (0)(1) + (1)(0) = 0
  $$
  它们已经正交了，所以我们无需进行施密特正交化。

#### 2. 单位化
将所有基向量 $\mathbf{p}_1, \mathbf{p}_2, \mathbf{p}_3$ 除以各自的模长，得到标准正交基：
- $||\mathbf{p}_1|| = \sqrt{(-1)^2 + 0^2 + 1^2} = \sqrt{2}$
- $||\mathbf{p}_2|| = \sqrt{1^2 + 0^2 + 1^2} = \sqrt{2}$
- $||\mathbf{p}_3|| = \sqrt{0^2 + 1^2 + 0^2} = 1$

得到标准正交的特征向量：
$$
\mathbf{q}_1 = \frac{1}{\sqrt{2}}\begin{pmatrix} -1 \\ 0 \\ 1 \end{pmatrix}, \quad \mathbf{q}_2 = \frac{1}{\sqrt{2}}\begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix}, \quad \mathbf{q}_3 = \begin{pmatrix} 0 \\ 1 \\ 0 \end{pmatrix}
$$

#### 3. 构造 Q 和 Λ
- 将标准正交特征向量作为列，构成正交矩阵 $Q$。
- 将对应的特征值放在对角线上，构成对角矩阵 $\Lambda$。

**最终答案**：
$$
Q = \begin{pmatrix} -1/\sqrt{2} & 1/\sqrt{2} & 0 \\ 0 & 0 & 1 \\ 1/\sqrt{2} & 1/\sqrt{2} & 0 \end{pmatrix}, \quad \Lambda = \begin{pmatrix} 2 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & 4 \end{pmatrix}
$$
*注意：Q 和 Λ 中列的顺序必须对应。例如，这里 Q 的第一列对应 $\lambda=2$，第二、三列对应 $\lambda=4$。*