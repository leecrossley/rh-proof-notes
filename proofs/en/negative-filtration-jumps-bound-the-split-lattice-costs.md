# Negative filtration jumps bound the split lattice costs

[Chinese proof](../zh/%E8%B4%9F%E8%BF%87%E6%BB%A4%E8%B7%B3%E7%82%B9%E6%80%8E%E6%A0%B7%E5%8F%98%E6%88%90%E5%88%86%E8%A3%82%E5%A4%84%E6%A0%BC%E6%8C%87%E6%95%B0%E7%9A%84%E8%A1%8C%E5%88%97%E4%BB%A3%E4%BB%B7.md)

## Local rank bound

Let $\ell$ be prime, $K/\mathbb Q_\ell$ finite, $L$ a finite coefficient field containing the images of every embedding of $K$, and $V$ a finite-dimensional continuous crystalline $L$-representation with $H^0(K,V)=0$. Assume the Bloch–Kato dimension formula and that at each embedding $\tau$ the difference $\dim_L D_{{\rm dR},\tau}(V)-\dim_L\operatorname{Fil}^0D_{{\rm dR},\tau}(V)$ counts the negative filtration jumps with multiplicity. Suppose every jump has multiplicity one and the jump set is $C_\tau\cup L_\tau$ with $C_\tau\subset\mathbb Z_{>0}$ and $|L_\tau|\le m$. Alternatively suppose $C_\tau\subset\mathbb Z_{<0}$ and the jump set is $\{-a-1:a\in C_\tau\cup L_\tau\}$ with $|L_\tau|\le m$. In either case,
$$
\dim_L H^1_f(K,V)\le[K:\mathbb Q_\ell]m. \tag{1}
$$
The formula expresses this dimension as $\dim H^0$ plus the sum of the filtration dimension differences. The former is zero, and only $L_\tau$ can contribute negative jumps in the first case. In the second case $a<0$ implies $-a-1\ge0$ and the map is injective, so again at most $m$ jumps contribute. Summing over the embeddings gives (1).

## From rank to the split lattice bound

Fix a record and good point at $\ell$ with decomposition `Decl`. Use disjoint row and column places $R,C$ with $b(w)\in C$ the conjugate of $w\in R$. Conjugation is an involution, hence $b$ is injective. Put $d_u=[E_u:\mathbb Q_\ell]$. By (1) the finite cohomology rank $j_u$ at a column is at most $d_um$. With nonnegative lifting exponent $e'$, cyclotomic valuation sum $v_\Delta$ and invariant length $h_W(u)$, the global index's column cost is $e'+j_u(e'+v_\Delta)+2v_\Delta+h_W(u)$. Replace $j_u$ by its bound. Suppose also that the row colength comparison at $w$ gives $d_{b(w)}me'+r c_0(b(w))$, where $r,c_0\ge0$. Its invariant term arises from the [zero-weight exclusion](absence-of-weight-zero-bounds-crystalline-quotient-invariants.md).

Sum the row bound through $b$ and enlarge its image to all of $C$ by nonnegativity. Together with the columns this gives
$$
\sum_{u\in C}\big(e'+d_um(2e'+v_\Delta)+2v_\Delta+h_W(u)+rc_0(u)\big). \tag{2}
$$
The second term involving $d_um e'$ comes from the row cost.

The independent input `GlobalLatticeIndexTheorem` assumes $\ell$ distinct from the two generator primes, the point in the required Hecke set, and finite $s_\pi$ and cohomology lengths. It bounds $v_\pi$ by the true row and column cost plus $s_\pi$, $\mathrm{VV}(\ell)$, $v_\ell(h_E)$, the row term $t\sum_{w\in R}(d_w+2)c_B$, $4n_V(|C|+1)v_\Delta+t|C|h_0$, and the remaining unit-difference lengths. Replace the first cost by (2), keeping all other terms. This gives the [full split estimate](explicit-split-estimate-constants-at-two-and-three.md). The internal index arguments include [congruence ideals and block lengths](one-determinant-for-the-congruence-ideal.md) and [conversion of length units](normalizing-the-global-lattice-index.md).

## Lean correspondence

- [`rank_eq_count`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JumpAndLengthOfAdmitted.lean#L23), [`rank_le_col`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JumpAndLengthOfAdmitted.lean#L41) and [`rank_le_row`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JumpAndLengthOfAdmitted.lean#L67) apply the dimension formula ([Bloch–Kato, Corollary 3.8.4](https://virtualmath1.stanford.edu/~conrad/BSDseminar/refs/BKTamagawa.pdf#page=23)).
- [`sum_lenW_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JumpAndLengthOfAdmitted.lean#L493), [`sum_lenW_split`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JumpAndLengthOfAdmitted.lean#L688) and [`length_bound_of_theorem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/JumpAndLengthOfAdmitted.lean#L742) give the injection, combined sum and substitution.
- [The global index statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DecompositionData.lean#L323), [split assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SplitCaseBoundAtPointOfAdmittedItems.lean#L14) and [the upstream entry](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/StatementOneBFromUnramified.lean#L142) give the remaining terms.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
