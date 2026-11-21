# 为什么变形的切向量满足 Bloch–Kato 局部条件

I 类要把表示的上同调消失传回分次变形环。先要验证变形环的一阶切向量确实满足那些上同调的局部条件。本篇完成这一步，再说明什么消失定理会给出需要的三条刚性。[刚性在长度证明中的作用](%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%88%86%E6%AC%A1%E8%BD%A8%E9%81%93%E7%9A%84%E8%B5%8B%E5%80%BC%E7%95%8C%E4%BC%A0%E7%BB%99Frobenius%E8%BF%B9.md)

## 命题

沿用[单特征估计](%E4%B8%80%E4%B8%AA%E7%89%B9%E5%BE%81%E7%9A%84%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E7%94%B1%E6%9C%89%E9%99%90%E4%B8%AA%E8%87%AA%E5%AE%88%E8%BF%B9%E5%B7%AE%E6%8E%A7%E5%88%B6.md)的 $\Omega,K,\ell,O,N,e,\psi,\eta,\Psi$ 与 `GD`，取对应的局部条件环 $U$，其局部条件理想为 $I$。令 $R$ 为在 $G_{\mathbb Q}$ 上表示归一化、消去指定剩余惯性核且满足 $I$ 的变形环，$r$ 为泛表示。记 $k=\overline{\mathbb Q}_\ell$，取任意 $O$-代数映射 $F:R\to k[\epsilon]/(\epsilon^2)$，其常数项 $f$ 是一个局部点，即把极大理想送到 $|z|_\ell<1$ 中。

令 $M_g$ 是 $r$ 在 $f$ 处的矩阵，$M_g+\epsilon N_g$ 是在 $F$ 处的矩阵。则

$$
\gamma(g)=N_gM_g^{-1}
$$

是取值于 $M_3(k)$ 的连续余闭链，系数作用为 $\operatorname{Ad}_{r_f}$，而且满足以下 Bloch–Kato 条件。

- 在每个 $\ell$ 外的素处，$\gamma$ 在其惯性群上的限制是余边界。
- 限制到 $G_{\mathbb Q_\ell}$ 后，$\gamma$ 在系数扩到晶体周期环 $B_{\mathrm{cris}}$ 后成为余边界。准确说，存在 $Y\in M_3(k)\otimes_{\mathbb Q_\ell}B_{\mathrm{cris}}$，使 $\gamma(g)\otimes1=gY-Y$ 对全部局部 $g$ 成立。这里 $g$ 同时作用在矩阵项和周期环上。

这是 `tanCoc_isBK`。它取 `CohInp` 为输入，以下证明实际用到的是局部条件理想的晶体结论。第二条的限制在源码中经一个 $\Omega\to\overline{\mathbb Q}_\ell$ 的嵌入写出，不同选择给共轭的分解群。

## 从首项相乘得到连续余闭链

半直积的符号分量保持不变。在 $F$ 处把表示写作 $(1+\epsilon\gamma(g),1)r_f(g)$。因为 $\epsilon^2=0$，乘法中两个一阶项只做相加，且后一项先被 $r_f(g)$ 共轭，于是

$$
\gamma(gh)=\gamma(g)+\operatorname{Ad}_{r_f(g)}\gamma(h).
$$

该共轭在符号 $-1$ 时先对矩阵作 $X\mapsto-JX^tJ$。这是 $M\mapsto J(M^{-1})^tJ$ 在单位阵的一阶项。连续性来自局部点的评价定理：对完备 Noether 局部 $O$-代数，向 $k[\epsilon]/(\epsilon^2)$ 的映射若常数分量把极大理想送进开单位球，则两个分量都取值于某个有限的 $\mathbb Q_\ell$ 扩域，且复合任何极大理想进连续的函数仍连续。源码先由 `ptFin` 将取值放进有限系数域，再用 `ptCont` 得到连续。将其用于每个泛矩阵条目，再作矩阵乘法与求逆，即得 $\gamma$ 连续。

## $\ell$ 外的条件来自有限陪集平均

固定 $\ell$ 外的惯性群 $I_p$。令 $H$ 为剩余基点表示在 $I_p$ 上的核。剩余域有限，故 $[I_p:H]$ 有限。变形环的消去条件使泛表示在 $H$ 上就是单位，因而 $\gamma|_H=0$。

一般地，在特征零向量空间 $V$ 上，若群 $G$ 作用为 $A_g$，余闭链 $z:G\to V$ 在有限指数子群 $H$ 上为零，则 $z$ 是余边界。因为 $z(gh)=z(g)$ 对 $h\in H$ 成立，令 $Z=\sum_{q\in G/H}z(q)$，选每个陪集的任意代表。左乘 $g$ 置换陪集。由余闭链公式，

$$
Z=[G:H]\,z(g)+A_g Z.
$$

除以非零的 $[G:H]$，得 $z(g)=A_g(-Z/[G:H])-(-Z/[G:H])$。将此式用于 $I_p$ 即得第一条。更一般地，若 $z|_H$ 已为余边界，先减去在 $H$ 上的那个全群余边界，再求平均。这一形式也用于下面的局部下降。

## $\ell$ 上方的条件来自同一个一阶晶体变形

由 $R$ 表示的局部条件，存在 $U\to R$，使其消去 $I$，并使泛表示在 $G_{\mathbb Q_\ell}$ 的限制来自这个映射。故沿 $F$ 得到 $U\to k[\epsilon]/(\epsilon^2)$，整个平方零值的表示仍消去 $I$。重要的是 $I$ 为零同时约束常数项与一阶项。

局部定理 `rtPoints` 的晶体结论在此处的适用形式如下。对项目的局部数据和 $U$，任取有限维的交换 $\mathbb Q_\ell$-系数代数 $B$，带相容 $O$ 结构。若一个带符号的秩三表示由 $U\to B$ 给出且消去 $I$，则它在 $H_\ell=\ker\eta_\ell\cap\ker\tau_\ell$ 上的矩阵表示是晶体的。这里 $\eta_\ell$ 是局部二次符号，$\tau_\ell$ 是数据中描述有限惯性型的特征，两者的核都开放。取 $B=E[\epsilon]/(\epsilon^2)$，其中有限扩域 $E/\mathbb Q_\ell$ 包含该局部点及一阶取值。

限制到 $H_\ell$ 后矩阵表示的符号为正。把这个平方零表示视为 $E$-线性表示，有正合列

$$
0\longrightarrow V\longrightarrow V_{\epsilon}\longrightarrow V\longrightarrow0,
$$

其扩张类由 $\gamma$ 给出。对晶体表示张量 $B_{\mathrm{cris}}$ 后，比较同构由 $B_{\mathrm{cris}}$ 不变量空间重建表示。晶体表示的正合列在该不变量空间中是正合的，可在固定系数域上线性分裂，故张量后的扩张在 $H_\ell$ 上分裂。这等价于 $\gamma|_{H_\ell}\otimes1$ 是矩阵与周期环张量上的余边界。源码用 `deformCr` 和 `dualCr` 表述该等价。用上一节有限陪集平均把余边界从 $H_\ell$ 传回 $G_{\mathbb Q_\ell}$，再扩回 $k$，便得第二条。

## 三条刚性怎样取得

对归一化全局模型的一个点，若限制表示既上三角又下三角，[基点唯一性](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%90%8C%E6%97%B6%E4%B8%8A%E4%B8%89%E8%A7%92%E5%92%8C%E4%B8%8B%E4%B8%89%E8%A7%92%E7%9A%84%E5%8F%98%E5%BD%A2%E5%8F%AA%E6%9C%89%E5%9F%BA%E7%82%B9.md)表明该点表示等于基点。

在基点，若切向量只带一个非正权 $j\le0$，刚刚证明它满足 Bloch–Kato 条件。项目对该权的上同调消失 `bloch_kato_nonpositive_weight` 便推出它是余边界。对两侧点，先用[秩三分类](%E4%B8%BA%E4%BB%80%E4%B9%88%E7%A7%A9%E4%B8%89%E7%9A%84%E4%B8%A4%E4%BE%A7%E7%82%B9%E5%8F%AA%E5%89%A9%E4%B8%A4%E7%A7%8D%E8%A1%A8%E7%A4%BA.md)。不可约型由其自守性及 `RigidityFirstCase` 给出整个伴随 Bloch–Kato 上同调消失。角块型用秩二扩张的自守性、`KatoTwoW` 与 `RigiditySecondCase` 同样得到伴随消失。此处“伴随上同调消失”的形式是：任意取值在矩阵模、满足上述两类局部条件的连续余闭链，都是全局余边界。于是这两个类型的全部切向量都是无穷小共轭。三条正好组成 `PtHyp`。

## Lean 对照与证明范围

- [`tanCoc_isBK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/TanCocIsBK.lean#L162) `tanCoc_isBK` 第 162 行，内部 `tanBK_avg` 给有限陪集平均。`finiteCocycles` 第 112 行给晶体周期环上的余边界定义。[全局切向量](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/TanCocIsBK.lean) · [有限局部条件](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/FiniteCohomology.lean)
- [`rtDual`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/RtDual.lean#L164) `rtDual` 第 164 行把局部条件传给切向量。`rtPoints` 第 11 行给局部晶体结论，`IsLCr` 第 44 行给它所用的开子群。[局部切向量](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/RtDual.lean) · [晶体变形](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/RtPoints.lean) · [开子群](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/IsInertiaInfiniteCyclotomic.lean)
- [`ptHyp_of_autB_of_lemW_of_isBase`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FPtHypU.lean#L15) `ptHyp_of_autB_of_lemW_of_isBase` 第 15 行合成三条刚性，[`bloch_kato_nonpositive_weight`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/BlochKatoNonpositiveWeight.lean#L297) `bloch_kato_nonpositive_weight` 第 297 行处理基点，[`bloch_kato_selmer_vanishes_of_type_ii_modular_ext`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/TypeIIOfBlochKatoLocalPoint.lean#L16) 给角块型的伴随消失。[刚性合成](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/FPtHypU.lean) · [基点非正权](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/BlochKatoNonpositiveWeight.lean) · [角块型](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/TypeIIOfBlochKatoLocalPoint.lean)

本篇为源码对读。局部晶体定理及两类自守刚性是明示输入。未重新编译或查询传递公理。[权零及负权的消失](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9F%BA%E7%82%B9%E7%9A%84%E9%9D%9E%E6%AD%A3%E6%9D%83%E4%B8%8A%E5%90%8C%E8%B0%83%E5%8F%AA%E6%9C%89%E4%BD%99%E8%BE%B9%E7%95%8C.md) · [角块型伴随分解](%E7%A7%A9%E4%BA%8C%E8%A7%92%E5%9D%97%E6%80%8E%E6%A0%B7%E5%88%86%E8%A7%A3%E7%A7%A9%E4%B8%89%E7%9A%84%E4%BC%B4%E9%9A%8F%E4%B8%8A%E5%90%8C%E8%B0%83.md)
