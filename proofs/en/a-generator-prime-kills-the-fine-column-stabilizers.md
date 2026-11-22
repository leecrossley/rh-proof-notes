# A generator prime kills the fine column stabilizers

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $E$ be the CM field in a candidate record, with maximal real subfield $F$ of degree $f$. The first Hermitian space has dimension $k$ over $E$. Let $U$ be the given fine column level in its finite adelic unitary group $G_f$. Let $g_0,g_1$ be the two rational generator primes, and suppose each has $f$ places in $F$, each with residue field of cardinality $g_j$ over $g_j$. Suppose $2fk<g_j-1$ for at least one of $j=0,1$.

Then for every $y\in G_f$,
$$
G(F)\cap yUy^{-1}=\{1\}.
\tag{1}
$$
The level of the record has two properties used here. First, its given double-coset representatives identify the rational stabilizers with finite lattice automorphism groups. Second, at a place $v$ above $g_j$ the unitary group is identified with $\mathrm{GL}_k(F_v)$ by the first projection of the split algebra. In the prescribed frame at $v$, $U_v$ projects into the group of integral matrices whose reduction is upper unitriangular. The splitting maps, frame and reduction condition are in `ColLevel`, and the finiteness assertion is encoded by the finite groups in its stabilizer data.

## Local torsion at a unipotent reduction

Let $\mathcal O$ be the ring of integers of $F_v$, with residue characteristic $p=g_j$. Suppose a finite-order matrix $M\in\mathrm{GL}_k(\mathcal O)$ has unipotent reduction, so $(\overline M-I)^r=0$ for some $r\ge1$. In characteristic $p$ the binomial formula gives
$$
\overline M^{p^r}=I+(\overline M-I)^{p^r}=I
$$
because $p^r\ge r$. Write the order of $M$ as $p^e m$ with $p\nmid m$. Then $A=M^{p^{e+r}}$ satisfies $A^m=I$ and $\overline A=I$. The identity
$$
(I+A+\cdots+A^{m-1})(A-I)=0
$$
has first factor congruent to $mI$ modulo the maximal ideal of $\mathcal O$. Its determinant is a unit, so the factor is invertible. Consequently $A=I$, and the order of $M$ is a power of $p$. An upper unitriangular reduction satisfies the unipotence hypothesis because its strictly upper triangular part is nilpotent.

## Applying the local step to the rational points

Take $\gamma$ in the left side of (1), with $y$ arbitrary. The fine column class set has representatives $y_c$ for all double cosets. Writing $y=a y_c u$ with $a\in G(F),u\in U$ carries the stabilizer by conjugation by $a$ to the stabilizer of $y_c$. The given finite lattice automorphism group therefore makes $\gamma$ of finite order.

Choose a place $v$ of $F$ over the large generator $p=g_j$, which exists by the splitting hypothesis and $f>0$. Apply the first projection $E\otimes_F F_v\to F_v$ to the local component of $y^{-1}\gamma y$. In the prescribed local frame it is a finite-order matrix in the unipotent-reduction group. The local argument makes its order a power of $p$. The resulting map on the original rational matrices is injective: the projection restricted to $E$ is an embedding into $F_v$, and the conjugations are isomorphisms. Thus $\gamma$ also has $p$-power order.

If $\gamma\ne1$, some power of $\gamma$ is a rational linear operator of exact order $p$ on $E^k$. Its minimal polynomial over $\mathbb Q$ divides $X^p-1$ and contains the irreducible factor $\Phi_p(X)$ of degree $p-1$. For example, $\Phi_p(X+1)$ is Eisenstein at $p$. This contradicts $\dim_{\mathbb Q}(E^k)=2fk<p-1$. Hence $\gamma=1$.

This form of triviality is used in the [fine-level class count](the-column-class-number-is-the-genus-mass-times-the-level-index.md), where the finer cosets run through all $y$, and in the [independence of lowest-type values](trivial-stabilizers-make-the-column-values-independent.md). In the separate rank proof the source also obtains the trivial-stabilizer clause directly from its definite normalization of the level.

## Lean correspondence

- [`eq_one_of_red_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L17) uses the geometric sum and local invertibility. [`exists_pow_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L42) eliminates the prime-to-$p$ part of the order. [`iwU_pow_eq_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L124) applies it to the local congruence group.
- [`eq_one_of_pow_prime_pow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L150) excludes the rational prime-power torsion using the prime cyclotomic polynomial and the degree bound. [`isOfFinOrder_of_mem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L171) uses the finite stabilizers at the given representatives. [`eq_one_of_mem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L199) carries the local equality back through the embedding of the rational matrices.
- [`columnStabilisersTrivial`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EqOneOfMembership.lean#L229) chooses the large generator place and concludes (1). The exact level condition, including its finite stabilizer maps, is used through the record in these declarations.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
