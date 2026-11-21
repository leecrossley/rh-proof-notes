# 为什么 Herr 对的两个算子差给出同一个扩张类

## 命题

沿用[整 Herr 比较](Herr%E4%BD%99%E9%97%AD%E9%93%BE%E6%80%8E%E6%A0%B7%E5%92%8C%E6%95%B4Galois%E4%B8%8A%E5%90%8C%E8%B0%83%E5%AF%B9%E5%BA%94.md)的局部群 $G$、分圆群 $\Delta\times\Gamma_1$、生成元 $\gamma$、模 $D(T)$ 及其周期比较 $J_T:D(T)\to P(T)$。设

$$
0\longrightarrow T\xrightarrow{\iota}T'\xrightarrow{q}O\longrightarrow0
$$

是连续 $G$-格的短正合列，$O$ 带平凡作用。取 $e\in D(O)$ 和 $e_0\in O^\times$，使 $J_O(e)=1\otimes e_0$，且 $\varphi(e)=e$、所有分圆作用都固定 $e$。对任意 $a\in O$，若 $x\in D(T')^\Delta$ 满足 $D(q)x=ae$，则由

$$
D(\iota)y=(\varphi-1)x,\qquad D(\iota)z=(\gamma-1)x
\tag{1}
$$

唯一确定的 $y,z\in D(T)^\Delta$ 构成 Herr 余闭链。若 $\kappa$ 由商格的生成元 $e_0$ 定义，也就是连接映射对 $e_0$ 的值，则 ${\rm cl}_T(y,z)=a\kappa$。

若用 $1\in O$ 来定扩张类 $\kappa_1$，则右端为 $ae_0\kappa_1$。工程中更换平凡格的两个生成元有时给出一个单位因子，这里说明它为什么只是一份 $O^\times$ 的倍数。

## 证明

由于 $e$ 被两算子固定，(1) 的两个右端都落在 $D(q)$ 的核。由[étale 模的正合性](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%89%A9%E5%88%B0%E5%91%A8%E6%9C%9F%E7%8E%AF%E7%9A%84%E6%AD%A3%E5%90%88%E6%80%A7%E8%83%BD%E4%BC%A0%E5%9B%9E%C3%A9tale%E6%A8%A1.md)，存在唯一的 $y,z$。因 $x$ 为 $\Delta$ 固定且相关算子互相交换，右端也为 $\Delta$ 固定，所以 $y,z\in D(T)^\Delta$。再在 $D(T')$ 上比较 $(\gamma-1)(\varphi-1)x$ 和 $(\varphi-1)(\gamma-1)x$，由 $D(\iota)$ 单射得 $(\gamma-1)y=(\varphi-1)z$。

取 $t\in T'$ 使 $q(t)=e_0$。扩张类 $\kappa$ 由 $c(\sigma)=\iota^{-1}(\sigma t-t)$ 代表。比较映射把 $x$ 送到 $P(T')$。因为 $J_{O}(D(q)x)=1\otimes ae_0$，向量

$$
J_{T'}(x)-1\otimes a t
$$

的像在 $P(O)$ 里为零。周期模是沿系数环作张量，而原格列作为 $O$-模分裂，所以 $P(T')$ 的核就是 $P(T)$。因此可用 $P(\iota)$ 的单射将此向量视为 $b\in P(T)$。

Frobenius 逐周期系数作用，所以固定 $1\otimes at$，而比较与 Frobenius 相容。由 (1)，得到 $(\varphi-1)b=J_T(y)$。若 $\sigma$ 的分圆像属于 $\Delta$，因它固定 $x$，有

$$
-(\sigma-1)b=1\otimes a c(\sigma).
$$

若分圆像等于 $\gamma$，则 $(\sigma-1)J_{T'}(x)=P(\iota)J_T(z)$，于是

$$
J_T(z)-(\sigma-1)b=1\otimes a c(\sigma).
$$

这两式就是 Herr 类映射的代表公式。两类元素拓扑生成 $G$，故该代表与 $a c$ 逐点相等，得到 ${\rm cl}_T(y,z)=a\kappa$。

最后解释给定一个任意固定生成元 $e'$ 时的单位。若 $e,e'$ 都生成 $N(O)$ 且都由 $\varphi,\Gamma$ 固定，写 $e'=u e$，其中 $u$ 在整系数环中可逆。比较后 $J_O(e')$ 及 $J_O(e)$ 都是 $\varphi$ 固定元，故由[周期 Frobenius 的核](%E6%80%8E%E6%A0%B7%E5%9C%A8Witt%E5%91%A8%E6%9C%9F%E7%8E%AF%E9%87%8C%E7%94%A8%E8%BF%B9%E4%B8%80%E5%85%83%E6%B6%88%E5%8E%BB%E5%B1%80%E9%83%A8%E4%BD%99%E9%97%AD%E9%93%BE.md)，$J_O(e')=1\otimes e_0'$ 对某个 $e_0'\in O$ 成立。因为乘 $u$ 在周期系数环中可逆，$e_0'$ 在 $O$ 中也是单位。否则 $e_0'$ 被 $O$ 的素元整除，而素元的像由于其某个幂与 $\ell$ 相差单位，属于大周期环的 Jacobson 根基，无法可逆。因此 $e_0'/e_0$ 是单位，可以先把 $x$ 乘其逆。这样获得的类恰为 $a\kappa$。

## Lean 对照

- `dict_K` 对 $G_K$ 使用两个算子差，求出的代表正是扩张余闭链。分圆层版本使用同一比较。[MemFixingSubgroupMaxUnramifiedOfMemLocalGalois.lean:451](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MemFixingSubgroupMaxUnramifiedOfMemLocalGalois.lean#L451)
- `unitVector` 选出平凡格中相容的两个基向量。主公式 `herr_extension_class_formula` 将它代入带标量的扩张，分别处理分圆层与带有限子群的版本。[UnitVectorOfUnitFor.lean:51](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/UnitVectorOfUnitFor.lean#L51) · [HerrExtensionClassFormula.lean:15](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/HerrExtensionClassFormula.lean#L15)
- `coreExtΔ_of` 在提回 Wach 格时先取温和平均，并乘单位的逆。它还验证 (1) 的各坐标满足分母条件。[ExtensionInvariantClause.lean:144](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/ExtensionInvariantClause.lean#L144)

状态为源码级推导。另行未重新编译。正文展开的是比较所给的扩张类公式，允许极点的坐标何时得到 Bloch–Kato 有限类由另外的晶体周期论证负责。
