# Changing the coset level isolates the auxiliary prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $E,K$ be number fields, $p$ a prime and $w$ a finite place of $K$ over $p$. Let $N,N'$ be full lattices over $\mathcal O_E$ in $E^a,E^b$, and write $M_T$ for the $E$-linear maps taking $N$ into $N'$ locally at all places in a finite set $T$ of $E$. Choose $S_0\subset S$ such that $p$ is a unit at the places in $S\setminus S_0$. In the application $S_0$ is the set of prime divisors of $\bar\pi$, where $\pi\bar\pi=p$, and $S$ contains no place over $p$ on the $\pi$ side. Take integers $c_A,c_B>0$, with $p\mid c_B$. Fix a family of linear theta jets $J_c(x)$ of common derivative multi-index, normalized with a single factor independent of $c,x$. The refinement law is
$$
J_c(x)=\sum_{y\in cM_S/(ck)M_S} J_{ck}(x+y)
\qquad(k>0),
\tag{1}
$$
for the admitted $x$ with $c_Ax\in M_S$ and $ck\mid c_Ac_B$. Use jets from the coefficient field where the weight in the following sum is nonzero. Equation (1) is differentiation of the finite refinement identity for the induced theta function. Each jet is constant modulo $cM_S$ at its level $c$.

Let $\Xi(x)$ take values in the valuation ring at $w$, vanish unless $x\in M_{S_0}$, and be invariant under translations by $pM_{S_0}\cap c_B M_{S\setminus S_0}$. For every positive divisor $c$ of $c_Ac_B$ assume the normalized jets $J_c(x)$ are defined over $K$ on the contributing terms of
$$
Z_c=\sum_{x\in c_A^{-1}M_S/cM_S}\Xi(x)J_c(x)
$$
whenever $\Xi$ is constant modulo $cM_S$. Fix $\kappa\in K$. Suppose
$$
v_w(\kappa J_{p b}(x))\ge0
\quad\text{if }b>0,\ p\nmid b,\ x\in b^{-1}M_S
\tag{2}
$$
for those terms, with $v_w(0)=+\infty$. Then $v_w(\kappa Z_{c_B})\ge0$. This is the level comparison within the bound on the actual arithmetic jet at an auxiliary prime.

## Proof

For two admissible levels $c_1,c_2$ dividing a common $M>0$, assume $\Xi$ is constant modulo each $c_j M_S$. Regroup the sum at level $M$ by cosets modulo $c_1 M_S$. In a given coarse coset the weight is fixed and the inner sum of jets is $J_{c_1}(x)$ by (1) with $k=M/c_1$. Thus $Z_M=Z_{c_1}$. Regrouping by $c_2 M_S$ gives $Z_M=Z_{c_2}$. Over the complex embedding (1) follows by linearity of repeated differentiation in a finite sum of smooth functions. All three weighted sums have values in $K$, so equality over $K$ follows by injectivity of the embedding. In particular the argument applies even when only the jets on the nonzero-weight terms have been descended.

Factor $c_Ac_B=p^n c_*$ with $p\nmid c_*$; here $n\ge1$. Both $c_B$ and $p c_*$ divide $M=c_Ac_B$. At the places in $S_0$ we have $c_B M_S\subset pM_{S_0}$ and $p c_* M_S\subset pM_{S_0}$. At the remaining places clearly $c_B M_S\subset c_B M_{S\setminus S_0}$. Also
$$
\frac{pc_*}{c_B}=\frac{p c_A}{p^n}
$$
is integral at every place in $S\setminus S_0$, since there $p$ is a unit and $c_A$ is integral. Thus $p c_* M_S\subset c_BM_{S\setminus S_0}$ as well. The translation invariance of $\Xi$ applies to both levels, so the regrouping gives $Z_{c_B}=Z_{p c_*}$.

For a contributing term at level $p c_*$, we know $x\in c_A^{-1}M_S$ and $x\in M_{S_0}$. At $P\in S_0$, $c_* x$ is integral as a lattice map. At $P\in S\setminus S_0$, $p^n c_* x=c_A c_B x$ is integral, and $p^n$ is a unit there. Thus $c_*x\in M_S$, which is the hypothesis of (2) with $b=c_*$. Multiplication by $\Xi(x)$ preserves this bound. The sum of such terms is integral by the ultrametric inequality, proving the claim.

In the construction, the scalar for a multi-index $k$ is
$$
\kappa=p^{f a b}\prod_{\tau,r,s} \tau(\bar\pi)^{k_{\tau,r,s}},
\quad f=\#\{\tau\}.
$$
All the chosen embeddings have the same restriction to the quadratic field containing $\pi$. The local split-prime jet estimate can therefore be applied with scaling $p^{f a b}\bar\pi^{|k|}$ in the corresponding $p$-adic embedding. The level comparison shows why the local estimate is needed at a level with exactly one factor of $p$. The rationality of the jets, the support and translation conditions for $\Xi$, and the [local split-prime jet estimate](extracting-the-scaled-jet-of-the-induced-theta-function.md) enter this argument as separate inputs.

## Lean correspondence

- [`DatumAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/JetOpIntegral.lean#L31) gives the support, integrality and invariance of $\Xi$. The next definition `JetLossAt` gives the multiplier.
- [`jetC_refine`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L51) proves (1). [`jetSum_level`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L87) passes through the common refinement.
- [`datum_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L108) proves the auxiliary-prime estimate conditional on (2). [`jetLossAll_of_jetSplitAmb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaJetIntegralityTypePrimeOfSplitTableBound.lean#L221) supplies the chosen embedding and invokes the split-prime bound.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
