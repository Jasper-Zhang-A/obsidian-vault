## 误差的基本概念

### 1. 绝对误差 (Absolute Error)
- 绝对误差（Error）指测量值与真值之间的差异。
- **公式**：
  $$ \Delta'N (\text{error}) = N_{i} (\text{measure}) - N (\text{true}) $$

### 2. 改正值 (Correction Value)
- 改正值（Correction Value）与绝对误差大小相等，符号相反。
- **公式**：
  $$ \Delta (\text{Correction value}) = N (\text{true}) - N_{i} (\text{measure}) = -\Delta'N (\text{error}) $$
- 如果知道改正值，可以通过测量值计算出更接近真值的结果：
  $$ N (\text{true}) = N_{i} (\text{measure}) + \Delta (\text{correction}) $$

### 3. 相对误差 (Relative Error)
- 相对误差（Relative Error）是绝对误差与真值的比值，通常用百分比表示，它能更好地反映测量的可信赖程度。
- **公式**：
  $$ E = \frac{\Delta'N}{N} \times 100\% $$
-  重要！一般当相对误差小于 10% 的时候，我们一般保留1位有效数字。一般当相对误差大于 10% 的时候，我们一般保留2位有效数字。

## 系统误差与偶然误差

### 1. 系统误差 (Systematic Error)
- **特点**：系统误差具有确定性或规律性，在相同条件下重复测量时，它会以相同的方式影响结果。
- **可消除性**：系统误差是**可以被发现并修正**的。
- **示例**：
  - **零点误差**：仪器（如天平、电压表）的起始读数不为零。可以通过测量前校准或在测量结果中减去零点读数来修正。

### 2. 偶然误差 (Random Error)
- **特点**：偶然误差（也称随机误差）是由各种不可预知的、随机的因素引起的。其大小和符号都无规律，但多次测量的整体会呈现出统计规律（如正态分布）。
- **概率分布**：单个偶然误差是不可预测的，但大量偶然误差的分布满足概率统计规律。

---

## 打靶比喻：精密度、正确度与准确度

这个比喻非常直观地解释了误差、精密度(Precision)、正确度(Trueness)和准确度(Accuracy)之间的关系。

- ### 精密度 (Precision)
  - **决定因素**：由**偶然误差 (Random Error)** 决定。
  - **表现**：多次打靶的弹着点的**离散或分散程度**。弹孔越集中，说明偶然误差越小，**精密度越高**。

- ### 正确度 (Trueness)
  - **决定因素**：由**系统误差 (Systematic Error)** 决定。
  - **表现**：所有弹着点**分布的中心**与**靶心**的偏离程度。弹着点中心离靶心越近，说明系统误差越小，**正确度越高**。

- ### 准确度 (Accuracy)
  - **定义**：准确度是**精密度**和**正确度**的综合体现，表示测量结果与真值的一致程度。
  - **关系式**：
    $$ \text{Accuracy} = \text{Precision} + \text{Trueness} $$
  - **表现**：一组弹孔既要**集中**（高精密度），又要**靠近靶心**（高正确度），才能被称为高准确度。

| Limited measure                                       | Infinite measure    |            |
| ----------------------------------------------------- | ------------------- | ---------- |
| $N = \frac{1}{m}\sum_{i = 1}^{m}N_{i} = \overline{N}$ | near the true value | true value |
| $\Delta N_{i} = N_{i} - \overline{N}$                 | deviation           | error      |

(三) Estimation error standard deviation

