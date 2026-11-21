# 从窗口估计到黎曼猜想

[English](../en/from-windows-to-rh.md) · [进度与复核状态](../../STATUS.md)

原证明在算术与几何一侧构造共同的窗口数据，比较格的斜率，再用有限 Fourier 分析把计数差传给加权素数和。解析一侧从加权和的上界排除右半平面的零点，最后用函数方程反射。本篇完整写出从**窗口上界**到 RH 的推导。上界的算术来源在文末定位。

## 1. 准确写出窗口假设

设 $J$ 是有限指标集，对每个 $j\in J$，取正整数 $N_j$、模 $N_j$ 的狄利克雷特征 $\chi_j$ 和正权重 $a_j$。主特征只允许取模 $1$ 的那个，记为 $\mathbf 1$，并假设族中包含它。令 $\Lambda$ 为冯·曼戈尔特函数，令 $\gamma_E$ 为欧拉常数。对 $y>0$，设

$$
S_\chi(y)=\sum_{1\le n\le y}\Lambda(n)\chi(n)(y/n-1),
\qquad
G_{\mathbf 1}(y)=S_{\mathbf 1}(y)-y\log y+(1+\gamma_E)y.
$$

非主特征取 $G_\chi(y)=S_\chi(y)+yL'(1,\chi)/L(1,\chi)$，全族的和为 $G(y)=\sum_{j\in J}a_j\operatorname{Re}G_{\chi_j}(y)$。

**命题。** 假设有固定的 $\lambda>1$、$B\in\mathbb R$ 和 $\varepsilon_0>0$，使每个 $0<\varepsilon<\varepsilon_0$ 和每个下界 $T\ge 1$ 都能找到 $Y\ge T$，在整个 $[Y,Y^\lambda]$ 上有

$$
G(y)\le y^{1/2+B\varepsilon}.
$$

则黎曼猜想成立。窗口可随 $\varepsilon$ 和 $T$ 改变。$B$ 先于 $\varepsilon$ 固定。

## 2. 排除右侧零点

假定 $\zeta$ 有零点 $s$ 满足 $\beta=\operatorname{Re}s>1/2$。取 $1/2<\theta<\min(\beta,1)$，再取足够小的 $\varepsilon>0$ 使 $1/2+B\varepsilon\le\theta$。对任意下界取假设中的窗口，因 $y\ge 1$，便有 $G(y)\le y^\theta$。

令 $g(u)=G(e^u)$。[留数引理](pole-data.md)给出 $g$ 的 Laplace 变换延拓。族中每个落在 $\operatorname{Re}z>0$ 的零点都会产生极点，实极点的留数为正。对任意 $\eta>0$ 及下界 $U_0$，取上面一个足够远的窗口，使 $U=\log Y\ge\max(1,U_0)$。在 $[U,\lambda U]$ 用 $R(u)=e^{\theta u}$ 控制 $g(u)$。于是

$$
\int_U^{\lambda U}R(u)e^{-\theta u}\,du=(\lambda-1)U\le e^{\eta U}.
$$

[Landau 窗口引理](landau-window.md)给出每个极点的实部至多为 $\theta$。由于 $L(s,\mathbf 1)=\zeta(s)$，假想零点会产生实部 $\beta>\theta$ 的极点，矛盾。

## 3. 反射到右半平面

设 $s$ 是实部小于 $1/2$ 的非平凡零点。由 $\zeta(0)=-1/2$，有 $s\ne0$。置 $u=1-s$，则 $\operatorname{Re}u>1/2$ 且 $u\ne1$。ζ 的函数方程给出

$$
0=\zeta(s)=2(2\pi)^{-u}\Gamma(u)\cos(\pi u/2)\zeta(u).
$$

指数因子和 Gamma 因子非零。余弦若为零，则 $u=2k+1$、$s=-2k$，其中 $k\in\mathbb Z$。$k<0$ 与 $\operatorname{Re}s<1/2$ 矛盾，$k=0$ 与 $s\ne0$ 矛盾，$k>0$ 给出被排除的平凡零点。故 $\zeta(u)=0$，与右侧非零矛盾。于是所有非平凡零点均在临界线上。

## 源码和上游输入

`core_gm` 把同一份算术数据上的逐点计数估计转换成加权素数和上界。`level_gm_le_on_family_scales` 把它放到满足条件的窗口族。`lemmaL` 负责 Landau 收尾，`rh_of_right` 负责函数方程部分。这里证明的是以上述窗口上界为输入的推论。原始 `Main.lean` 的 RH 声明没有这个额外数学前提。 [逐点估计](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/CoreGm.lean#L12) · [窗口上的估计](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/PrimitiveCosets/LevelGmLeOnFamilyScales.lean#L28) · [Landau 收尾](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/lemmaL.lean#L13) · [函数方程步骤](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GammaFactorNonvanishing/RhOfRight.lean#L5) · [最终声明](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Main.lean#L4)

外部阅读线索。O’Desky 的[加权素数和证明](https://andrewodesky.com/rh/s/bound-G.html)把所用算术条件逐一列出。[进度页](../../STATUS.md)标出了还未接上的构造。
