# 怎样从稠密 Frobenius 取值构造极限迹

## 命题

固定素数 $\ell$，令 $K=\overline{\mathbb Q}_\ell$ 带 $\ell$ 进绝对值，$L\subseteq K$ 为 $\mathbb Q_\ell$ 的有限扩张。设 $\Gamma$ 为拓扑群，$a\ge0$，$I,J$ 为任意指标集。对 $j\in J$ 给定 $x_j\in\Gamma$ 和 $\theta_j\in L$。对 $i\in I$ 给定连续表示 $\rho_i:\Gamma\to\mathrm{GL}_a(K)$、一列数 $\eta_{i,j}\in K$ 和集合 $D_i\subseteq J$。假定

$$
j\in D_i\ \Longrightarrow\ \eta_{i,j}=\operatorname{tr}\rho_i(x_j),
\qquad
\{x_j:j\in\bigcap_{i\in F}D_i\}\ \text{在 }\Gamma\text{ 中稠密}
\quad(F\subseteq I\text{ 有限}).
$$

称 $\theta$ 可由指标集 $A\subseteq I$ 作多项式逼近，如果对每个 $\varepsilon>0$，存在有限集 $F\subseteq A$ 和 $c_i\in K$，使对每个整系数多项式 $P\in\mathbb Z[X_j:j\in J]$ 同时有

$$
\left|P(\theta)-\sum_{i\in F}c_i P(\eta_i)\right|_\ell\le\varepsilon .
\tag{1}
$$

每个多项式只用有限个变量。此处的同一组 $F,c_i$ 必须适合全部 $P$。这就是工程的 `PolyApprox`，将相同取值列合并或任选代表，可以在取值列的集合和原指标之间切换。

若 $\theta$ 可由 $I$ 作多项式逼近，则存在 $t:\Gamma\to L$ 使以下两项成立。

1. 任意在 (1) 中成立的有限线性组合，仍以同样误差逼近全部 $t(g)$，即对每个 $g$，$\left|t(g)-\sum_i c_i\operatorname{tr}\rho_i(g)\right|_\ell\le\varepsilon$。
2. 若 $\theta$ 可由某个 $A\subseteq I$ 作多项式逼近，则 $t$ 可由 $\{\operatorname{tr}\rho_i:i\in A\}$ 作相同意义的多项式逼近，变量改以 $g\in\Gamma$ 为指标。并且每当 $j\in D_i$ 对所有 $i\in A$ 成立，就有 $t(x_j)=\theta_j$。

## 证明

记 $T_i(g)=\operatorname{tr}\rho_i(g)$。固定 $g\in\Gamma$，让 $j$ 满足两个逐渐加强的约束。一是 $x_j$ 进入 $g$ 的不断缩小的邻域 $U$，二是 $j$ 同时属于指定的有限多个 $D_i$。精确说，以

$$
J(U,F)=\{j:x_j\in U,\ j\in D_i\ \text{对所有 }i\in F\}
$$

为滤子的基。稠密性保证每个 $J(U,F)$ 非空；取两个邻域的交和两个有限集的并，可找到落在两个基集合中的一个基集合。这定义了对 $g$ 的趋近方式。

给定 $e>0$，选 (1) 的一组系数，误差取 $e/5$。其中 $P=X_j$ 表明，当 $j\in\bigcap_{i\in F}D_i$ 时，$\theta_j$ 距 $\sum_i c_i T_i(x_j)$ 至多 $e/5$。有限和 $f(g')=\sum_i c_iT_i(g')$ 连续。当 $U$ 足够小，$x_j\in U$ 使 $f(x_j)$ 距 $f(g)$ 小于 $e/5$。于是同一 $J(U,F)$ 中每个 $\theta_j$ 距 $f(g)$ 小于 $2e/5$，其中任意两者相距小于 $e$。因此 $\theta_j$ 沿这个滤子是 Cauchy 的。有限扩张 $L$ 完备，给出唯一极限 $t(g)\in L$。即使 $K$ 未完备，此处极限也已经在 $L$ 内。

现在固定任何一组满足 (1) 的 $F,c_i,\varepsilon$。取 $\Gamma$ 上变量为 $g$ 的任意多项式 $Q$，只涉及有限多个群元素 $g_1,\ldots,g_b$。对每个 $g_s$ 独立选取趋近指标 $j_s$，要求它们全部在 $\bigcap_{i\in F}D_i$。用多项式 $P=Q(X_{j_1},\ldots,X_{j_b})$ 应用 (1)，把 $\eta_{i,j_s}$ 写成 $T_i(x_{j_s})$。令各 $j_s$ 按各自滤子趋近 $g_s$。因为多项式和 $T_i$ 连续，误差不等式保持到极限，得到

$$
\left|Q(t)-\sum_{i\in F}c_iQ(T_i)\right|_\ell\le\varepsilon.
\tag{2}
$$

这里允许两个 $j_s$ 相同，代入后只是让两个变量变为同一个变量。取 $Q=X_g$ 给第一项。如果逼近系数全部从 $A$ 选，(2) 也给出第二项所说的多项式逼近。

最后设 $j\in D_i$ 对所有 $i\in A$ 成立。对任意 $\varepsilon>0$，从 $A$ 选误差至多 $\varepsilon/2$ 的逼近。由 (1) 对 $X_j$ 的结论及 (2) 对 $X_{x_j}$ 的结论，$\theta_j$ 和 $t(x_j)$ 距同一个 $\sum_i c_i\eta_{i,j}$ 都至多 $\varepsilon/2$。所以二者之差的绝对值至多 $\varepsilon$，令 $\varepsilon\to0$ 即得相等。作为直接推论，$t$ 是连续函数，因为第一项使它成为连续迹线性组合的一致极限。

## 在伽罗瓦相容性中的用途

在 `limWU4_of` 中，$x_j$ 是由球形 Hecke 算子读出的 Frobenius 幂，$\theta_j$ 是目标自守表示的本征值。几何上构造出的种子 $\rho_i$ 只在各自的 $D_i$ 上已有这些迹等式。对有限多个种子同时避开例外处，仍有稠密的共同 Frobenius 集。这给本引理的稠密条件。目标迹既保留指定 Frobenius 上的值，又保留全部多项式迹恒等式，下一步因而可以重建半单表示。

## Lean 对照

- [`exists_trace_limit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/ExistsTraceLimit.lean#L15) [`exists_trace_limit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/ExistsTraceLimit.lean#L15) 以趋近滤子证明 Cauchy 性。在源码中，最后一段的逐变量趋近写成乘积空间的闭包。
- [`limWU4_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/LimFinOddOf.lean#L16) [`limWU4_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/LimFinOddOf.lean#L16) 验证有限种子共用的稠密性并应用本引理。种子的独立构造及 `PolyApprox` 的 Hecke 同余输入由上游提供。本篇按源码对读。
