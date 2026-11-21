# 怎样在不除以整数时把矩阵行列式留在 Hecke 环

## 命题

设 $R$ 为交换环，$S\subseteq R$ 为含单位的子环，$G$ 为群，$\rho:G\to\operatorname{GL}_d(R)$ 为表示。令 $A$ 为 $\rho(G)$ 的 $S$-线性张成，因 $\rho(g)\rho(h)=\rho(gh)$，它是矩阵子环。设对所有 $g\in G$，

$$
\det(1-z\rho(g))\in S[z].
\tag{1}
$$

则对任意 $m\ge0$ 及 $a_1,\ldots,a_m\in A$，多变量多项式

$$
\det\Bigl(\sum_{i=1}^{m}u_i a_i\Bigr)
$$

的所有系数都在 $S$。此外，对任意 $g\times g$ 的 $A$-矩阵 $\Theta$，将每个条目当作 $d\times d$ 小矩阵排成大矩阵 $\Theta_{\mathrm{big}}$，有 $\det\Theta_{\mathrm{big}}\in S$。

工程的 $R$ 是分式域值函数环，$S$ 是整值 Hecke 函数环的像。式 (1) 表达 Hecke 环包含群元素的特征多项式系数。要取关系矩阵的方阵行列式，所用的是命题的第二个结论。

## 先处理一个块

先证明对每个有限和 $M=\sum_j a_j z^{n_j}\rho(g_j)$，其中 $a_j\in S$、$n_j\ge1$，有 $\det(1-M)\in S[z]$。固定一个截断次数 $N$，在 $R[z]/(z^{N+1})$ 中计算。选当前最低次数的一项 $B=a z^n\rho(g)$，记其余项之和为 $C$。因为 $B^{N+1}=0$，可以写

$$
1-(B+C)=(1-B)\left(1-\sum_{k=0}^N B^kC\right).
\tag{2}
$$

先取行列式。第一因子 $\det(1-B)$ 由 (1) 作代换 $z\mapsto a z^n$，在 $S[z]$ 内。第二因子中，$k=0$ 留下原有项，$k\ge1$ 的每个新项仍有 $S$-系数并带某个群元素矩阵，因为 $\rho$ 保持乘法。新项次数严格高于 $n$。

所以每次操作减少一个最低次的项，不会产生同次或更低次的新项。先消尽当前最低次项，再逐次提高次数，有限步后只剩次数超过 $N$ 的项，在截断环中全部为零。于是原行列式模 $z^{N+1}$ 是若干个 $S[z]$ 中的行列式相乘。每个 $N$ 都可这样做，所以所有系数在 $S$。这个正整次数的消去不需要在 $S$ 中除以任何整数。

接下来把 $u_i$ 并入系数环，取 $S[\mathbf u]\subseteq R[\mathbf u]$。令 $M=z\sum_i u_i a_i$，将各 $a_i$ 展为群元素的有限线性组合，可用以上结论。取 $\det(1-M)$ 的 $z^d$ 系数，得到 $(-1)^d\det(\sum_i u_i a_i)$ 的系数都在 $S$。因此给一个小矩阵 $A(z)$ 取 $A$ 中系数的形式幂级数，$\det A(z)$ 的各系数也在 $S$。要算某一阶，只保留 $A(z)$ 的有限截断，再把 $u_i$ 代成相应的 $z^i$ 即可。

## 用形式幂级数处理多块

考虑常数项为单位矩阵的块矩阵幂级数，其各块系数都在 $A$。对块数作归纳。把第一行和第一列分开，记作

$$
\begin{pmatrix} U & B\\ C & D\end{pmatrix}.
$$

其中 $U(0)=1,\ B(0)=C(0)=0,\ D(0)=1$。因 $U(0)=1$，$U^{-1}$ 的各系数由 $UU^{-1}=1$ 递推，仍在 $A$。于是 Schur 补 $D-CU^{-1}B$ 仍有同样的系数性质，常数项为单位矩阵。乘一个行列式为 $1$ 的块三角消元矩阵，给原行列式等于
$\det U\cdot\det(D-CU^{-1}B)$。
第一个因子用小块结论，第二个用归纳，故所有系数都在 $S$。

应用于 $1-z\Theta_{\rm big}$，取最高次系数，即 $(-1)^{gd}\det\Theta_{\rm big}$，得到命题。取角块多项式时，可以直接在 $S[T]\subset R[T]$ 中用第一部分，因为 $Te_B-X_0+(1-e_B)$ 是群元素矩阵的 $S[T]$-线性组合。

## 源码对照

- `alg_identity`、`key` 是 (2)，`stepD`、`core` 按次数消去。`det_poly_statement` 得多变量系数结论。[LemmaDetPoly.lean:107](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/LemmaDetPoly.lean#L107) · [第 183 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/LemmaDetPoly.lean#L183) · [第 393 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/LemmaDetPoly.lean#L393)
- `detGood`、`invGood`、`schur`、`blockDet` 对形式幂级数及块矩阵取系数。[IsUnitDetOfConst.lean:220](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/IsUnitDetOfConst.lean#L220) · [第 307 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/IsUnitDetOfConst.lean#L307) · [第 447 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/IsUnitDetOfConst.lean#L447)
- `blockPolyT` 将结论用在角块多项式，`eta_determinant_comparison` 用于关系矩阵。[CMemPolyT.lean:114](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/CMemPolyT.lean#L114) · [BridgeDet.lean:9](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/TruncatedSeriesCounting/TruncatedSeriesProofs/BridgeDet.lean#L9)

本篇为源码对读。给定 (1) 后，两个行列式的系数结论均已证明。
