# 过滤跳点怎样给 Wach 模的两侧 Frobenius 高度

## 命题

令 $\ell$ 为素数，$L/\mathbb Q_\ell$ 为含全部 $\ell^s$ 次单位根的有限扩张，$s\ge1$，$O=\mathcal O_L$。令 $A=\prod_{i\in\mathbb Z/n\mathbb Z}O[[U]]$，$n\ge1$。取晶体表示的整 Wach 模 $N$，为 $A$ 上的有限自由模，嵌在 $Q$ 可逆的环境模中。这里 $Q=\Phi_{\ell^s}(1+U)$，即第 $\ell^s$ 个分圆多项式代入 $1+U$。记 $N_i$ 为系数分量，半线性的 Frobenius $\Phi$ 把第 $i-1$ 分量送到第 $i$ 分量，记 $P_i=\operatorname{span}_{O[[U]]}\Phi(N_{i-1})$。

设 $N_i$ 与 $P_i$ 在反演 $Q$ 后相等。对每个本原 $\ell^s$ 次单位根 $\zeta$，设有与[分圆根处的标量代入](%E6%80%8E%E6%A0%B7%E5%9C%A8%E5%88%86%E5%9C%86%E6%A0%B9%E5%A4%84%E6%A3%80%E6%9F%A5%E6%95%B4%E5%B9%82%E7%BA%A7%E6%95%B0%E7%9A%84%E6%95%B4%E9%99%A4%E6%80%A7.md)相容的比较。它把 $N_i$ 的基展开为 $V_{i,\zeta}((t))$ 中的向量，其中 $V_{i,\zeta}$ 是相应的周期分量。所用的比较条件为：

1. 在该根处，$N_i$ 的基的展开在 $L[[t]]$ 张成的格，等于所有满足 $f_k\in\operatorname{Fil}^{-k}V_{i,\zeta}$ 的下方有界级数。其中过滤是递减的，且所有跳点属于 $[-M_i,h_i]$，$M_i,h_i\ge0$。这些周期向量已处在相应 de Rham 分量，所以过滤在最下面和最上面分别为全空间和零。
2. $\Phi$ 的比较把 $\zeta^\ell$ 处的展开送到 $\zeta$ 处，对第 $k$ 项施加周期 Frobenius 并乘 $\ell^k$。在 $\zeta^\ell$ 处，$N_{i-1}$ 的基展开为标准的非负幂级数格的一组基。周期 Frobenius 在这两个周期分量之间是线性同构。

则

$$
Q^{M_i}P_i\subset N_i,\qquad Q^{h_i}N_i\subset P_i .
$$

还可用 $Q$ 的各本原根逐坐标检查任何 $Q^{-m}N_i$ 中的向量是否属于 $N_i$。

## 证明

先写出局部比较的两个简单后果。过滤在所有次数 $a\le -M_i$ 是全空间，在 $a>h_i$ 是零，故比较后的 $N_i$ 满足

$$
t^{M_i}V_{i,\zeta}[[t]]
\ \subset\ (N_i)_{\zeta}\
\subset\ t^{-h_i}V_{i,\zeta}[[t]] .
\tag{1}
$$

下一层根 $\zeta^\ell$ 的标准格中，所有基向量的展开都没有负项。它们的常数向量是一组基，因为在模 $t$ 后整组仍生成空间，并且向量个数等于其维数。施加 $\Phi$ 后，常数向量变成周期 Frobenius 的像，仍是一组基。高次项乘 $\ell^k$ 不会产生负幂，所以 $P_i$ 在 $\zeta$ 处的展开恰为 $V_{i,\zeta}[[t]]$。

接下来说明怎样从这些展开传回整系数。设环境中的向量 $v$ 满足 $Q^mv\in N_i$。在 $N_i$ 的基下，令 $b_j\in O[[U]]$ 为 $Q^mv$ 的坐标。若该向量在每个 $\zeta$ 处属于 $t^m(N_i)_{\zeta}$，则各 $b_j$ 的展开都可被 $t^m$ 整除，因为基在展开格中仍然是基。由[逐根的整除引理](%E6%80%8E%E6%A0%B7%E5%9C%A8%E5%88%86%E5%9C%86%E6%A0%B9%E5%A4%84%E6%A3%80%E6%9F%A5%E6%95%B4%E5%B9%82%E7%BA%A7%E6%95%B0%E7%9A%84%E6%95%B4%E9%99%A4%E6%80%A7.md)，每个 $b_j$ 都被 $Q^m$ 整除。消去可逆的 $Q^m$，得到 $v\in N_i$。反向也成立，因为 $E_\zeta(Q)$ 为 $t$ 乘以单位。对 $\Phi(N_{i-1})$ 的基作同样的比较。若其基展开的首项线性无关，低于某一阶的项抵消只能来自每个坐标都在此前为零。这可由最低非零次数开始逐项看出。因此同一整除判据也适用于 $P_i$。

任取 $x\in P_i$。由互相可比性，$Q^mQ^{M_i}x\in N_i$ 对某个 $m$ 成立。$x$ 在每个根处的展开无负次项，$Q^{M_i}$ 使它成为 $t^{M_i}$ 倍。由 (1)，$Q^{M_i}x$ 在每个根处属于 $(N_i)_\zeta$，所以 $Q^mQ^{M_i}x$ 属于 $t^m(N_i)_\zeta$。整除判据给出 $Q^{M_i}x\in N_i$。

对任取 $y\in N_i$，其展开最低可能次数为 $-h_i$。于是 $Q^{h_i}y$ 在每个根处没有负次项，属于 $(P_i)_\zeta$。先乘一份任意的 $Q^m$ 进入 $P_i$，再用 $P_i$ 的整除判据消去 $Q^m$，即得 $Q^{h_i}y\in P_i$。这两条包含正好以 $M_i+h_i$ 的组合进入[格余核的 Frobenius 递推](%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%A4%E4%BE%A7%E7%9A%84Wach%E9%AB%98%E5%BA%A6%E7%95%8C%E8%BD%AC%E6%88%90%E4%BD%99%E6%A0%B8%E7%9A%84%E7%BB%9F%E4%B8%80%E7%95%8C.md)。

## 经典文献中的同一组高度

在经典的非分歧局部域、第一分圆层 $s=1$ 上，可直接引用 Berger 的命题 A.2。按他的权重约定，权重等于本篇过滤跳点的相反数。令 $a=-h_i$、$b=M_i$，纵向省去分量下标，记 $P=\varphi^*N$。当权重属于 $[a,b]$ 时，该命题给出 $\varphi^*(U^bN)\subset U^bN$ 以及 $Q^{b-a}U^bN\subset\varphi^*(U^bN)$。由于 $\varphi(U)=QU$，可将两侧共有的因子约去，得到 $Q^{M_i}P\subset N$ 和 $Q^{h_i}N\subset P$。这是在该文献适用范围内可直接引用的数学结论。本项目对一般分圆层由前述根处比较取得同样的形式。[Berger, *Bloch and Kato's exponential map: three explicit formulas*, Appendix A.2](https://www2.math.ethz.ch/EMIS/journals/DMJDMV/vol-kato/berger.dm.pdf#page=26)

## Lean 对照

- `mem_of_low`、`low_of_mem` 从过滤不再跳变推出 (1)，分别使用展开格包含足够高阶的所有向量和有统一极点界。`indep_const` 用低层标准格的常数项给首项线性无关。[WachLatticeHeightsFromHodgeJumps.lean:75](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L75) · [同文件:91](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L91) · [同文件:122](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L122)
- `mem_iff_roots`、`pole_bound`、`inv_pole_bound` 用所有本原根及基坐标消去先前的任意分母。正式入口是 `heights_from_jumps`。[同文件:213](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L213) · [同文件:228](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L228) · [同文件:271](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L271) · [同文件:382](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L382)
- 上游的根处展开由 `lat_eq_fil` 与 `lat_low` 分别给出当前层和较低层。它们是本篇的比较输入。[当前层展开源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean) · [低层标准格:186](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeExpansionsStdBelowLevel.lean#L186)

状态为源码级推导。另行未重新编译。从根处比较到两侧高度已展开。上游分别见[展开格的分次](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%B1%95%E5%BC%80%E6%A0%BC%E5%8F%AF%E4%BB%A5%E9%80%90%E4%B8%AA%E6%AC%A1%E6%95%B0%E6%A3%80%E6%9F%A5.md)、[当前层的过滤](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%B1%95%E5%BC%80%E7%9A%84%E5%8D%95%E9%A1%B9%E7%94%B1deRham%E8%BF%87%E6%BB%A4%E5%86%B3%E5%AE%9A.md)和[较低层的标准格](%E4%B8%BA%E4%BB%80%E4%B9%88%E8%BE%83%E4%BD%8E%E5%88%86%E5%9C%86%E5%B1%82%E7%9A%84%E5%B1%95%E5%BC%80%E6%A0%BC%E6%B2%A1%E6%9C%89%E8%B4%9F%E6%AC%A1%E9%A1%B9.md)。
