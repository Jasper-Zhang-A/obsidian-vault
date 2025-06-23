# 例题完整解答：二次型化为标准形 (PPT第34页)

> [!abstract] 核心思路回顾
> 解决这类问题的完整流程是：
> 1.  从二次型函数写出其对应的对称矩阵 $A$。
> 2.  求出矩阵 $A$ 的所有特征值 $\lambda_i$。
> 3.  求出每个特征值对应的标准正交特征向量 $\mathbf{q}_i$。（如果特征值不重复，则其特征向量必然正交，只需单位化；如果特征值重复，则需对同一特征空间的基向量进行施密特正交化再单位化）。
> 4.  利用特征值写出标准形，利用标准正交特征向量构造正交矩阵 $P$。

---

### **题目**
**已知二次型**: $Q(\mathbf{x}) = 9x_1^2 + 7x_2^2 + 11x_3^2 - 8x_1x_2 + 8x_1x_3$。
求正交矩阵 $P$ 和对应的标准形。

### **第一步：从二次型写出对称矩阵 A**
根据二次型的系数，我们可以得到其对应的对称矩阵 $A$：
$$
A = \begin{pmatrix} 9 & -4 & 4 \\ -4 & 7 & 0 \\ 4 & 0 & 11 \end{pmatrix}
$$

### **第二步：计算 A 的特征值 (λ)**
我们需要求解特征方程 $\det(A - \lambda I) = 0$。
$$
\det(A - \lambda I) = \begin{vmatrix} 9-\lambda & -4 & 4 \\ -4 & 7-\lambda & 0 \\ 4 & 0 & 11-\lambda \end{vmatrix} = 0
$$
展开行列式得到特征多项式：
$$
\lambda^3 - 27\lambda^2 + 207\lambda - 405 = 0
$$
通过尝试，可以发现 $\lambda=3, 9, 15$ 是方程的根。
所以，矩阵 $A$ 的特征值为 $\lambda_1 = 3, \lambda_2 = 9, \lambda_3 = 15$。

> [!tip]
> 我们可以立刻知道该二次型的标准形为 $3y_1^2 + 9y_2^2 + 15y_3^2$。接下来的步骤是为了求出变换矩阵 $P$。

### **第三步：计算标准正交特征向量 (q)**

#### 1. 当 $\lambda_1 = 3$ 时
求解线性方程组 $(A - 3I)\mathbf{x} = \mathbf{0}$：
$$
\begin{pmatrix} 6 & -4 & 4 \\ -4 & 4 & 0 \\ 4 & 0 & 8 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \mathbf{0}
$$
化简得到一个基础解系（基向量）：$\mathbf{p}_1 = \begin{pmatrix} -2 \\ -2 \\ 1 \end{pmatrix}$。
单位化：$||\mathbf{p}_1|| = \sqrt{(-2)^2+(-2)^2+1^2} = \sqrt{9} = 3$。
$$
\mathbf{q}_1 = \frac{\mathbf{p}_1}{||\mathbf{p}_1||} = \frac{1}{3}\begin{pmatrix} -2 \\ -2 \\ 1 \end{pmatrix}
$$

#### 2. 当 $\lambda_2 = 9$ 时
求解线性方程组 $(A - 9I)\mathbf{x} = \mathbf{0}$：
$$
\begin{pmatrix} 0 & -4 & 4 \\ -4 & -2 & 0 \\ 4 & 0 & 2 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \mathbf{0}
$$
化简得到一个基础解系：$\mathbf{p}_2 = \begin{pmatrix} 1 \\ -2 \\ -2 \end{pmatrix}$。
单位化：$||\mathbf{p}_2|| = \sqrt{1^2+(-2)^2+(-2)^2} = \sqrt{9} = 3$。
$$
\mathbf{q}_2 = \frac{\mathbf{p}_2}{||\mathbf{p}_2||} = \frac{1}{3}\begin{pmatrix} 1 \\ -2 \\ -2 \end{pmatrix}
$$

#### 3. 当 $\lambda_3 = 15$ 时
求解线性方程组 $(A - 15I)\mathbf{x} = \mathbf{0}$：
$$
\begin{pmatrix} -6 & -4 & 4 \\ -4 & -8 & 0 \\ 4 & 0 & -4 \end{pmatrix} \begin{pmatrix} x_1 \\ x_2 \\ x_3 \end{pmatrix} = \mathbf{0}
$$
化简得到一个基础解系：$\mathbf{p}_3 = \begin{pmatrix} 2 \\ -1 \\ 2 \end{pmatrix}$。
单位化：$||\mathbf{p}_3|| = \sqrt{2^2+(-1)^2+2^2} = \sqrt{9} = 3$。
$$
\mathbf{q}_3 = \frac{\mathbf{p}_3}{||\mathbf{p}_3||} = \frac{1}{3}\begin{pmatrix} 2 \\ -1 \\ 2 \end{pmatrix}
$$

### **第四步：写出正交矩阵 P 和标准形**

将我们求出的标准正交特征向量 $\mathbf{q}_1, \mathbf{q}_2, \mathbf{q}_3$ 作为列向量，即可构造出正交矩阵 $P$。

> [!success] 最终答案
> - **正交矩阵 P** 为：
>   $$
>   P = \begin{bmatrix} \mathbf{q}_1 & \mathbf{q}_2 & \mathbf{q}_3 \end{bmatrix} = \frac{1}{3}\begin{pmatrix} -2 & 1 & 2 \\ -2 & -2 & -1 \\ 1 & -2 & 2 \end{pmatrix}
>   $$
> - **二次型的标准形**为：
>   $$
>   3y_1^2 + 9y_2^2 + 15y_3^2
>   $$