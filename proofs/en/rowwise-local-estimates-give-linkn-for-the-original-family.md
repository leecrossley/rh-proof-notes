# Rowwise local estimates give LinkN for the original family

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E9%80%90%E8%A1%8C%E5%B1%80%E9%83%A8%E4%BC%B0%E8%AE%A1%E5%8F%96%E5%BE%97%E5%8E%9F%E6%97%8F%E7%9A%84LinkN.md)

## Statement

Use a family `FamP eps` indexed by scale $x$, with rows $i\in I(x)$, row data $D_{x,i}$ (field, Hecke data, lattices and layers $m$), size data $L_{x,i}$, divisibility parameters $P_{x,i}$, and norm data $\mathrm{nch}_{x,i}$ for $x>x_1$. The theorem `linkN_of_twGood_galoisPreconditions` assumes:

1. `GlobalTheory.NLink.Hypotheses₂`, comprising Fontaine crystalline comparison, global Artin reciprocity, Bloch–Kato local comparison, local Tate duality, Euler characteristic, finiteness and Bhatt–Scholze integral comparison.
2. `CutGivesAlt`, that each row with `GaloisPreconditions` and `Tie4` admits a good cut retaining the good points and admitting `NormChoiceFacts` and `Tie4` for the transferred norm data.
3. `TwGood`, eventual conjugate pairing of the twists and appropriate cutoff and finite support giving `TwGoodAt` for each row above $x_1$.
4. Every original row above $x_1$ admits `GaloisPreconditions` (norm, good-point, rank and local representation data) and `Tie4` (local Hecke, type polynomial and representation compatibility).


Then `LinkN` holds. Some constants $C_*,x_*$ work for $x\ge x_*$ in every row and layer $1\le j\le m$ with `ShaFinOdd` and summable $V(\ell)$:
$$
\eta_{\rm sum}(j)\le d_j\left(C_*\big(fm\,bL^2+(\log x)^2N_c\big)+\sum_\ell V(\ell)\right),
\qquad L=x^\varepsilon,\quad b=\exp L .
\tag{1}
$$
Here $f$ is the field degree parameter, $d_j$ the reference rank, $N_c$ a nonnegative lattice budget and $\eta_{\rm sum}$ the sum of local lengths at twist places with normalized log-prime weights. For primes, $V(\ell)=\log\ell\sum_{1\le e<t}\mathrm{shaLen}(\ell,e)$, and it is zero otherwise. `ShaFinOdd` gives finite lengths and summability is a separate premise.


## The common cut family and its estimates

Cut every row above $x_1$ using assumptions 2 and 4, taking the full row below. Transfer sizes and comparison data to $F'$ with identical indices and scale. By `twGood_gd` it inherits `TwGood`. The argument `exists_const_tieChi_bound_of_facts` uses assumption 1 to choose $C\ge0$ and integer $C_T\ge0$ uniformly before choosing a row. The norm and `Tie4` facts on each cut give the commuting operators and paired-character comparisons with those constants, which is `FactsFAlt`.

For the row's period objects and an appropriate representation family $X$, `at23_family_alt` gives uniform constants $C_a,x_a$ for two and for three outside the specified small-prime set. The inequality at a good point $\pi$ of record $k$ is
$$
v_{k,\pi}\le s_{k,\pi}+\operatorname{midF}(C_a)+\mathrm{VV}(\ell)+v_\ell(h_E)+\epsilon_\ell,\qquad
\operatorname{midF}(A)=A\,fm\,b\log x+A x^A L^2.
\tag{2}
$$
Here $v$ is the target valuation, $s$ the Galois reference term, $\mathrm{VV}$ the finite cohomology length sum and $h_E$ the class number. Other specified small primes apart from two have the corresponding bound from `starSF_of_prints` with $C_b,x_b$. Set $C_{23}=\max(0,C_a,C_b)$ and $x_{23}=\max(1,x_a,x_b)$. For $x>1$ the two terms of $\operatorname{midF}$ increase with nonnegative $A$. Negative $A$ gives nonpositive terms. This makes (2) uniform, placing all of $\operatorname{midF}(C_{23})$ in the error slot of the local table with the finer length slot zero.


## One set of data for a row

In `NLinkClose.main_alt_alt`, the comparison and duality inputs give $C_0$ and $C_2=\max(1,C_0)$. Polynomial parameter bounds give $C_1\ge1$, and $C_G$ locates ramified primes. Set
$$
C_s=\max\{3C_2+1,\ 22365,\ C_G,\ 2000(C+1)+5C_1,\ C_1,\ C_{23},\ C_T\}.
\tag{3}
$$
Take the maximum of the seven thresholds for comparison data, exceptional-prime counts and sizes, special-prime bounds, large-prime congruences, joint local conditions, parameter bounds, and (2).

For a row above the thresholds with finite cohomology lengths, first choose its exceptional set. Then choose one $X$ with representations, lengths, errors and this set for the entire row. Joint conditions give the intermediate-prime errors, large nonexceptional primes use their congruence, small primes use (2), and the chosen ramified primes use the $C_G$ bound. At the generator place use the type bound from paired characters and multiplicities. The [good-point multiplicity bound](good-hecke-multiplicities-are-bounded-by-local-rank.md) lets the reference rank factor out of the local sum. Every bound uses the same $C_s$ by monotonicity. These are the fifteen `Concl` fields for each row, including separate rank, annihilation and parameter conditions. With uniform constants they give `ConclF`.

## Summing and removing the cut

The argument `LinkFam.main` turns each $X$ into a table `AdmT`. The [prime sum](../zh/%E6%8A%8A%E5%90%84%E7%B1%BB%E7%B4%A0%E6%95%B0%E7%9A%84%E5%B1%80%E9%83%A8%E9%95%BF%E5%BA%A6%E5%8A%A0%E8%B5%B7%E6%9D%A5%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%8D%E5%9C%A8%E7%AA%97%E5%8F%A3%E5%86%85.md) proves (1) for $F'$. The [integral cut operator](the-group-order-clears-central-projector-denominators.md) bounds truncation losses by the valuations of the finite group order $A$. Their weighted sum is at most $d_j\log A$ by the [cut comparison](../zh/%E6%88%AA%E5%8F%96%E4%BA%A7%E7%94%9F%E7%9A%84%E5%B1%80%E9%83%A8%E8%AF%AF%E5%B7%AE%E6%80%8E%E6%A0%B7%E5%90%88%E6%88%90%E6%95%B4%E4%BD%93%E7%95%8C.md), using the original row's ranks and multiplicities. The family parameter bound gives $\log A\le C_1x^{C_1}L$. Eventually $x^{C_1}\le b$ and $L\ge1$, so enlarge $C_*$ to absorb this cost, preserving coefficient one on cohomology. The two families have matching scales and layers. The result enters [divisibility from cohomology lengths](cohomology-and-divisibility-loss.md).

## Lean correspondence

- [`linkN_of_twGood_galoisPreconditions`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkNFam.lean#L37) uses the [cut selection](central-idempotents-select-comparable-hecke-summands.md), then [`linkN_of_gd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/LinkNOfGd.lean#L38) to return.
- [`NLinkClose.main_alt_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/ImportsFurtherTail.lean#L22) chooses the constants and common $X$. [`Concl` and `ConclF`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/BoundAtTwoThreeFamily.lean#L124) give all fields.
- [`Hypotheses₂`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/BoundAtTwoAndThreeForFamily.lean#L18), [`at23_family_alt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/At23OfAll.lean#L19) and [`exists_good_cut_facts_tie4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/CFacts.lean#L58) specify the comparison inputs, including Chebotarev and local duality for the cut supply.
- [`LinkFam.main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/LinkNAlongFamilyOfLocalBounds.lean#L11) sums, and [`LinkN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean#L40) states (1).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
