# 怎样从本征值的模长范围得到 Frobenius 迹列表

同核特征的整数界依赖一个可在不同 $\ell$ 间共用的迹列表。这里证明先有本征值列表后，怎样产生秩三不可约和秩二角块两种迹数据。核心是不等式 $\sqrt q+2$，它来自本征值的模长范围和模长乘积。[这些迹怎样构成同一个整数](%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E8%BF%B9%E5%B7%AE%E7%9A%84%E4%B9%98%E7%A7%AF%E6%98%AF%E4%B8%80%E4%B8%AA%E9%9D%9E%E9%9B%B6%E6%95%B4%E6%95%B0.md)

## 本征值列表的精确含义

给定 $n,q\ge1$、整数权 $m_1,\ldots,m_n$ 和整数 $w$。`EigData` 是有限指标集 $S$，每个 $s$ 对应含重数的 $n$ 个复数 $\beta_s$。它满足下列三项。

1. 任意复域自同构 $\sigma$ 都在 $S$ 上诱导某个置换 $u$，使 $\beta_{u(s)}$ 是逐项施加 $\sigma$ 的多重集。
2. 写 $a=\sqrt q$、$C=q^{w/2}$。每个 $b\in\beta_s$ 满足 $C/a<|b|<aC$，而 $\prod_{b\in\beta_s}|b|=C^n$。
3. 若整数 $u$ 满足 $u\ge-\min_i m_i$，则每个 $q^u b$ 为代数整数。若 $u\ge\max_i m_i$，则每个 $q^u b^{-1}$ 为代数整数。

当这组数据“分类”某类 $\ell$ 进表示时，固定一个素处 $v$ 并取域同构 $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$，有一个把允许表示送到 $S$ 的映射。映到同一指标的表示一定同构。表示在 $v$ 不分歧，且对算术 Frobenius $\Phi$ 的逆，$\iota$ 下的本征值多重集为 $\{b^{-1}:b\in\beta_s\}$。对每个绝对素处的 Frobenius 提升都用同一个指标。不同指标可对应同一个多重集。

## 命题

令 $e\ge0$ 为整数。以下两种转换都保留指标集 $S$。

- 若输入为秩三 `EigData`，参数 $q\ge1$、$m=(e-1,-1,-e-1)$、$w=-2$，定义 $t_s=\sum_{b\in\beta_s}(q b)^{-1}$。
- 若输入为秩二 `EigData`，参数 $p\ge1$、$m=(e,-e)$、$w=0$，对任意整数 $h\ge0$ 令 $q=p^h$，定义 $t_s=1+\sum_{b\in\beta_s}b^{-h}$。

两种情形都有 $|t_s|\le\sqrt q+2$，$q^e t_s$ 为代数整数，且指标上的 Galois 置换对 $t_s$ 仍成立。这三个性质就是迹列表 `TrData`。

## 秩三的三项模长怎样相加

因 $w=-2$，设 $x_i=|(q b_i)^{-1}|$，即有 $a^{-1}\le x_i\le a$、$a=\sqrt q$，且 $x_1x_2x_3=1$。三者中有两项在 $1$ 的同一侧或等于 $1$。把它们记为 $u,v$，第三项记为 $z$。那么

$$
(u-1)(v-1)\ge0\quad\Longrightarrow\quad u+v\le1+uv=1+z^{-1}.
$$

另一方面，由 $a^{-1}\le z\le a$，有

$$
(a-z)(z-a^{-1})\ge0
\quad\Longrightarrow\quad z+z^{-1}\le a+a^{-1}\le a+1 .
$$

所以 $u+v+z\le a+2$。三角不等式给所需的迹上界。清分母时逐项写

$$
q^e(qb)^{-1}=q^{e-1}b^{-1}.
$$

因 $\max_i m_i=e-1$，这由定义第 3 条为代数整数，故相加仍为代数整数。自同构固定 $q$ 且与求逆、求和交换，所以保留 Galois 置换。

## 秩二怎样加上一个平凡特征

因输入权为零，$|b_1|\,|b_2|=1$，且两个 $|b_i^{-h}|$ 都至多 $a=\sqrt{p^h}$，乘积仍为 $1$。记这两个数为 $u,v$。则 $(a-u)(a-v)\ge0$ 给

$$
u+v\le a+a^{-1}\le a+1.
$$

再加上平凡项 $1$，得到 $|t_s|\le a+2$。两项分别由

$$
q^e b^{-h}=(p^e b^{-1})^h
$$

为代数整数，平凡项 $q^e$ 也为代数整数。Galois 稳定性和第一种情形相同。

## 为什么换算后恰是所需的 Frobenius 迹

以下取实际应用的 $e\ge1$，以及 $K$ 的一个 $p$ 上方素处 $v$，记 $q=\mathrm Nv=p^h$。令 $\ell$ 为奇素数，$\ell\ne p$。令 $\Phi$ 为 $v$ 的算术 Frobenius。项目要求分类的是 $\operatorname{tr}\rho(\Phi^{-1})$。

对不可约的 `Adm3U_s` 表示，先用 $\rho'=\rho\otimes\varepsilon_\ell^{-1}$。这把惯性权从 $(e,0,-e)$ 变成 $(e-1,-1,-e-1)$，保留互异性，反序配对和为 $-2$。局部旗标的各商同时乘 $\varepsilon_\ell^{-1}$，所以它们之间不存在相差 $\varepsilon_\ell$ 的关系仍保持。它在 $\ell$ 外惯性上是同一个表示。由 `CountKAlt` 的分类，将 $\rho'$ 送到秩三本征值列表 $\beta_s$，于是 $\rho'(\Phi^{-1})$ 的本征值在 $\iota$ 下为 $b^{-1}$。因为 $\varepsilon_\ell(\Phi)=q$，要回到 $\rho(\Phi^{-1})$，须再乘 $\varepsilon_\ell(\Phi^{-1})=q^{-1}$，恰得 $(qb)^{-1}$。对 $\rho'$ 的同构可用反扭曲传回 $\rho$。

对秩二角块，取允许性见证 $W:G_\mathbb Q\to\mathrm{GL}_2(\overline{\mathbb Q}_\ell)$，使 $\rho\simeq\mathbf1\oplus W|_{G_K}$。`NewAdmAlt` 使这个有秩二新形式、级 $M=N|\operatorname{disc} K|$ 及行列式权 $0$ 的 $W$ 进入 `CountQAlt` 的分类。设 $\Phi_p$ 为有理素处的算术 Frobenius（取同一个绝对素处）。限制到剩余域可知 $\Phi$ 在有理数域的分解群模惯性中等于 $\Phi_p^h$，所以 $\Phi(\Phi_p^h)^{-1}$ 属于惯性群。因为 $p\nmid M$ 且 $\ell\ne p$，$W$ 在 $p$ 处不分歧。于是 $W(\Phi^{-1})=W(\Phi_p^{-1})^h$。将 $W(\Phi_p^{-1})$ 在代数闭域上上三角化，取幂后对角线各本征值变成 $b^{-h}$，其中 $b^{-1}$ 由 `FrobEig` 给出。再加平凡块的迹 $1$，即为第二个公式。若两秩三点因选出的 $W$ 映到同一指标，则 $W$ 在 $G_\mathbb Q$ 上同构，限制并直和 $1$ 后秩三点也同构。

精确说，`CountKAlt` 对每个域 $K$ 和每个秩 $n\ge2$ 给 $c,A$，对每组严格递减的整数权 $|m_i|\le H$、$m_i+m_{n+1-i}=1-n$、级 $M\ge1$ 和 $p\nmid M|\operatorname{disc}K|$ 的素处，给统一覆盖全部 $\ell\ne2,p$ 的列表，大小至多 $c[M(H+1)]^A$。`CountQAlt` 对 $\mathbb Q$ 允许配对和为任意共同 $w$，排除 $p\mid M$，给同型上界。此处只用前者的 $n=3,H=e+1,M=N$ 和后者的 $n=2,H=e,M=N|\operatorname{disc}K|$。在固定 $K$ 后，因为 $e+2\le2(e+1)$，两条列表都有 $c_K[N(e+1)]^{A_K}$ 型大小界。它们的并集按不同分支保留各自的指标。

## Lean 对照与证明范围

- `EigData` 第 18 行，`EigData.Classifies` 第 34 行，`TrData` 第 70 行。[本征值及迹数据](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/WinDefs.lean)
- [`traces_from_eigenvalues_rank3`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/FrobeniusTraceCountBoundOfRatEigensystemCount.lean#L78) `traces_from_eigenvalues_rank3` 第 78 行，[`traces_from_eigenvalues_rank2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/FrobeniusTraceCountBoundOfRatEigensystemCount.lean#L169) `traces_from_eigenvalues_rank2` 第 169 行。两条都需保留指标，即使不同表示的迹相等。[两种列表转换](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/FrobeniusTraceCountBoundOfRatEigensystemCount.lean)
- [`frobenius_trace_count_bound_of_cm_eigensystem_count_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean#L418)、[`frobenius_trace_count_bound_of_rat_eigensystem_count_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean#L348) 在第 418、348 行分别将两条转换用于主线的允许表示，调用 `CountKAlt`、`CountQAlt` 与 `NewAdmAlt`。[主线实例化](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean)

本篇为源码对读。自守本征系统的计数及允许性是上游输入。未重新编译或查询传递公理。
