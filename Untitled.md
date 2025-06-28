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

|                                                       | Limited measure     | Infinite measure |
| ----------------------------------------------------- | ------------------- | ---------------- |
| $N = \frac{1}{m}\sum_{i = 1}^{m}N_{i} = \overline{N}$ | near the true value | true value       |
| $\Delta N_{i} = N_{i} - \overline{N}$                 | deviation           | error            |

(三) Estimation error standard deviation

 
| Multiple measure | standard deviation random measurement                                                     | standard deviation of mean value                                                                             |
| ---------------- | ----------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Equation         | $S = \sqrt{\frac{\sum_{i = 1}^{n}(N_{i} - \overline{N})^{2}}{n - 1}}$ （Degree of freedom） | $S_{\overline{N}} = \frac{S}{\sqrt{n}} = \sqrt{\frac{\sum_{i = 1}^{n}(N_{i} - \overline{N})^{2}}{n(n - 1)}}$ |
| Meaning          | Dispersion of each measurement                                                            | Deviation between mean value and true value                                                                  |
| n increase       | Changes slowly                                                                            | Fast Convergence                                                                                             |
| Purposes         | （Excluding bad value）                                                                     | Reduce accidental error                                                                                      |

## 剔除坏值 (Excluding Bad Value) — Pauta 准则

在多次测量中，有时会出现个别数据与其他数据偏离很远的情况，这种数据被称为“坏值”或“可疑值”。Pauta准则（也称 $3S$ 准则）为我们提供了一种统计上的判断依据，来决定是否应该剔除这些可疑数据。

### 1. 理论依据
- **基础**：偶然误差的分布遵循正态分布（高斯分布）。
- **概率**：对于一组测量数据，其测量值 $N_i$ 落在 $(\overline{N} \pm 3S)$ 区间内的概率高达 **99.7%**。
- **推论**：因此，一个测量值出现在该区间之外的概率仅为 **0.3%**，这是一个极小概率事件。在实验中，我们通常认为这种极小概率事件是不会发生的。如果它发生了，我们就有理由怀疑该数据是由过失（如读错、记错）而非偶然因素造成的。

### 2. Pauta 准则 (The Pauta Criterion)
- **定义**：对于一组测量数据，首先计算其算术平均值 $\overline{N}$ 和标准偏差 $S$。
- **判断条件**：计算每一个可疑数据 $N_i$ 与平均值的偏差的绝对值 $|\Delta N_i| = |N_i - \overline{N}|$。
  - 如果  $|N_i - \overline{N}| \geq 3S$，则判定 $N_i$ 为坏值，应予以剔除。
- **注意**：这里的 $S$ 是**单次测量的标准偏差**，不是平均值的标准偏差 $S_{\overline{N}}$。

### 3. 使用步骤与注意事项
1.  **剔除数据**：如果根据 $3S$ 准则判断出存在坏值，应将其从数据组中剔除。
2.  **重新计算**：剔除坏值后，**必须**用余下的数据重新计算新的平均值 $\overline{N}$ 和标准偏差 $S$。
3.  **重复检验**：用新的 $\overline{N}$ 和 $S$ 对余下的数据再次进行检验，直到没有新的坏值可以剔除为止。
4.  **适用范围**：Pauta 准则在测量次数 $n$ 较少时（特别是 **$n \leq 10$**）并不可靠，应谨慎使用或不使用。

### 4. 示例分析
幻灯片中给出了一个包含10个测量数据 ($n=10$) 的例子，其中第10个数据 $L_{10} = 20.33$ cm 明显偏离其他数据。

- **计算过程**：
  1.  包含 $L_{10}$ 在内的10个数据，计算出平均值 $\overline{L} \approx 11.34$ cm。
  2.  计算出标准偏差 $S \approx 3.16$ cm。
  3.  计算出3倍标准偏差 $3S = 9.48$ cm。
  4.  计算第10个数据的偏差：$|L_{10} - \overline{L}| = |20.33 - 11.34| = 8.99$ cm。
- **结论**：
  - 因为 $8.99 < 9.48$，即 $|L_{10} - \overline{L}| < 3S$。
  - 所以，根据 Pauta 准则，**不能**将 $L_{10}$ 作为坏值剔除。
- **示例启示**：这个例子恰好说明了当测量次数较少时（$n=10$），即使某个数据看起来非常“可疑”，Pauta准则也可能因为样本标准差过大而无法将其剔除，这印证了其在小样本量下的局限性。


## 直接测量的不确定度计算 (Calculations of Uncertainty in Direct Measurement)

对于直接测量的物理量，其总不确定度由A类不确定度和B类不确定度共同合成。

### 1. A类不确定度 ($u_A$)

- **来源**：来源于测量过程中的随机效应，通过对多次重复测量的数据进行**统计分析**来评定。
- **计算方法**：A类不确定度在数值上等于**算术平均值的标准偏差** ($S_{\overline{N}}$)。
- **公式**：
  $$ u_A = S_{\overline{N}} = \sqrt{\frac{\sum_{i=1}^{n}(N_i - \overline{N})^2}{n(n-1)}} $$
  其中：
  - $N_i$ 是第 $i$ 次的测量值。
  - $\overline{N}$ 是所有 $n$ 次测量的算术平均值。
  - $n$ 是总的测量次数。

### 2. B类不确定度 ($u_B$)

- **来源**：来源于非统计的因素，通常基于以往的经验、仪器说明书、校准证书等信息来评定。它主要包括**仪器误差**和**读数误差**。
- **计算方法**：假设误差源是均匀分布（或称矩形分布），其不确定度分量等于误差半宽度除以 $\sqrt{3}$。
- **公式**：
  - **仪器误差引入的不确定度** ($u_{\Delta_{ins}}$):
    $$ u_{\Delta_{ins}} = \frac{\Delta_{ins}}{\sqrt{3}} $$
    其中 $\Delta_{ins}$ 是仪器的最大允许误差或误差限。
  - **读数误差引入的不确定度** ($u_{\Delta_{read}}$):
    $$ u_{\Delta_{read}} = \frac{\Delta_{read}}{\sqrt{3}} $$
    其中 $\Delta_{read}$ 是估读引入的误差限。
  - **B类不确定度合成**：
    $$ u_B = \sqrt{u_{\Delta_{ins}}^2 + u_{\Delta_{read}}^2} $$

### 3. 合成不确定度 ($\sigma$)

- **定义**：直接测量的总不确定度，是A类和B类不确定度的合成。
- **公式**：
  $$ \sigma = \sqrt{u_A^2 + u_B^2} = \sqrt{u_A^2 + u_{\Delta_{ins}}^2 + u_{\Delta_{read}}^2} $$
- **简化原则**：在计算合成不确定度时，如果某一个不确定度分量（$u_A$ 或 $u_B$ 的某个分量）远小于其他分量（例如，小于最大分量的 **1/3**），则其平方项（小于最大分量平方的1/10）可以忽略不计，以简化计算。但这并不意味着该项误差不存在。

	






## 仪器误差的确定 (Determining Instrument Errors)

仪器误差 ($\Delta_{ins}$) 是B类不确定度的核心来源之一。根据仪器的不同，其误差限的确定方式可分为以下四类。

---

### 1. 根据仪器上的标志确定 (Labeling on the instrument)

这类仪器通常将最小分度或分辨率直接标注在仪器上，其误差与此标志直接相关。

- **示例：游标卡尺 (Vernier Caliper)**
  - **20分度卡尺**: 仪器上标志最小分度为 **0.05mm**。因此，其仪器误差限 $\Delta_{ins} = 0.05 \text{ mm}$。游标卡尺读数是确定的，无估读过程，因此读数误差 $\Delta_{read}=0$。
  - **50分度卡尺**: 仪器上标志最小分度为 **0.02mm**。因此，其仪器误差限 $\Delta_{ins} = 0.02 \text{ mm}$。同样，读数误差 $\Delta_{read}=0$。

---

### 2. 根据仪器准确度等级确定 (Label accuracy class)

这类仪器在表盘或铭牌上标有准确度等级，如0.1、0.5级等。

- **示例 1：指针式仪表 (Pointer Meter)**
  - **公式**: $\Delta_{ins} = \text{Range} \times \text{Level}\%$
  - **电流表 (Ammeter)**: 0.5级，使用30mA量程。
    - **仪器误差**: $\Delta_{ins} = 30 \text{ mA} \times 0.5\% = 0.15 \text{ mA}$
    - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.08 \text{ mA}$
  - **电压表 (Voltmeter)**: 0.1级，使用7.5V量程。
    - **仪器误差**: $\Delta_{ins} = 7.5 \text{ V} \times 0.1\% = 0.0075 \text{ V}$
    - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.002 \text{ V}$

- **示例 2：电阻箱 (Resistance Box)**
  - **公式**: $\Delta_{ins} = \text{Measured Value} \times \text{Level}\%$
  - **条件**: 0.1级，读数值为 2700Ω。
  - **仪器误差**: $\Delta_{ins} = 2700 \Omega \times 0.1\% = 2.7 \Omega$
  - **读数误差**: $\Delta_{read}=0$。

---

### 3. 根据仪器说明书或检定规程确定 (Implied or instructions labeling)

许多精密仪器的误差限会在其配套的说明书或相关的检定规程中给出。

- **示例 1：普通刻度尺 (Ruler)**
  - **条件**: 最小分度为 0.5mm。
  - **仪器误差**: $\Delta_{ins} = 0.5 \text{ mm}$
  - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.1 \text{ mm}$

- **示例 2：钢卷尺 (Steel Tape - GB level two)**
  - **条件**: 最小分度 1mm，误差公式遵循国家标准 (GB)。
  - **仪器误差**: $\Delta_{ins} = (0.2 \cdot L + 0.3) \text{ mm}$ (其中L为测量长度，单位m)。
    - 当 L=0.5m, $\Delta_{ins} = 0.4 \text{ mm}$
    - 当 L=1.5m, $\Delta_{ins} = 0.6 \text{ mm}$
    - 当 L=5m, $\Delta_{ins} = 1.3 \text{ mm}$
  - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.2 \text{ mm}$

- **示例 3：数字万用表 (Digital Multimeter - DT920)**
  - **条件**: 准确度由公式给出，如 `±(0.8% read + 2 digits)`。测量值为 408V 时。
  - **仪器误差**: $\Delta_{ins} = 0.8\% \times 408 + 2 = 3.3 + 2 = 5.3 \text{ V}$
  - **读数误差**: $\Delta_{read}=0$ (数值是确定的)。

- **示例 4：螺旋测微器 (Micrometer Screw)**
  - **条件**: 最小分度 0.01mm。
  - **仪器误差 (据说明书)**: $\Delta_{ins} = 0.005 \text{ mm}$
  - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.002 \text{ mm}$

- **示例 5：读数显微镜 (Shift Microscope)**
  - **条件**: 最小分度 0.01mm。
  - **仪器误差 (据说明书)**: $\Delta_{ins} = 0.01 \text{ mm}$
  - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.002 \text{ mm}$

- **示例 6：迈克尔逊干涉仪 (Michelson Interferometer)**
  - **条件**: 最小分度 0.0001mm。
  - **仪器误差 (据说明书)**: $\Delta_{ins} = 0.0001 \text{ mm}$
  - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.00002 \text{ mm}$

---

### 4. 根据经验估计确定 (Instrument error estimation)

在仪器未明确给出误差信息的情况下，可根据仪器类型进行估计。

- **a. 连续读数仪器 (Continuous reading instruments)**
  - **规则**: 仪器误差限 $\Delta_{ins}$ 估计为**最小分度值的一半**。
  - **示例 (刻度尺 Ruler)**:
    - **条件**: 最小分度 1mm。
    - **仪器误差**: $\Delta_{ins} = 0.5 \times \text{scale} = 0.5 \text{ mm}$
    - **读数误差**: $\Delta_{read} = 0.2 \times \text{scale} = 0.2 \text{ mm}$

- **b. 非连续读数仪器 (Discontinuous reading instruments)**
  - **规则**: 仪器误差限 $\Delta_{ins}$ 估计为**一个最小分度值**。
  - **示例 1 (数字秒表 Digital Stopwatch)**:
    - **条件**: 最小分度 0.01s。
    - **仪器误差**: $\Delta_{ins} = \text{minimum scale} = 0.01 \text{ s}$
    - **读数误差**: $\Delta_{read}=0$。
  - **示例 2 (分光计 Spectrometer)**:
    - **条件**: 最小分度 1' (1角分)。
    - **仪器误差**: $\Delta_{ins} = \text{minimum scale} = 1'$
    - **读数误差**: $\Delta_{read}=0$。


