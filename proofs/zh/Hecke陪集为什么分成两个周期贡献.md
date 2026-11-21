# Hecke 陪集为什么分成两个周期贡献

## 命题

设 $L$ 为全虚数域，$R=O_L$，$1\le j<r_2(L)$，$\pi\in R$ 为素元。给定 $n,d\ge1$，令 $N=n+d$，写 $\Gamma_m=\mathrm{GL}_m(R)$、$G_m=\mathrm{GL}_m(L)$。用 $\iota:\Gamma_n\to\Gamma_N$ 和 $G_n\to G_N$ 表示添单位阵。令 $q_m=\operatorname{diag}(\pi,1,\ldots,1)$，$J_m=\Gamma_m\cap q_m^{-1}\Gamma_mq_m$，$i_m=[\Gamma_m:J_m]$，$T_m$ 为沿 $J_m\backslash\Gamma_m$ 的归一化 Hecke 平均。对 $G_N$ 上 $\Gamma_N$-不变的实齐次 $j$ 阶余闭链 $F$ 和 $z\in Z_j(\Gamma_n,\mathbb R)$，有

$$
(T_NF)[\iota_*z]
=(1-i_n/i_N)F[\iota_*z]+(i_n/i_N)\big(T_n(F|_n)\big)[z].
$$

这是 `PKey` 的内容。它给[Hecke 周期衰减判别](%E4%B8%BA%E4%BB%80%E4%B9%88Hecke%E5%91%A8%E6%9C%9F%E4%B8%8D%E8%83%BD%E4%BB%A5%E4%BA%94%E5%88%86%E4%B9%8B%E4%B8%89%E8%A1%B0%E5%87%8F.md)提供系数随 $N$ 增大而变小的修正项。

## 一、看陪集在剩余域里的第一列

写 $K=R/(\pi)$、$e_0$ 为首个标准基向量。$q_m\gamma q_m^{-1}$ 在第一列、第一项以下将条目除以 $\pi$，其余位置仍整。只要这些条目整，它的行列式仍是单位，故属于 $\Gamma_m$。因此 $J_m$ 恰是模 $\pi$ 稳定直线 $K e_0$ 的矩阵。右陪集 $J_m c$ 由剩余直线 $K\overline{c^{-1}e_0}$ 唯一决定。这样 $i_m$ 有限，首个基向量与各个基向量互换给出 $m$ 个不同陪集，所以 $i_m\ge m$。

$\iota(J_n)=\iota(\Gamma_n)\cap J_N$，故小群嵌入给 $i_n$ 个陪集。它们恰对应于 $\overline{c^{-1}e_0}$ 的末 $d$ 项全为零的陪集。确实，若末 $d$ 项全零，则前 $n$ 项至少有一项非零。用整置换矩阵把它移到首项，再用初等整矩阵消去其余 $n-1$ 项模 $\pi$ 的值。这给 $c'\in\Gamma_n$，使 $\iota(c')c^{-1}\in J_N$，于是 $c$ 与 $\iota(c')$ 代表同一陪集。对这些陪集，$q_N=\iota(q_n)$，所以未归一化的周期贡献恰为 $i_n(T_n(F|_n))[z]$。

## 二、其余陪集上，稳定子给出同样的周期值

用 $X$ 表示剩余陪集，$\Gamma_n$ 通过右乘 $\iota(h)$ 作用于 $X$。固定 $x=J_N c\in X$，令 $H_x=\{h:c\iota(h)c^{-1}\in J_N\}$。取下半块一个坐标 $p$，使 $v_p\not\equiv0\bmod\pi$，其中 $v=c^{-1}e_0$。取 $u,s\in R$ 使 $u v_p+\pi s=1$，令

$$
y=(u/\pi)v+s e_p,\qquad A=I+(y-e_p)e_p^\mathsf{T}.
$$

$A$ 只是把第 $p$ 列换成 $y$。因为 $y_p=1/\pi$，它可逆且 $\det A=1/\pi$。令 $\delta=q_Nc A$。除第 $p$ 列外它的各列本来就整。第 $p$ 列为 $u e_0+s q_Nc e_p$，也整。又 $\det\delta=\det c$ 为单位，故 $\delta\in\Gamma_N$。

对 $h\in H_x$，有 $q_Nc\iota(h)c^{-1}q_N^{-1}\in\Gamma_N$，所以 $\alpha(h)=A^{-1}\iota(h)A$ 也在 $\Gamma_N$，因为两者以 $\delta$ 共轭。写 $S=\iota(h)$。第 $p$ 行和列均与单位阵相同，直接乘矩阵得

$$
A^{-1}S A=S+(S-I)y e_p^\mathsf{T}.
$$

右侧只在上右块加了一列，仍是 $\begin{pmatrix}h&B(h)\\0&I\end{pmatrix}$。这里调用 `SAff` 的准确结论：设 $L$ 全虚且 $j<r_2(L)$，任意群 $H$ 的两个整矩阵表示 $\alpha(h)=\begin{pmatrix}\alpha_0(h)&B(h)\\0&I_d\end{pmatrix}$ 与 $\iota\alpha_0(h)$，对任意 $j$ 阶实周期的像同调类相同。于是对 $H_x$ 的周期 $w$，沿 $\alpha$ 或沿 $\iota$ 取 $F$ 的值相同。

又 $q_Nc\iota(h)=\delta\alpha(h)A^{-1}$。对齐次余链，左侧的 $\delta$ 可由 $\Gamma_N$-不变性去掉。右端的 $A^{-1}$ 意味在沿 $\alpha$ 评价时用 $A^{-1}$ 为基点。更换基点的两个评价在周期上相同，因为两个等变的元组映射由棱柱链同伦连接。故在每个稳定子上，从该陪集来的 $F$ 与原 $F$ 在周期上的取值相同。

## 三、对剩余陪集求和

对每个 $x=J_Nc\in X$，定义小群上的齐次余闭链

$$
\Phi_x(h_0,\ldots,h_j)=F(q_Nc\iota(h_0),\ldots,q_Nc\iota(h_j))-F(\iota(h_0),\ldots,\iota(h_j)).
$$

它与代表 $c$ 无关。选 $c'=jc,\ j\in J_N$，在所有输入上多出的左因子为 $q_Nj q_N^{-1}\in\Gamma_N$。又 $\Phi_{x h}(y)=\Phi_x(hy)$，其中 $hy$ 在各顶点同时左乘。上一节说明 $\Phi_x$ 的限制在 $H_x$ 的全部周期上为零。

这里用到有限集上的余链转移 `PTransfer`。设群 $\Gamma$ 右作用于有限集 $X$，有实齐次余闭链 $\Phi_x$ 满足上述等变性。若每个 $\Phi_x$ 在 $x$ 的稳定子上对全部周期取零，则 $\sum_x\Phi_x$ 在 $\Gamma$ 上对全部周期取零。证明按轨道选代表 $x$。稳定子 $H$ 不变的齐次余链可直接定义在 $\Gamma$ 的元组上。选每个右陪集的代表，从 $\Gamma$ 到 $H$ 得到一个左 $H$-等变的收缩 $r$，并以棱柱证明限制到 $H$ 再沿 $r$ 拉回与原余链只差余边界。限制到 $H$ 的余链杀全部周期，故它在边界上定义一份线性原像，再延拓到全链群，得到余边界。于是原 $\Phi_x$ 也是一个 $H$-不变余链的余边界。对轨道求和得到一个 $\Gamma$-不变余链的余边界，因为换代表只改变某个左 $H$ 因子，各项相同。对所有轨道相加，得到所报结论。

应用于 $\Phi_x$，则所有剩余陪集的总贡献是 $(i_N-i_n)F[\iota_* z]$。加上第一节的 $i_n$ 个陪集的贡献，除以 $i_N$ 即得。

## 源码对照

- `PKey`、`PStabVan`，[PHeckeFormal.lean 第 110、96 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PHeckeFormal.lean)。`keyGen`、`pKey`，[KeyGenAlt.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/KeyGenAlt.lean)、[PKey.lean 第 13 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PKey.lean)。
- 陪集有限性、指数与首列消去 [PermMatrixMulApply.lean 第 138、177、291 行附近](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PermMatrixMulApply.lean)。`aff_gamma`、`aff_conj`、`pStabVan`，[Affine.lean 第 100、61、249 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Affine.lean)。
- 有限集转移 [Transfer.lean 第 14 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Transfer.lean)，稳定子余链的收缩 `pCobSub` 在 [TkFcPzTop.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/TkFcPzTop.lean)。仿射同调输入 `SAff` 见 [SBridgeAlt.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean)。

本篇为源码对读。仿射块不改变实同调类是第二节的核心上游输入。
