# Lebesgue 测度

> 从区间长度到一般集合的"大小"——测度论的基石。

## 1. 外测度

### 1.1 定义

**定义 1.1**　集合 $E \subseteq \mathbb{R}^n$ 的 **Lebesgue 外测度**：

$$m^*(E) = \inf \left\{ \sum_{i=1}^{\infty} |I_i| : E \subseteq \bigcup_{i=1}^{\infty} I_i, \ I_i \text{ 为开区间} \right\}$$

其中 $|I_i|$ 表示区间 $I_i$ 的体积。

> **直觉**：用可数个开区间覆盖 $E$，取体积和的下确界。

### 1.2 外测度的性质

**定理 1.1**　外测度满足：

| 性质 | 内容 |
|------|------|
| 非负性 | $m^*(E) \geq 0$，$m^*(\emptyset) = 0$ |
| 单调性 | $A \subseteq B \Rightarrow m^*(A) \leq m^*(B)$ |
| 次可数可加性 | $m^*\left(\bigcup E_i\right) \leq \sum m^*(E_i)$ |

**定理 1.2（区间的外测度）**　$m^*(I) = |I|$（区间 $I$ 的外测度等于其长度）。

**定理 1.3（平移不变性）**　$m^*(E + x) = m^*(E)$。

> **注意**：外测度不是测度——它对不相交集合不满足可加性（即 $m^*(A \cup B) \neq m^*(A) + m^*(B)$ 可能成立，当 $A, B$ 不"好"时）。

**反例**：存在不相交的 $A, B$ 使 $m^*(A \cup B) < m^*(A) + m^*(B)$（Vitali 集构造）。

---

## 2. 可测集

### 2.1 Carathéodory 条件

**定义 2.1**　集合 $E$ 是 **Lebesgue 可测的**，若对任意集合 $A$：

$$m^*(A) = m^*(A \cap E) + m^*(A \cap E^c)$$

> **直觉**：可测集能够"干净地"把任意集合切成两半，不丢失测度。

**等价条件**：$E$ 可测 $\iff$ 对任意 $A \subseteq E$，$B \subseteq E^c$：$m^*(A \cup B) = m^*(A) + m^*(B)$。

### 2.2 可测集的性质

**定理 2.1**：
1. 可测集全体构成一个 $\sigma$-代数（对可数并、可数交、补运算封闭）
2. Borel 集都是可测的（开集、闭集、$F_\sigma$、$G_\delta$ 集等）
3. 外测度为零的集合可测（零测集）

**$\sigma$-代数**：集合族 $\mathcal{F}$ 满足：
- $\emptyset \in \mathcal{F}$
- $A \in \mathcal{F} \Rightarrow A^c \in \mathcal{F}$
- $A_n \in \mathcal{F} \Rightarrow \bigcup A_n \in \mathcal{F}$

**推论 2.1**　可测集的可数并、可数交、差集、补集都可测。

**推论 2.2**　Borel $\sigma$-代数 $\mathcal{B}(\mathbb{R})$ 由开集生成，包含所有开集、闭集、$F_\sigma$、$G_\delta$、$F_{\sigma\delta}$、$G_{\delta\sigma}$ 等。

### 2.3 Lebesgue 测度

将外测度限制在可测集族上，得到 **Lebesgue 测度** $m$：

$$m(E) = m^*(E) \quad (\text{当 } E \text{ 可测})$$

**定理 2.2（Lebesgue 测度的性质）**：
- **可数可加性**：$E_i$ 互不相交可测 $\Rightarrow m\left(\bigcup E_i\right) = \sum m(E_i)$
- **平移不变性**：$m(E + x) = m(E)$
- **正则性**：对可测集 $E$：
  - $m(E) = \inf\{m(G) : E \subseteq G, G \text{ 开}\}$
  - $m(E) = \sup\{m(F) : F \subseteq E, F \text{ 闭}\}$

**定理 2.3（测度的连续性）**：
- **下连续性**：$E_1 \subseteq E_2 \subseteq \cdots$，$E = \bigcup E_n$ $\Rightarrow$ $m(E) = \lim m(E_n)$
- **上连续性**：$E_1 \supseteq E_2 \supseteq \cdots$，$m(E_1) < \infty$，$E = \bigcap E_n$ $\Rightarrow$ $m(E) = \lim m(E_n)$

**推论 2.3**　$m(\bigcup E_n) \leq \sum m(E_n)$（次可数可加性，对可测集）。

---

## 3. 不可测集

### 3.1 Vitali 集

**构造**：在 $[0, 1)$ 上定义等价关系 $x \sim y \iff x - y \in \mathbb{Q}$。从每个等价类中选一个代表元，组成集合 $V$（需要选择公理）。

**定理 3.1**　$V$ 不可测。

> **证明提示**：$\{V + r : r \in \mathbb{Q} \cap [0, 1)\}$ 是 $[0, 2)$ 的一个分割。若 $V$ 可测，则 $m(V) = 0$ 导致 $m([0, 2)) = 0$；$m(V) > 0$ 导致 $m([0, 2)) = \infty$。矛盾。

### 3.2 不可测集的存在性

**定理 3.2**　不可测集的存在依赖于**选择公理**。在不接受选择公理的某些模型中，所有实数子集都是可测的（Solovay 模型，1970）。

**推论 3.1**　Lebesgue 测度不能定义在 $\mathbb{R}$ 的所有子集上（保持平移不变性和可数可加性）。

---

## 4. 可测集的结构

### 4.1 $F_\sigma$ 集与 $G_\delta$ 集

- **$F_\sigma$ 集**：可数个闭集的并
- **$G_\delta$ 集**：可数个开集的交

**定理 4.1**　任意可测集 $E$ 都可以写成 $G_\delta$ 集减去零测集，或 $F_\sigma$ 集加上零测集。

> **证明提示**：正则性。取开集 $G_n \supseteq E$ 使 $m(G_n \setminus E) < 1/n$，则 $\bigcap G_n$ 为 $G_\delta$ 集。

**推论 4.1**　$E$ 可测 $\iff$ 存在 $G_\delta$ 集 $G$ 使 $E \subseteq G$ 且 $m(G \setminus E) = 0$。

### 4.2 可测集的逼近

**定理 4.2**　对任意可测集 $E$（$m(E) < \infty$）和 $\varepsilon > 0$，存在有限个开区间的并 $G$ 使得：

$$m(E \triangle G) < \varepsilon$$

（$E \triangle G = (E \setminus G) \cup (G \setminus E)$ 为对称差）

> **意义**：可测集可以用"简单"集合（开区间）任意逼近。

**定理 4.3（Lusin 定理的测度版）**　可测集 $E$ 可以写成 $E = F \cup Z$，$F$ 闭，$Z$ 零测。

---

## 5. 测度论视角下的比较

| | Riemann 积分 | Lebesgue 积分 |
|--|-------------|---------------|
| 分割 | 对定义域分割 | 对值域分割 |
| 可积函数类 | "几乎处处连续" | 所有可测函数 |
| 收敛定理 | 条件苛刻 | 控制收敛等强大工具 |
| 极限与积分交换 | 需一致收敛 | 需控制函数 |

> **核心思想**：Lebesgue 积分之所以强大，是因为它建立在更灵活的测度理论之上。

---

## 参考

- [01-集合与点集](01-集合与点集.md) — 点集拓扑基础
- [03-可测函数](03-可测函数.md) — Lebesgue 积分的被积函数
