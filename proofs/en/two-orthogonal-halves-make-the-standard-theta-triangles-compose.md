# Two orthogonal halves make the standard theta triangles compose

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the host CM data, with distinct primes $q,d$ satisfying $q\equiv3\bmod8$, the two imaginary quadratic generators, and a nonzero curve ideal with discriminant-normalized period. In even ranks $a,b$, let $\Lambda_1$ be the complex period lattice of the two standard Hermitian lattices. Let $\Lambda_2,\Lambda_3$ be those for two pairs with the same standard target and arbitrary self-dual sources, or the same standard source and arbitrary self-dual targets. Use the common normalized Hermitian form $H$ and the phase $\alpha$ of the host theta. Assume the lattice facts used in the source (`LatAll`): the three lattices are self-dual for $E=\operatorname{Im}H$, the phase is a semicharacter on each, and the lattices are commensurable. Also use the [arithmetic form identities](why-the-column-period-pairing-has-integral-phase.md)
$$
\sqrt d\,\operatorname{Re}H(x,y)\in\mathbb Z,\quad
\operatorname{Im}H(x,y)\in\mathbb Z,\qquad
\alpha(x)=(-1)^{Q(x)},\quad Q(x)=\tfrac{\sqrt d}{2}H(x,x)\in\mathbb Z
\tag{1}
$$
when $x,y$ belong to one of these lattices. The form is taken linear in the first argument. For an entire theta function $F$ at $\Lambda_1$, let $I_{ij}$ denote the [normalized average](three-theta-averages-differ-by-an-eighth-root.md) from $\Lambda_i$ to $\Lambda_j$. Then
$$
I_{23}I_{12}F=I_{13}F.
\tag{2}
$$
This proves the two triangle inputs at the standard pair, `Tr0L` and `Tr0R`, in the [host path proof](square-and-triangle-paths-give-the-host-theta-equations.md).

### The halves fixed by the standard lattice

When the target is standard, let $P$ keep the first $b/2$ rows of each complex matrix and set the others to zero. Let $\sigma$ exchange the row halves. On rational lattice maps these operations act by postcomposition with the corresponding projection or permutation of coordinates of the standard target. So they preserve all three Hom lattices. They commute with each scalar in the period module, and hence preserve all three complex lattices. When the source is standard, use the projection and exchange on the $a$ columns instead. On rational matrices these act by precomposition with the corresponding coordinate operators of the source. The same preservation proof applies.

In either case $P$ is an orthogonal projection and $\sigma$ a unitary involution exchanging its range $V_+$ with its kernel $V_-$. Each $\Lambda_i$ is the sum of its intersections with $V_+$ and $V_-$. The exchange identifies the plus and minus intersections in each lattice. Multiplication by an integer of $\mathcal O_{E_0}$ acts through the field embeddings in the complex blocks; it preserves all three period lattices and commutes with $P$.

### An arithmetic map reversing the phase on one half

Choose $e>0$ with $e\Lambda_2\subseteq\Lambda_1$ and $e\Lambda_3\subseteq\Lambda_1\cap\Lambda_2$, by multiplying the finite relative indices. Use [the norm congruence](two-quadratic-norms-represent-minus-one-modulo-every-integer.md) at $4e$ to obtain $\ell\in\mathcal O_{E_0}$, $s\in\mathbb Z$ with $\bar\ell\ell=-1+4es$. Multiplication by $\ell$, understood in the complex blocks, has two properties.

First, it is inverse to multiplication by $-\bar\ell$ modulo $e$ on each period lattice, since both compositions are multiplication by $1-4es$. In particular it induces automorphisms of the two quotients
$$
(\Lambda_2\cap V_+)/(\Lambda_1\cap\Lambda_2\cap V_+),\qquad
(\Lambda_3\cap V_+)/(\Lambda_2\cap\Lambda_3\cap V_+).
$$
The correction $4esx$ is in the denominator whenever $x$ is in the numerator. For the same reason, if $x\in\Lambda_2+\Lambda_3$, then $\ell x\in\Lambda_1$ if and only if $x\in\Lambda_1$. The forward implication applies $-\bar\ell$, then adds $4esx\in\Lambda_1$. The reverse uses preservation of $\Lambda_1$ by $\ell$.

Second, for $x\in\Lambda_i$, the diagonal phase satisfies $\alpha(\ell x)=\alpha(x)$. In fact
$$
Q(\ell x)=-Q(x)+2e\sqrt d\,\operatorname{Re}H(x,sx)
$$
by moving scalar multiplication to the adjoint side in $H$. The correction is even integral by (1). For $z\in\Lambda_3,y\in\Lambda_2$,
$$
E(\ell z,\ell y)=-E(z,y)+4\operatorname{Im}H(ez,sy),
$$
and $ez,sy$ both belong to $\Lambda_2$. Thus the last correction is an even integer. In the phase
$$
\psi(z,y)=\alpha(z)\alpha(y)\alpha(z+y)e^{-\pi iE(z,y)}
$$
for $z+y\in\Lambda_1$, multiplication of both arguments by $\ell$ preserves the signs and conjugates the exponential. It also preserves the membership condition $z+y\in\Lambda_1$.

### The absolute square

Choose representatives $R_2,R_3$ in $V_+$ for the two quotients just displayed. Then $\sigma R_2,\sigma R_3$ are representatives in $V_-$ for the corresponding minus quotients. A sum of one plus and one minus representative gives the full representative in the respective lattice quotient. Indeed the projection is integral on every period lattice, and decomposes each quotient as a direct sum. For the full finite triple sum
$$
S=\sum_{z,y\ :\ z+y\in\Lambda_1}\psi(z,y),
$$
the support test $z+y\in\Lambda_1$ separates into the two corresponding tests in $V_+$ and $V_-$. The phase also factors into the two half phases because the halves are orthogonal, and the lattice semicharacter rule on orthogonal pairs multiplies the signs without a correction. Thus $S$ factors into the plus sum $S_+$ times the minus sum for the exchanged representatives. That minus sum is $S_+$, since $\sigma$ preserves $H$, all the lattices and the signs.

Now use $\ell R_2,\ell R_3$ as the plus representatives and keep the minus ones. The automorphism of the two quotient groups makes these valid representatives. It conjugates the plus sum by the phase reversal just proved. The full sum for the new representatives is therefore $\overline{S_+}S_+$. The full triple sum is independent of representatives, by the [phase invariance on the finite quotient](three-theta-averages-differ-by-an-eighth-root.md#the-finite-quadratic-phase). When the theta $F$ is zero there is nothing to prove, and for nonzero $F$ this invariance applies. We conclude that $S=|S_+|^2\ge0$. The positive normalization of $S$ in the triple composition is an eighth root of unity and hence must equal $1$. This proves (2).

### Lean correspondence

- [`rowP`, `rowSw`, `colP` and `colSw`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/RowSwApply.lean#L91) give the projections and swaps. [Preservation of each period lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/RowSwApply.lean#L213) proves the preservation for the relevant fixed side.
- [`al_mul` and `altE_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/RowSwApply.lean#L302) prove the two phase comparisons, and [`mulO_inv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/RowSwApply.lean#L354) gives the inverse modulo the scaled periods.
- [`tripleSum_prod`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/TripleSumIndep.lean#L178) gives factorization. [`tripleSum_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/TripleSumIndep.lean#L241) changes the plus representatives, and [`tripleMu_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/TripleSumIndep.lean#L333) combines them into the absolute square. [`muOneL_of` and `muOneR_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/RightMoveTrianglesHold.lean#L57) supply the host hypotheses in the two cases; [`left_move_triangles_hold` and `right_move_triangles_hold`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/TripleSumIndependence/RightMoveTrianglesHold.lean#L117) conclude the triangle identities.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
