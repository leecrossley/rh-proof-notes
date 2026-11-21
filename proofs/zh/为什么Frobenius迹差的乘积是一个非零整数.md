# 为什么 Frobenius 迹差的乘积是一个非零整数

I 类计数需要一个和系数素数 $\ell$ 无关的整数。这个整数可以从一张有限的复 Frobenius 迹列表构造。这里给出确切乘积、非零性的来源，以及在任一 $\ell$ 进域里它如何同时界定许多迹差。

## 命题

设整数 $q\ge7,\ e\ge1$。令 $S$ 为一有限指标集，$t_s\in\mathbb C$（$s\in S$）满足

$$
|t_s|\le\sqrt q+2,\qquad q^e t_s\text{ 是代数整数}.
$$

还要求每个域自同构 $\sigma:\mathbb C\to\mathbb C$ 都可用一个 $S$ 的置换 $s\mapsto\sigma_*s$ 实现 $\sigma(t_s)=t_{\sigma_*s}$。这是主线的 `TrData`，列表允许不同指标有相同数值。再取一个有限指标集 $A$ 和单位根 $z_a\in\mathbb C^\times$（$a\in A$），也满足同样的 Galois 置换条件。定义

$$
E(q,e,z)=q^{-e}z+1+q^e z^{-1}.
$$

则存在非零整数 $D$，使

$$
\log|D|\le |A||S|\bigl(2e\log q+1\bigr).
\tag{1}
$$

这个整数同时满足以下性质。取任意素数 $\ell\nmid q$、域同构 $\iota:\overline{\mathbb Q}_\ell\to\mathbb C$、群 $\Gamma$ 和 $g\in\Gamma$。设对于一类给定的 $\rho:\Gamma\to\mathrm{GL}_3(\overline{\mathbb Q}_\ell)$，有一个编号 $s(\rho)\in S$ 使

$$
\operatorname{tr}\rho(g)=\iota^{-1}(t_{s(\rho)}), \qquad
s(\rho)=s(\rho')\ \Longrightarrow\ \rho\simeq\rho'.
$$

这里 $\rho\simeq\rho'$ 表示由一个固定可逆矩阵共轭。对每个 $a$ 取这类表示的任意有限子集 $X_a$，要求每个 $X_a$ 内两两不同构。则所有迹差非零，并且

$$
|D|_\ell\le
\prod_{a\in A}\prod_{\rho\in X_a}
\left|\operatorname{tr}\rho(g)-\iota^{-1}(E(q,e,z_a))\right|_\ell .
\tag{2}
$$

$\iota$ 只作域同构使用。复范数和 $\ell$ 进范数的过渡通过整数性完成。

## 先使每个迹差非零且整

设 $Q=q^e\ge q$。因为 $|z_a|=1$，

$$
|E(q,e,z_a)|\ge Q-1-Q^{-1}>\sqrt q+2\ge|t_s|.
$$

严格不等式可由 $\sqrt q\le q/2$ 和 $3+1/q<q/2$ 在 $q\ge7$ 时得到。故每个 $t_s-E(q,e,z_a)$ 非零。取

$$
F_{a,s}=q^e(t_s-E(q,e,z_a))
=Q t_s-z_a-Q-Q^2z_a^{-1}.
$$

右端每项都是代数整数。并且

$$
|F_{a,s}|\le Q^2+Q(\sqrt q+3)+1\le2Q^2.
$$

最后用 $Q\ge\sqrt q+3+1/Q$，也是刚才的不等式。于是 $\log|F_{a,s}|\le2e\log q+\log2\le2e\log q+1$。

## 取全乘积并只保留所需因子

令 $D=\prod_{a,s} F_{a,s}$。对任何复域自同构，$F_{a,s}$ 按 $A,S$ 上的置换同时改变下标。因此乘积固定。所有因子代数，取其共同的有限正规闭包，固定于全部复域自同构就推出乘积是有理数，因为正规闭包的自同构都可以延拓到 $\mathbb C$。代数整数的有理数是整数，乘积也由各因子非零得非零。逐因子取对数即得 (1)。

把这个乘积通过 $\iota^{-1}$ 送到 $\overline{\mathbb Q}_\ell$。代数整数的 $\ell$ 进绝对值至多 $1$。固定 $a$ 时，$\rho\mapsto s(\rho)$ 在 $X_a$ 上单射，因为相同编号意味着表示同构。故我们能删去该产品中未使用的 $s$；删去模不超过 $1$ 的因子只会使产品变大。对保留的因子，$q^e$ 的 $\ell$ 进模为 $1$，所以其模正是 (2) 中的迹差的模。得到 (2)。

## 主线怎样代入虚二次域

对虚二次域 $K$，取 $e\ge1,N\ge1$ 和素数 $p\ge7,\ p\nmid N|\operatorname{disc} K|$。取 $K$ 中一个 $p$ 上方的素处 $w$。$q=\mathrm Nw=p^f$，其中 $1\le f\le2$。源码构造两张这样的迹列表，分别接收秩三允许表示和 $1\oplus$ 秩二允许表示。它们给出对 $g$ 为 $w$ 处逆算术 Frobenius 的分类。两张列表分别有至多 $c_1[N(e+1)]^{A_1}$、$c_2[N|\operatorname{disc}K|(e+1)]^{A_2}$ 个指标，常数只依赖 $K$。取两个指标集的不交并，对同时属于两类的表示任选第一类的编号即可。要给出这个输入，需从复自守特征系统取得列表，并证明接收所规定的两类 Galois 表示。这里保留其完整数值接口，分类证明在上游。

把这张并起来的列表代入 (1)、(2)。因 $\log q\le2\log p$，令 $Y=N(e+1)$，有 $2e\log q+1\le 5Y\log p$。并且

$$
|S|\le (c_1+c_2|\operatorname{disc}K|^{A_2})Y^{A_1+A_2}.
$$

所以 $D$ 有界

$$
\log|D|\le 5(c_1+c_2|\operatorname{disc}K|^{A_2})\,
|A|\,Y^{A_1+A_2+1}\log p.
$$

这正是 `NumberU3U_s` 的整数和 $\ell$ 进乘积上界。它用于 I 类时，$A$ 是一族同核的复 Dirichlet 特征，$z_a$ 是它们在 $q=\mathrm Nw$ 的取值的逆。

## Lean 对照与证明范围

- 主线调用 [`eisenstein_trace_difference_log_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/FrobeniusTraceCountBoundOfRatEigensystemCount.lean#L237) 的单项估计和 [`frobenius_trace_norm_nonzero_log_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/FrobeniusTraceCountBoundOfRatEigensystemCount.lean#L329) `UpperTheory.GalN.V.Win.frobenius_trace_norm_nonzero_log_bound` 第 329 行。这个版本的复迹界为 $\sqrt q+2$。[非零迹差和整数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/FrobeniusTraceCountBoundOfRatEigensystemCount.lean) · [列表的定义和分类](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/AdmissibleResidues/WinDefs.lean)
- [`exists_int_eq_prod_of_galois_permuted_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/ExistsIntEqProdOfGaloisPermutedIntegral.lean#L5) 用 Galois 置换取整数乘积，[`adicNorm_prod_le_prod_of_injective_classes`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/AdicNormProdLeProdOfInjectiveClasses.lean#L5) 删除未使用的整数因子完成 (2)。[取整数](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/ExistsIntEqProdOfGaloisPermutedIntegral.lean) · [部分乘积](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/AdicNormProdLeProdOfInjectiveClasses.lean)
- [`numberU3U_of_adm2A_imp_adm2B`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/KeepNumU.lean#L25) `numberU3U_of_adm2A_imp_adm2B` 第 25 行组合两张列表并算出最后界，[`numberU3U_of_prints`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/KeepNumU.lean#L79) 第 79 行传入实际输入。[组合列表](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/KeepNumU.lean) · [两张列表的证明入口，第 348、418 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FrobeniusTraceCountBoundOfCmEigensystemCount.lean)

本篇为源码对读。由本征值列表构造两张迹列表的证明已另文展开。未重新编译或查询传递公理。[本征值到迹](%E6%80%8E%E6%A0%B7%E4%BB%8E%E6%9C%AC%E5%BE%81%E5%80%BC%E7%9A%84%E6%A8%A1%E9%95%BF%E8%8C%83%E5%9B%B4%E5%BE%97%E5%88%B0Frobenius%E8%BF%B9%E5%88%97%E8%A1%A8.md)
