# Lowest-alcove simplicity identifies the two value lattices

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $\lambda$ be a dominant integer weight of length $N$, and $p$ a prime satisfying $\lambda_i-\lambda_j+j-i\le p$ for all $i<j$. Normalize to the nonnegative weight $\nu=\lambda-\lambda_N(1,\ldots,1)$ for $N>0$, with the empty weight for $N=0$. Let $\Delta_{\mathbb Z}$ be the integral span of words in divided row operators applied to $h_\nu$, and $\nabla_{\mathbb Z}$ the integral dual Weyl space of column weight $\nu$. There is a single $c\in\mathbb Z$ with $p\nmid c$ and $c\nabla_{\mathbb Z}\subseteq\Delta_{\mathbb Z}$. Consequently the two standard lattices become equal at $p$.

In the word-prime application let $K$ be the coefficient number field and $w$ a place over $p$. For a finite list of coefficient embeddings and associated weights $\lambda_\tau$, suppose
$$
2\bigl(\lambda_{\tau,a}-\lambda_{\tau,b}+N\bigr)<p
\quad\text{for all }\tau,a,b.
$$
For any full source of lattice directions $L$ in the rank-$N$ Hermitian space, the transported tensor lattices of Weyl and dual Weyl polynomials on $L$ agree after localization at $w$. The local direction lattice in a factor is formed by scalar extension along that factor's embedding, with its dual for the polynomial variables, and both polynomial lattices are transported in the same local basis.

### Reduction of the integral model

Over $\mathbb F_p$ the Weyl span is a nonzero algebraic-group submodule of $\nabla_{\mathbb F_p}$. For stability, expansion in a formal row addition gives the divided row operators used to generate it. The Weyl stability under general invertible changes of row basis is the integral row stability theorem; its base change is valid over every coefficient algebra because the same divided-operator words generate after any base change. The empty word gives $h_\nu$, which is nonzero at the identity. Apply [simplicity](shifted-residues-force-simplicity-in-the-lowest-alcove.md) to conclude $\Delta_{\mathbb F_p}=\nabla_{\mathbb F_p}$.

For any $f\in\nabla_{\mathbb Z}$, the reduction of $f$ satisfies the polynomial identities defining the dual Weyl space modulo $p$. Express that reduction as a combination of divided-operator words and lift the coefficients to obtain $g\in\Delta_{\mathbb Z}$. Then $f-g=pu$ for an integral polynomial $u$. The column weight condition and the column invariance identities are homogeneous linear coefficient conditions over $\mathbb Z$; $pu$ satisfies all of them, so $u$ does too. Thus $\nabla_{\mathbb Z}=\Delta_{\mathbb Z}+p\nabla_{\mathbb Z}$.

The quotient $Q=\nabla_{\mathbb Z}/\Delta_{\mathbb Z}$ is finitely generated, since all its polynomials have total degree $\sum_i\nu_i$ before passing to the quotient. If $q_1,\ldots,q_r$ generate $Q$, write each $q_i$ as $p\sum_j a_{ij}q_j$ using $Q=pQ$. Multiply $(I-pA)q=0$ by its adjugate. The integer $c=\det(I-pA)$ annihilates $Q$ and is $1\bmod p$. This proves the single multiplier assertion, including $Q=0$.

### Transport to the local value lattice

For the standard model over $\mathcal O_K$, use the flag-minor span of the dual Weyl space. Each generating product is the scalar extension of an integral one, and the corresponding Weyl words also extend integrally. Hence multiplication by $c$ sends the standard dual Weyl lattice into the standard Weyl lattice. The image of $c$ is a unit at $w$: a Bézout relation between $p$ and $c$ would give $1\in w$ if $c\in w$. The stronger weight assumption in the application implies the required alcove bound in every factor, by $j-i<N$ and dominance. A pure tensor of dual Weyl polynomials can therefore be moved into the Weyl tensor lattice by multiplying the finitely many prime-to-$w$ factors, one for each embedding. Pure tensors generate, so after localization the standard tensor lattices agree.

Over the local discrete valuation ring all the direction lattices are free. The dual-basis change transports each standard lattice to the corresponding polynomial lattice for $L$, including the same determinant normalization on both sides. Transport the equality factor by factor and take the span of pure tensors. This gives the claimed equality of localized value lattices, the last step by which the word-prime jet proof returns a Weyl integral vector.

### Lean correspondence

- [`span_map_delSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/PublishedTheorems/GlobalTheta/WeylDualWeylLatticesAgreeOfLowestAlcove.lean#L26) gives base change of the divided-operator span. The same file proves [`delSq_eq_nablaSq_of_simple`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/PublishedTheorems/GlobalTheta/WeylDualWeylLatticesAgreeOfLowestAlcove.lean#L65) and [`exists_smul_mem_delSq_of_simple`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/PublishedTheorems/GlobalTheta/WeylDualWeylLatticesAgreeOfLowestAlcove.lean#L72).
- [`nabLeDel_of_local`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NabLeDelOfLocal.lean#L57) transports the local tensor-lattice inclusion through bases.
- [`localization_delAtr_eq_localization_nabAtr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LocPDelAtrEqLocPNabAtr.lean#L24) gives equality for the transported, localized lattices used by both word-prime kernel estimates.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
