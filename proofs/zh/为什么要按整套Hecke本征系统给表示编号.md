# 为什么要按整套 Hecke 本征系统给表示编号

同一个素处的迹相同，通常不足以确定一个 Galois 表示。然而整数乘积需要每个非同构表示都能占到一个独立指标。本篇说明工程怎样用几乎所有素处的 Hecke 本征值来编号，再只在一个素处读出所需的值。这给秩三和秩二的本征值列表提供上游输入。[本征值数据的定义及迹换算](%E6%80%8E%E6%A0%B7%E4%BB%8E%E6%9C%AC%E5%BE%81%E5%80%BC%E7%9A%84%E6%A8%A1%E9%95%BF%E8%8C%83%E5%9B%B4%E5%BE%97%E5%88%B0Frobenius%E8%BF%B9%E5%88%97%E8%A1%A8.md)

## 命题与所用自守输入

取 CM 数域 $K$、整数秩 $n\ge2$、严格递减的整数权 $\mathbf m=(m_1,\ldots,m_n)$，其中 $|m_i|\le H$、$m_i+m_{n+1-i}=w$。取级 $M\ge1$ 和有理素数 $p\nmid M|\operatorname{disc}K|$，以及 $K$ 中 $p$ 上方的素处 $v$，令 $q=\mathrm Nv$。对下面两个类别，项目在明确的自守输入下，构造同一份 `EigData`，它有至多 $c[M(H+1)]^A$ 个指标，分类所有 $\ell\ne2,p$ 的相应允许表示。这里 $c,A$ 只依赖 $K,n$。

- `CountKAlt` 取 $w=1-n$。复自守族 `SigK` 由满足以下条件的 $\mathrm{GL}_n(\mathbb A_K)$ 尖点表示组成：在每个复嵌入处的无穷小特征多重集为 $\{m_i+(n-1)/2\}$；对偶等于复共轭拉回；有限部分有主同余子群 $K(M)$ 的不变向量。
- `CountPAlt` 取 $K$ 为虚二次域，并允许任意共同的反序配对和 $w$。复自守族 `SigP` 的权与 $K(M)$ 的条件相同，对偶要求放宽到存在项目的极化伴随特征。

这里 $K(M)$ 是 $\mathrm{GL}_n(\widehat{\mathcal O_K})$ 中模 $M$ 同余于单位矩阵的主同余子群。两种情形具体使用如下条件。

1. 对任一同构类互异的有限自守子族，基数至多 $c[M(H+1)]^A$（`CardK` 或 `CardP`）。
2. 在每个 $u\nmid M$ 的有限素处，该自守表示有唯一的 Satake 多重集。它是未分歧局部表示的球面 Hecke 本征参数。把它乘 $(\mathrm Nu)^{(n-1)/2}$ 得到代数归一化的多重集 $\mathcal B_\pi(u)$。同构的表示给相同多重集。任给复域自同构 $\sigma$，族中仍有一个 $\pi'$，使所有这些素处的 $\mathcal B_{\pi'}(u)$ 都是逐项施加 $\sigma$ 的结果。
3. 在 $v$ 处，$\mathcal B_\pi(v)$ 的基数为 $n$，设 $\beta_\pi(v)$ 是逐项取逆。对 $\beta_\pi(v)$，有模长窗 $q^{w/2}/\sqrt q<|b|<q^{w/2}\sqrt q$，模长乘积为 $q^{nw/2}$。且若 $u$ 为整数，$u\ge-\min_i m_i$ 时 $q^u b$ 整，$u\ge\max_i m_i$ 时 $q^u b^{-1}$ 整。源码由 `win_algSat` 及两条代数整数性（`intK_of_prints` 或 `intP'_alt`）验证这一项。
4. 级相容性 `LevelKNAlt` 或 `LevelPNAlt` 保证：对任意允许的连续半单 $\ell$ 进表示 $r$，其给定的尖点自守见证属于相应的复自守族，而且在每个 $u\nmid \ell M$ 处，$r$ 不分歧，$\iota$ 下的逆算术 Frobenius 本征值就是 $\mathcal B_\pi(u)$。这一步同时使用表示的局部级和权、在 $\ell$ 上方的旗标安全条件及 `WitA` 中的局部相容性见证。

前两项只关乎复自守族，第三项只需在要读值的素处 $v$ 验证，第四项把 $\ell$ 进表示接到这个复族。后面的编号与计数只需要这些数学性质。

## 先固定整套系统，再投影到一个素处

写 $\mathcal W=\{u:u\nmid M\}$。对每个 $\pi$ 考虑函数

$$
\operatorname{sys}(\pi):\mathcal W\longrightarrow
\{\text{复数的有限多重集}\},
\qquad u\longmapsto \mathcal B_\pi(u).
$$

取 $S$ 为这些函数的集合。若取其中任意 $B$ 个互异函数，为每个选一个 $\pi$。由第 2 项，同构的两个 $\pi$ 有相同函数。因此选出的 $\pi$ 两两不同构。第 1 项给 $B\le c[M(H+1)]^A$。故整个 $S$ 有限且满足同一界。这里无需先证明一个本征系统只来自一个自守表示。

现在给每个 $s\in S$ 定义 $\beta_s$，即 $s(v)$ 中本征值的逆。第 2 项表明，逐项施加 $\sigma$ 把 $S$ 映进自身。用 $\sigma^{-1}$ 得到逆映射，所以它是有限集的一个置换，而且 $\beta_s$ 同样逐项变换。第 3 项恰保证 `EigData` 的其余性质。这样指标保留了整套系统的区别，随附的数值只取自 $v$。

## 同一编号为什么给同构

对每个允许表示 $r$，取第 4 项给出的尖点见证 $\pi(r)$ 并赋予指标 $\operatorname{sys}(\pi(r))$。若 $r,r'$ 的指标相同，则在每个 $u\nmid\ell M$ 处，两者的逆 Frobenius 特征多项式相同。对不分歧表示，Frobenius 元素可逆，取逆后的多项式相同也给原来的多项式相同，特别地给出迹相同。

Chebotarev 稠密定理加迹函数的连续性，给出两个表示的迹函数在全群上相同。用特征零的 Brauer–Nesbitt 定理，两个连续半单表示同构。源码把最后这段写为 `iso_of_frobenius_of_printed_results`。因为 $v\nmid M$ 且 $p\ne\ell$，第 4 项在 $v$ 给所需的 Frobenius 多重集，于是整个 `EigData.Classifies` 成立。它也解释了为什么只读一个 $v$ 的列表仍能给同构类计数。

## 多项式计数上游的形式

`CardK` 在源码通过紧开子群的上同调计数获得。给定权 $\mathbf m$，先选一个无穷处有限维系数系统 $\Xi$，使它的无穷小特征适合该权，且维数 $d_\Xi\le c_1(H+1)^{A_1}$（Weyl 维数）。每个所数尖点表示在此系数的 $(\mathfrak g,K_\infty)$ 上同调有贡献，因而也在级 $K(3M)$ 的自守上同调有贡献：确有 $K(3M)\subset K(M)$。Borel 型注入的计数结论是，取两两不同构的有限集合，其基数不超过这一级别、系数 $\Xi$ 所对应的总上同调维数。项目的基本域计数把这个维数界为 $c_2M^{A_2}d_\Xi$。所以总基数至多

$$
c_1c_2 M^{A_2}(H+1)^{A_1}
\le c_1c_2[M(H+1)]^{A_1+A_2}.
$$

极化的 `CardP` 有同样的 $\Xi$、同一级包含及同样的同调维数估计。两段使用的调和分析和上同调结论在此作为数学输入。它们作用在自守族上，之后才传到 $\ell$ 进 Galois 表示。

## Lean 对照与证明范围

- [`exists_eigData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/WinDefs.lean#L130) `exists_eigData` 第 130 行从本征系统的像构造列表。[通用构造](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/WinDefs.lean)
- [`countK_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean#L63) `countK_alt` 第 63 行、[`countP_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean#L129) `countP_alt` 第 129 行实例化所需条件。[两条 CM 域计数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean)
- `SigK`、`CardK`、`SlopesIn` 分别在第 13、19、58 行。`SigP` 第 16 行。`LevelKNAlt`、`LevelPNAlt` 第 51、58 行给级相容性。[共轭自对偶族](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/AutomorphicForms/IsoOfFrob.lean) · [极化族](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/CrystallineBaseChange/CqStmt.lean) · [分辨 Galois 表示的条件](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/AutQN.lean)
- `card_k_of_printed_results` 第 18 行直接合成 Weyl 维数、Borel 上同调计数和基本域计数。[多项式上界](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/TCardK.lean)

本篇为源码对读。复自守族的级相容性、共轭稳定、模长窗及代数整数性是明示输入。未重新编译或查询传递公理。
