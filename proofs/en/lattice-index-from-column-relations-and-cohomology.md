# The lattice index from column relations and three cohomological bounds

[Chinese proof](../zh/%E6%95%B4%E4%BD%93%E6%A0%BC%E6%8C%87%E6%95%B0%E6%80%8E%E6%A0%B7%E4%BB%8E%E5%88%97%E5%85%B3%E7%B3%BB%E4%B8%8E%E4%B8%89%E7%B1%BB%E4%B8%8A%E5%90%8C%E8%B0%83%E6%8E%A8%E5%87%BA.md)

Fix a prime $\ell$, a coefficient DVR $\mathcal O$ of fraction field $K$ with $e=\operatorname{ord}_{\mathcal O}(\ell)>0$, a host number field $E$, the good points $Z$ of one row and $\pi\in Z$. The congruence ideal $\mathfrak c_\pi$ consists of values at $\pi$ of integral Hecke functions vanishing off $Z$. At good points the normalized representation has a rank-$r$ block numbered zero and $t$ one-dimensional blocks, with $r\ge0,t\ge1$. Let the disjoint row and column place sets $R,C$ partition the places above $\ell$, and let $Q$ be the set of other specified ramification places. Put $d_w=[E_w:\mathbb Q_\ell]$.

**Proposition.** Assume the following comparison data.

1. The [column relation module](column-dimension-detects-outside-representations.md) is $N$, with left ideal $Y$ of column generators. The normalized algebra satisfies the generation, good-fiber independence, determinant integrality and evaluation hypotheses of the [determinant comparison](one-determinant-for-the-congruence-ideal.md), together with the [change of coefficients](congruence-length-after-residue-extension.md) when the residue field is too small. At each evaluation outside $Z$, the local dimension and nonfixed-vector hypotheses of the column relation comparison hold.
2. The denominator is $\Delta=\prod_{1\le a<t}u_1(1-x^{-a})$ for $x=1+\ell^{s_0}u$, units $u,u_1$ and $s_0\ge1$, with $s_0\ge2$ if $\ell=2$. Write $D_\Delta=\operatorname{ord}_{\mathcal O}(\Delta)$. For each column $w$ let $j_w,e'_w\ge0$ be the local finite rank and lifting index. The blocks have the actions and lifting conditions of the [column kernel comparison](column-relations-bound-the-kernel-in-three-blocks.md). The zero block has column invariant lengths $B_w$, and each higher block has column invariant length at most $H_0$. The zero and higher blocks satisfy the scalar comparison with $\Delta$ of the [coboundary comparison](coboundary-cost-of-two-denominators.md) for the specified project scalar there.
3. In the zero block, restrict globally to the submodule $Q_0$, and impose the finite column conditions using the lifted bases. In each row the strict condition is the annihilator under local duality of $F_{s,w}$. The produced classes are required to be orthogonal to a submodule $I_w\subseteq F_{s,w}$ of colength $A_w=\operatorname{length}(F_{s,w}/I_w)$. The global submodule satisfying all the strict conditions has length at most $S$.
4. In block $k\ge1$ the twist is $\epsilon^{-(k-1)}$ for the cyclotomic character $\epsilon$. At places above $\ell$, the strict conditions are unramified for block one and zero for higher blocks. The other global and local conditions give unramified classes at finite places where required. Assume $\ell\ne2$ or that $E$ has no real places. Let $\mathrm{Sha}_a$ be the $\mathbb Z_\ell$-length of the first cohomology localization kernel for $(\mathbb Q_\ell/\mathbb Z_\ell)(\epsilon^{-a})$ defined in the [higher-block comparison](higher-block-length-from-cyclotomic-localization.md).
5. Let $c_B\ge0$ be an integer such that multiplying each produced positive-block row class by $\ell^{c_B}$ puts it in the strict condition. In each $v\in Q$ there is a unit $\zeta_v\ne1$ satisfying the [inertia comparison](unit-differences-bound-ramified-local-relaxation.md). The positive-block column classes already satisfy the strict conditions.

Then, with $h_E$ the class number,
$$
\begin{aligned}
\operatorname{length}(\mathcal O/\mathfrak c_\pi)\le{}&
\sum_{w\in R}A_w+\sum_{w\in C}[ee'_w+j_w(ee'_w+D_\Delta)+2D_\Delta+B_w]\\
&+S+e\sum_{1\le a<t}\mathrm{Sha}_a+e\,v_\ell(h_E)
+t e c_B\sum_{w\in R}(d_w+2)\\
&+4(r+t)(|C|+1)D_\Delta+t|C|H_0
+t\sum_{v\in Q}\operatorname{ord}_{\mathcal O}(\zeta_v-1).
\end{aligned}
\tag{1}
$$
Lengths may be infinite. When the inputs on the right are finite, the left is finite and the estimate can be [normalized](normalizing-the-global-lattice-index.md).

## The column-relations determinant

Outside the good points, the column finite cocycle spaces modulo coboundaries have the prescribed dimensions. For an injective coboundary operator, the $j_w+1$ coefficients in a column map into a quotient of dimension at most $j_w$, giving a nonzero relation. If there is a kernel, a fixed vector supplies the relation. These relations give a nonzero map from $N$ to the corresponding evaluation module. Thus the square relation matrix obtained by choosing integral combinations of the columns has zero determinant at each such point. The combinations can be chosen to keep the integral relation kernels at all the good blocks. Good-fiber independence and determinant integrality put the value at $\pi$ in $\mathfrak c_\pi$. Blockwise expansion gives its valuation as the sum of lengths of the relation kernels, proving
$$
\operatorname{length}(\mathcal O/\mathfrak c_\pi)\le\sum_{k=0}^t L_k,\qquad
L_k=\operatorname{length}_{\mathcal O}\operatorname{Hom}_A(N,M_k).
\tag{2}
$$
Here $A$ is the normalized algebra and $M_k$ is the $k$th coefficient block.

## Three block estimates

A homomorphism gives cocycles by evaluation on the generators of $Y$. Taking cohomology classes splits the estimate into the kernel, the coboundaries, and the final cohomology image. In each positive block use the common relaxation cost
$$
U=e c_B\sum_{w\in R}(d_w+2)+\sum_{v\in Q}\operatorname{ord}_{\mathcal O}(\zeta_v-1).
$$
The first bound uses the finite-layer Euler characteristic and Tate local duality for the row quotient killed by $\ell^{c_B}$. The second comes from the one inertia value at each $v\in Q$. The global relaxed quotient injects into the sum of the respective local quotients after taking their strict kernels.

For block zero the column evaluation kernel is bounded by $\sum_{w\in C}[j_w(ee'_w+D_\Delta)+B_w]+|C|rD_\Delta$. Coboundaries add $2rD_\Delta$. The global strict image costs $S$ and the row relaxation costs at most $\sum_{w\in R} A_w$ by duality. Since $|C|+2\le4(|C|+1)$,
$$
L_0\le S+\sum_{w\in R}A_w+\sum_{w\in C}[j_w(ee'_w+D_\Delta)+B_w]+4r(|C|+1)D_\Delta.
$$
Block one has trivial action and zero coboundaries. Its column kernel costs at most $\sum_{w\in C}(ee'_w+2D_\Delta)+|C|D_\Delta$. The strict global classes are everywhere unramified additive characters, of length at most $e\,v_\ell(h_E)$ by the Hilbert class field. Thus
$$
L_1\le e\,v_\ell(h_E)+\sum_{w\in C}(ee'_w+2D_\Delta)+4(|C|+1)D_\Delta+U .
$$
For $2\le k\le t$ the column kernel costs at most $|C|(H_0+D_\Delta)$ and coboundaries at most $2D_\Delta$. The strict classes lie in the localization kernel at twist $-(k-1)$, giving
$$
L_k\le e\,\mathrm{Sha}_{k-1}+|C|H_0+4(|C|+1)D_\Delta+U .
$$
Summing these bounds in (2), the relaxation term occurs $t$ times, each localization kernel once, and the higher invariants cost at most $t|C|H_0$. The denominator costs total $4(r+t)(|C|+1)D_\Delta$. This gives (1).

## Inputs and Lean correspondence

- The normalization uses [integral projections](orthogonal-projections-from-an-integral-representation.md), [separation of corner roots](separating-corner-roots-away-from-the-good-point.md), and the [outside-point dimension comparison](finite-dimension-of-the-outside-column-conditions.md). Before normalizing, the coefficient extension and pointwise conjugation place the [common inertia element and congruence data](transferring-congruence-data-with-the-same-wild-inertia.md) on the selected family. `normalized_ring_data` and `realDisplayAllK_of` supply the interface. [Normalized ring](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/NormalizedRingData.lean#L20) · [Display](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/RealDisplayAllKOf.lean#L20)
- `blockRhoLat`, `blockChiOneLat`, `blockChiCLat` and `collectAlt` give the block estimates and their sum. [Block estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/CharacterColumnKernelsOfBlockChiCOfBlockChiOne.lean#L33) · [Determinant and length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/LengthBoundViaSplitting.lean#L12)
- `theorem_n5_from_inputs` instantiates (1), and `GlobalTheory.SelmerBoundAtPoint.main` supplies the class-field, duality and Euler inputs. Column lifting uses [the Wach comparison](crystalline-lifting-cost-of-two-wach-exponents.md) or, at $2$ and $3$, [descent after finite extension](descending-a-crystalline-lift-costs-the-degree-valuation.md). [Instantiation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/StatementOneBFromUnramified.lean#L142) · [Cohomological interfaces](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SelmerLengthBoundAtPoint.lean#L23)
- The next use combines the [denominator valuation](valuation-of-the-denominator-between-blocks.md) with [local rank bounds from negative jumps](negative-filtration-jumps-bound-the-split-lattice-costs.md) to obtain the [split-prime estimates at two and three](explicit-split-estimate-constants-at-two-and-three.md).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
