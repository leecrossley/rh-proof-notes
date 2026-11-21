# 为什么好 Hecke 点的重数和不超过局部秩

## 命题

固定工程的一行数据 $D$ 和对应的尺度数据 $L$。对 $1\le j\le m$，令 $M_j$ 为该层的有限维复自守形式空间，$S_\sigma$ 为由行标签 $\sigma$ 标记的等型子空间。设它们给出内部直和 $M_j=\bigoplus_\sigma S_\sigma$。固定工程中扭曲非平凡的有限处 $w$。以 $I(j,w)$ 表示所有同时处于层 $j$ 和处 $w$ 的局部记录。每条记录 $i$ 给出有限的好 Hecke 点集 $Z_i^{\rm good}$、各点的非负整数重数 $m(i,\pi)$，以及好行标签集

$$
B_i=\{\sigma:\sigma\text{ 是好行标签，且 }\sigma\text{ 在记录 }i\text{ 上出现}\}.
$$

假定以下条件。

1. 对每个 $i\in I(j,w)$，若 $Z_i^{\rm good}\ne\varnothing$，则 $\sum_{\pi\in Z_i^{\rm good}}m(i,\pi)=\dim_\mathbb C\sum_{\sigma\in B_i}S_\sigma$。这是 `ConclusionZ` 用到的重数等式，Lean 先由一个好点取得其前提 `HG`。
2. 对每个好行标签 $\sigma$，至多一个 $i\in I(j,w)$ 满足 $\sigma\in B_i$。这是 `LocalisationUniqueness`。
3. 设 $\mu_w$ 是 $w$ 所指定的扭曲标签，$A=\theta^T_{\mu_w,j}:M_j\to M_{\mu_w,j}$ 是正向的比较映射，$B=\theta_{\mu_w,j}$ 是反向映射。若 $I(j,w)\ne\varnothing$，每个非零 $S_\sigma$ 上的 $BA$ 为乘以某个 $\lambda_\sigma>0$。这是 `Conclusion42` 的标量条件。相同层、处的记录使用相同的 $\mu_w$。

则

$$
\sum_{i\in I(j,w)}\sum_{\pi\in Z_i^{\rm good}}m(i,\pi)
\ \le\ \dim_{\mathbb C}\operatorname{im}\theta^T_{\mu_w,j}
=L.\mathrm{zeroSpaceRankAtPlace}(j,w).
$$

这个不等式对所有 $j,w$ 同时成立，就是 `MultLe L`。它控制把各局部 Hecke 分量截下来时，误差中的赋值最多需要按多大重数来计。

## 证明

若 $I(j,w)$ 为空，左端为零。否则，任取 $i_0\in I(j,w)$。它的标量条件便适用于从 $M_j$ 到 $M_{\mu_w,j}$ 的映射 $A$。分解 $f=\sum_\sigma f_\sigma$，其中 $f_\sigma\in S_\sigma$。若 $Af=0$，则 $BAf=\sum_\sigma\lambda_\sigma f_\sigma=0$。直和分解的唯一性给每项 $\lambda_\sigma f_\sigma=0$，故 $f=0$。因此 $A$ 单射，$\dim\operatorname{im} A=\dim M_j$。

任取记录 $i$。有好点时，由第一项假设和直和分解得到

$$
\sum_{\pi\in Z_i^{\rm good}}m(i,\pi)
=\sum_{\sigma\in B_i}\dim S_\sigma .
$$

没有好点时左端为零，仍有相同方向的不等式。由第二项假设，各 $B_i$ 两两不交，故再对 $i$ 求和时，每个 $S_\sigma$ 的维数只计至多一次。于是左端至多为 $\dim M_j$，结合单射给所求上界。也可直接写成 $\dim\sum_{\sigma\in\bigcup_i B_i}S_\sigma\le\dim M_j$。

窗口使用的 `adm3` 进一步把这个局部秩识别为原行的基准秩 $d_j$，所以在每个 $w$ 都可用同一个 $d_j$ 作为 [截取误差](%E6%88%AA%E5%8F%96%E4%BA%A7%E7%94%9F%E7%9A%84%E5%B1%80%E9%83%A8%E8%AF%AF%E5%B7%AE%E6%80%8E%E6%A0%B7%E5%90%88%E6%88%90%E6%95%B4%E4%BD%93%E7%95%8C.md) 的系数。若还知道 $\dim M_j=D_0$，并且每层至少有一条当地记录，就可以在该记录所在的 $w$ 重用单射，再由 `adm3` 得 $d_j=D_0$。这就是同一证明被用于小层秩等式的方式。

## Lean 对照

- `Conclusion42` 与 `ConclusionZ` 的局部条件分别在 [`SumRepresentations.lean` 第 167 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/SumRepresentations.lean#L167) 和 [第 277 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/SumRepresentations.lean#L277)。`LocalisationUniqueness` 在 [`CommutingEndomorphismCondition.lean` 第 22 行](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JointConditionsZpowers/CommutingEndomorphismCondition.lean#L22)。
- [`injective_of_scalars`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/NandDIVa.lean#L10) [`injective_of_scalars`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/NandDIVa.lean#L10) 证明抽象单射。[`theta_injective_of_scalars`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/NandDIVb.lean#L38) [`theta_injective_of_scalars`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/NandDIVb.lean#L38) 用到给定的 $\theta^T$，同文件的 `family_rank_eq_of_scalars` 得小层秩等式。
- [`dM_eq_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProof.lean#L31) [`dM_eq_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProof.lean#L31) 把好行空间拆成维数和。[`multLe_of_rank`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProof.lean#L70) [`multLe_of_rank`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProof.lean#L70) 合成重数界。[`goodPointMultiplicityLeRank_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProofStatement.lean#L13) [主线入口](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProofStatement.lean#L13) 调用后者。本篇为源码对读。
