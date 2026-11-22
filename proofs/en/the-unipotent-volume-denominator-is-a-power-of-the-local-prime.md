# The unipotent volume denominator is a power of the local prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $P$ be a finite place of a number field $E$ with rational prime residue cardinality $q$. Put $A=\mathcal O_{E,P}$ and $V=E^{n+c}$ for $n,c\ge0$. In $V$ consider the flag $U_i$ spanned by the first $n+i$ standard basis vectors for $0\le i\le c$. Let $U$ be the subgroup `N1` that fixes $U_0$ pointwise, fixes the first extra basis vector if there is one, and preserves this flag with identity action on the successive one-dimensional quotients. Let $J$ be a subgroup of the stabilizer of the standard lattice $L=A^{n+c}$, and take $h\in\mathrm{GL}(V)$. Set
$$
U_0^{\rm int}=U\cap\operatorname{Stab}(L),\qquad U_h=U\cap hJh^{-1},\qquad G_0=U_h\cap U_0^{\rm int}.
$$
If $G_0$ has finite index in $U_h$, then $[U_h:G_0]$ is a power of $q$. This bounds the denominator of the inverse normalization `volN`, which in the project's convention is
$$
\operatorname{volN}^{-1}=\frac{[U_0^{\rm int}:G_0]}{[U_h:G_0]}.
$$
The group construction `Cbe` also imposes the first-parabolic conditions, which $U$ already satisfies. With the source convention that infinite index is assigned the value $0$ and inverse of zero is zero in the coefficient field, the same conclusion for the inverse normalization is that it is integral at any coefficient prime $w$ where $q$ is a unit. This is the estimate `VolumeAtQ`. In the type case, the reference lattice is scaled along the extra coordinates and $h$ preserves it. If $J$ also preserves that lattice, the same inverse normalization is a nonnegative integer in the coefficient field.

### A uniform prime power puts each element in the integral subgroup

The two lattices $L$ and $hL$ have a common denominator bound: take $b\ge0$ with
$$
q^b L\subseteq hL,\qquad q^b hL\subseteq L.
$$
Such a $b$ exists by clearing the finitely many denominators in $h$ and $h^{-1}$ over the valuation ring. Any $g\in U_h$ preserves $hL$. Write $Z=g-1$. By the flag conditions, $Z U_i\subseteq U_{i-1}$ for $1\le i\le c$, and $ZU_0=0$. Hence $Z^{c+1}=0$, and $Z(hL)\subseteq hL$.

Let $N=q^{2b+c}$. For each $i$ with $1\le i\le c$, the binomial coefficient $\binom Ni$ is divisible by $q^{2b}$. To see this, use $i\binom Ni=N\binom{N-1}{i-1}$. Since $i\le c\le q^c$ when $c\ge1$, the exponent of $q$ dividing $i$ is at most $c$. This gives the indicated divisibility even if the coefficient vanishes. For $v\in L$, the inclusions of lattices give
$$
q^{2b}Z^i v=q^b Z^i(q^b v)\in L.
$$
Using the binomial expansion of $(1+Z)^N$, all the terms with $i\ge c+1$ vanish, and all the remaining terms take $v$ into $L$. Thus $g^N L\subseteq L$. Since $g^{-1}\in U_h$, applying the same result to $g^{-1}$ gives equality. In particular every element of $U_h$ has its $N$th power in $G_0$.

### The relative index and the normalization

Suppose $[U_h:G_0]$ is finite. Acting on the finite set of left cosets gives a finite quotient of $U_h$ by the normal core of $G_0$, the intersection of its conjugates. Every element in the quotient has $q$-power order. Indeed every conjugate of each element of $U_h$ has its $N$th power in $G_0$, so the $N$th power of the original element belongs to the normal core. The finite quotient is therefore a $q$-group by Cauchy's theorem. The index of $G_0$ divides this quotient's order and so is also a $q$-power.

In the inverse normalization the numerator is a nonnegative integer, hence is integral at every coefficient prime. When $q$ is a unit, the denominator is a unit as well whenever the index is finite. An infinite denominator index is assigned zero in the source convention, which makes the value of the inverse normalization zero. Thus in either case the normalization is integral at $w$.

In the type case replace $L$ by the scaled reference lattice; by assumption $h$ and $J$ both stabilize it. It follows that $U_h\subseteq U_0^{\rm int}$, so $G_0=U_h$. The denominator index is $1$ and the inverse normalization is the integer numerator. This is why that branch keeps integrality at the type prime itself.

### Lean correspondence

- [`Ufl`, `R1cond` and `N1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L468) give the flag and unipotent subgroup. [`Cbe` and `volN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L521) define the conjugated level and index ratio.
- [`volq_choose` and `volq_pow_mem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/VolqExistsPow.lean#L33) use divisibility of binomial coefficients and commensurability. [`volq_nil`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/VolqExistsPow.lean#L104) gives the nilpotence length.
- [`volq_index`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/VolqExistsPow.lean#L11) uses the normal core. [`volq_relIndex` and `volumeAtQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/VolqExistsPow.lean#L160) apply it to the volume at a twist place.
- [`volN_inv_nat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/UnfoldingIsGoodCyclotomicInvariantReferenceLatti.lean#L184) gives the integral type normalization.

Status. Source-based reconstruction draft. The twist application uses that the rational prime $q$ is a unit at the coefficient prime in question. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
