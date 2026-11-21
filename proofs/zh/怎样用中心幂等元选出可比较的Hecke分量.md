# 怎样用中心幂等元选出可比较的 Hecke 分量

## 命题

固定一行数据 $D$、其中归一化所选的扭曲数据 $n$，假定 `GaloisPreconditions D n` 和 `Tie4 D`。这是 `exists_good_alt` 中的点条件和自守相容条件。给定第 $i$ 条局部记录，以 $O_i$ 为系数整数环、$K_i$ 为分式域、$M_i$ 为带 Hecke 代数作用的格、$X_i$ 为工程的有限本征特征集。$Z_i\subseteq X_i$ 是具有指定自守分解的点，$Z_i^{\mathrm{good}}\subseteq Z_i$ 是其中通过两处惯性类型检验的点。令 $A\ge1$ 为 `restRowsFiniteGroupCard` 给出的有限群的阶。再假定下节明列的中心元输入。则可为每个 $i$ 选取集合 $X'_i\subseteq X_i$，并仅保留 $Z_i^{\rm good}\ne\varnothing$ 的记录，使得

1. $X'_i$ 包含 $Z_i^{\rm good}$，且 $X'_i\cap Z_i=Z_i^{\rm good}$。
2. 对每条保留的记录，有一个与 Hecke 作用交换的 $O_i$-线性 $\alpha_i$ 作用在 $M_i$ 上。扩到 $K_i$ 后，它在 $Z_i^{\rm good}$ 的本征空间上乘以 $A$，在所有 $x\notin X'_i$ 的本征空间上为零。
3. 对每条保留记录中属于 $X'_i$ 的点，任何对应的自守表示在宿主两个指定素数的上方各处均满足 `Nc` 类型条件。

第 3 项中的 `Nc` 是 Weil–Deligne 参数的三个条件。对每个野惯性元素，特征多项式是 $(X-1)^r$，其中 $r$ 是参数的秩。单值算子为零。对任意温和惯性的生成元，如果其某个本征值的重数至少达到 $\operatorname{thr}(w,r)$，该本征值的 $(\#k_w-1)$ 次幂必须等于 $1$。这里 $k_w$ 是剩余域，阈值在底下的素数 $p$ 完全分裂且满足 $r=1$ 或 $16r^2<p$ 时为 $2$，其余情形为 $1$。下文把它的取得归结为局部类型判据。结论是 `CutD.Good`。这一步选出用于估计的截取对象，并给出 [截取比较所需的整数算子](%E6%88%AA%E5%8E%BB%E4%B8%80%E9%83%A8%E5%88%86%E7%89%B9%E5%BE%81%E4%B8%BA%E4%BD%95%E5%8F%AA%E6%8D%9F%E5%A4%B1%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md)。

## 从局部投影到整数算子

设 $\mathcal P$ 为两个指定素数上方各处的集合。每处 $v\in\mathcal P$ 有有限群类型按多项式标签 $s_v$ 分类。将属于同一标签的不可约类型的中心幂等元相加，得到 $e_{v,s_v}$。在全部这些有限群的乘积群代数中，各处作用交换。以 $\mathcal T$ 表示通过 `goodTuple` 检验的标签组合，良好类型的中心投影为

$$
e_0=\sum_{s\in\mathcal T}\prod_{v\in\mathcal P}e_{v,s_v}.
$$

`CentralElt` 给出的输入是：对每个组合 $s$，复群代数中的 $A\prod_v e_{v,s_v}$ 都来自一个 $O_i$-系数中心元 $z_{i,s}$。源码用首一多项式的低次系数向量列举标签，每个多项式恰出现一次。令 $z_i$ 为所有被选 $z_{i,s}$ 的和，则其扩系数后等于 $Ae_0$。由 `Tie4` 中所选的 `Pend` 数据，$z_i$ 在 Hecke 格上给出与 Hecke 代数交换的整系数映射 $\alpha_i$。`EigSpan` 比较同一个中心元在复自守形式空间和在 $K_i$ 的 Hecke 本征空间上的作用。如果它在点 $x$ 的全部对应复空间上乘以 $a\in O_i$，则扩到 $K_i$ 后在 $x$ 的本征空间上也乘以 $a$。后文用 $a=A,0$。

## 选取 $X'_i$ 并验证三个条件

对 $x\in X_i$，当且仅当存在对应的自守表示 $\Pi$ 和其中的形式 $F$ 使 $e_0F\ne0$ 时，将 $x$ 放入 $X'_i$。对属于 $Z_i$ 的点，`onMt_e0_eq_self_of_mem_zgood_and_eq_zero_of_notMem` 给出 $e_0F=F$ 或 $e_0F=0$，分别对应 $x\in Z_i^{\rm good}$ 或 $x\notin Z_i^{\rm good}$。这一判别所用的具体相容条件如下。点的自守分解在相同特征下只差排列。每个 $Z_i$ 点的分解可将其指定的一维扭曲项移到最后。其余分量决定一个局部参数组，`Pend` 允许为该组选择一个类型标签，并且 `SerLoc` 让局部的中心投影在对应类型空间上按标签作用。对一个好点，可用它的好分解见证，得到好标签，因而投影为恒等。反过来，若某 $Z_i$ 点的标签是好的，则该自守分解和标签本身构成 $Z_i^{\rm good}$ 的见证。故其余 $Z_i$ 点的投影为零。

在好点 $x$，满射 $ \Pi\mapsto x$ 给至少一个自守空间，且该空间含有非零形式。取这样的 $F$，有 $e_0F=F\ne0$，所以 $x\in X'_i$。若 $x\in Z_i\setminus Z_i^{\rm good}$，任何这种 $F$ 的投影都为零，所以 $x\notin X'_i$。因此第一项成立，且一条保留记录的 $X'_i$ 必非空。在好点上，$\alpha_i$ 通过 $z_i$ 对应 $Ae_0$，即乘以 $A$。在任何未进入 $X'_i$ 的点上，投影按定义对全部对应形式为零。用 `EigSpan` 把这两项送到 $K_i$ 的本征空间，得到第二项。

最后设 $x\in X'_i$，取 $\Pi,F$ 使 $e_0F\ne0$。和式中至少有一项 $\prod_v e_{v,s_v}F\ne0$，而且其每个因子 $e_{v,s_v}F$ 都非零。因每个因子是该标签下各中心幂等元之和，至少一个类型幂等元在 $F$ 上非零，故每处确有一个出现的类型，其多项式标签为 $s_v$。输入 `nc_of_type` 说：若一个自守表示的指定型空间在所有这些处都出现了同一个好标签组合的类型，则在这两个素数上方的每处，其局部参数满足 `Nc`。于是 $\Pi$ 满足要求。任意另一自守表示 $\Pi'$ 若给同一个 $x$，其自守分解与 $\Pi$ 的分解相差排列，相同分解给这些分裂处同样的局部参数，故 $\Pi'$ 也满足 `Nc`。

## Lean 对照

- [`CutD.Good` 的完整接口](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/RhoBar.lean#L46)。[`onMt_e0_eq_self_of_mem_zgood_and_eq_zero_of_notMem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/EigenActionAtGoodPoint.lean#L45) [好点上的中心投影判别](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/EigenActionAtGoodPoint.lean#L45)。
- [`exists_unit_one_add_generator`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/ExistsUnitOneAddGenerator.lean#L17) [中心元在格上的作用](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/ExistsUnitOneAddGenerator.lean#L17)，[`exists_tuple`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/ExistsUnitOneAddGenerator.lean#L58) [选非零投影项](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/ExistsUnitOneAddGenerator.lean#L58)，[`exists_type`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/ExistsUnitOneAddGenerator.lean#L99) [从标签取实际类型](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/ExistsUnitOneAddGenerator.lean#L99)。
- [`exists_good_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ExistsGood.lean#L15) [`exists_good_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ExistsGood.lean#L15) 使用上述证明。[`exists_good_cut_facts_tie4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/CFacts.lean#L58) [`exists_good_cut_facts_tie4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/CFacts.lean#L58) 供应 [中心元的整系数构造](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E9%99%90%E7%BE%A4%E7%9A%84%E9%98%B6%E8%83%BD%E6%B8%85%E6%8E%89%E4%B8%AD%E5%BF%83%E6%8A%95%E5%BD%B1%E7%9A%84%E5%88%86%E6%AF%8D.md)，并给截取后的数据所需的相容和归一化条件。见 [从多项式标签得到 `Nc`](%E6%9C%89%E9%99%90%E5%9F%9F%E7%9A%84%E7%B1%BB%E5%9E%8B%E6%A0%87%E7%AD%BE%E6%80%8E%E6%A0%B7%E7%BA%A6%E6%9D%9F%E6%B8%A9%E5%92%8C%E6%83%AF%E6%80%A7.md) 和 [`Nc` 定义](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TypeConditions/AutomorphicGaloisAdmissible.lean#L21)。本篇按源码对读。
