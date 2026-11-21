# 为什么固定周期环和 étale 像在两种精度下都闭合

## 命题

设 $C=\mathbb C_\ell$、$C^\flat$ 为其倾斜域，$R=\mathcal O_{C^\flat}$。设 $O$ 是有限 $\mathbb Q_\ell$ 扩张的整数环，$A=O[[U]]^d$，$d\ge1$，$E=\widehat{A[1/U]}$ 为 $\ell$-进完备化。记

$$
B^+=O\otimes_{\mathbb Z_\ell}W(R),\quad B=O\otimes_{\mathbb Z_\ell}W(C^\flat).
$$

设有相容的 $A\hookrightarrow B^+$、$E\hookrightarrow B$，后一个映射将 $U$ 的像记作 $t=1\otimes([\epsilon_s]-1)$，其中 $\epsilon_s$ 是相容分圆参数在倾斜域中的第 $s$ 层根，$s\ge1$。记 $\mathcal F_m=t^mB^++\ell B$。假定 Frobenius $\varphi$ 保持这些映射，固定 $O$，循环置换 $A$ 的系数分量。设群 $H$ 逐 Witt 坐标作用于 $B$，固定 $O,t,E$。令 $S=B^H$。

则：

1. $S,E$ 都在 $B$ 中对 $\ell$ 饱和，且 $E$ 在 $B$ 的 $\ell$-进拓扑下闭。$S$ 可逐项求和 $\sum_i\ell^i x_i$，$x_i\in S$。
2. 对每个 $k\ge0$，若 $f_i\in S\cap\mathcal F_{i+k}$，则存在 $f\in S$ 使 $f-\sum_{i<j}f_i\in\mathcal F_{j+k}$ 对每个 $j$ 成立。
3. 若 $x\in\bigcap_m(E+\mathcal F_m)$，则 $x\in E+\ell B$。

三项分别供[固定周期商上的 Frobenius 差算子](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9B%BA%E5%AE%9A%E5%91%A8%E6%9C%9F%E5%95%86%E9%87%8C%E7%9A%84Frobenius%E5%87%8F%E4%B8%80%E5%8F%AF%E9%80%86.md)使用。

## 证明

**模 $\ell$ 的含义。** 取 $O$ 的 $\mathbb Z_\ell$-基，将 $B$ 写成有限个 $W(C^\flat)$ 的坐标。因 $C^\flat$ 完美，模 $\ell$ 由每个 Witt 向量的第零坐标给出。在这些坐标中，$\mathcal F_m$ 就是所有模 $\ell$ 坐标属于 $(\epsilon_s-1)^mR$ 的元素。这个识别也给出 $\bigcap_m\mathcal F_m=\ell B$，因为 $0<|\epsilon_s-1|<1$。

**固定环的完备性。** 由于 $\ell$ 在 $B$ 中无挠，若 $\ell x$ 被 $H$ 固定，则 $x$ 固定。又 $B$ $\ell$-进完备、分离，$\sum_i\ell^i x_i$ 的极限仍被 $H$ 固定，故得到第 1 条关于 $S$ 的部分。对第 2 条，先模 $\ell$ 求和。倾斜整数环 $R$ 在 $\epsilon_s-1$ 进拓扑下完备，所以每个坐标的级数收敛到 $c\in R$，余项落在 $(\epsilon_s-1)^{j+k}R$。这是完备非阿基米德域内的几何级误差。每个部分和都被 $H$ 固定，极限也固定，因为 $H$ 固定参数并保持 $R$。用 $c$ 的 Teichmüller 提升 $[c]$ 作为该坐标的 Witt 向量，仍被 $H$ 固定，且模 $\ell$ 等于 $c$。逐坐标提升后得到 $f\in S$ 和第 2 条。

**分圆参数的整除性。** 先证对 $a\in A$，若其像在 $\mathcal F_m$，则

$$
a\in U^m A+\ell A .
\tag{1}
$$

当 $m=1$，将 $a$ 的每分量拆成常数与 $U$ 倍。当 $a$ 在 $\mathcal F_1$，其常数向量 $a_0$ 也在 $\mathcal F_1$。乘分量幂等元 $e_i$，得到其中的 $o_i e_i$ 在 $\mathcal F_1$。Frobenius 保持 $\mathcal F_1$，因为 $t$ 模 $\ell$ 变为 $t^\ell$，而整系数仍整。它固定 $o_i$ 并循环置换 $e_i$，故 $o_i e_j$ 对每个 $j$ 都在 $\mathcal F_1$。将它们相加，得到对角常数 $o_i$ 在 $\mathcal F_1$。在 $O$ 的 $\mathbb Z_\ell$-基下，$o_i$ 模 $\ell$ 的坐标属于 $\mathbb F_\ell$，任何非零坐标在 $C^\flat$ 中绝对值为 $1$，无法被 $\epsilon_s-1$ 整除。所以 $o_i\in\ell O$，这就得到 $m=1$ 的拆分。一般 $m\ge1$ 可先用一级拆分 $a=Ua_1+\ell a_2$。在 $B/\ell B$ 中 $t$ 可逆，因为 $t$ 在 $B$ 内是 $U$ 的可逆像。故 $a_1$ 的像在 $\mathcal F_{m-1}$，归纳即可得 (1)。

对 $e\in E$，若其像在 $\mathcal F_m$，先写 $U^Ne\equiv a\pmod{\ell E}$ 对某个 $N\ge0,a\in A$ 成立。则 $a$ 的像在 $\mathcal F_{m+N}$。由 (1) 写 $a=U^{m+N}b+\ell b'$，再消去 $U^N$，得 $e\in U^m A+\ell E$。特别地，当 $e$ 的像在 $\ell B$，先取 $m=0$ 写 $e\equiv a\bmod\ell E$ 且 $a\in A$。每个 $m$ 都说明 $a\equiv0\bmod U^mA+\ell A$，逐次看系数得 $a\in\ell A$。这里用到 $A/\ell A\to E/\ell E$ 单射。所以 $E\cap\ell B=\ell E$。这也可直接用[整周期环交式](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%95%B4%E5%91%A8%E6%9C%9F%E5%9D%90%E6%A0%87%E8%90%BD%E5%9B%9E%E5%88%86%E5%9C%86%E5%B9%82%E7%BA%A7%E6%95%B0%E7%8E%AF.md)中的饱和结论。继续逐次消去 $\ell$ 得 $E\cap\ell^k B=\ell^kE$ 对每个 $k$ 成立，结合 $E$ 的完备性与 $B$ 的分离性，得到 $E$ 在 $B$ 的 $\ell$-进闭性。

**模 $\ell$ 的闭性。** 设 $x-e_m\in\mathcal F_m$。于是 $e_{m+1}-e_m\in\mathcal F_m$。由上一段，

$$
e_{m+1}-e_m\ \equiv U^m a_m\pmod{\ell E},\qquad a_m\in A.
$$

级数 $a=\sum_m U^ma_m$ 在 $A$ 内收敛。取 $e=e_0+a$，则 $e-e_m\in U^m A+\ell E$，在周期环中属于 $\mathcal F_m$。所以 $x-e\in\bigcap_m\mathcal F_m=\ell B$，给出第 3 条。

## Lean 对照

- `nearPi_sep_complete` 用有限个 Witt 第零坐标处理参数过滤的完备和分离。`fixed_complete_generic` 对固定元的部分和取极限，再用 `exists_fix_lift_of_fix_mod` 选固定的 Witt 提升。[NearPiSepComplete.lean:197](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NearPiSepComplete.lean#L197) · [GaloisFixedTensorWittCompletePiAdicModEll.lean:26](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisFixedTensorWittCompletePiAdicModEll.lean#L26) · [固定提升源码](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsGaloisFixedLiftOfFixedModPrime.lean)
- `near_one_split`、`near_split` 用 Frobenius 的循环和常数项取得 (1)，`near_abstract` 将整除性传到 $E$。`near_closed_abstract` 求和得到模 $\ell$ 的闭性。[MemPiPowEllOfNearPi.lean:29](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemPiPowEllOfNearPi.lean#L29) · [整除性传到 étale 环](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EtaleComparisonPiAdicFiltrationModEll.lean#L36) · [模 $\ell$ 的闭性](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EtaleRingImageAddEllPiAdicClosed.lean#L51)

状态为源码级推导。另行未重新编译。采用工程给出的倾斜完备性、Witt 环及系数映射。
