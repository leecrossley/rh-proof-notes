# Commuting the Hecke product through the column chain

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Consider the chain of $m$ theta lifts $K_i$ between spaces of forms $F_i$, for $0\le i<m$, at a place $w$ of the coefficient field $K$ over the word prime $T=T_u$. Write $e_w=v_w(T)>0$. Write $H_j$ for the product of the $U$-operators at the top embeddings on the selected side of $w$, and for the identity on the conjugate side. Let $h$ be the number of factors in this product and $s=(t+1)/2$ for the odd rank increment $t$. Assume the maps preserve the indicated spaces of forms, satisfy the [commutation relation](weighted-incidence-gives-the-word-prime-hecke-commutation.md), and have the [single-step inclusion](restoring-the-word-prime-value-lattice-after-one-lift.md) $T^e H_{i+1}K_i(S_i(w))\subseteq S_{i+1}(w)$. The exponent $e$ is $2\sum_\tau W_\tau+fN_m$ on the selected side and zero otherwise.

Use the starting lattice $N_\lambda(w)=T^{a}H_0^mS_{\rm ram}(w)$ in the level-zero space, where $S_{\rm ram}(w)\subseteq S_0(w)$ is the ramified part of the localized lattice and $a=m\sum_{v\ {\rm top}}b_{\tau(w,v)}\ge0$ comes from the nonnegative top exponents. The output column $C_m$ is the composition of the $m$ lifts. Then for $x'\in N_\lambda(w)$ and any nonzero $c\in K$ with
$$
v_w(c)\ge e_w m E_T(w),\qquad
 E_T(w)=e+sh(m+1)/2,
\tag{1}
$$
the form $cC_m x'$ is the image of a vector in $S_m(w)$. On the selected side $h$ equals the number of top embeddings; on the conjugate side $h=0$. In the base chain $E_T(w)=\mathrm{EatT}(u,w)$. The twisted chain gives the same bound when its step-zero identification preserves the selected side and sends $N_\lambda(w)$ into its twisted starting lattice.

## Accumulating the exponents

Put $C_0=1$ and $C_j=K_{j-1}\cdots K_0$ for $1\le j\le m$. By commuting all $h$ operators through one step, $H_{i+1}K_i=T^{sh}K_iH_i$. Moving the product through $j$ successive steps gives
$$
H_j C_j=T^{shj} C_j H_0.
\tag{2}
$$
Now prove by induction that for every $x\in S_0(w)$,
$$
T^{B_j} C_j H_0^j x\ \in\ S_j(w),\qquad
B_j=je+sh\sum_{k=1}^j k.
\tag{3}
$$
Here and below membership of a form means membership in the image of the lattice's scalar embedding. The case $j=0$ is the assumption on $x$. Applying $T^e H_{j+1}K_j$ to the left side of (3) gives a vector in $S_{j+1}(w)$ by the single-step inclusion. By (2) at $j+1$, that vector is
$$
T^{B_j+e+sh(j+1)}C_{j+1}H_0^{j+1}x.
$$
This proves (3). The triangular sum equals $m(m+1)/2$, so $B_m=mE_T(w)$ is an integer even when $E_T(w)$ is half-integral. The loss from commuting grows with the layer index because each new product crosses all the preceding lifts.

For $x'=T^a H_0^m x$ with $x\in S_{\rm ram}(w)$, multiply the vector in (3) by $cT^a/T^{B_m}$. This scalar is in $\mathcal O_w$ because (1) gives $v_w(c)-e_w B_m\ge0$ and $a\ge0$. The result is $cC_m x'$, proving the inclusion.

## Stabilizers and the twist

The prime-to-$T$ stabilizer condition used in the single-step estimate follows from the rank restriction on the class models. Suppose every class stabilizer at rank $N_i$ embeds in $\mathrm{GL}_{N_i}(E)$, where $E$ is the host CM field, and $T>[E:\mathbb Q]N_m+1$. This embedding is the faithful action on the corresponding decorated lattice in the source. If $T$ divides a finite stabilizer order, Cauchy's theorem gives an element $A$ of order $T$. As a rational linear map, $A$ acts on a space of dimension $[E:\mathbb Q]N_i$ and has minimal polynomial dividing $X^T-1$. It is distinct from the identity, so its minimal polynomial contains $1+X+\cdots+X^{T-1}$, irreducible by Eisenstein after translating $X$ by $1$. It follows that $T-1\le[E:\mathbb Q]N_i$, contrary to the rank restriction. The row-period stabilizers inject into the terminal stabilizers, so their orders are also prime to $T$.

For a twisted tuple $\mu$, the matrices defining the $U$-product and the local lattices can change. The step-zero comparison carries $N_\lambda(w)$ into the twisted starting lattice and identifies the output column via the twisted embedding. The maximal weights $W_\tau$, $f,N_m$ and the number of top embeddings are the same in the two chains. The selected side is also the same at $w$, so $E_T(w)$ remains unchanged. Apply (1) in the twisted chain to the transported $x'$. Choose $c$ of valuation $e_w B_m$, for example $T^{B_m}$. If $y\in S_m(w)$ has image $cC_mx'$, the unscaled column is represented by $c^{-1}y$. Its normalized scalar valuation is $-B_m$, which is the required $\mathrm{ColGeTw}$ bound. The base case gives the corresponding $\mathrm{ColGe0}$ by the same division. These are the column inputs of [the period estimate at $T_u$](the-period-bound-at-each-finite-place.md).

The true-column theorem obtains the required chain models from the split decorated lattices and the matching coordinates, with the point kernel entry estimates supplied by the corresponding coefficient-kernel laws. The argument above uses those laws through the single-step bound and the commutation identity.

## Lean correspondence

- [`expT` and `Nlam`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/LevelChainSharpColumnValuationOwnChainIff.lean#L71) define $a$ and the starting lattice. [`ETpi`, `ET` and `Conclusion5Sharp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/LevelChainSharpColumnValuationOwnChainIff.lean#L318) state (1).
- [`chain_into`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelChainSharpColumnValuationOfStability.lean#L91) is (3), followed by [`loss_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelChainSharpColumnValuationOfStability.lean#L150) and [`levelChainSharpColumnValuation_of_stability`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelChainSharpColumnValuationOfStability.lean#L174).
- [`stabUnit_of_embed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NotDvdCardStabilizerForm.lean#L157) uses the prime-order rank bound.
- [`sharpBound_stability_latticeColumnChain`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SharpBoundStabilityLatticeColumnChain.lean#L17) and [`trueColumns_chain_last_step_sharp_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TrueColumnsRowSharpBounds.lean#L17) assemble the point-model hypotheses.
- [`tupleChainSharpColumnValuation_of_twisted`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TupleChainSharpColumnValuationOfTwisted.lean#L25) transports the input. [`colGeTw_of_tupleChainSharpColumnValuation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ColumnWeightTwisted.lean#L25) removes the multiplier. The base case is [`ColGe0_atT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/DIVfromGLi.lean#L34).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
