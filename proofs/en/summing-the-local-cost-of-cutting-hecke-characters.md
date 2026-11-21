# Summing the local cost of cutting Hecke characters

[Chinese proof](../zh/%E6%88%AA%E5%8F%96%E4%BA%A7%E7%94%9F%E7%9A%84%E5%B1%80%E9%83%A8%E8%AF%AF%E5%B7%AE%E6%80%8E%E6%A0%B7%E5%90%88%E6%88%90%E6%95%B4%E4%BD%93%E7%95%8C.md)

## Statement and proof

Let $K$ be a number field of degree $F$, $W$ a finite set of finite places, and $p(w),e_w,f_w$ their residue characteristics, ramification indices and residue degrees. Set $\lambda_w=e_w f_w\log p(w)/F$. For an integer $A\ge1$, $d\ge0$ and two real families with $\eta_w\le\eta'_w+d\,v_{p(w)}(A)$ at each $w\in W$, we have
$$
\sum_{w\in W}\lambda_w\eta_w\le\sum_{w\in W}\lambda_w\eta'_w+d\log A.
$$
Indeed, for every $p$, $\sum_{w\mid p}e_w f_w=F$, as seen from the factorization of $p\mathcal O_K$ and the cardinality $p^F$ of $\mathcal O_K/p\mathcal O_K$. Thus the selected weights over $p$ sum to at most $\log p$. The total error after weighting is at most $d\sum_{p\mid A}v_p(A)\log p=d\log A$. This includes $A=1$.

## Use a common rank for the local bounds

In the project $W$ is the part of the finite lattice support with nontrivial twist. At layer $j$ the terms $\eta_w$ and $\eta'_w$ are sums of normalized lengths from the original and cut data, respectively. The cut keeps the Hecke characters for which the Galois comparison applies. At each retained block $i$ the comparison uses a scalar $A$, the order of a finite group associated with the other rows. At an omitted block `CutD.Good` guarantees there are no good characters and the corresponding quotient is zero. Summing over the blocks at $j,w$ gives
$$
\eta_w\le\eta'_w+M_{j,w}v_{p(w)}(A),\qquad
M_{j,w}=\sum_{i\text{ at }j,w}\sum_{\pi\text{ good at }i}\operatorname{mult}(i,\pi),
$$
where the multiplicity is the dimension of the character space. The input `MultLe` bounds $M_{j,w}$ by the local rank at level zero for this layer, which `TwistedPlaces.adm3` identifies with $d_j=L.\mathrm{dZ0}(j)$. Thus the statement with $d=d_j$ gives $\mathrm{etaSum}(j)\le\mathrm{etaSum}'(j)+d_j\log A$. [The local comparison](the-valuation-cost-of-cutting-hecke-characters.md)

## Return the bound to the original family

Fix $\varepsilon>0$ and put $L=x^\varepsilon$, $b=e^L$ at scale $x$. Let $N_c$ be the nonnegative contribution from the other parameters and write $F(x)=fm bL^2+(\log x)^2N_c$, where $f,m$ are the positive degree and layer parameters for the row. The cut family `gd Fm c` changes only the local Hecke data. Its relevant ranks, scales, weights and cohomology terms agree with those of the original family.

Suppose the cut family satisfies `LinkN`. Thus for uniform $C,x_0$, every row with $x\ge x_0$ and $1\le j\le m$ satisfies, under `ShaFinOdd` and summability of the prime terms,
$$
\mathrm{etaSum}'(j)\le d_j\left(C F(x)+\sum_p V(p)\right),\qquad
V(p)=\log p\sum_{1\le a<t}\operatorname{length}H_{p,a},
$$
where $H_{p,a}$ is the global-to-local cohomology kernel for twist index $a$. Assume the family also has a uniform $\log A\le C_1 x^{C_1} L$ eventually, with $C_1\ge0$. For sufficiently large $x$ we have $C_1\log x\le x^\varepsilon$ and $L\ge1$. Hence $\log A\le C_1bL\le C_1F(x)$. The local comparison gives the original family's bound
$$
\mathrm{etaSum}(j)\le d_j\left((C+C_1)F(x)+\sum_p V(p)\right).
$$
This retains coefficient one on the cohomology sum, allowing the window bound to be inserted in the next divisibility estimate. [Using the cohomology length on the window](cohomology-and-divisibility-loss.md)

## Source and inputs

- `admissibleMeanCondition_holds` applies the degree formula, with `sum_val_le` and `etaSum_le_add` giving the weighted error bound. [Weights by place](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/TwistedPlaces.lean) · [Summed valuations](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/EvPowLeExp.lean)
- `etaJ_le` compares the totals per place. `linkN_of_gd` uses that estimate with `MultLe`, `adm3` and the family size bound. [Local block sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/IsHeckeGaloisIff.lean) · [Returning from the cut](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/LinkNOfGd.lean) · [Family bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/NonGaloisDescent/BoundAtTwoThreeFamily.lean)
- `linkN_of_twGood_galoisPreconditions` selects the cut in each row, obtains `LinkN` on the cut data via the local Galois comparison and length bounds, then applies the transfer above. [Main-route application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ThetaCorrespondence/ThetaPairLifts/ThirdPlaceSeries/LinkNFam.lean) · [Definition of LinkN](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalTheoremInputs.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
