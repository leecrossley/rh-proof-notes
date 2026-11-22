# The column level index factors into finite-field indices

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement and local data

Let $E/F$ be the host CM extension, with $[F:\mathbb Q]=f$. Fix a word $u$ in a candidate record whose first Hermitian space has rank $k\ge1$. Let $g_0,g_1,T=T_u$ be its distinct rational generator and word primes. Assume each has $f$ places in $F$, with residue-field cardinality equal to the given rational prime at each place. Put $G_v=U(H)(F_v)$, the unitary group of the first Hermitian space over the completion of $F$ at $v$. The fine adelic column level $U$ has local groups $U_v\subseteq G_v$. Let $N$ be any full self-dual lattice stabilized adelically by $U$; write $K,K_v$ for its adelic and local stabilizers.

Use the actual project's local level data in the following form.

- A full self-dual lattice in this space admits an integral orthonormal frame at every finite place $v$. The [local frame theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsFrameCm.lean#L169) states that an invertible matrix carries the standard integral coordinate lattice to the given one and gives a basis in which the Hermitian Gram matrix is the identity. The lattice stabilizers are compact open and the [local unitary group is unimodular](unitary-reflections-preserve-the-local-haar-measure.md).
- The [reference overlattice](the-two-split-components-give-a-self-dual-overlattice.md) supplies a self-dual lattice $N_0$ stabilized by $U$, equal locally to the base lattice off $T$. Off $g_0,g_1,T$, $U_v$ is the full stabilizer of the localized base lattice.
- At $v\mid g_j$ the split first projection identifies $G_v$ with $\mathrm{GL}_k(F_v)$. In the specified level frame, $U_v$ is the inverse image in $\mathrm{GL}_k(\mathcal O_{F_v})$ of the upper unitriangular subgroup of the residue group.
- At $v\mid T$ the first projection identifies the stabilizer of the localized $N_0$ with $\mathrm{GL}_k(\mathcal O_{F_v})$ in its lattice frame. In this frame $U_v$ is the inverse image of the stabilizer of a *nonzero* row functional on the residue vector space. The comparison `LocalAtT` comes with the reference overlattice and supplies the nonzero functional.

Then, writing $\mathrm{Upp}_k$ for upper unitriangular matrices, the finite index is
$$
[K:U]=
\prod_{j=0}^1\left(
  \frac{|\mathrm{GL}_k(\mathbb F_{g_j})|}{|\mathrm{Upp}_k(\mathbb F_{g_j})|}
  \right)^f(T^k-1)^f .
\tag{1}
$$
The statement in `IndexAt` allows any $N$ with $U\subseteq K$.

## Local changes of stabilizer

The global containment $U\subseteq K$ implies $U_v\subseteq K_v$ for every $v$: realize a member of $U_v$ as the finite adele equal to it at $v$ and equal to the identity elsewhere. Membership in both levels is tested at every place. The same observation applies to the stabilizer of $N_0$.

Two local self-dual lattices with orthonormal frames $B,B'$ are carried into each other by $B'B^{-1}$, which preserves the Hermitian form. Their stabilizers $K_v,K'_v$ are therefore conjugate. Unimodularity gives equal Haar measure to these compact open subgroups. Intersecting them gives a common open subgroup of finite index, and division by its nonzero Haar measure gives
$$
[K_v:K_v\cap K'_v]=[K'_v:K_v\cap K'_v].
$$
Since $U_v$ is contained in both, multiplying the two indices by $[K_v\cap K'_v:U_v]$ gives $[K_v:U_v]=[K'_v:U_v]$. At the finitely many primes where a nontrivial quotient occurs, $U_v$ is open by the given congruence descriptions. At other primes it is the full reference stabilizer. This index comparison is the reason the calculation can use the reference frame.

Off the three rational primes, use the reference lattice $N_0$. Its stabilizer equals $U_v$, so the index is one. At $v\mid g_j$, choose the full matrix lattice in the prescribed level frame under the split projection. Its stabilizer is a conjugate of $K_v$ and contains $U_v$. The preceding argument compares their indices. Reduction $\mathrm{GL}_k(\mathcal O_{F_v})\to\mathrm{GL}_k(\mathbb F_{g_j})$ is surjective since any lift of an invertible residue matrix has unit determinant. Consequently the local index is the finite group index of the upper unitriangular subgroup. Its order is $g_j^{k(k-1)/2}$, with an arbitrary entry for each position above the diagonal. The number of invertible matrices is $\prod_{a=0}^{k-1}(g_j^k-g_j^a)$, from choosing the columns consecutively outside the span of previous columns.

At $v\mid T$, use $N_0$ and its frame. Reduction is again onto, and the chosen row is nonzero. The general linear group over $\mathbb F_T$ acts transitively on the nonzero rows by right multiplication: each nonzero row can be extended to a basis of the dual space and a basis change sends any such basis to another. Its orbit therefore has $T^k-1$ points, which is the index of its stabilizer. By the first-projection description of the two level groups this is $[K_v:U_v]$. The inverse image description is essential here, since it puts the entire reduction kernel in $U_v$.

## Multiplying the indices

Let $S$ be the set of places of $F$ above $g_0,g_1,T$. A coset of $U$ in $K$ determines one coset of $U_v$ in $K_v$ for each $v\in S$. Equality of these cosets implies that the difference of representatives belongs to $U$, since the conditions off $S$ are automatic. Conversely, a finite list of local representatives is realized by the product of the adeles supported at the individual places. Each belongs to $K$, so the map on cosets is onto. The three rational primes give disjoint sets, each of size $f$. This proves (1), which is the index input to the [column class-number proof](the-column-class-number-is-the-genus-mass-times-the-level-index.md).

## Lean correspondence

- [`IndexAt` and `StabiliserLevelIndexFormula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/SelfDualLatticeIndex.lean#L30) give the exact global input and its positivity. [`relIndex_selfDual`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LocalLevelRelIndexAtLevelPrimeSelfDual.lean#L173) compares orthonormal frames. [`relIndex_conj_levelVL`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RelIndexConjLevelVL.lean#L192) uses local unimodularity to compare the two intersection indices. The input on the modular character is [`modular_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/ExistsIsHeckeOpFullDualLab.lean#L107).
- [`relIndex_at_g`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LocalLevelRelIndexAtLevelPrimeSelfDual.lean#L195) handles the pullback and change of frame at a generator. [`index_upperUni`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsUnitriGlEquiv.lean#L64) computes the finite reduction index. [`local_level_relIndex_at_level_prime_selfDual`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LocalLevelRelIndexAtLevelPrimeSelfDual.lean#L236) reduces the word-prime index to [the nonzero-row orbit](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/StabilizerIndex.lean#L11).
- [`relIndex_eq_prod_local`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsMemProjEqOnFinset.lean#L39) and [`relIndex_level`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LocalLevelRelIndexAtLevelPrimeSelfDual.lean#L277) give the product. [`selfDualLatticeIndex_stabiliserLevelIndexFormula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/StabiliserSelfDualLatticeLevelIndexFormula.lean#L10) applies it with the project's reference lattice and orthonormal frames.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
