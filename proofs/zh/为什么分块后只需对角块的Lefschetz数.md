# 为什么分块后只需对角块的 Lefschetz 数

## 命题

设 $Z$ 为 $\mathbb C$ 上光滑射影纯 $d$ 维概形，$c_1,c_2:Y\to Z$ 为两个有限平展的 $\mathbb C$-态射。设 $F=\{y\in Y(\mathbb C):c_1(y)=c_2(y)\}$ 有限。对每个 $y\in F$，记 $z=c_1(y)=c_2(y)$，用 $A_y$ 表示 $d c_2(y)\circ d c_1(y)^{-1}:T_zZ\to T_zZ$ 的矩阵。假定 $\det(I-A_y)\ne0$。其中 `IsTan` 的坐标形式是，先在 $z$ 取 $d$ 个正则函数 $t_l$，使 $d(c_1^*t_l)(y)$ 成为余切空间的基，再用 $A_y$ 的第 $j$ 行记录 $d(c_2^*t_j)(y)$ 在此基下的系数。

固定任意整数 $a\ge0$。以 $H^{a,b}(Z)=H^b(Z,\Omega_Z^a)$ 表示代数 Hodge 上同调，$c_{1*}$ 为有限平展态射的迹，$c_2^*$ 为拉回。则各 $H^{a,b}(Z)$ 有限维，并有

$$
\sum_{b=0}^{d}(-1)^b\operatorname{tr}
\left(c_{1*}c_2^*:H^{a,b}(Z)\longrightarrow H^{a,b}(Z)\right)
=\sum_{y\in F}\frac{[T^a]\det(I+TA_y)}{\det(I-A_y)}.
$$

本节证明源码最后两层的归约，所用深层输入为：上述命题在 $Z,Y$ 均为整概形时成立。该输入保留相同的有限平展、射影、纯维数、固定点和行列式假设。它是 [`holomorphic_lefschetz_finiteEtale_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/HolomorphicLefschetzFiniteEtaleIntegral.lean#L74)。

## 证明

光滑概形的局部环是正则局部环，因此是整环。不同的不可约分支不能相交，否则交点的局部环会有多个极小素理想。准紧的光滑概形在这里为 Noether 概形，所以只有有限个不可约分支。因分支既闭又互不相交，每个又是开集，并且以约化结构成为整概形。把 $Z$ 写成这些开闭分支 $Z_j$ 的不交并。$Y$ 由有限平展于 $Z$ 而光滑，且有限于射影概形从而准紧，同样可作这种分解。

先令 $Y_{jk}=c_1^{-1}(Z_j)\cap c_2^{-1}(Z_k)$。它是 $Y$ 的开闭子概形，限制后的两个映射分别通到 $Z_j,Z_k$，且仍有限平展。开闭不交并上的微分形式以及其上同调均按分支直和分解。因此在 $H^{a,b}(Z)=\bigoplus_j H^{a,b}(Z_j)$ 下，算子 $c_{1*}c_2^*$ 的第 $j,k$ 块，恰由 $Y_{jk}$ 上拉回、再取迹给出。理由是，$c_2^*$ 将第 $k$ 个分支的类限制到 $Y_{jk}$，而 $c_{1*}$ 对落在同一 $Z_j$ 上的各片取迹后相加。这条加法可在每个仿射开集上的有限代数直积中验证：乘法算子分块对角，各块迹相加。上同调上的加法由此逐项传下去。

线性算子的迹等于对角块的迹之和，只需考虑 $Y_{jj}$ 上的对应。如果 $Y_{jj}$ 有多个整分支，再对来源作开闭分解，拉回后在每个分支取迹并相加。固定点必须满足两投影在同一个 $Z_j$，因此只出现在 $Y_{jj}$ 上，每个点随后属于唯一一个整分支。开集限制不改变该点的切空间或两个微分，所以其 $A_y$ 与行列式条件不变。

现在可对 $Z_j$ 和 $Y_{jj}$ 的每个整分支应用输入，逐个给出交错迹公式。将来源各片的公式相加，再将 $j$ 的公式相加，恰将左端合成全部上同调的交错迹，右端覆盖 $F$ 且每点只算一次。目标各分支的有限维性来自光滑射影上同调的有限维定理，故来源为空时同样适用上述相加。若 $a>d$，两边都由微分形式的次数和多项式次数给出零。

## Lean 对照

- [`IsTan` 的余切坐标定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Divisors/IsGaloisCover.lean#L14)。[光滑概形的有限整分支](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/ExistsIntegralClopenDecompositionOfSmooth.lean#L7)。
- [`holomorphic_lefschetz_finiteEtale_correspondence`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/HolomorphicLefschetzFiniteEtaleCorrespondence.lean#L43) 将来源拆成整分支。[`lefschetz_fixedPoint_finite_etale_correspondence`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/LefschetzFixedPointFiniteEtaleCorrespondence.lean#L255) 拆分目标并取迹的对角块。
- [`geoOne_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/GeometricFlagBases/WeightOneGeometricRealization.lean#L11) 为权一几何实现调用这条公式。本篇为发布版源码对读，整概形上的固定点公式是本篇明列的输入。
