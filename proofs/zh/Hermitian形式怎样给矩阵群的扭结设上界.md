# Hermitian 形式怎样给矩阵群的扭结设上界

## 命题

设 $L$ 为全虚数域，$n=[L:\mathbb Q]$、$D=|\operatorname{disc}L|$。对整数 $e\ge1$、$1\le N\le4e+6$ 和 $0\le m\le2e+1$，群 $H_m(\mathrm{GL}_N(O_L),\mathbb Z)$ 的扭结子群有限，且

$$
\log|\operatorname{Tor}H_m(\mathrm{GL}_N(O_L),\mathbb Z)|
\ \le\ \exp\!\big((2en)^{24}\log(2D)\big).
$$

这是 `torsAll`。主线 `STors` 取 $N=4e+6$，用于[小指标计数](%E5%B0%8F%E6%8C%87%E6%A0%87%E7%9A%84%E4%BA%8C%E9%98%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E7%95%8C%E6%80%8E%E6%A0%B7%E7%94%B1%E8%AE%A1%E6%95%B0%E5%90%88%E6%88%90.md)中的两项扭结。

## 一、群作用在哪个复形上

记 $\mathcal H=\prod_{w\mid\infty}\operatorname{Herm}_N(\mathbb C)$，每对复嵌入取一个代表。对格向量 $y\in O_L^N$，定义 $Q_h(y)=\sum_w y_w^*h_wy_w$。令 $\mathcal R$ 为满足对每个非零格向量 $Q_h(y)\ge1$ 的 $h\in\mathcal H$。取 $\mathcal P$ 为各处半正定的锥。这里源码的 `Ry`、`Psd` 分别是 $\mathcal R,\mathcal P$。实际上 $\mathcal R$ 中每个 $h$ 各处正定。

顶点 $v$ 是 $\mathcal R$ 中被其最短向量等式唯一确定的形式。精确说，若 $Q_v(y)=1$ 的所有 $y$ 都满足 $Q_k(y)=0$，则 $k=0$。一个 $p$ 阶单形是一个有序 $(p+1)$ 元组 $(v_0,\ldots,v_p)$，允许重复，要求存在实线性泛函 $x$ 在 $\mathcal P\setminus\{0\}$ 上严格正，且所有 $v_i$ 同时极小化 $x$ 在 $\mathcal R$ 上的值。这就是 `Sx`。群 $\mathrm{GL}_N(O_L)$ 通过 $g\cdot h=(g^{-1})^*h g^{-1}$ 作用，保留格向量长，因而保持顶点和单形条件。边界是交错删除一个顶点，和此作用可交换。

源码的 `sx_exact` 给出所得增广整数链列在所有阶正合。它调用的凸集结论是：若凸非空空间 $X$ 被一族闭凸集 $A_i$ 覆盖，且 $X$ 内任意有限点集的凸包只碰有限个 $A_i$，则以非空交集定义的有序神经复形无约化同调。这是 `nerve_convex`，用有限条链涉及的公共点取凸包，归约到有限闭凸覆盖。这里 $X$ 取在 $\mathcal P\setminus\{0\}$ 上严格为正的泛函，$A_v$ 取在 $v$ 上达到最小值的泛函集。源码用 `good`、`cone_finite` 和 `exists_vert` 检查覆盖与局部有限性。于是可以应用[置换复形的通用扭结界](%E6%80%8E%E6%A0%B7%E7%94%A8%E6%9C%89%E9%99%90%E8%BD%A8%E9%81%93%E5%92%8C%E7%A8%B3%E5%AE%9A%E5%AD%90%E6%95%B0%E5%87%BA%E7%BE%A4%E5%90%8C%E8%B0%83%E6%89%AD%E7%BB%93.md)。

## 二、为什么轨道和稳定子都有界

令 $d=nN,\ I_0=D^Nd^d,\ R_0=N^NI_0^2$。源码给出的轨道数上界为

$$
A_p=I_0^{1+dN}\big((2R_0+1)^d+1\big)^{dN(p+1)}.
$$

论证先把任意单形的全部顶点放到同一份短向量坐标中。它们共同的最短格向量张成 $L^N$，所以可取其中 $N$ 个作列，组成 $\det A\ne0$ 的 $A\in M_N(O_L)$。这个张成性是 `sx_basis` 的内容，由正泛函的共同极小条件经 `simp_span` 和 `spanpsd` 得到。

对任一顶点 $h$，在第 $w$ 处换成这些列后，矩阵 $A_w^*h_w A_w$ 各对角元至多 $1$，因为同一列的各处对角元非负且和是 $1$。Hadamard 给其行列式至多 $1$，而所有处的行列式乘积等于 $|N_{L/\mathbb Q}\det A|\prod_w\det h_w$。源码的格体积界 `detlow` 给 $\prod_w\det h_w\ge I_0^{-1}$。所以 $|N_{L/\mathbb Q}\det A|\le I_0$。

Hermite 归约 `hnf` 断言：对给定正整数 $J$，行列式范数至多 $J$ 的非奇异 $N\times N$ 整矩阵，在 $\mathrm{GL}_N(O_L)$ 左乘下，可以从一个至多 $J^{1+dN}$ 元的集合取代表。取 $J=I_0$。对一份固定代表 $A$，`nearvx` 给出以 $A$ 各列为最短向量的顶点至多 $((2R_0+1)^d+1)^{dN}$ 个。这个计数先用矩阵逆和整数坐标得到可能的最短向量至多 $(2R_0+1)^d$ 个，再以至多 $\dim_\mathbb R\mathcal H\le dN$ 条独立等式唯一确定顶点。每个单形可在共同的 $A$ 上为每个位置选择一个顶点。乘上 $A$ 的选择数，得到 $A_p$。

稳定子先由最短向量有限得到有限性。固定顶点的元素置换其有限最短向量集，由于该集含有 $L^N$ 的一组基，稳定子在这组向量上的像唯一确定元素。整个单形的稳定子包含在第一个顶点的稳定子中。再将其模 $3$ 约化。有限子群约化是单射，因为矩阵整数环中 $1+3M_N(O_L)$ 没有非平凡有限阶元。为见此，设 $u=1+3^aX\ne1$，$a\ge1$ 最大。若 $r$ 与 $3$ 互素，则展开 $u^r$ 得 $u^r-1\equiv r3^aX\bmod3^{a+1}$，其非零最低层不变。展开 $u^3$ 得 $u^3-1\equiv3^{a+1}X\bmod3^{a+2}$，最低层恰升一级。把任意指数分成 $3$ 的幂乘互素部分即可。故稳定子阶至多模 $3$ 的全矩阵环大小 $s=3^{nN^2}$。

## 三、把计数合成指数 $24$

取 $A=A_m$，因为 $A_p\le A_m$ 对 $p\le m$ 成立。`orbnum` 将 $A_m$ 简化为

$$
A\le (2Dd)^{12(m+1)d^3N}.
$$

这来自逐因子上界。令 $B=2Dd\ge2$，则 $I_0\le B^{2d}$、$N^N\le B^d$、$2R_0+1\le B^{5d+2}$，从而 $(2R_0+1)^d+1\le B^{(5d+2)d+1}$。加上第一因子的指数，再用 $N\le d$ 即得。

扭结界取 $b=m+2$。其对数不超过 $A\log(m+2)+mAs^m\log s$。写

$$
a=12(m+1)(nN)^3N\log(2DnN),\qquad
\sigma=2nN^2 .
$$

由 $A\le e^a,\ s\le e^\sigma$ 及 $\log(m+2)\le m+1,\ \log s\le s,\ 2m+1\le e^{2m}$，可把对数压到 $\exp(a+(m+1)\sigma+2m)$。

最后设 $u=en\ge1,\ Y=\log(2D)\ge0.69$。利用 $nN,N\le10u$、$m+1\le4u$，以及

$$
\log(2DnN)\le Y+nN-1\le16uY,
$$

得 $a+(m+1)\sigma+2m\le7681212\,u^6Y\le(2u)^{24}Y$。这里第一项系数是 $12\cdot4\cdot10^4\cdot16=7680000$，第二项和末项分别可按 $1200u^6Y$ 与 $12u^6Y$ 计。代入即得命题。

## 源码对照

- `Sx`、`sx_exact`、`tors_le`，[SmulNeZeroLat.lean 第 76 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/SmulNeZeroLat.lean)、[Assembly.lean 第 14、25 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Assembly.lean)。凸神经 [AcycSimp.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ConvexNerveComplexes/AcycSimp.lean)、[NerveConvex.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ConvexNerveComplexes/NerveConvex.lean)。
- `sx_basis`、`orb`、`orbnum`，[ColsMinSmul.lean 第 13、34 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/ColsMinSmul.lean)、[Orbnum.lean 第 80 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Orbnum.lean)。`nrmle`、`hnf` 和 `nearvx` 的陈述分别在 [DetPull.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/DetPull.lean)、[Hnf.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Hnf.lean)、[Nearvx.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Nearvx.lean)。
- `stab`、`mink3`、`torsfree`，[ImportsAlt.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/ImportsAlt.lean)、[Mink3.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Mink3.lean)、[Torsfree.lean 第 48 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Torsfree.lean)。
- `exponent_le`、`torsAll`、[`sTors`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/ExponentLe.lean#L122) `sTors`，[ExponentLe.lean 第 6、75、122 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/ExponentLe.lean)。

本篇为源码对读。凸覆盖的极小点与局部有限性、共同最短向量的张成性和 Hermite 归约仍用项目中的具体引理。
