# 怎样把同一个野惯性元和同余数据送给任意 Hecke 表示族

## 命题

固定工程数据 $N$ 和其中一个局部指标 $i$。记 $X=N.X(i)$ 为有限的评价点集，$Z=N.Z(i)\subseteq X$ 为指定好点集，$O=N.O(i)$ 为系数离散赋值环，$k={\rm Frac}(O)$，$\ell=N.l(i)$，$G={\rm Gal}(\Omega/E)$。Hecke 函数环 $T=N.T(i)$ 是 $O^X$ 的 $O$-子代数。固定 $t$ 个分块分解中出现的一维特征 $\chi_1,\ldots,\chi_t:G\to O^\times$，总维数为 $n$，其余块维数为 $r=n-t$。

采用工程的 Chebotarev 输入。设存在两族整表示 $r_{0,x}:G\to{\rm GL}_n(O)$、$\rho_{0,x}:G\to{\rm GL}_r(O)$，满足 `GoodR` 和 `TakenWild`。前者是说 $r_{0,x}$ 对每个 $x$ 连续，在 $k$ 上半单，而且在工程指定的分裂外素处，其 Frobenius 的特征多项式等于该点的 Hecke 多项式。后者的具体内容在下一节。

则对任意另一族满足 `GoodR` 的整表示 $r_x$，任意一族 $\rho_x:G\to{\rm GL}_r(O)$，以及任意 $\pi\in Z$，只要在 $\pi$ 有分式域上的分解

$$
r_\pi \simeq \rho_\pi\oplus\chi_1\oplus\cdots\oplus\chi_t,
$$

就有工程所需的 `GoodCongruenceObjects`，其中选出的 $g_0$ 满足下列惯性条件。它在至少一个 $\ell$ 上方处属于惯性群，其分圆特征为 $1+\ell^{s_0}u$，其中 $s_0=N.s0(i)$，$u\in\mathbb Z_\ell^\times$。若 $\ell$ 等于数据指定的两个素数之一，则在所有它属于惯性的 $\ell$ 上方处，它进一步属于野惯性。迁移同余对象时可以保留初始族对 $\pi$ 选出的同一个 $g_0$。[DataN.lean:1223](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DataN.lean#L1223) · [IsWildInertiaCyclotomicElement.lean:85](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/IsWildInertiaCyclotomicElement.lean#L85) · [ResidualConstruction.lean:82](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/NonGaloisCusps/ResidualConstruction.lean#L82)

## 初始族已经具备什么

`TakenWild` 要求一个有限于 $\mathbb Z_\ell$ 的离散赋值环 $A$，有相容的嵌入 $A\hookrightarrow O$。原表示族在 $A$ 上有模型 $r_A,\rho_A,\chi_A$，分别在全体点、好点、指定字符上扩标量为 $r_0,\rho_0,\chi$。有 $A$-函数环 $T_A\subset A^X$，它的像在 $O$ 上张成 $T$。环 $T_A$ 是局部环，能区分不同评价点。每个 $r_{A,x}$ 在分式域上是互异绝对不可约表示的直和，所有群元素的特征多项式系数是 $T_A$ 中的函数。各点剩余特征多项式相同。好点有上面的字符分解，且好点的补块在模极大理想后仍绝对不可约。

此外对每个 $\pi\in Z$ 已选好 $g_0,L,e_B,e_1,X_0$。前两个矩阵 $e_B,e_1$ 是在 $T_A$ 与群作用生成的矩阵环里的正交幂等元。在 $\pi$ 处，$e_B$ 投到字符块，$e_1$ 投到补块中的一条直线。若 $\varpi_A$ 是 $A$ 的统一化元，则

$$
X_0=e_Br_A(g_0)e_B+\varpi_A^L S_\pi,
$$

其中 $S_\pi$ 是同余模中的角块修正，在 $\pi$ 取零。对每个 $x\in X$，$X_0(x)$ 的角块多项式具有 $t$ 个互异根，并在 $k$ 上分裂。角块多项式是 $\det(Y e_B-X_0+I-e_B)$；因为首一且系数在 $O$，其属于 $k$ 的根也在 $O$。这是利用一个原来较小的系数环控制修正项，同时在终点系数环中取得全部根的条件。[IsWildInertiaCyclotomicElement.lean:89](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/IsWildInertiaCyclotomicElement.lean#L89) · [ResidualConstruction.lean:48](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/NonGaloisCusps/ResidualConstruction.lean#L48) · [同文件:60](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/NonGaloisCusps/ResidualConstruction.lean#L60) · [同文件:87](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/NonGaloisCusps/ResidualConstruction.lean#L87)

## 证明

先在原族的 $\pi$ 处使用上述选择。将根排序组成有限覆空间，在覆空间上加入各根函数，并在指定覆点按分解读取补块。这样得到完整的同余对象；它提供一般行列式系数及分块行列式的整性，在指定覆点取补块的映射也满射。根差积控制字符块上谱投影的分母。所得结构中的 $g_0$ 就是初始选出的那个。这个构造的主要步骤已在[根排序与下降](%E6%80%8E%E6%A0%B7%E6%8E%92%E5%BA%8F%E5%90%84%E7%82%B9%E7%9A%84%E6%A0%B9%E5%B9%B6%E6%8A%8A%E5%87%BD%E6%95%B0%E4%B8%8B%E9%99%8D%E5%88%B0%E5%8E%9FHecke%E7%8E%AF.md)、[行列式的整性](%E6%80%8E%E6%A0%B7%E5%9C%A8%E4%B8%8D%E9%99%A4%E4%BB%A5%E6%95%B4%E6%95%B0%E6%97%B6%E6%8A%8A%E7%9F%A9%E9%98%B5%E8%A1%8C%E5%88%97%E5%BC%8F%E7%95%99%E5%9C%A8Hecke%E7%8E%AF.md)和[好点处的规范化块环](%E6%80%8E%E6%A0%B7%E5%9C%A8%E5%A5%BD%E7%82%B9%E6%8D%A2%E5%9F%BA%E5%B9%B6%E6%9E%84%E9%80%A0%E8%A7%84%E8%8C%83%E5%8C%96%E5%9D%97%E7%8E%AF.md)中各自展开。[CharacterValuesInjectiveLength.lean:225](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CharacterValuesInjectiveLength.lean#L225) · [同文件:325](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CharacterValuesInjectiveLength.lean#L325)

现在令 $x$ 任取于 $X$。两族在该点读同一套 Frobenius 特征多项式。由 Chebotarev 与半单表示的迹判别，有 $P_x\in{\rm GL}_n(k)$ 将旧表示逐群元素送到新表示。特别在好点 $\pi$ 可以用 $P_\pi$ 比较旧分解与新分解。两侧共有 $\chi_1\oplus\cdots\oplus\chi_t$，消去这些直和因子，得补块上的共轭 $Q\in{\rm GL}_r(k)$。这里用到的只是好点的分解，对其他点的 $\rho_x$ 无需这样的条件。[相同 Hecke 多项式怎样决定表示](%E4%B8%BA%E4%BB%80%E4%B9%88%E7%9B%B8%E5%90%8C%E7%9A%84Hecke%E5%A4%9A%E9%A1%B9%E5%BC%8F%E5%86%B3%E5%AE%9A%E5%8D%8A%E5%8D%95Galois%E8%A1%A8%E7%A4%BA.md) · [直和消去](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%A0%E6%8E%89%E5%90%8C%E4%B8%80%E6%89%B9%E5%AD%97%E7%AC%A6%E5%90%8E%E4%B8%A4%E4%B8%AA%E8%A1%A5%E8%A1%A8%E7%A4%BA%E4%BB%8D%E7%AD%89%E4%BB%B7.md)

最后把每个矩阵函数用 $P_x$ 按点共轭，按原来那组整系数及群元素重新展开，因此仍处于新族的整张成。用对角分块共轭检验行列式，在好点用 $Q$ 共轭检验取补块的满射。角块的多项式不变，故整根代数、指定覆点和根差积都可以沿用。其余定义条件由这些变换逐项保留。这就把旧结构转成新结构。原来的 $g_0$ 本身在 $G$ 中没有改变，所以各处的惯性和分圆取值条件仍成立。[按点共轭怎样保留整性](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%8C%89%E7%82%B9%E5%85%B1%E8%BD%AD%E4%BB%8D%E8%83%BD%E4%BF%9D%E7%95%99Hecke%E5%90%8C%E4%BD%99%E5%AF%B9%E8%B1%A1%E7%9A%84%E6%95%B4%E6%80%A7.md)

## 在整体格指数中的位置

整体格指数估计要对随后由局部条件指定的表示族使用，不能假定所用的表示族恰好就是起初造整角块时选出的族。这条定理解除选择之间的耦合。它还保留同一个 $g_0$，所以后续计算分圆特征差、取惯性及构造上同调限制时，可以用同一个群元素计算。[整体格指数贯通稿](%E6%95%B4%E4%BD%93%E6%A0%BC%E6%8C%87%E6%95%B0%E6%80%8E%E6%A0%B7%E4%BB%8E%E5%88%97%E5%85%B3%E7%B3%BB%E4%B8%8E%E4%B8%89%E7%B1%BB%E4%B8%8A%E5%90%8C%E8%B0%83%E6%8E%A8%E5%87%BA.md)

## Lean 对照

- `GlobalTheory.ConsEveryFamilyWild.main` 从 `TakenWild` 解包 $A,T_A$ 和初始选择，再按点共轭并消去字符。最后由 $g_0$ 相等传回惯性条件。[ExistsGlobalObjectsEveryFamilyWild.lean:15](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsGlobalObjectsEveryFamilyWild.lean#L15)
- `GoodCongruenceObjects` 包含幂等元及角块、根代数、根差关系、取补块满射及行列式条件。[QuotientHomNonvanishingBound.lean:473](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/QuotientHomNonvanishingBound.lean#L473)

状态为源码对读。另行未重新编译。初始族满足 `TakenWild` 是这条定理的数学前提。它在更上游由选择足够大的系数环取得。[SideEigenHeckeMatch.lean:19](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SideEigenHeckeMatch.lean#L19)
