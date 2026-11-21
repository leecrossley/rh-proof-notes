# 分裂素处的晶体提升为什么要付两份 Wach 指数

## 命题

固定奇素数 $\ell$，令 $K/\mathbb Q_\ell$ 为有限不分歧扩张，$L/\mathbb Q_\ell$ 为包含分圆层 $K(\mu_\ell)$ 各嵌入像的有限扩张，$O=\mathcal O_L$，$G=G_K$。给定两个有限维连续晶体 $L$-表示及其稳定满格 $T_1,T_2$，和等变格满射 $F:T_1\twoheadrightarrow T_2$。设在每个 $K\hookrightarrow L$ 下，源表示的过滤跳点均在 $[-M,h]$，其中 $M,h\ge0$ 为整数。令 $S$ 为源表示的跳点集合，并按[提升指数的算术式](%E5%B1%80%E9%83%A8%E6%8F%90%E5%8D%87%E6%8C%87%E6%95%B0%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%AA%E4%BE%9D%E8%B5%96%E8%BF%87%E6%BB%A4%E7%AA%97%E5%8F%A3%E7%9A%84%E5%AE%BD%E5%BA%A6.md)定义 $e_W=e_W(\ell,M+h)$ 与 $e_U=e_U(\ell,M,S)$。

在下文列出的局部 Wach 比较输入下，对每个 $\kappa\in H_f^1(G,T_2)$，有 $\kappa_1\in H_f^1(G,T_1)$ 使

$$
F_*\kappa_1=\ell^{2e_W+e_U}\kappa .
$$

此处保留整系数。$H^1_f(G,T)$ 指整上同调中在有理晶体周期环上变成余边界的类。

这里处理奇素数上不分歧局部域的一层分圆情形。工程在二和三处另用情形 B，再经余限制回到原域。[二和三处的局部提升路线](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%8F%90%E5%8D%87%E6%8C%87%E6%95%B0%E5%9C%A8%E6%8D%A2%E5%9B%9E%E5%8E%9F%E5%B1%80%E9%83%A8%E5%9F%9F%E6%97%B6%E5%8F%AA%E5%8A%A0%E6%AC%A1%E6%95%B0%E8%B5%8B%E5%80%BC.md)

## 局部比较输入

将格 $T$ 送到一个带两个交换算子 $\varphi,\gamma$ 的模 $D(T)$，并在其中取 Wach 子模 $N(T)$。下面都在有限的温和分圆群 $\Delta$ 的不变量上工作；它的阶为 $\ell-1$，平均投影有效。取 $X=\pi_0$，分圆不变量参数，$Q=X+\ell$。允许的一次项是

$$
\{(y,z):Q^My\in N(T)^\Delta,\ z\in XN(T)^\Delta\}.
$$

它的 Herr 微分为 $(\gamma-1)y-(\varphi-1)z$。这里用到以下具体输入。

1. 任何格满射，在晶体源的跳点位于该窗口时，其 Wach 模的余核被 $\ell^{e_W}$ 消去。也就是说，目标 Wach 子模的每个 $n$ 都有 $\ell^{e_W}n$ 的原像。这个结论也适用于最后一项为平凡格的晶体扩张。
2. Herr 类映射 $\operatorname{cl}_T$ 与格映射相容。允许的一次余闭链经此映成 $H_f^1(G,T)$。对晶体扩张 $0\to T\to T'\xrightarrow{q} O\to0$，设 $\kappa$ 为该扩张的类。若平凡格的 Wach 不变生成元 $1$ 的 $\ell^e$ 倍有 Wach 原像，则可在允许的一次余闭链中代表 $\ell^e\kappa$。下面说明它的两个坐标怎样来。
3. 在 $0\to T_0\to T_1\to T_2\to0$ 中，核格 $T_0$ 的 Wach 比较给出[二次障碍的精确校正](%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%9C%89%E7%90%86%E7%9A%84Herr%E6%8F%90%E5%8D%87%E6%94%B9%E6%88%90%E6%9C%89%E7%BB%9F%E4%B8%80%E4%BB%A3%E4%BB%B7%E7%9A%84%E6%95%B4%E6%8F%90%E5%8D%87.md)所需的正合性、饱和性和乘某次 $\ell$ 幂后可解的条件。[分次及多项式计算](%E6%80%8E%E6%A0%B7%E7%94%A8%E5%88%86%E6%AC%A1%E4%B8%8E%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%B6%88%E5%8E%BBHerr%E5%A4%8D%E5%BD%A2%E7%9A%84%E4%BA%8C%E6%AC%A1%E9%9A%9C%E7%A2%8D.md)又给出消去该二次障碍的统一次数 $e_U$。核格的跳点包含在源的跳点集合 $S$ 中，所以可用源的整化多项式和统一指数。

## 证明

先把 $\kappa$ 写成[晶体表示的扩张](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E9%99%90%E4%B8%8A%E5%90%8C%E8%B0%83%E7%B1%BB%E5%8F%AF%E4%BB%A5%E5%86%99%E6%88%90%E6%99%B6%E4%BD%93%E8%A1%A8%E7%A4%BA%E7%9A%84%E6%89%A9%E5%BC%A0.md) $0\to T_2\to T'\xrightarrow{q}O\to0$。这个扩张新增一个跳点 $0$，而原窗口 $[-M,h]$ 包含 $0$。由格的满射取 Wach 原像的第一条，$\ell^{e_W}\cdot1$ 在 $N(T')$ 中有原像 $b$。用 $(\ell-1)^{-1}\sum_{\delta\in\Delta}\delta$ 平均保住像，使 $b$ 属于 $\Delta$ 不变量。

因为商生成元被 $\varphi,\gamma$ 固定，$(\varphi-1)b$、$(\gamma-1)b$ 都落在核模。通过核模的单射写出对应的 $y,z$。两算子交换给出

$$
(\gamma-1)y-(\varphi-1)z=0.
$$

晶体比较的分母界给 $Q^My\in N(T_2)^\Delta$；因为 $(\gamma-1)N$ 带一份分圆参数，且 $\Delta$ 不变量中与该参数相交的理想由 $X=\pi_0$ 生成，所以 $z\in XN(T_2)^\Delta$。Herr 比较的连接映射把这对 $(y,z)$ 送到 $\ell^{e_W}\kappa$。在 Lean 中，比较的生成元允许差一个 $O$ 单位，先将 $b$ 乘这个单位的逆，最后便有精确等式。

接下来沿原来的 $F:T_1\to T_2$ 提升这两个坐标。再次使用第一条，可在源 Wach 模中分别提升 $Q^My$ 和 $z/X$ 的 $\ell^{e_W}$ 倍。所得两项未必满足余闭链等式，但其微分落在核格的 Herr 复形中。这正是第 3 条的二次障碍。乘 $\ell^{e_U}$ 并减去核模里的一次项，就得到允许的源余闭链 $(y_1,z_1)$，其像逐项等于 $\ell^{e_W+e_U}(y,z)$。

令 $\kappa_1=\operatorname{cl}_{T_1}(y_1,z_1)$，由有限条件和相容性，有

$$
F_*\kappa_1
=\ell^{e_W+e_U}\operatorname{cl}_{T_2}(y,z)
=\ell^{2e_W+e_U}\kappa.
$$

第一份 $e_W$ 用来把扩张类写成满足整分母条件的 Herr 余闭链，第二份把这个余闭链的坐标从目标提回源格，$e_U$ 用于校正坐标提升产生的微分。

## Lean 对照

- `coreExtΔ_of` 对原像取温和平均，取两个算子差，验证微分为零及二者的整分母，最后使用 Herr 比较的连接映射。[ExtensionInvariantClause.lean:144](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExtensionInvariantClause.lean#L144)
- `lqa_lifts` 在 Wach 模层用同一个 $\ell^{e_W}$ 提起两项，然后校正微分。源码在 $D(T_1)/D(T_0)$ 上作正合比较，其两个坐标满足相同的整性条件。[BaseChangePreservesUnitaryOf.lean:4542](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L4542)
- `coreLiftA_of'` 把两段组合，并在末尾实际相加指数为 $2e_W+e_U$。`wach_statement_case_A` 给第一个输入的来源。[BaseChangePreservesUnitaryOf.lean:4694](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L4694) · [FrobeniusPowUniformizerFactorisation.lean:3686](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/FrobeniusPowUniformizerFactorisation.lean#L3686)

状态为源码级推导。另行未重编译。正文处理提升的主组合。[Wach 余核的指数](%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%A4%E4%BE%A7%E7%9A%84Wach%E9%AB%98%E5%BA%A6%E7%95%8C%E8%BD%AC%E6%88%90%E4%BD%99%E6%A0%B8%E7%9A%84%E7%BB%9F%E4%B8%80%E7%95%8C.md)已沿源码单独展开。[Herr 周期比较的满射与自然性](Herr%E4%BD%99%E9%97%AD%E9%93%BE%E6%80%8E%E6%A0%B7%E5%92%8C%E6%95%B4Galois%E4%B8%8A%E5%90%8C%E8%B0%83%E5%AF%B9%E5%BA%94.md)及[扩张类公式](%E4%B8%BA%E4%BB%80%E4%B9%88Herr%E5%AF%B9%E7%9A%84%E4%B8%A4%E4%B8%AA%E7%AE%97%E5%AD%90%E5%B7%AE%E7%BB%99%E5%87%BA%E5%90%8C%E4%B8%80%E4%B8%AA%E6%89%A9%E5%BC%A0%E7%B1%BB.md)各有证明。[晶体扩张的分母条件](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%99%B6%E4%BD%93%E6%89%A9%E5%BC%A0%E7%9A%84%E4%B8%A4%E4%B8%AAHerr%E5%9D%90%E6%A0%87%E6%9C%89%E6%8C%87%E5%AE%9A%E5%88%86%E6%AF%8D.md)及[允许分母的 Herr 对为何仍是有限类](%E4%B8%BA%E4%BB%80%E4%B9%88%E9%99%90%E5%88%B6Herr%E5%AF%B9%E7%9A%84%E5%88%86%E6%AF%8D%E5%B0%B1%E8%83%BD%E5%BE%97%E5%88%B0%E6%99%B6%E4%BD%93%E6%9C%89%E9%99%90%E7%B1%BB.md)补齐两个方向，后者依次用到[开圆盘周期评价](%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%BC%80%E5%9C%86%E7%9B%98%E7%BA%A7%E6%95%B0%E5%8F%96%E5%80%BC%E5%88%B0%E6%99%B6%E4%BD%93%E5%91%A8%E6%9C%9F%E7%8E%AF.md)和底层的周期比较。
