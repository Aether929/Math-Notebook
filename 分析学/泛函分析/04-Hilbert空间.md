# Hilbert 空间

> 完备的内积空间——几何直觉与无穷维的融合。

## 1. 内积空间

### 1.1 定义

**定义 1.1**　设 $H$ 为实（或复）线性空间，$\langle \cdot, \cdot \rangle: H \times H \to \mathbb{R}$（或 $\mathbb{C}$）满足：

1. **正定性**：$\langle x, x \rangle \geq 0$，$\langle x, x \rangle = 0 \iff x = 0$
2. **线性**：$\langle \alpha x + \beta y, z \rangle = \alpha \langle x, z \rangle + \beta \langle y, z \rangle$
3. **共轭对称**：$\langle x, y \rangle = \overline{\langle y, x \rangle}$

则 $(H, \langle \cdot, \cdot \rangle)$ 为**内积空间**。

**诱导范数**：$\|x\| = \sqrt{\langle x, x \rangle}$

### 1.2 基本不等式

**定理 1.1（Cauchy-Schwarz 不等式）**：

$$|\langle x, y \rangle| \leq \|x\| \|y\|$$

等号成立 $\iff$ $x, y$ 线性相关。

**定理 1.2（平行四边形等式）**：

$$\|x + y\|^2 + \|x - y\|^2 = 2(\|x\|^2 + \|y\|^2)$$

> **意义**：范数来自内积 $\iff$ 满足平行四边形等式。$L^p$（$p \neq 2$）的范数不满足此等式。

### 1.3 极化恒等式

**实内积空间**：

$$\langle x, y \rangle = \frac{1}{4}(\|x + y\|^2 - \|x - y\|^2)$$

**复内积空间**：

$$\langle x, y \rangle = \frac{1}{4}\sum_{k=0}^{3} i^k \|x + i^k y\|^2$$

---

## 2. Hilbert 空间

### 2.1 定义

**定义 2.1**：完备的内积空间称为 **Hilbert 空间**。

**常见 Hilbert 空间**：
- $\mathbb{R}^n$（标准内积）
- $\ell^2$：$\langle x, y \rangle = \sum x_n \overline{y_n}$
- $L^2$：$\langle f, g \rangle = \int f \bar{g}$
- Sobolev 空间 $H^1$

> **注意**：$L^p$（$p \neq 2$）不是 Hilbert 空间（范数不满足平行四边形等式）。

### 2.2 可分性

**定理 2.1**：$\ell^2$ 和 $L^2[a, b]$ 是可分的 Hilbert 空间。

**推论 2.1**　可分 Hilbert 空间在结构上唯一——都与 $\ell^2$ 等距同构。

---

## 3. 正交性

### 3.1 正交与正交补

**定义 3.1**：
- $x \perp y \iff \langle x, y \rangle = 0$
- $M \perp N \iff \forall x \in M, y \in N: \langle x, y \rangle = 0$
- $M^\perp = \{x \in H : \langle x, m \rangle = 0, \forall m \in M\}$

**性质**：
- $M^\perp$ 是闭子空间
- $M \subseteq N \Rightarrow N^\perp \subseteq M^\perp$
- $M \cap M^\perp = \{0\}$

### 3.2 正交分解

**定理 3.1**　设 $M$ 是 $H$ 的闭子空间，则：

$$H = M \oplus M^\perp$$

即 $\forall x \in H$，存在唯一的 $x = y + z$，$y \in M, z \in M^\perp$。

> **意义**：Hilbert 空间中的闭子空间总有正交补——这是 Hilbert 空间优于一般 Banach 空间的关键。

**推论 3.1**　$(M^\perp)^\perp = M$（$M$ 闭时）。

---

## 4. 正交投影

### 4.1 投影定理

**定理 4.1**　设 $M$ 是 $H$ 的闭子空间，$\forall x \in H$，存在唯一 $y_0 \in M$ 使得：

$$\|x - y_0\| = \inf_{y \in M} \|x - y\|$$

$y_0$ 称为 $x$ 在 $M$ 上的**正交投影**，记 $y_0 = P_M x$。

### 4.2 投影算子的性质

**定理 4.2**：$P_M$ 是有界线性算子，满足：
- $P_M^2 = P_M$（幂等性）
- $P_M^* = P_M$（自伴性）
- $\|P_M\| \leq 1$（$M \neq \{0\}$ 时 $\|P_M\| = 1$）
- $I - P_M = P_{M^\perp}$

> **意义**：正交投影是 Hilbert 空间中最"自然"的算子。

**推论 4.1**　$\langle P_M x, x - P_M x \rangle = 0$（投影的正交性）。

---

## 5. 正交系与 Fourier 级数

### 5.1 正交系

**定义 5.1**：$\{e_\alpha\}$ 为**正交系**，若 $\langle e_\alpha, e_\beta \rangle = 0$（$\alpha \neq \beta$）。

**标准正交系**（ONS）：$\|e_\alpha\| = 1$。

### 5.2 Bessel 不等式

**定理 5.1（Bessel 不等式）**　设 $\{e_n\}$ 为 ONS，$\forall x \in H$：

$$\sum_{n=1}^{\infty} |\langle x, e_n \rangle|^2 \leq \|x\|^2$$

### 5.3 完全正交系

**定义 5.2**：ONS $\{e_n\}$ **完全**（或**极大**），若 $\{e_n\}^\perp = \{0\}$。

等价条件：
- $\operatorname{span}\{e_n\}$ 稠密
- **Parseval 等式**：$\|x\|^2 = \sum |\langle x, e_n \rangle|^2$
- $x = \sum \langle x, e_n \rangle e_n$（Fourier 展开）

### 5.4 Hilbert 基

**定义 5.3**：完全的 ONS 称为 **Hilbert 基**。

**定理 5.2**：
- 每个可分 Hilbert 空间都有可数的 Hilbert 基
- 所有可分无穷维 Hilbert 空间都与 $\ell^2$ 等距同构

> **意义**：可分 Hilbert 空间在结构上只有一个——$\ell^2$。

### 5.5 Gram-Schmidt 正交化

设 $\{f_n\}$ 线性无关，令：

$$e_1 = \frac{f_1}{\|f_1\|}, \quad g_n = f_n - \sum_{k=1}^{n-1} \langle f_n, e_k \rangle e_k, \quad e_n = \frac{g_n}{\|g_n\|}$$

则 $\{e_n\}$ 为 ONS，且 $\operatorname{span}\{e_1, \ldots, e_n\} = \operatorname{span}\{f_1, \ldots, f_n\}$。

---

## 6. Hilbert 空间中的算子

### 6.1 伴随算子

**定理 6.1**　设 $T \in \mathcal{B}(H)$，存在唯一 $T^* \in \mathcal{B}(H)$ 使得：

$$\langle Tx, y \rangle = \langle x, T^* y \rangle, \quad \forall x, y \in H$$

**性质**：
- $(T^*)^* = T$
- $\|T^* T\| = \|T\|^2$
- $\ker T^* = (\operatorname{Im} T)^\perp$
- $(ST)^* = T^* S^*$

### 6.2 自伴算子

**定义 6.1**：$T = T^*$（即 $\langle Tx, y \rangle = \langle x, Ty \rangle$）。

**性质**：
- 自伴算子的特征值都是实数
- 不同特征值对应的特征向量正交

### 6.3 正算子

**定义 6.2**：$T$ 正（$T \geq 0$），若 $\langle Tx, x \rangle \geq 0$（$\forall x$）。

**性质**：$T \geq 0 \iff T = T^*$ 且 $\sigma(T) \subseteq [0, \infty)$。

### 6.4 酉算子

**定义 6.3**：$U$ 酉（unitary），若 $U^* U = UU^* = I$。

**性质**：
- $\|Ux\| = \|x\|$（保范）
- $\langle Ux, Uy \rangle = \langle x, y \rangle$（保内积）

---

## 参考

- [02-赋范空间与Banach空间](02-赋范空间与Banach空间.md) — Banach 空间
- [06-谱理论](06-谱理论.md) — 自伴算子的谱分解
- [实变函数/06-Lp空间](../实变函数/06-Lp空间.md) — $L^2$ 的具体构造
