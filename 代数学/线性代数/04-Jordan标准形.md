# Jordan 标准形

> 不可对角化矩阵的"最简"形式——线性代数的巅峰。

## 1. 广义特征向量

**定义 1.1**　$\boldsymbol{\alpha}$ 是 $\lambda$ 的 **$k$ 级广义特征向量**：$(\lambda I - A)^k \boldsymbol{\alpha} = \mathbf{0}$ 但 $(\lambda I - A)^{k-1} \boldsymbol{\alpha} \neq \mathbf{0}$。

**定义 1.2**　**广义特征子空间**：$W_\lambda = \ker(\lambda I - A)^{n}$（$n = \dim V$）。

**定理 1.1**　$V = W_{\lambda_1} \oplus \cdots \oplus W_{\lambda_k}$（$\lambda_1, \ldots, \lambda_k$ 为互异特征值）。

> **证明提示**：利用最小多项式 $m(\lambda) = (\lambda - \lambda_1)^{r_1} \cdots (\lambda - \lambda_k)^{r_k}$ 和中国剩余定理。

**定理 1.2**　$\dim W_\lambda = m_\lambda$（几何重数不一定等于代数重数，但广义特征子空间的维数等于代数重数）。

---

## 2. Jordan 块与 Jordan 标准形

**定义 2.1**　$r$ 阶 **Jordan 块**：

$$J_r(\lambda) = \begin{pmatrix} \lambda & 1 & & \\ & \lambda & 1 & \\ & & \ddots & 1 \\ & & & \lambda \end{pmatrix}$$

**定义 2.2**　**Jordan 标准形**：分块对角矩阵 $J = \operatorname{diag}(J_{r_1}(\lambda_1), \ldots, J_{r_s}(\lambda_s))$。

**定理 2.1（Jordan 标准形定理）**　任何复矩阵 $A$ 相似于 Jordan 标准形（不计 Jordan 块的排列次序）。

> **证明提示**：在每个广义特征子空间 $W_\lambda$ 中构造 Jordan 链：$\boldsymbol{\alpha}_1, (\lambda I - A)\boldsymbol{\alpha}_1 = \boldsymbol{\alpha}_2, \ldots$

---

## 3. Jordan 链

**定义 3.1**　$\boldsymbol{\alpha}_1, \boldsymbol{\alpha}_2, \ldots, \boldsymbol{\alpha}_r$ 为 **Jordan 链**：

$$(\lambda I - A)\boldsymbol{\alpha}_1 = \mathbf{0}$$
$$(\lambda I - A)\boldsymbol{\alpha}_2 = \boldsymbol{\alpha}_1$$
$$\vdots$$
$$(\lambda I - A)\boldsymbol{\alpha}_r = \boldsymbol{\alpha}_{r-1}$$

即 $\boldsymbol{\alpha}_1$ 是特征向量，$\boldsymbol{\alpha}_k$ 是 $k$ 级广义特征向量。

**定理 3.1**　Jordan 链的长度 $=$ 对应 Jordan 块的阶数。

---

## 4. 不变量

**定义 4.1**　$\lambda$ 对应的 **Jordan 块的个数** $=$ $\dim V_\lambda$（几何重数）。

**定义 4.2**　$\lambda$ 对应的 **最大 Jordan 块的阶数** $=$ $\lambda$ 作为最小多项式根的重数。

**定理 4.1**　Jordan 标准形由以下数据唯一确定：

1. 特征值 $\lambda_1, \ldots, \lambda_k$
2. 每个 $\lambda_i$ 对应的 Jordan 块的大小分布

等价地，由以下不变量确定：
- 特征多项式
- 最小多项式
- $\operatorname{rank}(\lambda_i I - A)^j$（$j = 1, 2, \ldots$）

---

## 5. 求 Jordan 标准形的方法

**方法一：通过不变因子**

1. 计算 $\lambda I - A$ 的 Smith 标准形（初等因子）
2. 不变因子确定 Jordan 块

**方法二：通过广义特征空间**

1. 求特征值 $\lambda$
2. 计算 $\operatorname{rank}(\lambda I - A)^j$ 的递减序列
3. 差分得各阶 Jordan 块的个数

**具体公式**：设 $r_j = \operatorname{rank}(\lambda I - A)^j$，$d_j = r_{j-1} - r_j$（$r_0 = n$），则 $k$ 阶 Jordan 块的个数 $= d_k - d_{k+1}$。

---

## 6. 例子

**例 1**：$A = \begin{pmatrix} 2 & 1 & 0 \\ 0 & 2 & 1 \\ 0 & 0 & 2 \end{pmatrix}$

已为 Jordan 标准形：$J = J_3(2)$（一个 $3$ 阶 Jordan 块）。

**例 2**：$A = \begin{pmatrix} 4 & 1 & -1 \\ 0 & 3 & 0 \\ 1 & 1 & 2 \end{pmatrix}$

特征值 $\lambda = 3$（$3$ 重）。计算 $\operatorname{rank}(3I - A) = 1$，$\operatorname{rank}(3I - A)^2 = 0$。

$d_1 = 3 - 1 = 2$，$d_2 = 1 - 0 = 1$，$d_3 = 0$。$1$ 阶块 $= d_1 - d_2 = 1$，$2$ 阶块 $= d_2 - d_3 = 1$。

$$J = \begin{pmatrix} 3 & 1 & 0 \\ 0 & 3 & 0 \\ 0 & 0 & 3 \end{pmatrix}$$

---

## 7. Jordan 标准形的应用

**应用 1：矩阵函数**

$A$ 的函数 $f(A) = P f(J) P^{-1}$，其中 $f(J_r(\lambda))$ 为上三角 Toeplitz 矩阵：

$$f(J_r(\lambda)) = \begin{pmatrix} f(\lambda) & f'(\lambda) & \frac{f''(\lambda)}{2!} & \cdots \\ & f(\lambda) & f'(\lambda) & \cdots \\ & & \ddots & \vdots \\ & & & f(\lambda) \end{pmatrix}$$

**应用 2：矩阵指数**

$e^{At} = P e^{Jt} P^{-1}$，$e^{J_r(\lambda)t} = e^{\lambda t} \begin{pmatrix} 1 & t & \frac{t^2}{2!} & \cdots \\ & 1 & t & \cdots \\ & & \ddots & \vdots \\ & & & 1 \end{pmatrix}$

**应用 3：判断可对角化**

$A$ 可对角化 $\iff$ 所有 Jordan 块为 $1$ 阶 $\iff$ 最小多项式无重根。

---

## 8. 有理标准形

**定义 8.1**　**有理标准形**（Frobenius 标准形）：由不变因子对应的 **友矩阵**组成。

友矩阵：$C(f) = \begin{pmatrix} 0 & 0 & \cdots & -a_0 \\ 1 & 0 & \cdots & -a_1 \\ & 1 & \cdots & -a_2 \\ & & \ddots & \vdots \\ & & & -a_{n-1} \end{pmatrix}$

**定理 8.1**　任何矩阵在 $F$ 上相似于唯一的有理标准形。

**优势**：不需要代数闭域，系数仍在原域中。
