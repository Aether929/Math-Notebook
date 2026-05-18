# 连续时间 Markov 链

> 从离散到连续——Q 矩阵与生灭过程。

## 1. 定义

### 1.1 基本概念

**定义 1.1**　连续时间随机过程 $\{X(t), t \geq 0\}$ 是**连续时间 Markov 链**（CTMC），若状态空间 $S$ 可数，且：

$$P(X(t + s) = j \mid X(s) = i, X(u) = x(u), 0 \leq u < s) = P(X(t + s) = j \mid X(s) = i)$$

**时齐**：转移概率 $p_{ij}(t) = P(X(t+s) = j \mid X(s) = i)$ 与 $s$ 无关。

### 1.2 转移概率矩阵

$$P(t) = (p_{ij}(t)), \quad P(0) = I$$

**Chapman-Kolmogorov 方程**：$P(t + s) = P(t) P(s)$

**半群性质**：$\{P(t)\}_{t \geq 0}$ 构成 Markov 半群。

**推论 1.1**　$P(t)$ 是随机矩阵：行和为 1。

---

## 2. 转移速率矩阵（Q 矩阵）

### 2.1 定义

**转移速率（强度）**：

$$q_{ij} = \lim_{t \to 0^+} \frac{p_{ij}(t) - \delta_{ij}}{t}, \quad i \neq j$$

$$q_i = -q_{ii} = \sum_{j \neq i} q_{ij}$$

**Q 矩阵**（无穷小生成元）：$Q = (q_{ij})$

> **直觉**：$q_{ij}$ 是从 $i$ 到 $j$ 的瞬时跳转速率，$q_i$ 是离开 $i$ 的总速率。

### 2.2 在状态 $i$ 的逗留时间

**定理 2.1**：在状态 $i$ 的逗留时间 $\sim \text{Exp}(q_i)$。

离开 $i$ 后跳到 $j$ 的概率：$p_{ij} = q_{ij} / q_i$（$j \neq i$）。

### 2.3 Kolmogorov 方程

**后向方程**：$P'(t) = Q P(t)$

**前向方程**：$P'(t) = P(t) Q$

初始条件：$P(0) = I$。

**推论 2.1**　Q 矩阵完全确定了 CTMC 的转移概率。

---

## 3. 生灭过程

### 3.1 定义

状态空间 $S = \{0, 1, 2, \ldots\}$，转移只在相邻状态间：

$$q_{i, i+1} = \lambda_i \quad (\text{出生率}), \quad q_{i, i-1} = \mu_i \quad (\text{死亡率})$$

### 3.2 常见特例

| 过程 | $\lambda_i$ | $\mu_i$ | 应用 |
|------|-------------|---------|------|
| 纯生过程 | $\lambda$ | $0$ | Poisson 过程 |
| 纯灭过程 | $0$ | $\mu$ | 放射性衰变 |
| $M/M/1$ 队列 | $\lambda$ | $\mu$ | 单服务台排队 |
| $M/M/c$ 队列 | $\lambda$ | $\min(i, c)\mu$ | 多服务台排队 |
| 线性生灭 | $i\lambda$ | $i\mu$ | 人口模型 |
| Yule 过程 | $i\lambda$ | $0$ | 纯出生（繁殖） |

### 3.3 平稳分布

**定理 3.1**：生灭过程存在平稳分布 $\iff$ $\sum_{n=1}^{\infty} \frac{\lambda_0 \lambda_1 \cdots \lambda_{n-1}}{\mu_1 \mu_2 \cdots \mu_n} < \infty$

平稳分布：

$$\pi_n = \pi_0 \prod_{k=0}^{n-1} \frac{\lambda_k}{\mu_{k+1}}$$

---

## 4. 排队论

### 4.1 $M/M/1$ 队列

**模型**：到达 $\sim \text{PP}(\lambda)$，服务时间 $\sim \text{Exp}(\mu)$，单服务台。

**强度**：$\rho = \lambda / \mu$

**平稳条件**：$\rho < 1$

**平稳分布**：$\pi_n = (1 - \rho) \rho^n$

**性能指标**：

| 指标 | 公式 |
|------|------|
| 平均队长 | $L = \frac{\rho}{1 - \rho}$ |
| 平均等待时间（系统） | $W = \frac{1}{\mu - \lambda}$ |
| 平均等待时间（队列） | $W_q = \frac{\rho}{\mu - \lambda}$ |
| 平均队列长度 | $L_q = \frac{\rho^2}{1 - \rho}$ |

**Little 公式**：$L = \lambda W$，$L_q = \lambda W_q$

**推论 4.1**　Little 公式是排队论中最基本的关系。

### 4.2 $M/M/c$ 队列

**模型**：$c$ 个服务台并行。

**强度**：$\rho = \frac{\lambda}{c\mu}$

**平稳条件**：$\rho < 1$

**Erlang C 公式**：等待概率

$$C(c, a) = \frac{\frac{a^c}{c!} \cdot \frac{1}{1 - \rho}}{\sum_{k=0}^{c-1} \frac{a^k}{k!} + \frac{a^c}{c!} \cdot \frac{1}{1 - \rho}}$$

其中 $a = \lambda / \mu$。

### 4.3 $M/G/1$ 队列

**模型**：到达 $\sim \text{PP}(\lambda)$，一般服务时间分布。

**Pollaczek-Khinchin 公式**：

$$L_q = \frac{\rho^2 + \lambda^2 \sigma^2}{2(1 - \rho)}$$

其中 $\sigma^2$ 为服务时间方差。

> **意义**：服务时间的方差越大，等待越长——减小方差比减小均值更有效。

---

## 5. 连续时间 Markov 链的极限行为

### 5.1 状态分类

与离散时间类似：
- **常返**：从 $i$ 出发几乎必然返回
- **非常返**：返回概率 $< 1$
- **遍历**：正常返 + 非周期

### 5.2 平稳分布

**定理 5.1**：不可约遍历 CTMC 存在唯一平稳分布 $\boldsymbol{\pi}$，满足：

$$\boldsymbol{\pi} Q = 0, \quad \sum_i \pi_i = 1$$

等价于 $\sum_i \pi_i q_{ij} = \pi_j q_j$（对所有 $j$）。

### 5.3 嵌入链

**嵌入离散时间 Markov 链**：只看跳转的时刻和去向。

转移概率：$\hat{p}_{ij} = q_{ij} / q_i$（$j \neq i$），$\hat{p}_{ii} = 0$。

> CTMC 的常返性等价于其嵌入链的常返性。

**推论 5.1**　嵌入链"遗忘"了逗留时间，只保留跳转结构。

---

## 6. 可逆性

### 6.1 定义

CTMC **可逆**，若存在 $\boldsymbol{\pi}$ 满足**细致平衡条件**：

$$\pi_i q_{ij} = \pi_j q_{ji}, \quad \forall i, j$$

### 6.2 性质

- 可逆 $\Rightarrow$ $\boldsymbol{\pi}$ 是平稳分布
- 可逆 CTMC 的嵌入链也可逆（关于同一 $\boldsymbol{\pi}$）
- 生灭过程总是可逆的

**推论 6.1**　细致平衡条件比平稳方程更强——可逆是平稳的特殊情况。

---

## 参考

- [03-Markov链](03-Markov链.md) — 离散时间 Markov 链
- [02-Poisson过程](02-Poisson过程.md) — Poisson 过程
- [概率论/03-随机变量与分布](../概率论/03-随机变量与分布.md) — 指数分布
