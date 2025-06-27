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