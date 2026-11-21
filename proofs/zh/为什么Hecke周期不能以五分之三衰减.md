# 为什么 Hecke 周期不能以五分之三衰减

## 命题

设 $L$ 是全虚数域，$j\ge1,\ j<r_2(L)$，令 $\pi$ 是 $O_L$ 中的素元。对每个 $N\ge1$，令 $\Gamma_N=\mathrm{GL}_N(O_L)$、$G_N=\mathrm{GL}_N(L)$。以源码的 $q_N=\operatorname{diag}(\pi,1,\ldots,1)$ 定义

$$
J_N=\Gamma_N\cap q_N^{-1}\Gamma_Nq_N,\qquad i_N=[\Gamma_N:J_N].
$$

对 $\Gamma_N$-不变的实齐次 $j$ 阶余链 $F$（定义在 $G_N^{j+1}$，系数作用平凡），$T_NF$ 是对 $J_N\backslash\Gamma_N$ 的代表 $\gamma$ 将所有输入同时左乘 $q_N\gamma$ 后的归一化平均。令 $F[z]$ 表示限制到 $\Gamma_N$ 后在实 bar 周期 $z$ 上的取值。则存在 $N_0$，使得对每个 $N\ge N_0$，若 $F$ 为余闭链，且每个 $j$ 阶周期 $z$ 都有常数 $C_z$ 使

$$
|(T_N^rF)[z]|\le C_z(3/5)^r\qquad(r\ge0),
$$

则 $F[z]=0$ 对所有周期成立。此为 `SHecke`，用在[不变形式满射](Hecke%E8%BF%AD%E4%BB%A3%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%91%A8%E6%9C%9F%E7%A7%AF%E5%88%86%E5%BD%92%E5%88%B0%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)的最后一步。它让 $L^2$ 上的快速衰减推出这一余闭链的全部周期为零。

## 一、固定小矩阵大小，得到一个与大 $N$ 无关的算子范数

取 $n=2j+4$。同调稳定性给 $H_j(\Gamma_n,\mathbb R)\to H_j(\Gamma_N,\mathbb R)$ 对 $N\ge n$ 为同构。这个小矩阵群的实同调有限维，源码用 `SFin` 提供有限个周期 $z_1,\ldots,z_s$，其同调类生成。对定义在 $G_n$ 的 $\Gamma_n$-不变齐次余闭链 $H$，记

$$
P(H)=(H[z_i])_i,\qquad Q(H)=((T_nH)[z_i])_i .
$$

$P(H)=0$ 说明 $H$ 在 $\Gamma_n$ 上的全部周期取值为零。项目的 `PHeckeKer` 说明 Hecke 平均保留这个零取值条件。准确说，对任意群嵌入 $\Gamma\hookrightarrow G$ 和 $q\in G$，若 $J=\Gamma\cap q^{-1}\Gamma q$ 指数有限，则在 $G$ 上的 $\Gamma$-不变余闭链，若其在 $\Gamma$ 上的周期值都为零，归一化 $J\backslash\Gamma$ 平均后也都为零。这来自对应 $J\to\Gamma$ 的限制、共轭和转移保持上同调类零。由此 $\ker P\subseteq\ker Q$。于是 $Q$ 是 $P$ 后接 $\operatorname{im}P\to\mathbb R^s$ 的一个线性映射。有限维性给定 $K\ge0$，对所有 $H$ 有 $\|Q(H)\|\le K\|P(H)\|$，范数取最大值范数。$n$ 已固定，$K$ 不依赖大 $N$ 或迭代次数。

## 二、大矩阵上的平均把大多数周期贡献保留下来

用源码的双陪集计算 `PKey`，表述如下。若 $N=n+d,\ n,d\ge1$，在上述全虚性与 $j<r_2(L)$ 下，给任意 $G_N$ 上的 $\Gamma_N$-不变齐次 $j$ 阶余闭链 $F$，以及 $\Gamma_n$ 上第 $j$ 阶周期 $z$，写 $\iota z$ 为补单位阵后的周期，$F|_n$ 为沿小矩阵群限制，则

$$
(T_NF)[\iota z]=(1-i_n/i_N)F[\iota z]+(i_n/i_N)(T_n(F|_n))[z].
$$

小子群上的陪集共有 $i_n$ 个，给后一项。其余陪集按小矩阵群作用合成若干轨道，转移到稳定子后，余链的周期取值与原取值相同，给系数 $1-i_n/i_N$。稳定子上的相等用到源码 `SAff` 的仿射块消去。另一个输入 `PIndex` 给出 $i_N$ 有限且 $i_N\ge N$。故取 $N\ge n+1+\lceil5(1+K)i_n\rceil$，有 $a=i_n/i_N\ge0$ 且 $a(1+K)\le1/5$。

## 三、比较同一组周期上的两个指数

令 $F_r=T_N^r F$，$x_r=(F_r[\iota z_i])_i$。Hecke 平均是有限和，保持不变性，与齐次余边界交换，因此每个 $F_r$ 都是同类型的余闭链。用双陪集公式和第一节，

$$
x_{r+1}=(1-a)x_r+aQ(F_r|_n),\qquad
\|Q(F_r|_n)\|\le K\|x_r\|.
$$

三角不等式给 $\|x_{r+1}\|\ge (1-a-aK)\|x_r\|\ge(4/5)\|x_r\|$。归纳得到 $\|x_r\|\ge(4/5)^r\|x_0\|$。另一方面，衰减假设用于有限个固定周期 $\iota z_i$，给 $\|x_r\|\le C(3/5)^r$ 且 $C<\infty$ 与 $r$ 无关。所以 $\|x_0\|\le C(3/4)^r$ 对所有 $r$ 成立。令 $r\to\infty$，得到 $x_0=0$。由同调稳定，$\iota z_i$ 的类生成大矩阵群的同调，因此 $F$ 的全部周期值为零。

## 源码对照

- `SHecke`，[SBridgeAlt.lean 第 73 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean)。归一化平均和 $q_N$ 在 [ActLPos.lean 第 42、150 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ActLPos.lean)。
- `PHeckeKer`、`PIndex`、`PKey`，[PHeckeFormal.lean 第 67、74、110 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PHeckeFormal.lean)。双陪集步骤的入口 [PKey.lean 第 13 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PKey.lean)，固定小尺寸的范数估计和上下衰减比较 [Assemble.lean 第 119 行起](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Assemble.lean)。
- `sHecke_of`，[SHeckeOf.lean 第 9 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/SHeckeOf.lean)。零类的转移和指数分别见 [Formal.lean 第 108 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Formal.lean)、[PermMatrixMulApply.lean 第 177 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PermMatrixMulApply.lean)。

本篇为源码对读。两个指数的比较已展开。双陪集计数和稳定子上的求值见[陪集分组与转移](Hecke%E9%99%AA%E9%9B%86%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E6%88%90%E4%B8%A4%E4%B8%AA%E5%91%A8%E6%9C%9F%E8%B4%A1%E7%8C%AE.md)。
