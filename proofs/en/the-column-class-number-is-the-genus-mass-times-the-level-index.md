# The column class number is the genus mass times the level index

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## The double-coset formula

Let $G$ be a group, let $\Gamma,U,K$ be subgroups, and suppose $U\subseteq K$ with finite index $[K:U]$. Suppose the set $\Gamma\backslash G/K$ is finite. For every representative $y$ of this set, assume $S_y=\Gamma\cap yKy^{-1}$ is finite. Assume also that $\Gamma\cap xUx^{-1}=\{1\}$ for every $x\in G$. Then the fine-level set is finite and
$$
|\Gamma\backslash G/U|=[K:U]\,\sum_{[y]\in\Gamma\backslash G/K}|S_y|^{-1}.
\tag{1}
$$

Indeed, the fiber over $[y]$ of the map from fine to coarse double cosets consists of all $\Gamma y k U$, with $k\in K$. On the finite set of right cosets $kU$ in $K$, the group $S_y$ acts by $s(kU)=(y^{-1}sy)kU$. Two elements $k,k'$ give the same fine-level class exactly when their cosets are in the same orbit. In fact $\gamma y k u=y k'$, with $\gamma\in\Gamma,u\in U$, forces $\gamma\in S_y$, since $y^{-1}\gamma y=k'u^{-1}k^{-1}\in K$. The converse follows by multiplying the orbit relation by $y$. The stabilizer at $kU$ is $S_y\cap ykUk^{-1}y^{-1}$, which equals $\{1\}$ by the hypothesis at $x=yk$. So the fiber has $[K:U]/|S_y|$ elements. Summation gives (1).

## The column level of a candidate

Fix a candidate record $D$ and its column level data. Its first Hermitian space is totally definite of dimension $k$ over the host CM field $E$, whose maximal real field is $F$ of degree $f$. Let $G$ be the unitary group over the finite adeles of $F$ and $\Gamma$ its rational points. For a word $u$, let $U$ be the prescribed column level and $T=T_u$ its rational prime. The two generator primes $g_0,g_1$ are distinct from $T$. Suppose that at least one satisfies $g_j-1>2fk$, and that $g_0,g_1,T$ each have $f$ places in $F$ with residue-field size equal to the prime. Write
$$
I_\pi=\prod_{j=0}^1\left(\frac{|\mathrm{GL}_k(\mathbb F_{g_j})|}
{|\mathrm{Upp}_k(\mathbb F_{g_j})|}\right)^f ,
$$
where $\mathrm{Upp}_k$ is the upper unitriangular group. Let $C_u$ be the column class set for the word. Then
$$
|C_u|=\operatorname{mass}_k(D)\,I_\pi\,(T^k-1)^f .
\tag{2}
$$
Here $\operatorname{mass}_k(D)$ is the mass of the genus of the standard unimodular rank-$k$ Hermitian lattice in the project, a sum of inverse automorphism orders. This is `ClassNumberFormula₂` for $D$.

For (2), use the self-dual overlattice theorem `SelfDualOverBase`. Since $T$ splits as specified, it supplies a full self-dual lattice $M$ in the first Hermitian space, containing the base column lattice and stabilized adelically by $U$. The source first constructs the lattice in $E^k$ and transports it by the given coordinate isometry. Let $K$ be the adelic stabilizer of $M$. The local index theorem gives
$$
[K:U]=I_\pi(T^k-1)^f>0 ,
\tag{3}
$$
where positivity follows from $k\ge1$, $T\ge2$, and the positive group orders. In particular the index is finite. The theorem applies to self-dual lattices that are stabilized by $U$, and uses all three splitting hypotheses.

The coarse class set $\Gamma\backslash G/K$ is identified with the genus of $M$, and its rational stabilizers are the automorphism groups of the corresponding lattices. The mass identity in the source supplies both finiteness conditions of (1) and identifies the mass there with the genus mass of $M$. The definite standard-mass comparison for the first Hermitian space identifies that mass with $\operatorname{mass}_k(D)$, using the unimodularity of $M$. The [fine stabilizers are trivial](a-generator-prime-kills-the-fine-column-stabilizers.md) by `columnStabilisersTrivial`, using the large generator and the splitting conditions at the two generators. Finally the level representatives in the record give the bijection $C_u\simeq\Gamma\backslash G/U$. Now (1) and (3) prove (2).

The argument applies to every candidate and level in the specified class. Given a family $F$, it gives the class-number formula at every $x>F.x_1$ and every candidate, as an implication with the same word-level hypotheses. Thus its family closure has zero lower requirements and can use the parameter range $0<\varepsilon\le1$. The [design proof](the-selected-twists-supply-the-missing-design-estimates.md) combines this closure with the [dimension formula at trivial stabilizers](trivial-stabilizers-make-the-column-values-independent.md) to obtain the mass comparison on the chosen family.

## Lean correspondence

- [`card_fiber_mul_card_stab`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DoubleCosetCount.lean#L9) gives the fiber calculation, and [`card_eq_index_mul_mass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/MassSelfDualLatticeFirstSpaceEq.lean#L21) uses it with the mass.
- [`mass_selfDualLattice_firstSpace_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/MassSelfDualLatticeFirstSpaceEq.lean#L85) gives the standard genus mass, and [`cosetSum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TotallyDefiniteMass.lean#L49) relates lattice mass to the double cosets. The fine stabilizer input is [`columnStabilisersTrivial`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L226).
- [`classNumber`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/MassSelfDualLatticeFirstSpaceEq.lean#L96) and [`classNumber_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/ClassNumberAll.lean#L11) prove the actual formula from the overlattice and index theorems. [`classNumber_closed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ClassNumberClosed.lean#L10) gives its closure. The overlattice, local index and genus mass identifications are mathematical inputs to the class count above.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
