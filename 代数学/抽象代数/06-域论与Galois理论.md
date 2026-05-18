# 域论与 Galois 理论

> 用群论理解方程的可解性——代数学的巅峰。

## 1. 域的基本概念

**定义 1.1**　**域**：交换除环，即有单位元的交换环，每个非零元素有逆元。

**常见域**：$\mathbb{Q}$，$\mathbb{R}$，$\mathbb{C}$，$\mathbb{F}_p = \mathbb{Z}/p\mathbb{Z}$（$p$ 素数），$\mathbb{Q}(\sqrt{2})$。

**定义 1.2**　域的**特征** $\operatorname{char} F$：使 $n \cdot 1 = 0$ 的最小正整数 $n$；若不存在则为 $0$。

**命题 1.1**　域的特征为 $0$ 或素数 $p$。

> **证明提示**：设 $\operatorname{char} F = n = ab$，则 $(a \cdot 1)(b \cdot 1) = 0$，域中无零因子，$a=1$ 或 $b=1$。

---

## 2. 域扩张

**定义 2.1**　$K$ 是 $F$ 的**扩域**（$F \subseteq K$），记 $K/F$。$[K:F] = \dim_F K$ 为**扩张次数**。

**定理 2.1（次数公式）**　$F \subseteq L \subseteq K$，则

$$[K:F] = [K:L] \cdot [L:F]$$

> **证明提示**：取 $L/F$ 的基和 $K/L$ 的基，证明它们的乘积是 $K/F$ 的基。

**推论 2.1**　$[K:F]$ 有限 $\iff$ $K = F(\alpha_1, \ldots, \alpha_n)$（有限生成）。

**定义 2.2**　$\alpha$ 在 $F$ 上**代数**：存在 $f(x) \in F[x]$ 使 $f(\alpha) = 0$。否则为**超越元**。

**定义 2.3**　$F(\alpha)$ 为在 $F$ 上添加 $\alpha$ 得到的域。

- $\alpha$ 代数：$F(\alpha) \cong F[x]/(m_\alpha(x))$，$[F(\alpha):F] = \deg m_\alpha$
- $\alpha$ 超越：$F(\alpha) \cong F(x)$（有理函数域）

---

## 3. 最小多项式

**定义 3.1**　$\alpha$ 在 $F$ 上的**最小多项式** $m_\alpha(x)$：首一、不可约、$m_\alpha(\alpha) = 0$、次数最低。

**定理 3.1**　最小多项式唯一，且整除任何以 $\alpha$ 为根的多项式。

**定理 3.2**　$[F(\alpha):F] = \deg m_\alpha$。

**定理 3.3**　$F(\alpha) \cong F(\beta) \iff$ $\alpha$ 和 $\beta$ 有相同的最小多项式。

---

## 4. 代数扩张

**定义 4.1**　$K/F$ 是**代数扩张**：$K$ 中每个元素在 $F$ 上代数。

**定理 4.1**　有限扩张 $\Rightarrow$ 代数扩张。

> **证明提示**：$[F(\alpha):F] = n$，则 $1, \alpha, \ldots, \alpha^n$ 线性相关，存在非零多项式 $f$ 使 $f(\alpha) = 0$。

**定理 4.2**　代数扩张的代数扩张仍是代数扩张。

> **证明提示**：设 $\alpha$ 在 $L$ 上代数，$L/F$ 代数，则 $[F(\alpha):F] \leq [L(\alpha):L] \cdot [L:F] < \infty$。

**定义 4.2**　$F$ 的**代数闭包** $\bar{F}$：$F$ 的扩域，每个 $f(x) \in F[x]$ 在 $\bar{F}$ 中有根，且 $\bar{F}$ 在自身上代数闭。

**定理 4.3**　$\mathbb{C}$ 是 $\mathbb{R}$ 的代数闭包。$\bar{\mathbb{Q}}$ 是 $\mathbb{Q}$ 的代数闭包。

---

## 5. 分裂域

**定义 5.1**　$f(x) \in F[x]$ 的**分裂域**：最小的扩域 $K$ 使 $f$ 在 $K$ 中完全分解为一次因式之积。

**定理 5.1**　分裂域存在且唯一（同构意义下）。

> **证明提示**：存在性：逐次添加根。唯一性：归纳法，利用同构延拓定理。

**定理 5.2**　$[K:F] \leq n!$（$n = \deg f$）。

**例子**：
- $x^2 - 2$ 在 $\mathbb{Q}$ 上的分裂域：$\mathbb{Q}(\sqrt{2})$，次数 $2$
- $x^3 - 2$ 在 $\mathbb{Q}$ 上的分裂域：$\mathbb{Q}(\sqrt[3]{2}, \omega)$（$\omega = e^{2\pi i/3}$），次数 $6$

---

## 6. 可分扩张

**定义 6.1**　$f(x)$ **可分**：在分裂域中无重根。

**定义 6.2**　$\alpha$ 在 $F$ 上**可分**：最小多项式无重根。

**定义 6.3**　扩张 $K/F$ **可分**：$K$ 中每个元素在 $F$ 上可分。

**定理 6.1**　特征 $0$ 的域上，不可约多项式都可分。

**定理 6.2**　特征 $p$ 的域上，$f(x)$ 不可分 $\iff$ $f'(x) = 0$ $\iff$ $f(x) = g(x^p)$。

**定义 6.4**　$F$ **完美**：$F$ 上每个代数扩张都可分。特征 $0$ 的域和有限域都是完美的。

---

## 7. Galois 理论

**定义 7.1**　$K/F$ 是**Galois 扩张**：$K$ 是某个可分多项式的分裂域。

等价条件：
1. $K/F$ 可分且正规
2. $|\operatorname{Aut}(K/F)| = [K:F]$

**定义 7.2**　**Galois 群** $\operatorname{Gal}(K/F) = \{\sigma \in \operatorname{Aut}(K) : \sigma|_F = \operatorname{id}\}$。

**定理 7.1（Galois 对应）**　$K/F$ 为有限 Galois 扩张，则中间域与 $\operatorname{Gal}(K/F)$ 的子群之间存在反序一一对应：

$$L \longleftrightarrow \operatorname{Gal}(K/L)$$

- $L_1 \subseteq L_2 \iff \operatorname{Gal}(K/L_1) \supseteq \operatorname{Gal}(K/L_2)$
- $[L:F] = [\operatorname{Gal}(K/F) : \operatorname{Gal}(K/L)]$
- $L/F$ Galois $\iff$ $\operatorname{Gal}(K/L) \trianglelefteq \operatorname{Gal}(K/F)$，此时 $\operatorname{Gal}(L/F) \cong \operatorname{Gal}(K/F)/\operatorname{Gal}(K/L)$

---

## 8. Galois 群的计算

**定理 8.1**　$f(x)$ 的 Galois 群同构于 $S_n$ 的子群（$n = \deg f$）。

**例子**：

| $f(x)$ | 分裂域 | Galois 群 |
|---------|--------|-----------|
| $x^2 - 2$ | $\mathbb{Q}(\sqrt{2})$ | $\mathbb{Z}_2$ |
| $x^3 - 2$ | $\mathbb{Q}(\sqrt[3]{2}, \omega)$ | $S_3$ |
| $x^4 - 2$ | $\mathbb{Q}(\sqrt[4]{2}, i)$ | $D_4$（8阶二面体群）|
| $\Phi_p(x)$（分圆多项式） | $\mathbb{Q}(\zeta_p)$ | $\mathbb{Z}_{p-1}$ |

**定理 8.2**　$\operatorname{Gal}(\mathbb{Q}(\zeta_n)/\mathbb{Q}) \cong (\mathbb{Z}/n\mathbb{Z})^*$。

---

## 9. 方程的可解性

**定义 9.1**　$G$ **可解**：存在正规列使因子为 Abel 群。

**定理 9.1（Galois 定理）**　$f(x) \in F[x]$ 可用根式求解 $\iff$ $\operatorname{Gal}(f/F)$ 可解。

> **证明提示**：根式扩张对应于 Galois 群的正规列。每次开 $n$ 次方对应一个循环扩张。

**定理 9.2**　$S_n$（$n \geq 5$）不可解 $\Rightarrow$ 一般五次方程不可用根式求解。

> **证明提示**：$S_n$（$n \geq 5$）的唯一非平凡正规子群是 $A_n$，而 $A_n$（$n \geq 5$）是单群，故 $S_n$ 不可解。

---

## 10. 有限域

**定理 10.1**　有限域的阶必为 $p^n$（$p$ 素数）。阶为 $p^n$ 的有限域唯一，记 $\mathbb{F}_{p^n}$ 或 $\operatorname{GF}(p^n)$。

**定理 10.2**　$\mathbb{F}_{p^n}$ 是 $x^{p^n} - x$ 在 $\mathbb{F}_p$ 上的分裂域。

**定理 10.3**　$\mathbb{F}_{p^n}^*$ 是 $p^n - 1$ 阶循环群。

> **证明提示**：有限域的乘法群是有限 Abel 群，利用"有限 Abel 群中若 $x^d = 1$ 的解 $\leq d$ 个则为循环群"。

**推论 10.1**　$\mathbb{F}_{p^n}$ 的元素都是 $x^{p^n} - x$ 的根：$a^{p^n} = a$（**Frobenius 自同构**）。

**推论 10.2**　$\mathbb{F}_{p^n}$ 的子域形如 $\mathbb{F}_{p^d}$，其中 $d \mid n$。
