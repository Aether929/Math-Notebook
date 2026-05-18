# Poisson 过程

> 最基本的计数过程——独立增量、平稳增量。

## 1. 定义

### 1.1 计数过程定义

**定义 1.1**　计数过程 $\{N(t), t \geq 0\}$ 是参数为 $\lambda$ 的 **Poisson 过程**，若：

1. $N(0) = 0$
2. 独立增量
3. 平稳增量：$N(t+s) - N(s) \sim \text{Poisson}(\lambda t)$

### 1.2 等价定义（间隔时间）

**定理 1.1**：$\{N(t)\}$ 是 Poisson 过程 $\iff$ 到达间隔 $\{T_n\}$ i.i.d. $\sim \text{Exp}(\lambda)$。

### 1.3 等价定义（稀疏性）

计数过程是 Poisson 过程 $\iff$ 满足：
1. $P(N(h) = 1) = \lambda h + o(h)$
2. $P(N(h) \geq 2) = o(h)$
3. 独立增量

**推论 1.1**　稀疏性条件刻画了 Poisson 过程的"局部"行为。

---

## 2. 基本性质

### 2.1 分布性质

$$P(N(t) = k) = \frac{(\lambda t)^k}{k!} e^{-\lambda t}, \quad k = 0, 1, 2, \ldots$$

$$E(N(t)) = \lambda t, \quad \text{Var}(N(t)) = \lambda t$$

### 2.2 到达间隔与到达时刻

**到达间隔**：$T_1, T_2, \ldots$ i.i.d. $\sim \text{Exp}(\lambda)$

**第 $n$ 次到达时刻**：$S_n = T_1 + T_2 + \cdots + T_n \sim \Gamma(n, \lambda)$

**推论 2.1**　$S_n$ 的密度为 Erlang 分布。

### 2.3 条件分布

**定理 2.1**：给定 $N(t) = n$，$n$ 个到达时刻 $S_1, \ldots, S_n$ 的联合分布与 $[0, t]$ 上 $n$ 个独立均匀随机变量的顺序统计量相同。

> **应用**：模拟 Poisson 过程——先生成 $n \sim \text{Poisson}(\lambda t)$，再在 $[0, t]$ 上均匀分布 $n$ 个点。

---

## 3. Poisson 过程的叠加与分解

### 3.1 叠加

**定理 3.1**：$N_1(t) \sim \text{PP}(\lambda_1)$，$N_2(t) \sim \text{PP}(\lambda_2)$ 独立，则：

$$N_1(t) + N_2(t) \sim \text{PP}(\lambda_1 + \lambda_2)$$

### 3.2 随机稀释

**定理 3.2**：$N(t) \sim \text{PP}(\lambda)$，每个事件以概率 $p$ 独立地被"保留"，则保留的事件构成 $\text{PP}(\lambda p)$。

### 3.3 分解

**定理 3.3**：$N(t) \sim \text{PP}(\lambda)$，每个事件独立地属于类型 $i$（概率 $p_i$，$\sum p_i = 1$），则各类型事件分别构成独立的 Poisson 过程 $\text{PP}(\lambda p_i)$。

**推论 3.1**　Poisson 过程的叠加和分解都保持 Poisson 结构。

---

## 4. 非齐次 Poisson 过程

### 4.1 定义

**定义 4.1**　强度函数 $\lambda(t) \geq 0$ 的非齐次 Poisson 过程：
1. $N(0) = 0$
2. 独立增量
3. $N(t+s) - N(s) \sim \text{Poisson}\left(\int_s^{s+t} \lambda(u) \, du\right)$

### 4.2 性质

$$E(N(t)) = \int_0^t \lambda(u) \, du =: \Lambda(t)$$

**时间变换**：令 $m(t) = \Lambda(t)$，则 $\{N(m^{-1}(s))\}$ 是齐次 Poisson 过程（强度 1）。

**推论 4.1**　非齐次 Poisson 过程可以通过时间变换化为齐次的。

---

## 5. 复合 Poisson 过程

### 5.1 定义

$$X(t) = \sum_{i=1}^{N(t)} Y_i$$

其中 $\{N(t)\} \sim \text{PP}(\lambda)$，$\{Y_i\}$ i.i.d.，与 $N(t)$ 独立。

### 5.2 性质

$$E(X(t)) = \lambda t E(Y_1)$$

$$\text{Var}(X(t)) = \lambda t E(Y_1^2)$$

$$\text{矩母函数}: M_{X(t)}(s) = e^{\lambda t (M_{Y_1}(s) - 1)}$$

### 5.3 应用

- 索赔过程：$N(t)$ = 索赔次数，$Y_i$ = 索赔金额
- 总损失：$X(t)$ = 到时刻 $t$ 的总损失

**推论 5.1**　复合 Poisson 过程的矩母函数有简洁的指数形式。

---

## 6. 更新过程

### 6.1 定义

**定义 6.1**：到达间隔 $\{T_n\}$ i.i.d.（分布为 $F$，不必是指数分布），$N(t) = \max\{n : S_n \leq t\}$。

Poisson 过程是更新过程的特例（$F = \text{Exp}(\lambda)$）。

### 6.2 更新方程

**更新函数**：$m(t) = E(N(t))$

**更新方程**：

$$m(t) = F(t) + \int_0^t m(t - s) \, dF(s)$$

### 6.3 更新定理

**基本更新定理**：

$$\lim_{t \to \infty} \frac{m(t)}{t} = \frac{1}{\mu}$$

其中 $\mu = E(T_1)$。

**Blackwell 更新定理**：$m(t + a) - m(t) \to a/\mu$。

**Smith 关键更新定理**：若 $h$ 非负可积，更新方程 $z(t) = h(t) + \int_0^t z(t-s) \, dF(s)$ 的解：

$$\lim_{t \to \infty} z(t) = \frac{1}{\mu} \int_0^\infty h(s) \, ds$$

### 6.4 更新报酬过程

每次更新获得报酬 $R_n$，总报酬 $R(t) = \sum_{n=1}^{N(t)} R_n$：

$$\lim_{t \to \infty} \frac{E(R(t))}{t} = \frac{E(R_1)}{E(T_1)}$$

**推论 6.1**　长期平均报酬 = 单次报酬期望 / 间隔时间期望。

---

## 参考

- [01-随机过程基本概念](01-随机过程基本概念.md) — 基本概念
- [03-Markov链](03-Markov链.md) — 离散 Markov 过程
- [概率论/03-随机变量与分布](../概率论/03-随机变量与分布.md) — 指数分布、Gamma 分布
