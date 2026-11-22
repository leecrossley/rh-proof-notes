# The theta move gives the word-prime neighbour identity

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a true adjacent step $i\to i+1$ at a word prime $T$, and let $P$ be one of its selected primes in the Hermitian field. Retain the field, prime, prime-selection and avoidance conditions, the fixed class labels at both layers, and the hypotheses of [the coefficient factorization](isolating-the-word-prime-residue-condition-in-the-kernel.md). Let $d,d'$ be points at the two layers, with the decorated-lattice structure of [the neighbour calculation](matching-one-prime-lattice-neighbours-by-a-residue-map.md). Let $a,b$ be the two ranks, with $b-a=t+1$ and $t$ odd. The ranks are even. Suppose the normalized theta kernel satisfies [the adjacent movement law](theta-movement-across-the-word-prime-lattices.md) for self-dual lattice replacements away from the indicated word prime, with the same bad-place frames and an admissible common box weight. Then for every source value $F$ in the coefficient-field weight space,
$$
\sum_{d_1\text{ above }d'} k_i(d,d_1)F
=T^{(t+1)/2}\sum_{d_0\text{ below }d} k_i(d_0,d')F.
$$
Both sums are the finite neighbours at $P$. This is the coefficient law `KerUK` for the true adjacent kernels.

### Both sums have a common pair of lattices

Write $D(d)$ for the canonical lower lattice of a decorated lattice $d$, with $D(d)_P=\ker f_P$ and the dual correction at $\overline P$. All lower neighbours of $d$ have underlying lattice $D(d)$ and differ only in the residue functional. Likewise, for every upper neighbour $d_1$ of $d'$, the lower lattice of $d_1$ equals the lattice of $d'$. Let $\Xi_0$ be the common bad-place weight from the coefficient factorization. These moves change localizations only at $P$ and $\overline P$, so the bad-place frames and coset data can be held fixed. Hence the weights in all kernels are $\Xi_0$ times the corresponding word-prime compatibility indicator.

For a fixed $d_1$ above $d'$, apply the movement law from the lattice pair $(N(d),N(d_1))$ to the pair $(D(d),N(d'))$, with the same weight
$$
\Xi(x)=\phi_T(d,d_1;x)\,\Xi_0(x).
$$
Here $\phi_T(d,d_1;x)=1$ exactly when the map $x$ is compatible with this pair of residue functionals, and is zero otherwise. Both pairs are self-dual and agree locally away from $T$. To check the support condition for movement, a nonzero value of $\Xi$ already gives the required $c_A$-scaled integrality at all bad places. At the selected places it requires the unscaled map to satisfy the residue conditions. In particular, $xD(d)_P\subseteq N(d')_P$, because a kernel of the source functional maps into the kernel of the upper target functional. All other selected localizations are unchanged, so the second box has the required support as well.

For the period in the original box take $z$ integral between its lattices at every indicated place. The perturbation $c_B z$ at a selected place carries into the lattice and kills the target residue functional because that place divides $c_B$. In the second box let $z$ instead be integral from the lower source to the lower target. At $P$ every $v\in N(d)_P$ has $c_Bv\in D(d)_P$, so the perturbation sends $v$ into $N(d')_P$. This is precisely the kernel of the upper target functional. Thus adding this perturbation again preserves membership and the equalities of residue functionals in both directions. The two periods at the other selected places are the same, and the bad-place factor has the required period by the factorization. These arguments verify all support and period inputs for the same weight on the two pairs.

### The multiplier and the coefficient count

In the movement law the differences of determinant exponents for the two source lattices and the two target lattices both equal one at $P$. This follows from the index-one-in-valuation calculation for the lower moves. They are zero at every other selected prime. Consequently the ratio of the character factors at $P$ is the zeroth power of the local character value. The volume exponent there is $b/2-a/2=(t+1)/2$. The two kernels are therefore related by the multiplier $T^{(t+1)/2}$.

For the terms on the lower-source side no theta move is required: each lower neighbour $d_0$ has lattice $D(d)$, so its kernel is already a sum for the fixed pair $(D(d),N(d'))$. Its weight is $\phi_T(d_0,d';x)\Xi_0(x)$. After moving the upper-target sum to this pair, all its terms use the same finite quotient of the local Hom module and the same normalized theta jet operator on each representative. By linearity we may sum their scalar weights first. The [neighbour matching proof](matching-one-prime-lattice-neighbours-by-a-residue-map.md#matching-the-compatible-neighbours) gives, for each $x$,
$$
\sum_{d_1\text{ above }d'} \phi_T(d,d_1;x)
=\sum_{d_0\text{ below }d} \phi_T(d_0,d';x).
$$
Upon multiplication by $\Xi_0(x)$ this identifies the scalar weights of the two finite sums on the common lattice pair. Reinsert the multiplier from the movement law.

In the actual point spaces a neighbour is specified by its decorated lattice with the same remaining bad-place frames and coset. Those data are allowed because the localizations at all bad places are unchanged. Forgetting the retained data gives a bijection on each upward or downward fibre, since they determine the extra point coordinates. Therefore the arithmetic identity just proved is the claimed point-entry sum, and applying it to $F$ gives the formula. This provides the local input to [the weighted Hecke incidence calculation](weighted-incidence-gives-the-word-prime-hecke-commutation.md).

### Lean correspondence

- [`MoveStep` and `UKTerm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/BelowFiniteNonempty.lean#L40) state the movement law and the resulting identity on decorated-lattice terms. [`inBox_up` and `inBox_dn`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L434) verify the two box conditions.
- [`moveScal_dnN`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L478) computes the multiplier from [`locScal_one_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/IndexExponentDegree.lean#L77). [`kerOf_sum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L461) moves the neighbour sum inside the common quotient, and [`ukTerm_of_moveStep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UkTermOfMoveStep.lean#L491) applies the equal indicator counts.
- [`bijOn_up` and `bijOn_dn`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SameOfAbove.lean#L34) identify the neighbour fibres. [`kAt_uk`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SameOfAbove.lean#L61) passes to the actual kernel. [`kernelCondition_at_row_family`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FivePointLawsTrueChains.lean#L35) supplies the movement law from the normalized theta and jet hypotheses.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
