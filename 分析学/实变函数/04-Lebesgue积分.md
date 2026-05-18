# Lebesgue 积分

> 测度论上的积分——分析学最强大的工具之一。

## 1. 积分的定义

### 1.1 简单函数的积分

设 $\varphi = \sum_{i=1}^{n} a_i \chi_{E_i}$（$E_i$ 互不相交可测，$m(E_i) < \infty$），定义：

$$\int_E \varphi \, dm = \sum_{i=1}^{n} a_i \cdot m(E_i)$$

**性质**：
- $\int \varphi \geq 0$（若 $\varphi \geq 0$）
- $\int (a\varphi + b\psi) = a\int \varphi + b\int \psi$

### 1.2 非负可测函数的积分

设 $f \geq 0$ 可测，定义：

$$\int_E f \, dm = \sup \left\{ \int_E \varphi \, dm : 0 \leq \varphi \leq f, \varphi \text{ 简单函数} \right\}$$

> 可能为 $+\infty$。

**定理 1.1**　对非负可测函数 $f$，存在简单函数列 $0 \leq \varphi_1 \leq \varphi_2 \leq \cdots \leq f$ 使 $\varphi_n \uparrow f$ 逐点，且 $\int f = \lim \int \varphi_n$。

### 1.3 一般可测函数的积分

设 $f$ 可测，$f = f^+ - f^-$（$f^+ = \max(f, 0)$，$f^- = \max(-f, 0)$），定义：

$$\int_E f \, dm = \int_E f^+ \, dm - \int_E f^- \, dm$$

要求右边两个积分不同时为 $+\infty$。若两者都有限，称 $f$ 在 $E$ 上 **Lebesgue 可积**，记 $f \in L^1(E)$。

**定理 1.2**　$f \in L^1(E) \iff |f| \in L^1(E)$。

---

## 2. 积分的性质

### 2.1 基本性质

| 性质 | 公式 |
|------|------|
| 线性 | $\int (af + bg) = a \int f + b \int g$ |
| 单调性 | $f \leq g$ a.e. $\Rightarrow$ $\int f \leq \int g$ |
| 绝对值不等式 | $\left|\int f\right| \leq \int |f|$ |
| 零测集上积分为零 | $m(E) = 0 \Rightarrow \int_E f = 0$ |
| 积分零 $\Rightarrow$ $f = 0$ a.e. | $f \geq 0$，$\int f = 0$ $\Rightarrow$ $f = 0$ a.e. |

**定理 2.1**　$f \in L^1(E)$，$A \subseteq E$ 可测 $\Rightarrow$ $f|_A \in L^1(A)$。

**定理 2.2（积分的绝对连续性）**　$f \in L^1(E)$，$\forall \varepsilon > 0$，$\exists \delta > 0$，$m(A) < \delta$ $\Rightarrow$ $\left|\int_A f\right| < \varepsilon$。

> **证明提示**：对 $|f|$ 用单调收敛定理逼近简单函数。

### 2.2 与 Riemann 积分的关系

**定理 2.3**　若 $f$ 在 $[a, b]$ 上 Riemann 可积，则 $f$ Lebesgue 可积，且两者相等。

> **意义**：Lebesgue 积分是 Riemann 积分的真推广——可积函数类更大。

**定理 2.4（Lebesgue 可积性判据）**　有界函数 $f$ 在 $[a, b]$ 上 Riemann 可积 $\iff$ $f$ 的不连续点集为零测集。

---

## 3. 收敛定理

这是 Lebesgue 积分理论最核心的部分，也是它优于 Riemann 积分的关键。

### 3.1 单调收敛定理（MCT）

**定理 3.1（Levi）**　设 $0 \leq f_1 \leq f_2 \leq \cdots$ 为可测函数列，$f_n \to f$ a.e.，则：

$$\lim_{n \to \infty} \int f_n \, dm = \int f \, dm$$

> **证明思路**：利用积分定义（简单函数逼近）和单调性。关键步骤：对简单函数 $\varphi \leq f$，证明 $\int \varphi \leq \lim \int f_n$。

**推论 3.1（Beppo Levi）**　$f_n \geq 0$ 可测 $\Rightarrow$ $\int \sum f_n = \sum \int f_n$。

**推论 3.2**　$0 \leq f_n \uparrow f$ a.e. $\Rightarrow$ $\int f_n \uparrow \int f$（允许 $+\infty$）。

### 3.2 Fatou 引理

**定理 3.2**　设 $f_n \geq 0$ 可测，则：

$$\int \liminf_{n \to \infty} f_n \, dm \leq \liminf_{n \to \infty} \int f_n \, dm$$

> **注意**：不等号不能改为等号（反例：$f_n = n \chi_{(0, 1/n)}$，$\int f_n = 1$，但 $\liminf f_n = 0$）。

**证明提示**：令 $g_k = \inf_{n \geq k} f_n$，则 $g_k$ 递增收敛于 $\liminf f_n$，用 MCT。

**推论 3.3（Fatou 引理的推广）**　$f_n \geq g$，$g \in L^1$ $\Rightarrow$ $\int \liminf f_n \leq \liminf \int f_n$。

> **证明提示**：对 $f_n - g \geq 0$ 用标准 Fatou 引理。

### 3.3 控制收敛定理（DCT）

**定理 3.3（Lebesgue）**　设 $f_n \to f$ a.e.，且存在可积函数 $g$ 使得 $|f_n| \leq g$ a.e.，则：

$$\lim_{n \to \infty} \int f_n \, dm = \int f \, dm$$

> **证明思路**：对 $g + f_n \geq 0$ 和 $g - f_n \geq 0$ 分别用 Fatou 引理。

**推论 3.4（有界收敛定理）**　$m(E) < \infty$，$|f_n| \leq M$，$f_n \to f$ a.e. $\Rightarrow$ $\int f_n \to \int f$。

**推论 3.5（DCT 的逐项积分版）**　$|f_n| \leq g \in L^1$，$f_n \to f$ a.e. $\Rightarrow$ $\int |f_n - f| \to 0$。

**推论 3.6（DCT 的级数版）**　$|g_n| \leq h_n$，$\sum h_n$ 可积 $\Rightarrow$ $\int \sum g_n = \sum \int g_n$。

### 3.4 定理对比

| 定理 | 条件 | 结论 |
|------|------|------|
| MCT | $f_n \geq 0$ 单调递增 | $\lim \int f_n = \int \lim f_n$ |
| Fatou | $f_n \geq 0$ | $\int \liminf f_n \leq \liminf \int f_n$ |
| DCT | $\|f_n\| \leq g \in L^1$ | $\lim \int f_n = \int \lim f_n$ |

> **使用优先级**：DCT 最常用，MCT 适合非负递增列，Fatou 用于只需要不等式的情形。

---

## 4. 逐项积分与极限交换

### 4.1 非负级数

**定理 4.1（逐项积分）**　设 $f_n \geq 0$ 可测：

$$\int \sum_{n=1}^{\infty} f_n \, dm = \sum_{n=1}^{\infty} \int f_n \, dm$$

**证明**：令 $S_N = \sum_{n=1}^{N} f_n$，用 MCT。

### 4.2 一般级数

**定理 4.2**　若 $\sum \int |f_n| < \infty$，则 $\sum f_n$ 几乎处处绝对收敛，且：

$$\int \sum f_n = \sum \int f_n$$

> **证明提示**：对 $\sum |f_n|$ 用非负级数结论，再用 DCT。

---

## 5. 重积分与 Fubini 定理

### 5.1 乘积测度

设 $(X, \mathcal{A}, \mu)$ 和 $(Y, \mathcal{B}, \nu)$ 为测度空间，可定义乘积测度 $\mu \times \nu$ 在 $X \times Y$ 上。

### 5.2 Fubini 定理

**定理 5.1（Fubini 定理）**　设 $f$ 在 $X \times Y$ 上关于 $\mu \times \nu$ 可积，则：

$$\int_{X \times Y} f \, d(\mu \times \nu) = \int_X \left(\int_Y f(x, y) \, d\nu(y)\right) d\mu(x) = \int_Y \left(\int_X f(x, y) \, d\mu(x)\right) d\nu(y)$$

**定理 5.2（Tonelli 定理）**　$f \geq 0$ 可测，则上述等式自动成立（各项可为 $+\infty$）。

> **使用技巧**：先用 Tonelli 验证 $\int |f| < \infty$，再用 Fubini 交换积分次序。

**推论 5.1**　$f \geq 0$ 可测 $\Rightarrow$ $\int f = \int_0^\infty m(\{f > t\}) \, dt$（**层饼表示**）。

**推论 5.2**　$f \in L^1$ $\Rightarrow$ $\int f = \int_0^\infty m(\{f > t\}) \, dt - \int_0^\infty m(\{f < -t\}) \, dt$。

---

## 6. Lebesgue 积分与 Riemann 积分

### 6.1 广义 Lebesgue 积分

若 $f$ 非负可测，定义 $\int f = \lim_{n \to \infty} \int_{[-n, n]} \min(f, n)$。

对于一般 $f$，若 $\int |f| < \infty$，则 $f$ 可积。

> **注意**：Lebesgue 积分要求绝对可积。$\int_0^\infty \frac{\sin x}{x} dx$ 在 Riemann 意义下条件收敛，但在 Lebesgue 意义下不可积。

### 6.2 Lebesgue 积分的优势

| 方面 | Riemann | Lebesgue |
|------|---------|----------|
| 可积函数类 | 连续函数 | 所有可测函数 |
| 收敛定理 | 一致收敛 | DCT, MCT |
| 极限交换 | 条件苛刻 | 条件宽松 |
| 理论框架 | 基于区间 | 基于测度 |

---

## 参考

- [03-可测函数](03-可测函数.md) — 被积函数的性质
- [05-微分与不定积分](05-微分与不定积分.md) — 微积分基本定理的 Lebesgue 版本
- [数学分析/04-定积分](../数学分析/04-定积分.md) — Riemann 积分
