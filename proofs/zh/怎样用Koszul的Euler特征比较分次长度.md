# 怎样用 Koszul 的 Euler 特征比较分次长度

分次长度引理同时要把方程平方、取商并比较不同系数格。这里说明它为什么可以用同一个整数衡量这几种操作。在源码中，这个整数由递归定义的 `chi` 表示。用 Koszul 复形解释，可以把递归中符号和移位的来源一并看清。

## 命题与记号

令 $B$ 为 Noether 局部环，极大理想 $\mathfrak m$。设 $R=\bigoplus_{\mathbf d\in\mathbb N^k}R_{\mathbf d}$ 为标准多分次 $B$-代数，$R_{\mathbf0}=B$，每个单位次数 $R_{\mathbf e_i}$ 有限生成，这些分量生成 $R$。令 $M$ 为有限生成的 $\mathbb Z^k$ 分次 $R$-模。记

$$
\mathfrak I=\prod_{i=1}^k (R_{\mathbf e_i}),\qquad
J_{\boldsymbol s}=(s_1,\ldots,s_n),
$$

其中 $(R_{\mathbf e_i})$ 是相应齐次分量生成的理想，$s_i\in R_{\boldsymbol\delta_i}$ 为齐次截面。条件 `admitted` 指存在整数 $N\ge0$，使

$$
(\mathfrak m R\cdot\mathfrak I)^N\subseteq \operatorname{Ann}_R M+J_{\boldsymbol s}.
\tag{1}
$$

下文“充分大的 $\mathbf d$”指每个坐标都充分大。若 (1) 成立，则在这些次数，Koszul 复形 $K(\boldsymbol s;M)$ 的齐次同调模有有限 $B$-长度。令

$$
\chi(\boldsymbol s;M)_{\mathbf d}
=\sum_j(-1)^j\operatorname{length}_B H_j(K(\boldsymbol s;M))_{\mathbf d}.
\tag{2}
$$

则 (2) 等于源码的 `chi`。它与 $\boldsymbol s$ 的顺序无关，对严格分次短正合列可加，且

$$
0\le\chi(\boldsymbol s;M)_{\mathbf d}.
\tag{3}
$$

具体地，若 $(\boldsymbol s,\boldsymbol u)$ 满足 (1)，则

$$
\chi(\boldsymbol s,\boldsymbol u;M)_{\mathbf d}
\le \chi(\boldsymbol u;M/J_{\boldsymbol s}M)_{\mathbf d}.
\tag{4}
$$

若 $M\twoheadrightarrow M'$ 是分次满射，且 $\boldsymbol s$ 对 $M$ 满足 (1)，则 $\chi(\boldsymbol s;M')_{\mathbf d}\le\chi(\boldsymbol s;M)_{\mathbf d}$。

另取 $b\in B$，假设 $b$ 在 $M$ 上乘法单射，且 (1) 对 $M/bM$ 和空截面列成立。设首个截面 $y$ 的次数为 $\boldsymbol\delta$，$c\ge0$，且 $(b^cy,\boldsymbol u)$ 对 $M$ 满足 (1)。以 $h(\mathbf d)=\operatorname{length}_B(M/bM)_{\mathbf d}$，记差分 $\Delta_{\boldsymbol\delta}h(\mathbf d)=h(\mathbf d)-h(\mathbf d-\boldsymbol\delta)$。则

$$
\chi(b^cy,\boldsymbol u;M)_{\mathbf d}
=\chi(y,\boldsymbol u;M)_{\mathbf d}
+c\!\left(\prod_{u\in\boldsymbol u}\Delta_{\deg(u)}h\right)(\mathbf d).
\tag{5}
$$

## 为什么 Euler 特征在大次数有意义

每个 Koszul 同调是有限生成的分次模，并由 $\operatorname{Ann}_R M+J_{\boldsymbol s}$ 消去。截面消去同调是因为截面乘法在 Koszul 复形上链同伦于零。对任一个这样的同调模 $L$，取有限个齐次生成元。若 $\mathbf d$ 比每个生成元的次数在各坐标都至少大 $N$，标准多分次的生成条件给出 $L_{\mathbf d}\subseteq(\mathfrak I^N L)_{\mathbf d}$。于是 (1) 给 $\mathfrak m^N L_{\mathbf d}=0$。每个 $L_{\mathbf d}$ 有限生成，故在 Artin 局部环 $B/\mathfrak m^N$ 上长度有限。

用乘法 $s$ 的二项复形先计算同调，得到商 $M/sM$ 和移位后的 $\ker(s:M\to M)$。再用余下的 Koszul 复形，并取同一齐次次数。双复形两种求同调的 Euler 特征相同，因为在足够大的次数二者的同调项长度都有限，逐页求同调保留交替和。这给出递归

$$
\chi(s,\boldsymbol u;M)
=\chi(\boldsymbol u;M/sM)-\chi(\boldsymbol u;\ker(s)[-\deg s]),
\tag{6}
$$

其中 $(L[-\boldsymbol\delta])_{\mathbf d}=L_{\mathbf d-\boldsymbol\delta}$。这就是源码的定义。排列截面只会重排 Koszul 因子并改变某些基的符号，复形同构。短正合列用 Koszul 复形的长正合序列给出可加性。

## 非负性怎样从素商得到

对有限生成的分次模取齐次素过滤，每个商是某个 $R/P$ 的分次移位。可从有限齐次生成元中反复选一个齐次元素，使它在当前商中的湮灭理想在这些湮灭理想中极大。由极大性，该理想对齐次元素的乘积具有素理想性质；用 $\mathbb Z^k$ 上与加法相容的全序考察各式的最高非零次，即得它是素理想。Noether 条件使所得到的子模链终止。每个素商的湮灭理想含 $\operatorname{Ann}_R M$，故 (1) 对每一项仍成立。由可加性，只需证素商。

若 $P$ 含 $\mathfrak I$，则至少一个方向的单位次分量都在 $P$，所以 $R/P$ 的大次数分量为零。截面的次数与所有移位都固定，其 Euler 特征最终为零。余下的 $P$ 在每个单位次数方向都有一个不落在 $P$ 的截面。因此在每个 $\boldsymbol\delta\ge0$ 可选一个同次非零元素 $s'$（次数零用 $1$）。

现在对截面数归纳。空列时是长度。对首个截面 $s$，若其在整环 $R/P$ 中非零，则乘法单射，(6) 化成商上的短列。若 $s=0$，把它换成刚才的同次 $s'$。此时设 $N_0=R/P$，有分次正合列

$$
0\to N_0[-\deg s']\xrightarrow{s'}N_0\to N_0/s'N_0\to0.
$$

取剩余截面的 Euler 特征，就得到它在 $N_0$ 及其移位的差，而这个差正是首截面为 $0$ 时的 (6)。此处 (1) 对素商原来的剩余截面已经成立，因为 $s$ 在其中为零。因此换截面仍可使用 (1)，并可在所得商上按截面数归纳。这样证明 (3)。

用 (6) 逐个处理 $\boldsymbol s$，每次删掉一个非负的核项，就得到 (4)。这些核由相应截面和原湮灭理想消去，所以缩短的截面列仍满足 (1)。同理，对满射取其分次核，核的 Euler 特征由 (3) 非负，遂得满射下的比较。

## 分离一个均匀化元的幂

若 $b$ 的乘法单射，则 $\ker(by)=\ker(y)$，并有

$$
0\to M/yM\xrightarrow{\ b\ }M/byM\to M/bM\to0.
$$

映射为乘 $b$，其左端的单射性也正来自 $b$ 在 $M$ 上的单射性。因为 $\deg b=0$，这些商无额外移位。用 (6) 消掉相同的核项，再用可加性，得到

$$
\chi(by,\boldsymbol u;M)
=\chi(y,\boldsymbol u;M)+\chi(\boldsymbol u;M/bM).
$$

迭代 $c$ 次。对 $M/bM$，空列满足 (1)，故大次数下连 Koszul 各链模本身都有限长，Euler 特征等于链模长度的交替和。这个交替和恰为 $\prod_{u}\Delta_{\deg(u)}h$，于是得到 (5)。

若有 $n\ge1$ 个同次截面 $b^{c_i}y_i$，再有一列 $\boldsymbol u$，可以逐个抽出 $b^{c_i}$。每次抽取时，另外 $n-1$ 个截面的次数都保持原值，故每次出现同一个差分。最后把所有无 $b$ 因子的截面所剩的 Euler 特征用 (3) 下界为零，即得

$$
\chi(b^{c_1}y_1,\ldots,b^{c_n}y_n,\boldsymbol u;M)_{\mathbf d}
\ \ge\
\left(\sum_{i=1}^n c_i\right)
\left(\Delta_{\boldsymbol\delta}^{n-1}\prod_{u\in\boldsymbol u}\Delta_{\deg(u)}h\right)(\mathbf d).
\tag{7}
$$

## Lean 对照与证明范围

源码直接以 (6) 定义 `chi`，以分次模的短正合列和素过滤建立规则。本文用 Koszul 复形给相同递归、可加性和调序一个共同解释。

- `chi`、`admitted` 第 66、94 行。[定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerVanishingBelowDimension.lean)
- [`euler_additivity_of_rules`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerAdditivityExactSequence.lean#L386) `euler_additivity_of_rules` 第 386 行，[`euler_rule_two_of_graded_finite_iso`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerIndependenceOfOrder.lean#L586) `euler_rule_two_of_graded_finite_iso` 第 586 行。[可加性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerAdditivityExactSequence.lean) · [调序](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerIndependenceOfOrder.lean)
- [`rulePos`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/RulePos.lean#L24) `rulePos` 第 24 行，[`ruleUB`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/RuleUB.lean#L25) `ruleUB` 第 25 行，[`ruleMono`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/RuleMono.lean#L11) `ruleMono` 第 11 行。[非负性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/RulePos.lean) · [删掉核项](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/RuleUB.lean) · [满射比较](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/RuleMono.lean)
- [`euler_rule_product_zero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerRuleProductZero.lean#L60) `euler_rule_product_zero` 第 60 行与 [`la_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/GradedModulesLength/LaDifPerm.lean#L77) `la_holds` 第 77 行是 (5)、(7) 的入口。[乘积公式](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/ValuationFrobeniusEpsilon/LeastPrimeTwists/QuotientShiftIrreducible/NoetherianQuotientCalc/EulerRuleProductZero.lean) · [提出幂次](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/GradedModulesLength/LaDifPerm.lean)

本篇为源码对读，未重新编译或查询传递公理。
