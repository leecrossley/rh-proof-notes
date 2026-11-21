# Good Hecke multiplicities are bounded by local rank

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A5%BDHecke%E7%82%B9%E7%9A%84%E9%87%8D%E6%95%B0%E5%92%8C%E4%B8%8D%E8%B6%85%E8%BF%87%E5%B1%80%E9%83%A8%E7%A7%A9.md)

## Statement

Fix row data $D$ and size data $L$. At a layer $1\le j\le m$, let the finite-dimensional complex automorphic form space split as $M_j=\bigoplus_\sigma S_\sigma$ into row isotypic spaces. At a finite place $w$ with nontrivial twist, let $I(j,w)$ index the records at that layer and place. Each has good eigenpoints $Z_i^{\rm good}$ with multiplicities $m(i,\pi)\ge0$, and a set $B_i$ of good row labels occurring there. Assume:

1. For nonempty $Z_i^{\rm good}$, $\sum_{\pi\in Z_i^{\rm good}}m(i,\pi)=\dim_\mathbb C\sum_{\sigma\in B_i}S_\sigma$, as in `ConclusionZ` with `HG` from a good point.
2. Each good row label belongs to at most one $B_i$ for fixed $j,w$, by `LocalisationUniqueness`.
3. For the common twist $\mu_w$, there are comparison maps $A=\theta^T_{\mu_w,j}:M_j\to M_{\mu_w,j}$ and $B=\theta_{\mu_w,j}$ back. If $I(j,w)$ is nonempty, $BA$ acts on each nonzero $S_\sigma$ by a scalar $\lambda_\sigma>0$, by `Conclusion42`.

Then
$$
\sum_{i\in I(j,w)}\sum_{\pi\in Z_i^{\rm good}}m(i,\pi)
\le\dim_\mathbb C\operatorname{im} A=L.\mathrm{zeroSpaceRankAtPlace}(j,w).
$$
This for all $j,w$ is `MultLe L`.

## Proof

If there are no records the left sum is zero. Otherwise take the scalar condition from any one record since $A,B$ depend only on $j,w$. If $Af=0$, write $f=\sum_\sigma f_\sigma$. Then $BAf=\sum_\sigma\lambda_\sigma f_\sigma=0$ makes each $f_\sigma=0$, so $\dim\operatorname{im}A=\dim M_j$. For each record the multiplicity sum equals $\sum_{\sigma\in B_i}\dim S_\sigma$ if its good set is nonempty, and is at most that expression otherwise. Across records, disjointness counts each dimension at most once. This gives the bound by $\dim M_j$.

The window's `adm3` identifies the local rank with the reference rank $d_j$, providing a common factor in the [cut error](summing-the-local-cost-of-cutting-hecke-characters.md). If each layer has a record and $\dim M_j=D_0$, injectivity at that record and `adm3` also give $d_j=D_0$.

## Lean correspondence

- [`Conclusion42`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/SumRepresentations.lean#L167), [`ConclusionZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/SumRepresentations.lean#L277) and [`LocalisationUniqueness`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JointConditionsZpowers/CommutingEndomorphismCondition.lean#L22) give the inputs.
- [`injective_of_scalars`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/NandDIVa.lean#L10) and [`theta_injective_of_scalars` and `family_rank_eq_of_scalars`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/NandDIVb.lean#L38) prove injectivity and the rank comparison.
- [`dM_eq_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProof.lean#L31), [`multLe_of_rank`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProof.lean#L70) and [`goodPointMultiplicityLeRank_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GoodPointMultiplicityLeRankProofStatement.lean#L13) give the count and the entry point.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
