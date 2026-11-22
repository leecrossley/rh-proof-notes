# The zero Hecke term pays for its own valuation loss

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a layer $0\le j<m$ at a place of residue characteristic $p$ and a list $B$ of distinct local components. For a component $v$, let $T_{v,i}$ be the normalized degree-$i$ Hecke operator on layer $j+1$, with $T_{v,0}=1$ and $0\le i\le r$, and denote by $A_v$ the sum of top gaps on the even slots of $v$. Assume the following one-layer point-map estimate. For an integral source vector and any choice of $i_v$ supported on $B$, the valuation of the product of $T_{v,i_v}$ after the lift $K_j$ is bounded below by the sum of the corresponding cofactor floors minus $d_j$. On $B$ assume a floor at least $G_v$ when $i_v>0$, and at least $G_v-A_v$ when $i_v=0$, where $G_v$ is at most the system's $g_B(v,j+1)$. Off $B$ assume the ordinary $i_v=0$ floor $G_{0,v}$. This is the combination of `PlaceB` and `form_of_place`. [Entry, form, and component bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/PlaceB.lean#L14) · [`form_of_place`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/RamifiedLatticeOfChainEstimates.lean#L90)

For each $v\in B$, let $u_v(l)$ be the unit scalars from the Hecke relation and write $b_v=\prod_{l=1}^{j+1}u_v(l)$. The operator used in the layer induction is
$$
Z_v=\sum_{l=0}^r (-1)^l c_{v,l}\,b_v^{-(r-l)}T_{v,r-l}.
$$
Assume $v_p(c_{v,l})\ge0$ for $l\le r$ and $v_p(c_{v,r})\ge A_v$. Then for each integral $F$ at layer $j$,
$$
v_{L_{j+1}}\bigl((\prod_{v\in B} Z_v)K_jF\bigr)\ \ge\
\sum_{v\in B}G_v+\sum_{v\notin B}G_{0,v}-d_j.
$$
[`cl`, `Ttu` and `Zop`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/FormalGroupSystem.lean#L344) · [`ZL_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/AofUpdate.lean#L172)

Expand the ordered product, choosing $l_v$ for each distinct component. In a fixed term the index of the Hecke operator is $i_v=r-l_v$. Its scalar has valuation at least $\sum_{v\in B:i_v=0} A_v$, since signs and the $b_v$ are units. In the corresponding operator product the loss from a zero choice at a component of $B$ is at most $A_v$. Thus the one-layer estimate for that term, after multiplication by its scalar, gives the claimed lower bound. The sums retain the floor by the ultrametric inequality, equivalently by closure of the scaled target lattice under addition. The source encodes the same expansion as an induction on the list, using a span of terms indexed by the $i_v$. Choosing a new component preserves the old indices because each occurs at most once. [The weighted generating terms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/AofUpdate.lean#L50) · [Expanding at one component](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/AofUpdate.lean#L91) · [Compensation of the zero choices](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GrowthBounds/MultisetValuation/AofUpdate.lean#L183)

This is the one-layer bound needed in [the layer induction](choosing-at-each-layer-which-operators-to-use.md). The [coefficient estimate](the-alternating-hecke-coefficients-are-integral.md) proves the required bounds on $c_{v,l}$. The [component product argument](integral-parameter-monomials-separate-the-cofactors-at-all-places.md) and the [class-kernel transfer](coefficients-of-the-hecke-kernel-bound-the-layer-lattice.md) derive the one-layer point-map estimate from the [cofactor bounds](the-three-served-jet-floors-apply-to-the-local-formal-group.md) and the admitted frame laws.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
