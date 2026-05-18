# Brown 运动

> 连续时间随机过程的"原子"——从物理到金融。

## 1. 定义

### 1.1 标准 Brown 运动

**定义 1.1**　$\{B(t), t \geq 0\}$ 是标准 **Brown 运动**（Wiener 过程），若：

1. $B(0) = 0$
2. 独立增量：$B(t_2) - B(t_1), \ldots, B(t_n) - B(t_{n-1})$ 独立（$t_1 < \cdots < t_n$）
3. $B(t) - B(s) \sim N(0, t - s)$（$0 \leq s < t$）
4. 轨道 $t \mapsto B(t)$ 连续（a.s.）

**定理 1.1（存在性）**　标准 Brown 迥动存在（由 Kolmogorov 存在定理保证）。

构造方法：
- Lévy 构造（Haar 函数展开）
- 随机游走的缩放极限（**Donsker 定理**）

**定理 1.2（Donsker 定理）**　$X_i$ i.i.d.，$E(X_i) = 0$，$D(X_i) = 1$，令 $S_n = \sum X_i$，则

$$\frac{S_{\lfloor nt \rfloor}}{\sqrt{n}} \xrightarrow{d} B(t)$$

（在 $C[0,1]$ 的一致拓扑下）

### 1.2 一般 Brown 运动

$X(t) = \mu t + \sigma B(t)$，漂移 $\mu$，扩散系数 $\sigma$。

$$E(X(t)) = \mu t, \quad \text{Var}(X(t)) = \sigma^2 t$$

---

## 2. 基本性质

### 2.1 分布性质

**定理 2.1**：
- $B(t) \sim N(0, t)$
- $\text{Cov}(B(s), B(t)) = \min(s, t)$
- $E(B(s) B(t)) = \min(s, t)$

**推论 2.1**　$\text{Corr}(B(s), B(t)) = \sqrt{\min(s,t)/\max(s,t)}$。

**定理 2.2（联合分布）**　$0 < t_1 < t_2 < \cdots < t_n$，$(B(t_1), \ldots, B(t_n))$ 为多元正态，协方差矩阵 $\Sigma_{ij} = \min(t_i, t_j)$。

### 2.2 轨道性质

**定理 2.3**：
- $B(t)$ 的轨道几乎必然连续
- $B(t)$ 的轨道**几乎处处不可导**
- $B(t)$ 的轨道在任意区间上几乎处处不单调
- $B(t)$ 的**二次变差**：$\sum_{k} (B(t_{k+1}) - B(t_k))^2 \xrightarrow{P} t$

**推论 2.2**　Brown 运动不是有界变差函数（a.s.）。

> **直觉**：Brown 运动的轨道"无限振荡"，比任何连续函数都"粗糙"。

**定理 2.4（Hölder 连续性）**　$B(t)$ 的轨道是 $\alpha$-Hölder 连续的（$\forall \alpha < 1/2$），不是 $1/2$-Hölder 连续的。

### 2.3 自相似性

$$B(ct) \overset{d}{=} \sqrt{c} B(t), \quad c > 0$$

**推论 2.3**　$B(t)/\sqrt{t} \sim N(0, 1)$（$\forall t > 0$）。

### 2.4 反射原理

**定理 2.5（反射原理）**：

$$P\left(\max_{0 \leq s \leq t} B(s) \geq a\right) = 2P(B(t) \geq a) = 2\left(1 - \Phi\left(\frac{a}{\sqrt{t}}\right)\right)$$

> **证明提示**：利用对称性——在首次到达 $a$ 之后，$B$ 与 $2a - B$ 同分布。

**推论 2.4**　$\max_{0 \leq s \leq t} B(s)$ 与 $|B(t)|$ 同分布。

**推论 2.5**　$P\left(\max_{0 \leq s \leq t} B(s) \geq a, B(t) \leq b\right) = P(B(t) \geq 2a - b)$（$a > 0$，$b \leq a$）。

---

## 3. Brown 运动的变换

### 3.1 Markov 性

**定理 3.1**　$\{B(t)\}$ 是 Markov 过程，转移密度：

$$p(s, x; t, y) = \frac{1}{\sqrt{2\pi(t-s)}} \exp\left(-\frac{(y - x)^2}{2(t - s)}\right)$$

**推论 3.1**　$B(t)$ 是时齐 Markov 过程。

### 3.2 鞅性

**定理 3.2**　以下均为鞅：
- $B(t)$
- $B(t)^2 - t$
- $\exp(\sigma B(t) - \sigma^2 t / 2)$（**指数鞅**/几何布朗运动鞅）
- $\exp(i \theta B(t) + \theta^2 t / 2)$（特征函数鞅）

**推论 3.2**　$E(B(t)^2) = t$（由 $B(t)^2 - t$ 是鞅和 $E(B(0)^2) = 0$ 推出）。

### 3.3 高维 Brown 运动

$\mathbf{B}(t) = (B_1(t), \ldots, B_d(t))$，各分量独立标准 Brown 运动。

**定理 3.3**　高维 Brown 运动是旋转不变的：$O\mathbf{B}(t) \overset{d}{=} \mathbf{B}(t)$（$O$ 为正交矩阵）。

---

## 4. 首达时与首达分布

### 4.1 首达时

**定义 4.1**　$\tau_a = \inf\{t > 0 : B(t) = a\}$（首达时）

**定理 4.1**　首达时的密度（$a > 0$）：

$$f_{\tau_a}(t) = \frac{|a|}{\sqrt{2\pi t^3}} \exp\left(-\frac{a^2}{2t}\right)$$

这是 **Lévy 分布**（逆 Gamma 分布的特例）。

### 4.2 性质

- $P(\tau_a < \infty) = 1$（一维 Brown 运动**常返**）
- $E(\tau_a) = \infty$（期望无穷）
- $\tau_a \overset{d}{=} a^2 \tau_1$（自相似性）

**推论 4.1**　虽然 Brown 运动一定会到达任意水平，但平均等待时间无穷。

**定理 4.2（有吸收壁的 Brown 运动）**：

$$P\left(\max_{0 \leq s \leq t} B(s) < a\right) = 1 - 2\left(1 - \Phi\left(\frac{a}{\sqrt{t}}\right)\right)$$

---

## 5. Brown 桥

### 5.1 定义

**定义 5.1**　**Brown 桥**：$\{B^0(t) = B(t) - t B(1), 0 \leq t \leq 1\}$

性质：$B^0(0) = B^0(1) = 0$，条件分布为给定 $B(1) = 0$ 的 Brown 运动。

**定理 5.1**　$B^0(t) \sim N(0, t(1-t))$，$\text{Cov}(B^0(s), B^0(t)) = \min(s,t) - st$。

### 5.2 应用

- Kolmogorov-Smirnov 检验的极限分布
- 经验过程的极限
- 金融中的利率模型

---

## 6. 几何 Brown 运动

### 6.1 定义

$$S(t) = S(0) \exp\left(\left(\mu - \frac{\sigma^2}{2}\right)t + \sigma B(t)\right)$$

### 6.2 性质

$$E(S(t)) = S(0) e^{\mu t}$$

$$\text{Var}(S(t)) = S(0)^2 e^{2\mu t}(e^{\sigma^2 t} - 1)$$

$$dS(t) = \mu S(t) \, dt + \sigma S(t) \, dB(t)$$（**随机微分方程**）

**推论 6.1**　$\ln S(t) \sim N(\ln S(0) + (\mu - \sigma^2/2)t, \sigma^2 t)$。

### 6.3 应用

- **Black-Scholes 模型**：股票价格的几何 Brown 运动
- **期权定价**：利用风险中性测度
- $E(e^{-rT} \max(S(T) - K, 0))$ = 欧式看涨期权价格

---

## 7. Brown 运动与偏微分方程

### 7.1 热方程

$$\frac{\partial u}{\partial t} = \frac{1}{2} \frac{\partial^2 u}{\partial x^2}$$

解的 Feynman-Kac 表示：

$$u(x, t) = E_x[f(B(t))]$$

其中 $u(x, 0) = f(x)$。

### 7.2 Dirichlet 问题

$$\begin{cases} \Delta u = 0 & \text{in } D \\ u = g & \text{on } \partial D \end{cases}$$

解：$u(x) = E_x[g(B(\tau_D))]$，其中 $\tau_D$ 是首次离开 $D$ 的时间。

---

## 8. 变种

### 8.1 反射 Brown 运动

$$|B(t)| \text{ 或 } \max(B(t), 0)$$

**定理 8.1**　$|B(t)|$ 是 Brown 运动在原点处的反射，其分布为折叠正态分布。

### 8.2 有漂移的 Brown 运动

$$X(t) = \mu t + \sigma B(t)$$

首达时分布：**逆 Gaussian 分布**。

**定理 8.2**　$P(\tau_a < \infty) = \begin{cases} 1 & \mu \leq 0 \\ e^{-2\mu a / \sigma^2} & \mu > 0 \end{cases}$

### 8.3 分数 Brown 运动

$$E(B_H(t) B_H(s)) = \frac{1}{2}(|t|^{2H} + |s|^{2H} - |t-s|^{2H})$$

- $H = 1/2$：标准 Brown 运动
- $H > 1/2$：长程正相关
- $H < 1/2$：长程负相关

---

## 参考

- [01-随机过程基本概念](01-随机过程基本概念.md) — 基本概念
- [06-鞅论](06-鞅论.md) — Brown 运动的鞅理论
- [02-Poisson过程](02-Poisson过程.md) — 另一基本过程
