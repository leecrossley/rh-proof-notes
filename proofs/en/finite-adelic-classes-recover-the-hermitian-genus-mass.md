# Finite adelic classes recover the Hermitian genus mass

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM quadratic extension. Let $V=E^r$ carry a nondegenerate Hermitian form $h(x,y)=\bar x^tJ y$ that is definite at every infinite place, and let $\Lambda$ be a full $\mathcal O_E$-lattice in $V$. For each finite place $v$ of $F$ let $\Lambda_v$ be its extension to the local order $\mathcal O_E\otimes_{\mathcal O_F}\mathcal O_{F_v}$. Write $G=U(h)$ for the unitary group, and let
$$
K=\prod_{v<\infty}\{u\in G(F_v):u\Lambda_v=\Lambda_v\}
\subset G(\mathbb A_{F,f}).
$$
The genus of $\Lambda$ consists of the full lattices $L\subset V$ for which $L_v$ and $\Lambda_v$ are isometric by $G(F_v)$ at every finite $v$. The mass of this genus is $\sum_{[L]}|\operatorname{Aut}_h(L)|^{-1}$, with one term for each rational unitary isometry class. Then
$$
\sum_{[g]\in G(F)\backslash G(\mathbb A_{F,f})/K}
       |G(F)\cap gKg^{-1}|^{-1}
=\sum_{[L]\text{ in the genus of }\Lambda}|\operatorname{Aut}_h(L)|^{-1}.
\tag{1}
$$
The left side is the class mass in the [column class-number calculation](the-column-class-number-is-the-genus-mass-times-the-level-index.md). This equality holds for any full lattice in the stated space. The finiteness input for the two sums is specified below.

### The finite adelic lattice and its rational points

For $g=(g_v)_v$, prescribe the completed lattices $N_v=g_v\Lambda_v$. At all but finitely many places these equal $\Lambda_v$, by the restricted product defining the finite adeles and the fact that $\Lambda_v$ is the standard coordinate lattice outside a finite set. Set
$$
L_g=\{x\in V:x\in N_v\text{ for every finite }v\}.
$$
Choose an integer $d>0$ such that $d\Lambda_v\subseteq N_v\subseteq d^{-1}\Lambda_v$ for every $v$. One can take sufficiently large powers of the rational primes below the finitely many differing places. The finite module $d^{-1}\Lambda/d\Lambda$ is the direct sum of its primary parts, obtained by the Chinese remainder theorem on its annihilator. These are its completed quotients, grouped together for the primes of $E$ over each $v$. Under this decomposition take the direct sum of the subgroups $N_v/d\Lambda_v$ and its inverse image in $d^{-1}\Lambda$. Its local membership conditions give exactly $L_g$. Thus $L_g$ is full and its completion is $N_v$. The same argument proves uniqueness of a global full lattice from all its completions.

For any lattice $L$ of the genus, choose $g_v\in G(F_v)$ carrying $\Lambda_v$ to $L_v$. Full lattices in the same rational space agree outside a finite set, by clearing denominators in both directions. Take $g_v=1$ there and form the finite adele. The preceding uniqueness gives $L_g=L$.

### The semilocal genus in Lean

At a prime $P$ of $E$, Lean defines the localized lattice by allowing a denominator outside both $P$ and its conjugate. The condition is membership over the semilocal ring for the whole orbit $P,\bar P$, or for just that prime when it is fixed. Two such localized lattices agree if their completions at the orbit agree. For a rational vector, test membership by the ideal of integral denominators that put it into the lattice. Membership after completion says this ideal is not contained in any prime of the orbit. Prime avoidance then gives one denominator outside the whole orbit. The converse follows from invertibility of the denominator in each completion.

The source genus condition further asks that at that orbit the isometry can be taken in $G(F)$. For a completed unitary $g_v$ there is a rational unitary close enough to give the same lattice at $v$. This follows by the [Cayley approximation](simultaneous-unitary-approximation-of-hermitian-lattices.md#one-global-unitary-matrix), using in place of ordinary conjugate transpose the adjoint $X^\dagger=J^{-1}X^*J$. Multiplication by a rational scalar of norm one puts $g_v$ in the chart where $I+g_v$ is invertible. The Cayley matrix is skew-adjoint. Ordinary entrywise approximation followed by $X\mapsto (X-X^\dagger)/2$ gives a rational skew-adjoint matrix arbitrarily close to it. The inverse Cayley map returns a rational unitary. The stabilizer of a completed lattice contains the matrices sufficiently close to identity. In a local basis, a matrix congruent to identity modulo the maximal ideal is integral with integral inverse. This is an open condition in every factor, so the rational isometry reaches the same completed lattice. The membership equivalence transfers it to the semilocal ring. Conversely a rational isometry of localized lattices gives a completed one. Thus the two genus conditions coincide.

### Classes and stabilizers

For $u\in G(F)$ and $k\in K$, the lattices satisfy $L_{ugk}=uL_g$ by their completed values. Conversely, if $uL_g=L_{g'}$ for $u\in G(F)$, comparing completions gives $g'^{-1}ug\in K$. Therefore the map on double cosets is injective, and the previous construction makes it onto the genus classes. Taking $L_{g'}=L_g$ in the same argument identifies $\operatorname{Aut}_h(L_g)$ with $G(F)\cap gKg^{-1}$.

Every automorphism group here is finite. Its elements preserve the lattice as a finite-rank $\mathbb Z$-module and are bounded at the infinite places because $h$ is definite there. In a fixed $\mathbb Z$-basis the action on each basis vector therefore has only finitely many possibilities. The finiteness of the double-coset set is the additional definite lattice theorem `ClassSetFiniteL`. For a nondegenerate totally definite Hermitian space over a CM extension and any full finitely generated lattice, the double-coset set at the finite-adelic stabilizer of that lattice is finite. The [class-set proof](bounded-trace-forms-give-finitely-many-hermitian-lattice-classes.md) bounds scaled integral trace forms and the dual lattices. Using finiteness, the bijection and equality of stabilizer orders now give (1).

### Lean correspondence

- [`hcompl`, `loc` and `SameGenus`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HermitianLattices/StatementLat.lean#L57) specify the conjugate-compatible localization. [`mem_loc_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/AlgebraMapApply.lean#L219) recovers it from membership at one finite place of $F$. [`weak_approx_at`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/UnitaryTranspose.lean#L91) gives the rational unitary that matches the local lattice.
- [`globLat_mem_genus`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/UnitaryMassLatticeEqGenusMass.lean#L136) and [`exists_globLat_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/UnitaryMassLatticeEqGenusMass.lean#L154) give the two directions of the lattice construction.
- [`mk_eq_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/UnitaryMassLatticeEqGenusMass.lean#L217) compares double cosets, and [`card_stabAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/UnitaryMassLatticeEqGenusMass.lean#L277) compares their stabilizer orders. [`lattice_class_set_finite_local_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/ClassSet.lean#L16) supplies finiteness.
- [`classMass_lattice_eq_genus_mass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/UnitaryMassLatticeEqGenusMass.lean#L300) concludes (1). [`cosetSum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TotallyDefiniteMass.lean#L49) transports it to the coordinates of an abstract host Hermitian space.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
