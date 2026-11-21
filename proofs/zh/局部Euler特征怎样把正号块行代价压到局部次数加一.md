# 局部 Euler 特征怎样把正号块行代价压到局部次数加一

## 命题

设 $\ell$ 为素数，$L/\mathbb Q_\ell$ 为有限扩张，$D=G_L$，$d=[L:\mathbb Q_\ell]$。设 $K/\mathbb Q_\ell$ 为有限系数扩张，整数环为 $\mathcal O$，均匀化元为 $\varpi$，剩余域大小为 $q$。记 $e_{\mathcal O}=\operatorname{ord}_{\mathcal O}(\ell)$，记 $\epsilon:D\to\mathbb Z_\ell^\times$ 为分圆特征。对整数 $a\ge0$，令 $M_a=(K/\mathcal O)(\epsilon^{-a})$，即 $g$ 乘以 $\epsilon(g)^{-a}$。

令 $H_a=H^1_{\rm cont}(D,M_a)$。若 $a>0$，取 $F_a=0$。若 $a=0$，取 $F_0=H^1_{\rm ur}(D,M_0)$，即在惯性群上为零的类。则 $H_a/F_a$ 作为 $\mathcal O$-模同构于

$$
(K/\mathcal O)^d\oplus C
$$

其中 $C$ 是有限循环 $\mathcal O$-模，允许 $C=0$。因此对每个 $c\ge0$，有

$$
\operatorname{length}_{\mathcal O}\bigl((H_a/F_a)[\ell^c]\bigr)
 \le e_{\mathcal O}\,c(d+1).
\tag{1}
$$

以下以有限系数的 Tate 局部对偶及局部 Euler 特征公式为输入。对有限的 $\ell$-幂扭结 $D$-模 $U$，这些定理给 $H^2(D,U)$ 与 $H^0(D,U^\vee(1))$ 等大，且 $|H^1(D,U)|=|H^0(D,U)|\,|H^2(D,U)|\,|U|^d$。这里 $U^\vee=\operatorname{Hom}(U,\mathbb Q/\mathbb Z)$，$(1)$ 为分圆扭曲。[Milne, *Arithmetic Duality Theorems*, I.2，推论 2.3](https://www.jmilne.org/math/Books/ADTnot.pdf#page=36) · [定理 2.8](https://www.jmilne.org/math/Books/ADTnot.pdf#page=39)

## 计算有限层的点数

对 $n\ge1$，置 $U_n=M_a[\varpi^n]$。其底模同构于 $\mathcal O/\varpi^n$，故 $|U_n|=q^n$。分圆特征在 $D$ 上的像是 $\mathbb Z_\ell^\times$ 中的开子群，因为 $L/\mathbb Q_\ell$ 有限，而 $\mathbb Q_\ell$ 上整条分圆塔的伽罗瓦群为 $\mathbb Z_\ell^\times$。所以对任意正指数 $b$，总可取 $g$ 使 $\epsilon(g)^b\ne1$。

若 $a>0$，取 $b=a$ 得 $M_a^D$ 被一个非零标量 $\epsilon(g)^{-a}-1$ 消去，因而有限。有限模上乘 $\varpi^n$ 的核和余核等大，由此

$$
|M_a^D/\varpi^n M_a^D|=|U_n^D|.
$$

若 $a=0$，$M_a^D=M_a$ 可除，左边为 $1$，而右边是 $q^n$。

短正合列 $0\to U_n\to M_a\xrightarrow{\varpi^n}M_a\to0$ 在 $H^1$ 给出

$$
0\longrightarrow M_a^D/\varpi^n M_a^D
\longrightarrow H^1(D,U_n)\longrightarrow H_a[\varpi^n]\longrightarrow0.
$$

有限层 Euler 特征和刚算过的 $H^0$ 项遂给

$$
|H_a[\varpi^n]|=
\begin{cases}
q^{nd}|H^2(D,U_n)|,& a>0,\\
q^{n(d+1)}|H^2(D,U_n)|,& a=0 .
\end{cases}
\tag{2}
$$

由 Tate 局部对偶，$|H^2(D,U_n)|$ 是其扭曲对偶固定子群的大小。该对偶的底 $\mathcal O$-模是一个循环模 $\mathcal O/\varpi^n$，作用为 $\epsilon^{a+1}$。底模的识别可用有限长度的 $\mathcal O$-对偶，或者选一个加法字符，在 $\mathcal O/\varpi^n$ 的最小非零理想上非零，再将它按环元素平移。由最小非零理想包含在每个非零理想中，所得字符给出满的对偶。取能移动 $a+1$ 次幂的 $g$。固定子模被 $\epsilon(g)^{a+1}-1$ 消去，其大小因此在 $1$ 与某个独立于 $n$ 的常数 $C_0$ 之间。特别地在 $n=1$ 时不超过 $q$。

在平凡作用时，$H^1_{\rm ur}(D,M_0)=\operatorname{Hom}_{\rm cont}(\widehat{\mathbb Z},K/\mathcal O)\simeq K/\mathcal O$，同构由 Frobenius 取值给出。这个子模可除。因此 $H_0[\varpi^n]\to(H_0/F_0)[\varpi^n]$ 满射。一个商类被 $\varpi^n$ 消去时，先从任一提升中扣掉一个 $F_0$ 元素，将提升的 $\varpi^n$ 倍改为零。映射的核有 $q^n$ 个元素。于是除去 (2) 的一份 $q^n$，两种情形统一为

$$
q^{nd}\le |(H_a/F_a)[\varpi^n]|\le C_0 q^{nd},\qquad
 |(H_a/F_a)[\varpi]|\le q^{d+1}.
\tag{3}
$$

## 怎样从点数看出模的结构

连续余闭链到离散扭结模的像有限，所以被某个 $\varpi^n$ 整体消去。故 $B=H_a/F_a$ 为 $\varpi$-幂扭结模。它的 $\varpi$-扭结由 (3) 知有限。这里用到下述模论事实。若 $\mathcal O$ 完备，任一这样的 $B$ 同构于 $(K/\mathcal O)^m\oplus U$，其中 $U$ 为有限扭结模。

证明此事实时，先设 $s=\dim_{k}B[\varpi]$，将 $B[\varpi]$ 嵌入 $(K/\mathcal O)^s$。在主理想整环上，可除模是内射模，所以可延成 $B\to(K/\mathcal O)^s$。它仍单射，因为任何非零的 $\varpi$-幂扭结子模都有非零的 $\varpi$-扭结。取以 $K/\mathcal O$ 为靶的对偶，得到 $B^\vee_{\mathcal O}$ 是 $\mathcal O^s$ 的商。这里 $\operatorname{End}_{\mathcal O}(K/\mathcal O)\simeq\varprojlim_n\mathcal O/\varpi^n=\mathcal O$。自然评价 $B\to (B^\vee_{\mathcal O})^\vee_{\mathcal O}$ 是同构。可把后者视为 $(K/\mathcal O)^s$ 中使所有在 $B$ 上消失的泛函都为零的元素。若某一元素不在 $B$，它在商中的非零循环子模上可取一个非零取值的泛函，再由内射性延拓到整个商，故该元素不会在双对偶中。最后对有限生成模 $B^\vee_{\mathcal O}$ 用离散赋值环上的结构定理，再对偶回去，就得上述分解。

由分解可知当 $n$ 充分大时，$|B[\varpi^n]|=q^{nm}|U|$。与 (3) 两边比较得 $m=d$。再看 $n=1$，得 $\dim_k U[\varpi]\le1$，所以有限扭结模 $U$ 只可能有一个非零循环直和项。此即 $C$。最后 $\ell^c$ 与 $\varpi^{e_{\mathcal O}c}$ 相差单位，$d$ 份可除商格的消去子模共长 $d e_{\mathcal O}c$，$C$ 上的再多一份至多 $e_{\mathcal O}c$。得到 (1)。

## 在各行上使用

正号块的局部条件 $F_a$，在非平凡负扭曲时取零，在平凡作用时取不分歧子空间。取行 $w$，如果这里所产生的全部类 $z$ 都满足 $\ell^{c_B}z\in F_a$，就选 $F_a$ 在 $\ell^{c_B}$ 下的逆像作放宽条件。其商是 $H_a/F_a$ 的 $\ell^{c_B}$-消去子模，(1) 将当地代价控制在 $e_{\mathcal O}c_B(d_w+1)$。工程最后用较宽的 $e_{\mathcal O}c_B(d_w+2)$ 统一记账。$\ell^{c_B}z\in F_a$ 来自 Wach 整格的局部消去界。

## 源码对照

- `shapeG_of_localDuality`、`shapeUnr_of_localDuality` 分别计算负扭曲及平凡作用模去不分歧的结构。[CohomologyShapeOfTateDualityEuler.lean:34](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CohomologyShapeOfTateDualityEuler.lean#L34) · [GaloisHomModuloUnramifiedShapeOfLocalDuality.lean:142](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GaloisHomModuloUnramifiedShapeOfLocalDuality.lean#L142)
- `rowChiReal` 选择相应局部条件，`rowTB` 用结构界给放宽后的长度。[RowChiReal.lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RealClassMaps/RealClassMapProofs/RowChiReal.lean) · [LengthMapQuotLe.lean:47](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CoprimeLiftBounds/CoprimeLiftProofs/LengthMapQuotLe.lean#L47)

本篇为源码对读。有限层计数、去掉不分歧方向及模的结构已展开。局部 Euler 公式和 Tate 局部对偶有文献出处。局部消去界本身仍是应用条件。
