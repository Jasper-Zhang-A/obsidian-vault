# 详解：通过行变换求解 PA = B

> [!example] 题目详情 (源自手写稿P2)
> 已知实数 $a$，矩阵 $A = \begin{pmatrix} 1 & 1 & 2 \\ 2 & 3 & 7 \\ a & 0 & -a \end{pmatrix}$ 与矩阵 $B = \begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \\ 2 & 1 & 1\end{pmatrix}$ 是行等价的。
> 
> (a) 求 $a$ 的值。
> (b) 求一个可逆矩阵 $P$，使得 $PA=B$。

> [!tip] 解题方法
> 根据提示，我们的核心策略是构建增广矩阵 `[A | I]`，然后通过一系列初等行变换，将左侧的矩阵A变换为矩阵B。在这一过程中，右侧的单位矩阵I将自动变换为我们所求的矩阵P。即：
> $$
> [A | I] \xrightarrow{\text{初等行变换}} [B | P]
> $$

---

### 探索与分析

在我们开始计算前，有一个前提需要验证。如果两个矩阵是行等价的，那么它们的**简化行阶梯形矩阵 (RREF)** 必须是相同的。让我们先分别求一下 A 和 B 的RREF。

#### 1. 对矩阵 A 进行行化简

$$
A = \begin{pmatrix} 1 & 1 & 2 \\ 2 & 3 & 7 \\ a & 0 & -a \end{pmatrix} 
\xrightarrow[R_3 \to R_3 - aR_1]{R_2 \to R_2 - 2R_1}
\begin{pmatrix} 1 & 1 & 2 \\ 0 & 1 & 3 \\ 0 & -a & -3a \end{pmatrix}
$$
$$
\xrightarrow[R_3 \to R_3 + aR_2]{R_1 \to R_1 - R_2}
\begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{pmatrix}
$$
所以，矩阵 $A$ 的简化行阶梯形矩阵 `RREF(A)` 是 $\begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 3 \\ 0 & 0 & 0 \end{pmatrix}$，无论 $a$ 取何值。

#### 2. 对矩阵 B 进行行化简

$$
B = \begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \\ 2 & 1 & 1\end{pmatrix}
\xrightarrow{R_3 \to R_3 - 2R_1}
\begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \\ 0 & 1 & 3 \end{pmatrix}
$$
$$
\xrightarrow{R_3 \to R_3 - R_2}
\begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \\ 0 & 0 & 2 \end{pmatrix}
\xrightarrow{R_3 \to \frac{1}{2}R_3}
\begin{pmatrix} 1 & 0 & -1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{pmatrix}
$$
$$
\xrightarrow[R_2 \to R_2 - R_3]{R_1 \to R_1 + R_3}
\begin{pmatrix} 1 & 0 & 0 \\ 0 & 1 & 0 \\ 0 & 0 & 1 \end{pmatrix} = I
$$
所以，矩阵 $B$ 的简化行阶梯形矩阵 `RREF(B)` 是单位矩阵 $I$。

> [!warning] 发现问题
> **RREF(A) $\neq$ RREF(B)**。
> 
> 根据线性代数的定义，两个矩阵是行等价的**充要条件**是它们拥有相同的简化行阶梯形矩阵。
> 
> 在本题中，我们计算出 $A$ 的RREF是一个有全零行的矩阵（说明 $A$ 是奇异矩阵，秩为2），而 $B$ 的RREF是单位矩阵（说明 $B$ 是可逆矩阵，秩为3）。由于它们的RREF不同，所以**矩阵A和矩阵B在任何情况下都不可能是行等价的**。

---

### 结论

> [!abstract] 最终答案
> 由于题目给出的核心条件“矩阵A与矩阵B是行等价的”与两个矩阵本身的性质相矛盾，所以这道题的**前提条件不成立**。
> 
> - **(a) 值**: 不存在任何实数 $a$ 能使得 $A$ 与 $B$ 行等价。
> - **(b) P**: 因为 $A$ 和 $B$ 不行等价，所以也就不存在一个可逆矩阵 $P$ (初等行变换的乘积)，使得 $PA=B$。
> 
> 这很可能是原始题目中的笔误。不过，通过分析RREF来判断行等价性的这个思路本身，是解决这类问题的关键。