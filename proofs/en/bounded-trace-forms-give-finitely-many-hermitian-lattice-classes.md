# Bounded trace forms give finitely many Hermitian lattice classes

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM extension, let $(V,h)$ be a nondegenerate Hermitian space definite at every infinite place, and let $\Lambda$ be a full $\mathcal O_E$-lattice in $V$. Then the finite adelic double-coset set at the stabilizer of $\Lambda$ is finite. Equivalently, the genus of $\Lambda$ has finitely many rational unitary isometry classes, with the [double-coset correspondence](finite-adelic-classes-recover-the-hermitian-genus-mass.md#classes-and-stabilizers). This is the finiteness input for the coarse mass in the column calculation.

### Uniform bounds from a reference lattice

We can scale $h$ by a nonzero element of $F$ whose sign at every real place matches the sign of $h$ there. Such an element exists by ordinary approximation in the real embeddings. For example, the image of a rational basis of $F$, with real coefficients, spans the full real product, and replacing these coefficients by sufficiently close rationals preserves all the signs. Scaling by this fixed element makes $h$ positive at every embedding and preserves its unitary group, hence the genus. We use the rescaled form throughout.

For any lattice $L$ in the genus, write
$$
L^\#=\{x:h(L,x)\subseteq\mathcal O_E\}.
$$
There are positive integers $d,e$ such that $d h(L,L)\subseteq\mathcal O_E$ and $e L^\#\subseteq L$ for every $L$ in the genus. To choose them first take $L=\Lambda$. Clear the denominators of the pairings of its generators and clear the denominators of a generating set of $\Lambda^\#$ in $\Lambda$. The same bounds hold at each completion of $L$, since there it is isometric to the reference lattice and duals commute with completion. A full lattice and the integers of a number field are recovered by imposing their membership conditions at all finite places, so the bounds hold globally.

Put $B(x,y)=\mathrm{Tr}_{E/\mathbb Q}(h(x,y))$, a rational symmetric form on the underlying $\mathbb Q$-space, and use its positive definite real extension as a Euclidean inner product. Symmetry follows from invariance of the field trace under conjugation, and positivity follows by summing the positive signatures. Write $N=[E:\mathbb Q]\dim_E V$. The case $N=0$ has just one lattice, so take $N\ge1$. For $x\ne0$ in $L$, $d B(x,x)$ is a positive integer, hence $\|x\|\ge d^{-1/2}$.

There is also a uniform upper bound on the covolume. Let $\mathfrak D_E^{-1}=\{a\in E:\mathrm{Tr}_{E/\mathbb Q}(a\mathcal O_E)\subseteq\mathbb Z\}$ and choose an integer $b>0$ with $b\mathfrak D_E^{-1}\subseteq\mathcal O_E$. The Euclidean dual $L^\vee$ for $B$ is rational, as can be seen from the inverse of the rational Gram matrix in a basis of $L$. If $x\in L^\vee$, testing $B(ay,x)$ for every $a\in\mathcal O_E,y\in L$ gives $h(y,x)\in\mathfrak D_E^{-1}$, since conjugation permutes $\mathcal O_E$. Thus $b L^\vee\subseteq L^\#$ and $eb L^\vee\subseteq L$. By the dual-basis formula $\operatorname{covol}(L^\vee)=\operatorname{covol}(L)^{-1}$, so inclusion gives
$$
\operatorname{covol}(L)^2\le(eb)^N.
\tag{2}
$$

### Short vectors give bounded integral Gram data

Use the upper half of Minkowski's second theorem. For a full lattice $L$ in $\mathbb R^N$, a compact origin-symmetric convex body $K$ with nonempty interior, and $\lambda_i$ the least $t>0$ for which $tK$ contains $i$ independent lattice vectors, the theorem gives
$$
\operatorname{vol}(K)\prod_{i=1}^N\lambda_i
\le 2^N\operatorname{covol}(L).
$$
Take $K$ to be the Euclidean unit ball. Each $\lambda_i$ is at least $d^{-1/2}$. Equation (2) bounds their product and hence each $\lambda_i$. Thus one can select independent $u_1,\ldots,u_N\in L$ with lengths at most a single constant $C$ for the whole genus. They are a $\mathbb Q$-basis of $V$. [Minkowski, Geometrie der Zahlen, 1910, p. 187](https://archive.org/details/geometriederzahl00minkrich/page/187/mode/2up) · [Henk's statement and proof of the upper bound](https://arxiv.org/abs/math/0204158)

Fix an integral basis $\omega_1,\ldots,\omega_{[E:\mathbb Q]}$ of $\mathcal O_E$. Record the numbers $B(u_i,u_j)$ and $B(u_i,\omega_s u_j)$ for all indices. They belong to $d^{-1}\mathbb Z$ by the integral pairing bound on $L$. Their absolute values are bounded by $C^2$ and $C^2$ times the real operator norms of multiplication by the fixed $\omega_s$, respectively. There are only finitely many possible records.

### The same record gives a Hermitian isometry

Suppose another short basis $u'_1,\ldots,u'_N$ has the same record. The rational linear map $T(u_i)=u'_i$ preserves $B$ by equality of the first Gram matrix. For all $i,j,s$,
$$
B(u'_i,T(\omega_s u_j))=B(u_i,\omega_s u_j)=B(u'_i,\omega_s u'_j).
$$
Nondegeneracy of $B$ gives $T(\omega_s u_j)=\omega_s u'_j$. Since the $\omega_s$ span $E$ over $\mathbb Q$, $T$ is $E$-linear. For arbitrary $x,y$, preservation of $B(x,ay)$ for each $a\in E$ gives $\mathrm{Tr}_{E/\mathbb Q}(a(h(Tx,Ty)-h(x,y)))=0$ for all $a$. The trace pairing on the number field is nondegenerate, so $T$ preserves $h$.

In the rational coordinates of the short basis, let $M=\sum_i\mathbb Z u_i$. Then
$$
M\subseteq L\subseteq d^{-1} M^\vee .
$$
The last containment holds because $d B(M,L)\subseteq\mathbb Z$. Both endpoint lattices are determined in these coordinates by the ordinary Gram matrix, and the quotient of the larger by the smaller is finite. Its subgroups give only finitely many intermediate lattices. Within each possible record and intermediate subgroup, the map $T$ above takes one lattice to the other by a Hermitian isometry. This proves the finite class count.

### Lean correspondence

- [`trace_form_positive`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/CsTrace.lean#L36) chooses the scaling for positivity. [`scale_bound_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/CsScale.lean#L184) and [`dual_lattice_bound_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/CsDual.lean#L123) give the two uniform lattice bounds. [`covolume_of_dual_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/CsCovol.lean#L195) bounds the covolume using trace Gram matrices and the dual condition.
- [`shortVectors`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HermitianLattices/HermitianLatticesProofs/ShortVectors.lean#L40) obtains the short vectors by Minkowski's second theorem. [`classSetAssembly_main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HermitianLattices/HermitianLatticesProofs/ClassSetAssembly.lean#L558) uses traces of basis vectors and their scalar multiples, then counts the intermediate lattices. [`isomOfTrace`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/HermitianLattices/HermitianLatticesProofs/IsomOfTrace.lean#L10) passes from a linear trace isometry to the Hermitian one.
- [`class_set_finite_bounded_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/ClassSetFiniteBoundedHolds.lean#L23) runs this argument under the two uniform lattice bounds. [`classSetFiniteL_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/CsAsmHformSmulRight.lean#L41) applies the resulting bounds to the completed genus. [`lattice_class_set_finite_local_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SatakeDualWeyl/AdelicIwasawaHecke/ClassSet.lean#L16) is the closed class-set finiteness statement.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
