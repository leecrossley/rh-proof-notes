# 怎样从逐行局部估计取得原族的 LinkN

## 命题

固定项目的一族 `FamP eps`。它以实数 $x$ 为尺度，每个 $x$ 有一组行指标 $i\in I(x)$。一行带有数域、局部 Hecke 数据、整数格与层数 $m$，合记为 $D_{x,i}$。族同时给这一行的大小数据 $L_{x,i}$ 和整除比较所用的参数 $P_{x,i}$。有一个族阈值 $x_1$，在 $x>x_1$ 时有配套的范数参数 ${\rm nch}_{x,i}$。

本篇翻译 `linkN_of_twGood_galoisPreconditions`。它假设以下四项。

1. 有 `GlobalTheory.NLink.Hypotheses₂` 的全部七项局部及整体输入。它们是 Fontaine 的晶体比较、整体 Artin 互反、Bloch–Kato 局部比较、局部 Tate 对偶、局部 Euler 特征、局部有限性与 Bhatt–Scholze 整比较。
2. 有 `CutGivesAlt`。对于任意单行 $D$ 及其范数参数 ${\rm nch}$，如果这行具备 `GaloisPreconditions` 和 `Tie4`，则可选一个好 Hecke 截取 $c$。好截取保留全部要计数的好点，并且 ${\rm cut}(D,c)$ 在传去的范数参数下具有 `NormChoiceFacts` 和 `Tie4`。
3. 原族满足 `TwGood`。含义是存在统一的实阈值，使在其后且 $x>x_1$ 时，每行的扭曲数据有共轭配对，并有截断指标和有限展开支撑使 `TwGoodAt` 成立。
4. 对任意 $x>x_1$、$i\in I(x)$，原行 $(D_{x,i},{\rm nch}_{x,i})$ 满足 `GaloisPreconditions`，且 $D_{x,i}$ 满足 `Tie4`。前者是比较用的范数、好点、秩与局部表示数据，后者把局部 Hecke 特征、类型多项式及表示比较联系起来。

结论是 `LinkN`。也就是说，存在实常数 $C_*,x_*$，对任意 $x\ge x_*$、每行 $i\in I(x)$ 及每层 $1\le j\le m$，在该行 `ShaFinOdd` 成立且 $V(\ell)$ 可求和时，

$$
\eta_{\rm sum}(j)
\ \le\
d_j\left(C_*\bigl(fm\,b L^2+(\log x)^2 N_c\bigr)+\sum_{\ell}V(\ell)\right),
\qquad L=x^\varepsilon,\quad b=e^L .
\tag{1}
$$

其中 $f$ 是数域次数参数，$d_j$ 是这一层的基准秩，$N_c$ 是源自格参数的非负预算。左边是各扭曲处的局部长度乘归一化对数素数权之和。若 $\ell$ 为素数，$V(\ell)=\log\ell\sum_{1\le e<t}{\rm shaLen}(\ell,e)$，合成该素数和有限多个扭曲指标上的上同调长度。非素数项为零。该条件断言有限长度，可求和性另为 (1) 的前提。

## 证明

**选择整族的截取。** 对 $x>x_1$ 的每行，用第 2、4 项选择一个好截取 $c_{x,i}$。在 $x\le x_1$ 处可令 $c_{x,i}$ 保留全部，以便同一族的定义在所有 $x$ 上有效。用 $c_{x,i}$ 替换该行的 Hecke 数据，沿着替换传递 $L_{x,i}$、$P_{x,i}$ 等结构，得到新族 $F'$，仍保持原参数 $x$ 和指标 $i$。第 3 项由 `twGood_gd` 传给 $F'$。好截取的实际构造及它的整系数算子已分别展开。[截取的选择](%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%AD%E5%BF%83%E5%B9%82%E7%AD%89%E5%85%83%E9%80%89%E5%87%BA%E5%8F%AF%E6%AF%94%E8%BE%83%E7%9A%84Hecke%E5%88%86%E9%87%8F.md) · [整系数算子](%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E9%99%90%E7%BE%A4%E7%9A%84%E9%98%B6%E8%83%BD%E6%B8%85%E6%8E%89%E4%B8%AD%E5%BF%83%E6%8A%95%E5%BD%B1%E7%9A%84%E5%88%86%E6%AF%8D.md)

**把证据固定在同一行。** `exists_const_tieChi_bound_of_facts` 使用第一项，先选出独立于 $x,i$ 的 $C\ge0$ 和整数 $C_T\ge0$。对每个 $x>x_1$ 的截取行，用该行的 `NormChoiceFacts` 和 `Tie4`，得到交换算子条件及常数 $C,C_T$ 的配对特征界。换言之，截取族 $F'$ 有 `FactsFAlt`。富有内容的是这些局部条件的供给，常数的提取可以在选定任何一行之前完成。

另用 `at23_family_alt` 得截取族在 $2$，以及不在指定小素数集内的 $3$ 处的局部整除比较。它由 $2$ 处和 $3$ 处各自的局部界导出，并有统一常数 $C_a$、阈值 $x_a$。具体地，给定该行的局部比较所需周期对象和一个合用的表示族 $X$，每个所涉扭曲局部指标 $k$、好点 $\pi$ 有

$$
v_{k,\pi}\le s_{k,\pi}+\operatorname{midF}(C_a)+{\rm VV}(\ell)+v_\ell(h_E)+\epsilon_\ell .
\tag{2}
$$

这里 $v_{k,\pi}$ 是该好点的目标赋值，$s_{k,\pi}$ 是伽罗瓦表示的基准项，${\rm VV}(\ell)$ 为有限上同调长度之和，$h_E$ 为数域类数。函数

$$
\operatorname{midF}(A)=A\,fm\,b\log x+A x^A L^2 .
$$

其他指定小素数（排除 $2$）的对应估计由 `starSF_of_prints` 给 $C_b,x_b$。统一取 $C_{23}=\max(0,C_a,C_b)$ 及 $x_{23}=\max(1,x_a,x_b)$。因 $x>1$，在 $A\le C_{23}$ 时 $\operatorname{midF}(A)\le\operatorname{midF}(C_{23})$。正的 $A$ 可逐因子比较，若 $A<0$ 则两项非正。这就把两套估计合成一份。可用一张简表记录该合成局部界，细长度栏置零，把整个 $\operatorname{midF}(C_{23})$ 记入同一误差栏。

**选一个同时管住各项的常数。** `NLinkClose.main_alt_alt` 的组装如下。局部比较与对偶定理给 $C_0$，置 $C_2=\max(1,C_0)$。参数族的多项式界给 $C_1\ge1$，另有定位分歧素数的常数 $C_G$。选择

$$
C_s=\max\{3C_2+1,\ 22365,\ C_G,\ 2000(C+1)+5C_1,\ C_1,\ C_{23},\ C_T\}.
\tag{3}
$$

阈值取七个统一阈值的最大值。这七个分别使比较数据的存在性、例外素数的个数与大小界、特殊素数上界、大素数同余界、联合局部条件、参数界和 (2) 有效。

现取任何超过阈值的 $x$ 和该 $x$ 的任意一行 $i$，假定该行的上同调有有限长度。先用例外素数定理在这行选例外集，再用比较数据的存在性构造同一个 $X$，它包含本行的比较表示、局部长度项、误差和例外集。各局部估计都对这个 $X$ 使用。一般中等素数的误差来自联合局部条件，大而非例外的素数有同余比较，小素数使用已经合并的 (2)，两处指定分歧素数使用由 $C_G$ 控制的局部定理，生成元处的类型误差由配对特征和重数估计共同控制。另用 [好点的重数界](%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A5%BDHecke%E7%82%B9%E7%9A%84%E9%87%8D%E6%95%B0%E5%92%8C%E4%B8%8D%E8%B6%85%E8%BF%87%E5%B1%80%E9%83%A8%E7%A7%A9.md)，保证从逐好点估计转为逐处长度时可提出基准秩。已有参数界和可比较性是这一组估计的独立条件。

取 (3) 的理由是这些估计随所用的上界常数单调。因此所有条款可同时对 $X,C_s$ 成立。源码将它们写成 `Concl` 的十五个字段。它包括常数非负、从好点到局部长度的比较、重数上界、秩等式、消去条件、普通局部数值界、中等素数比较及误差、大素数比较、例外集界、小素数比较、指定分歧素数比较、生成元处类型界、参数界及特殊素数位置界。得到了存在统一 $C_s,x_0$，使每个 $x\ge x_0$ 且 $x>x_1$ 的每个合用行有这样的 $X$，即 `ConclF`。

**先由截取族得到整体界，再传回原族。** `LinkFam.main` 将每个 $X$ 的局部估计写成一张 `AdmT` 表，以同一个 $C_s$ 对 $F'$ 的每行使用。对各有理素数求和的证明给出 (1) 在 $F'$ 上的版本。[各类素数的求和与吸收](%E6%8A%8A%E5%90%84%E7%B1%BB%E7%B4%A0%E6%95%B0%E7%9A%84%E5%B1%80%E9%83%A8%E9%95%BF%E5%BA%A6%E5%8A%A0%E8%B5%B7%E6%9D%A5%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%8D%E5%9C%A8%E7%AA%97%E5%8F%A3%E5%86%85.md)。最后回到原族。每个局部格的截取误差受有限群阶赋值控制，逐处加权后不超过 $d_j\log A$，其中 $A$ 是该行截取所用的有限群阶。原行的好点重数界及秩等式由第 4 项提供。全族的参数界给统一 $C_1$，使 $\log A\le C_1 x^{C_1}L$。对充分大的 $x$，$x^{C_1}\le b$ 且 $L\ge1$，所以 $d_j\log A$ 只增加 (1) 中的 $C_*$，保留上同调项系数 $1$。各截取行的尺度、层与原行对应，故得到原族的 (1)。[截取误差的完整证明](%E6%88%AA%E5%8F%96%E4%BA%A7%E7%94%9F%E7%9A%84%E5%B1%80%E9%83%A8%E8%AF%AF%E5%B7%AE%E6%80%8E%E6%A0%B7%E5%90%88%E6%88%90%E6%95%B4%E4%BD%93%E7%95%8C.md)

## 源码对照

- `linkN_of_twGood_galoisPreconditions` 逐行截取、组装截取族的 `LinkN`，再调用 `linkN_of_gd` 返回原族。[LinkNFam.lean 第 37 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkNFam.lean#L37) · [LinkNOfGd.lean 第 38 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/LinkNOfGd.lean#L38)
- `NLinkClose.main_alt_alt` 构造 (3)，选择同时使用的比较数据。`Concl` 与 `ConclF` 给每行及全族的完整字段。[ImportsFurtherTail.lean 第 22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ImportsFurtherTail.lean#L22) · [BoundAtTwoThreeFamily.lean 第 124 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/BoundAtTwoThreeFamily.lean#L124) · [第 141 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/BoundAtTwoThreeFamily.lean#L141)
- `Hypotheses₂` 的七项输入及 `at23_family_alt` 的两个局部界入口。好截取在下一级的实际供应 `exists_good_cut_facts_tie4` 明列 Chebotarev、局部有限性、Tate 对偶和 Euler 特征输入。[BoundAtTwoAndThreeForFamily.lean 第 18 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/BoundAtTwoAndThreeForFamily.lean#L18) · [At23OfAll.lean 第 19 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/At23OfAll.lean#L19) · [CFacts.lean 第 58 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/CFacts.lean#L58)
- `LinkFam.main` 将逐行估计送入表格与求和，`LinkN` 的结论是 (1)。[LinkNAlongFamilyOfLocalBounds.lean 第 11 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LinkNAlongFamilyOfLocalBounds.lean#L11) · [GlobalTheoremInputs.lean 第 40 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean#L40)

以上为源码对读。各素数比较定理和表示供应是本篇明列的输入。由 (1) 接续[窗口中的上同调长度怎样进入整除式](%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%B1%80%E9%83%A8%E6%95%B4%E9%99%A4%E6%8D%9F%E5%A4%B1.md)，才得到下一步计数使用的整除下界。
