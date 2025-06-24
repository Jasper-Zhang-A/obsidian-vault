# 综合文件中的行列式问题全解

> [!abstract] 笔记说明
> 本笔记汇总了您提供的所有文件中关于行列式计算的练习题，并为每一题提供了详细的、循序渐进的解答过程。所有数学公式均使用 LaTeX 书写。

---

## 源自《行列式题目.pdf》

> [!example] Q1. 计算行列式
> $$
> \begin{vmatrix} 5 & 5 & 6 & 6 & 7 \\ 4 & 0 & 4 & 0 & 4 \\ 3 & 0 & 0 & 3 & 0 \\ 0 & 0 & 0 & 2 & 0 \\ 5 & 6 & 7 & 1 & 8 \end{vmatrix}
> $$
> 
> **解答过程**:
> 观察到第四行只有一个非零元素，因此沿第四行进行代数余子式展开最为简便。
> $$
> \det = (-1)^{4+4} \cdot 2 \cdot \begin{vmatrix} 5 & 5 & 6 & 7 \\ 4 & 0 & 4 & 4 \\ 3 & 0 & 0 & 0 \\ 5 & 6 & 7 & 8 \end{vmatrix}
> $$
> 接下来，对得到的4x4行列式沿第三行展开：
> $$
> = 2 \cdot \left( (-1)^{3+1} \cdot 3 \cdot \begin{vmatrix} 5 & 6 & 7 \\ 0 & 4 & 4 \\ 6 & 7 & 8 \end{vmatrix} \right)
> $$
> 现在计算这个3x3行列式：
> $$
> = 6 \cdot [5(32-28) - 6(0-24) + 7(0-24)]
> $$
> $$
> = 6 \cdot [5(4) + 6(24) - 7(24)] = 6 \cdot [20 - 24] = 6 \cdot (-4) = -24
> $$
> 
> **最终答案**: -24

> [!example] Q2. 行列式性质应用
> 如果 $\begin{vmatrix} a & b & c \\ d & e & f \\ g & h & i \end{vmatrix} = 7$，计算以下行列式：
> (a) $\begin{vmatrix} a & b & c \\ 2d+a & 2e+b & 2f+c \\ g & h & i \end{vmatrix}$
> (b) $\begin{vmatrix} a & b & c \\ d+3g & e+3h & f+3i \\ g & h & i \end{vmatrix}$
> 
> **解答过程**:
> (a) 利用行列式的线性性质，将第二行拆分：
> $$
> \begin{vmatrix} a & b & c \\ 2d+a & 2e+b & 2f+c \\ g & h & i \end{vmatrix} = \begin{vmatrix} a & b & c \\ 2d & 2e & 2f \\ g & h & i \end{vmatrix} + \begin{vmatrix} a & b & c \\ a & b & c \\ g & h & i \end{vmatrix}
> $$
> 第二个行列式因为有两行相同，其值为0。第一个行列式可以从第二行提出公因子2：
> $$
> = 2 \begin{vmatrix} a & b & c \\ d & e & f \\ g & h & i \end{vmatrix} + 0 = 2 \times 7 = 14
> $$
> (b) 这个变换是初等行变换中的倍加变换：$R_2 \to R_2 + 3R_3$。该变换不改变行列式的值。
> 
> **最终答案**:
> (a) 14
> (b) 7

> [!example] Q3. 行列式与矩阵运算
> 设 A 和 B 均为 $4 \times 4$ 矩阵，且 $\det A = -3$，$\det B = -1$。计算：
> (a) $\det AB$
> (b) $\det B^5$
> (c) $\det 2A$
> (d) $\det A^T B A$
> (e) $\det B^{-1} A B$
> 
> **解答过程**:
> (a) $\det(AB) = (\det A)(\det B) = (-3)(-1) = 3$
> (b) $\det(B^5) = (\det B)^5 = (-1)^5 = -1$
> (c) $\det(2A) = 2^4 (\det A) = 16(-3) = -48$  (因为A是4x4矩阵)
> (d) $\det(A^TBA) = (\det A^T)(\det B)(\det A) = (\det A)(\det B)(\det A) = (-3)(-1)(-3) = -9$
> (e) $\det(B^{-1}AB) = (\det B^{-1})(\det A)(\det B) = \frac{1}{\det B}(\det A)(\det B) = \det A = -3$
> 
> **最终答案**:
> (a) 3, (b) -1, (c) -48, (d) -9, (e) -3

> [!example] Q4. 行列式与直线方程
> 证明：$\mathbb{R}^2$ 中经过两个不同点 $(x_1, y_1)$ 和 $(x_2, y_2)$ 的直线方程可以写成：
> $$
> \det \begin{pmatrix} 1 & x & y \\ 1 & x_1 & y_1 \\ 1 & x_2 & y_2 \end{pmatrix} = 0
> $$
> 
> **解答过程**:
> 沿第一列展开行列式：
> $$
> 1(x_1y_2 - x_2y_1) - 1(xy_2 - x_2y) + 1(xy_1 - x_1y) = 0
> $$
> 整理后得到：
> $$
> x(y_1 - y_2) - y(x_1 - x_2) + (x_1y_2 - x_2y_1) = 0
> $$
> 这可以改写为 $(y_1 - y_2)x + (x_2 - x_1)y + (x_1y_2 - x_2y_1) = 0$，是一个形如 $Ax+By+C=0$ 的直线方程。
>
> 验证：
> 1.  如果将 $(x,y)$ 替换为 $(x_1, y_1)$，行列式的第一行和第二行相同，值为0。
> 2.  如果将 $(x,y)$ 替换为 $(x_2, y_2)$，行列式的第一行和第三行相同，值为0。
> 因此，点 $(x_1, y_1)$ 和 $(x_2, y_2)$ 都在这条直线上。证毕。

> [!example] Q5. 伴随矩阵与逆矩阵
> (a) $A = \begin{pmatrix} 1 & 1 & 3 \\ -2 & 2 & 1 \\ 0 & 1 & 1 \end{pmatrix}$
> (b) $B = \begin{pmatrix} 1 & -1 & 2 \\ 0 & 2 & 1 \\ 2 & 0 & 4 \end{pmatrix}$
> 
> **解答过程 (a)**:
> 1.  计算 $\det(A) = 1(2-1) - 1(-2-0) + 3(-2-0) = 1 + 2 - 6 = -3$。
> 2.  计算A的九个代数余子式，构成余子矩阵：
>     $C = \begin{pmatrix} 1 & 2 & -2 \\ 2 & 1 & -1 \\ -5 & -7 & 4 \end{pmatrix}$
> 3.  将余子矩阵转置得到伴随矩阵：
>     $\text{adj}(A) = C^T = \begin{pmatrix} 1 & 2 & -5 \\ 2 & 1 & -7 \\ -2 & -1 & 4 \end{pmatrix}$
> 4.  计算逆矩阵 $A^{-1} = \frac{1}{\det(A)}\text{adj}(A)$。
> 
> **解答过程 (b)**:
> 5.  计算 $\det(B) = 1(8-0) - (-1)(0-2) + 2(0-4) = 8 - 2 - 8 = -2$。
> 6.  计算B的余子矩阵：
>     $C = \begin{pmatrix} 8 & 2 & -4 \\ 4 & 0 & -2 \\ -5 & -1 & 2 \end{pmatrix}$
> 7.  将余子矩阵转置得到伴随矩阵：
>     $\text{adj}(B) = C^T = \begin{pmatrix} 8 & 4 & -5 \\ 2 & 0 & -1 \\ -4 & -2 & 2 \end{pmatrix}$
> 8.  计算逆矩阵 $B^{-1} = \frac{1}{\det(B)}\text{adj}(B)$。
> 
> **最终答案**:
> (a) $\text{adj}(A) = \begin{pmatrix} 1 & 2 & -5 \\ 2 & 1 & -7 \\ -2 & -1 & 4 \end{pmatrix}$, $A^{-1} = -\frac{1}{3}\begin{pmatrix} 1 & 2 & -5 \\ 2 & 1 & -7 \\ -2 & -1 & 4 \end{pmatrix}$
> (b) $\text{adj}(B) = \begin{pmatrix} 8 & 4 & -5 \\ 2 & 0 & -1 \\ -4 & -2 & 2 \end{pmatrix}$, $B^{-1} = -\frac{1}{2}\begin{pmatrix} 8 & 4 & -5 \\ 2 & 0 & -1 \\ -4 & -2 & 2 \end{pmatrix}$

---
## 源自《李良线性代数复习.pdf》

> [!example] 第18页 例题1
> 如果 $$|\begin{matrix} a_{1}&b_{1}&c_{1}\\ a_{2}&b_{2}&c_{2}\\ a_{3}&b_{3}&c_{3} \end{matrix}|=-2$$，计算 $$\begin{matrix} a_{1}+b_{1}&b_{1}+c_{1}&a_{1}+c_{1}\\ a_{2}+b_{2}&b_{2}+c_{2}&a_{2}+c_{2}\\ a_{3}+b_{3}&b_{3}+c_{3}&a_{3}+c_{3} \end{matrix}$$。
> 
> **解答过程**:
> 记原矩阵为 $D$。新行列式为 $D'$。利用行列式的线性性质，对每一列进行拆分。
> 1.  对第一列拆分:
>     $D' = |\mathbf{a+b}, \mathbf{b+c}, \mathbf{a+c}| = |\mathbf{a}, \mathbf{b+c}, \mathbf{a+c}| + |\mathbf{b}, \mathbf{b+c}, \mathbf{a+c}|$
> 2.  对第一个行列式继续拆分:
>     $|\mathbf{a}, \mathbf{b+c}, \mathbf{a+c}| = |\mathbf{a}, \mathbf{b}, \mathbf{a+c}| + |\mathbf{a}, \mathbf{c}, \mathbf{a+c}| = |\mathbf{a}, \mathbf{b}, \mathbf{a}| + |\mathbf{a}, \mathbf{b}, \mathbf{c}| + |\mathbf{a}, \mathbf{c}, \mathbf{a}| + |\mathbf{a}, \mathbf{c}, \mathbf{c}|$
>     其中含相同列的行列式值为0，所以此项等于 $|\mathbf{a}, \mathbf{b}, \mathbf{c}| = \det(A) = -2$。
> 3.  对第二个行列式继续拆分:
>     $|\mathbf{b}, \mathbf{b+c}, \mathbf{a+c}| = |\mathbf{b}, \mathbf{b}, \mathbf{a+c}| + |\mathbf{b}, \mathbf{c}, \mathbf{a+c}| = 0 + |\mathbf{b}, \mathbf{c}, \mathbf{a}| + |\mathbf{b}, \mathbf{c}, \mathbf{c}|$
>     $|\mathbf{b}, \mathbf{c}, \mathbf{a}|$ 通过两次列交换得到 $|\mathbf{a}, \mathbf{b}, \mathbf{c}|$，所以 $|\mathbf{b}, \mathbf{c}, \mathbf{a}| = (-1)^2 |\mathbf{a}, \mathbf{b}, \mathbf{c}| = -2$。
> 4.  将结果相加: $D' = (-2) + (-2) = -4$。
> 
> **另解**: 观察到新矩阵的列向量是原矩阵列向量的线性组合。设 $C_1, C_2, C_3$ 为新矩阵的列， $c_1, c_2, c_3$ 为原矩阵的列。则 $C_1 = c_1+c_2, C_2=c_2+c_3, C_3=c_1+c_3$。可以看作是原矩阵右乘了一个矩阵 $K=\begin{pmatrix} 1&0&1 \\ 1&1&0 \\ 0&1&1 \end{pmatrix}$。
> $\det(D') = \det(A \cdot K) = \det(A) \det(K) = (-2) \cdot (1(1)-0+1(1)) = (-2)(2) = -4$。
>
> **最终答案**: -4