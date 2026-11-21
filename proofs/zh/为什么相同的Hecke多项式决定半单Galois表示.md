# 为什么相同的 Hecke 多项式决定半单 Galois 表示

## 命题

设 $F$ 为 CM 数域，$F^+$ 是其最大实子域，$G_F={\rm Gal}(\overline F/F)$。令 $O$ 为项目某个局部指标 $i$ 的完整离散赋值系数环，$k={\rm Frac}(O)$ 的特征为零。给定有限评价点集 $X$，每个 $x\in X$ 给定 Hecke 多项式 $P_{x,w}(T)$，其中 $w$ 遍历在 $F/F^+$ 中分裂、且避开项目有限例外集合的素理想。设 $r=(r_x)$、$r'=(r'_x)$ 为两组连续 $G_F\to{\rm GL}_d(O)$ 的表示，扩到 $k$ 后半单。假定任意这样的 $w$ 及其在绝对 Galois 群里的 Frobenius 提升 $\sigma_w$ 都满足

$$
\det(T-r_x(\sigma_w))=P_{x,w}(T)=\det(T-r'_x(\sigma_w)).
$$

则每个 $x$ 都存在 $P_x\in{\rm GL}_d(k)$ 使 $P_x r_x(g)=r'_x(g)P_x$ 对全体 $g\in G_F$ 成立。上述连续性、半单性、Hecke 多项式相合就是工程条件 `GoodR` 对各 $x$ 的展开。它是将整体格指数的同余对象从自守构造中给出的族传给任意另一个表示族的第一步。

## 为什么只查这些素理想就够

先固定 $x$。若 $r_x,r'_x$ 的迹在某个 $g$ 不同，由连续性与 $O$ 的 Hausdorff 性，可找一个有限指数开正规子群 $H$ 使两迹在整个 $Hg$ 上都不同。开正规子群对应有限 Galois 扩张 $F_1/F$。项目使用的 `Cheb` 是以下形式。对任意有限排除集，可取一个绝对剩余次数 $1$、绝对分歧指数 $1$ 的素理想 $w$，在 $F_1$ 中不分歧，并且在 $w$ 上某个选择的 Frobenius 提升落在 $Hg$。

这个形式可直接由经典切博塔廖夫密度定理推出。对 $g$ 在 ${\rm Gal}(F_1/F)$ 中所属的共轭类，其素理想的 Dirichlet 密度为正。绝对剩余次数至少二的素理想的倒数和有界，因为上方的有理素数为 $p$ 时，其范数至少 $p^2$，而每个 $p$ 上方至多 $[F:\mathbb Q]$ 项。因此抛去这些素理想不改变密度。绝对分歧指数大于一的素理想只有有限个，可一并抛去。最后换 $w$ 上方的素理想，使 Frobenius 在有限商中等于指定的 $gH$。这里引用密度定理作为明确的文献截止点。Lean 工程另有从分圆相交构造得到 `Cheb` 的证明。[MIT 18.785 讲义，定理 28.9 与绝对次数一的说明](https://ocw.mit.edu/courses/18-785-number-theory-i-fall-2021/mit18_785f21_lec28.pdf#page=6)

还需 $w$ 在 $F/F^+$ 中分裂。取一个代数整数 $a\in\mathcal O_F$ 使它不被复共轭 $c$ 固定，剔除所有整除 $c(a)-a$ 的 $w$。若 $w$ 被 $c$ 固定，则它的剩余域 $\mathbb F_p$ 上的自同构只能是恒等，从而 $c(a)-a\in w$，矛盾。因此 $w,c(w)$ 不同，恰说明 $w$ 在二次扩张中属于分裂情形。再排除原有的有限集，就找到一个允许的 $w$ 及 $\sigma_w\in Hg$。由于特征多项式的次高系数是迹的相反数，两迹在 $\sigma_w$ 相等，与选 $Hg$ 时的条件矛盾。故两迹在 $G_F$ 上处处相等。

## 为什么迹能识别半单表示

下面在任意特征零域 $k$ 上证明所需的代数事实。设 $V,W$ 是同一个 $k$-代数 $A$ 的有限维半单模，且所有 $a\in A$ 在二者上的迹相等。这里可取 $A=k[G_F]$，因为迹在群元素相等会线性延伸到群代数。

若 $V\to W$ 或 $W\to V$ 有非零 $A$-线性映射，利用半单性分裂它的核与像，就能在 $V,W$ 中取下一个共同的非零直和因子 $S$。新得到的两个模仍然半单，且从两个迹等式中消去同一个 ${\rm tr}_S(a)$，故仍有相同的迹。对维数和归纳，只需处理两个方向的同态都为零的情形。

令 $M=V\oplus W$，$p:M\to M$ 为投影到 $V$。因为 $V,W$ 间的同态都为零，每个 $A$-线性自同态都在两块上分别作用，因而与 $p$ 交换。要证明存在 $a\in A$ 在整个 $M$ 上等于 $p$，取一组 $k$-基 $v_1,\ldots,v_d$，考虑

$$
I=\{(a v_1,\ldots,a v_d):a\in A\}\subset M^d .
$$

这是一个 $A$-子模。若 $(p v_i)_i\notin I$，因为 $M^d$ 半单，其商 $M^d/I$ 有一个简单直和因子检测该向量的非零像。这个简单模也是 $M$ 的一个直和因子。所以得到一个 $A$-线性映射 $\lambda:M^d\to M$，它消去 $I$ 且在 $(p v_i)_i$ 上非零。将 $\lambda$ 写作 $\sum_i\lambda_i$，其中 $\lambda_i:M\to M$ 是 $A$-线性映射。则

$$
\lambda((p v_i)_i)=\sum_i\lambda_i(p v_i)
                  =p\sum_i\lambda_i(v_i)=0,
$$

最后因为 $(v_i)_i\in I$。矛盾。于是确有 $a$ 在整个 $M$ 上等于 $p$。此时 $a$ 在 $V,W$ 的迹分别为 $\dim_k V$ 与 $0$，特征零使 $\dim_k V=0$。再用 $1\in A$ 的迹得 $\dim_k W=0$。归纳完成。

将该结论用于每个 $x$，得到 $k$-线性等变同构。在两组原基下写成矩阵就是 $P_x$。这个证明不要求 $k$ 代数闭。

## Lean 对照

- `eq_univ_of_frob` 从允许的 Frobenius 元传到整个绝对 Galois 群，`isRx_unique` 从相同的迹认出等变同构。`PointRepConj.main` 将它写成分式域矩阵共轭。[T2SpaceCoefficientRing.lean:166](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceCoefficientRing.lean#L166) · [同文件:203](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/T2SpaceCoefficientRing.lean#L203) · [PointGaloisRepsConjugateOverFractionField.lean:29](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PointGaloisRepsConjugateOverFractionField.lean#L29)
- `finrank_eq_zero_of_hom` 用 Jacobson 稠密性实现块投影。`split_of_hom` 与 `exists_equiv_of_trace_eq` 对公共直和因子归纳。上面的有限基检测给出该处实际所用的稠密性特例。[NonemptyLinearEquivOfCharpolyEq.lean:37](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NonemptyLinearEquivOfCharpolyEq.lean#L37) · [同文件:79](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NonemptyLinearEquivOfCharpolyEq.lean#L79) · [同文件:138](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NonemptyLinearEquivOfCharpolyEq.lean#L138)
- `Cheb` 给出带绝对次数一的 Frobenius 条件，`cheb_holds` 是项目中提供它的定理。[GaloisSideTwistedSelmerAuxiliaryPrimes.lean:11](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/GaloisSideTwistedSelmerAuxiliaryPrimes.lean#L11) · [ChebotarevDegreeOne.lean:66](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ChebotarevDegreeOne.lean#L66)

状态为源码级推导。另行未重新编译。切博塔廖夫部分给出经典文献中与项目陈述相接的短证。
