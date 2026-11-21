# 为什么 CM 共轭把 Hodge–Tate 权反射到同一个整数

## 命题

设 $E$ 为任意 CM 数域，即一个全实数域 $F$ 的全虚二次扩张。写 $c$ 为 $E/F$ 的非平凡自同构。取整数 $a\ge1$，取 ${\rm GL}_a(\mathbb A_E)$ 的尖点自守表示 $\pi$ 和 $F$ 上的连续 Hecke 特征 $\chi:F^\times\backslash\mathbb A_F^\times\to\mathbb C^\times$。令 $\psi=\chi\circ N_{E/F}$。

对每个 $\tau:E\hookrightarrow\mathbb C$，记 $\Lambda_\tau$ 为项目归一化的无穷小特征多重集。假设 $\pi$ 正则代数，即 $\Lambda_\tau$ 有 $a$ 个两两不同的元，均属于 $(a-1)/2+\mathbb Z$。再假设 $(\pi,\chi)$ 按项目的 `PolarizedPair` 极化。这里用到的极化条件是 $\pi\otimes(\psi^{-1}\circ\det)$ 与 $\pi$ 具有按 $c$ 扭转的不变非退化对偶配对。

则存在一个整数 $w$，使对所有 $\tau$，有多重集等式

$$
\Lambda_{\tau c}=\{a-1-w-z:z\in\Lambda_\tau\}.
\tag{1}
$$

给定素数 $\ell$ 及抽象域同构 $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$，定义整数多重集

$$
H_\sigma=\{(a-1)/2-z:z\in\Lambda_{\iota\sigma}\}
\qquad(\sigma:E\hookrightarrow\overline{\mathbb Q}_\ell).
$$

则 $H_{\sigma c}=\{w-h:h\in H_\sigma\}$。当后续表示构造识别这些整数为过滤跳点时，这就是其 Hodge–Tate 权的共轭公式。

## 证明

设 $b_\tau$ 为 $\psi$ 在复嵌入 $\tau$ 方向的无穷小指数。对一个复处 $\{\tau,\tau c\}$，两个指数对应局部特征中 $z$ 和 $\bar z$ 的两个方向。无穷小特征与扭曲及对偶的配合给

$$
\Lambda_{\tau c}=\{b_\tau-z:z\in\Lambda_\tau\}.
\tag{2}
$$

具体使用的两条输入是，张量 $\psi^{-1}\circ\det$ 把 $\Lambda_\tau$ 每项平移 $-b_\tau$，而共轭方向上的不变配对把这组平移后的参数逐项取负。后者等式按多重集成立。于是，任取 $z\in\Lambda_\tau$，$z=(a-1)/2+m$ 与 $b_\tau-z=(a-1)/2+m'$，其中 $m,m'\in\mathbb Z$。由于 $a\ge1$ 能选择这样的 $z$，相加可得 $b_\tau=a-1+m+m'\in\mathbb Z$。

对偶公式还留下一个问题，$b_\tau$ 是否随嵌入改变。由 $\psi$ 通过范数从 $F$ 拉回，且复处的范数为 $z\bar z$，有 $b_{\tau c}=b_\tau$。记 $b_\phi$ 为两个延拓到 $E$ 的公共指数，其中 $\phi:F\hookrightarrow\mathbb R$。设 $x\in F^\times$ 全正，在每个实处给 $\chi$ 放入 $\phi(x)>0$。在相应的复处取正的 $\sqrt{\phi(x)}$，其范数是 $\phi(x)$。拉回特征在这样一个分量上的两个指数都是 $b_\phi$，乘起来为 $(\sqrt{\phi(x)})^{2b_\phi}=\phi(x)^{b_\phi}$。所以

$$
\chi_\infty(x)=\prod_{\phi:F\hookrightarrow\mathbb R}\phi(x)^{b_\phi}
\qquad\text{对每个全正 }x\in F^\times.
\tag{3}
$$

**各指数相等。** 令 $u\in\mathcal O_F^\times$。把 $u$ 在各有限处的分量放入 $\chi$，它们属于紧群 $\prod_{v<\infty}\mathcal O_{F_v}^{\times}$。连续特征在该紧群上的绝对值为 $1$，因为 $\mathbb R_{>0}$ 的紧子群只有 $\{1\}$。对角主 idèle 上的特征值为 $1$，所以 $|\chi_\infty(u)|=1$。源码用同一个紧性事实的序列证明。每个固定有限处的单位对任意 $\mathfrak m_v^k$ 的剩余商中都有有限阶。于是 $m!$ 次幂在每个有限处趋于 $1$，并在有限 idèle 单位积的拓扑中趋于 $1$。若原绝对值大于或小于 $1$，其阶乘次幂就不能趋于 $1$。

将 (3) 用在全正单位 $u^2$ 上，取对数并除以 $2$，得到

$$
\sum_\phi b_\phi\log|\phi(u)|=0
\qquad(u\in\mathcal O_F^\times).
\tag{4}
$$

单位的范数绝对值为 $1$，给出 $\sum_\phi\log|\phi(u)|=0$。选 $\phi_0$ 使 $b_{\phi_0}$ 最小。由 Dirichlet 单位定理的对数格满秩结论，可取 $u$ 使除 $\phi_0$ 之外的每个 $\log|\phi(u)|$ 都严格为负。确切地说，在和为零的超平面中向 $\phi_0$ 坐标为 $r-1$、其余为 $-1$ 的方向走足够远，其中 $r=[F:\mathbb Q]$。对数格有紧基本域，故可以在有界距离内找格点。远处的格点保留这些严格符号。$r=1$ 时只有一个指数。用这个单位，将 (4) 减去 $b_{\phi_0}$ 乘范数等式。各项
$(b_\phi-b_{\phi_0})\log|\phi(u)|$ 都非正，和为零，所以凡 $\phi\ne\phi_0$ 都有 $b_\phi=b_{\phi_0}$。

写共同值为 $b$。令 $w=a-1-b$，(2) 就是 (1)。对任意 $z\in\Lambda_{\iota\sigma}$，共轭方向的对应项给

$$
\frac{a-1}{2}-(b-z)=w-\left(\frac{a-1}{2}-z\right).
$$

故 $H_{\sigma c}$ 由 $H_\sigma$ 逐项作这次反射得到。

## 源码对照

- `exists_isWeight` 先从不变配对和正则代数性导出 $b_\tau\in\mathbb Z$，再在实处选平方根的 idèle 取得 (3)，最后使用平行指数引理。[ExistsIsWeight.lean 第 25 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsIsWeight.lean#L25)
- `infChar_conjEmbedding_neg_of_invariant_pairing` 给 (2) 所需的对偶公式。[InfCharConjEmbeddingNegOfInvariantPairingStatement.lean 第 15 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/InfCharConjEmbeddingNegOfInvariantPairingStatement.lean#L15)
- `heckeChar_parallel_weight` 在全实域中推出 (4)，并用 Dirichlet 单位定理证明指数平行。[HeckeCharParallelWeight.lean 第 178 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/HeckeCharParallelWeight.lean#L178) · [第 234 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/BuildingsResidueChars/HeckeCharParallelWeight.lean#L234)
- `IsWeight` 的等式是 (1)，`PropsB.weights_conj` 将它与 $(a-1)/2-z$ 的归一化结合。[IsWeight.lean 第 21 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/IsWeight.lean#L21) · [WeightsConjBis.lean 第 62 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TypeConditions/WeightsConjBis.lean#L62)

这里按固定的发布版对读源码。已证明整数多重集的共轭关系，识别过滤跳点还使用[全局迹逼近与局部幂和](%E6%80%8E%E6%A0%B7%E6%B2%BF%E9%80%BC%E8%BF%91%E6%A0%BC%E5%A1%94%E4%BC%A0%E9%80%92%E7%AE%97%E5%AD%90%E7%9A%84%E5%B9%82%E5%92%8C.md)及几何输入。
