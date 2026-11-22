# Integral moment approximants give an integral jet operator

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a number field, $w$ a finite place over $p$, and $\iota:K\hookrightarrow\mathbb C_p$ induce $w$; thus integrality of $z\in K$ at $w$ means $|\iota(z)|_p\le1$. In a finite set of factors $\tau$, fix ranks $a<b$, dominant weights $\lambda_\tau,\lambda'_\tau$, and source and target direction lattices in $K^a,K^b$ with local basis matrices $B_\tau,B'_\tau$. Write $\delta_\tau$ for the last entry of $\lambda_\tau$. Suppose integers $s_\tau,s'_\tau$ and $n_\tau\ge0$ obey
$$
\lambda'_{\tau,i}+s_\tau=\lambda_{\tau,i}+s'_\tau\ (i\le a),\qquad
\lambda'_{\tau,i}=-s_\tau\ (i>a),\qquad n_\tau=\delta_\tau+s'_\tau .
$$
In particular the determinant shift of $\lambda'_\tau$ is $-s_\tau$.

For a polynomial $F$ in the source tensor dual Weyl space, multiply in each factor by $\det(X_\tau)^{n_\tau}$ to obtain $F^\sharp$. Substitute $A_\tau X'_{\tau,\le a}$ for $X_\tau$, using variable matrices $A_\tau$ of size $a\times b$ and the first $a$ columns of $X'_\tau$. Expand as $\sum_m A^m P_m(X')$. The jet operator for a table $J$ with entries in $K$ sends $F$ to $\mathcal J(F)=\sum_m J(m)P_m$. Every parameter exponent in the expansion has total degree $\sum_{i\le a}(\lambda_{\tau,i}+s'_\tau)$ in factor $\tau$; the set of these degrees is finite. Suppose for these exponents that $\iota(J)$ is in the closure of the $\mathcal O_{\mathbb C_p}$-span of the tables $m\mapsto\iota(\kappa)A^m$, where $\kappa\in K$ and the matrices $A_\tau$ carry the extended target direction lattices into the extended source direction lattices. Closure here means simultaneous approximation to arbitrary positive error on every finite list of exponents, by finite sums with all scalar coefficients of norm at most one. Then for each $F$ in the localized source dual Weyl lattice,
$$
\mathcal J(F)=
\kappa\left(\prod_\tau(\det B_\tau)^{s'_\tau}(\det B'_\tau)^{-s_\tau}\right)G
$$
for some $G$ in the localized target dual Weyl lattice.

### Substitution at a single point

In the lattice bases, the matrices $A^0_\tau=\iota(B_\tau)^{-1}A_\tau\iota(B'_\tau)$ have integral entries. The source polynomial in its lattice basis is
$$
F_0(X)=\left(\prod_\tau(\det B_\tau)^{\delta_\tau}\right) F((B_\tau X_\tau)_\tau).
$$
Its coefficients are integral at $w$ by the value-lattice characterization in a basis. Now substitute $A_\tau\iota(B'_\tau)X'_{\tau,\le a}=\iota(B_\tau)A^0_\tau X'_{\tau,\le a}$ into $F^\sharp$. The factor from pulling out $B_\tau$ in the determinant powers and in $F_0$ is $\iota(\det B_\tau)^{n_\tau-\delta_\tau}=\iota(\det B_\tau)^{s'_\tau}$. The rest is an integral polynomial, obtained by substituting $A^0_\tau$ in $F_0\prod_\tau\det(X_\tau)^{n_\tau}$. Applying the target basis normalizer multiplies by $\prod_\tau\iota(\det B'_\tau)^{-s_\tau}$. This proves the determinant factor for each table.

Column addition invariance is preserved by the substitution: additions involving only the first $a$ columns commute with left multiplication by $A_\tau$, and additions to a later column have no effect. For these first $a$ columns the weights are $\lambda_{\tau,i}-\delta_\tau+n_\tau=\lambda'_{\tau,i}+s_\tau$; the later ones have weight zero. Both assertions hold in the polynomial ring with the parameters $A$ still formal. They therefore hold for every coefficient $P_m$ and for $\mathcal J(F)$.

### Taking the limit without changing coefficient fields

The coefficient of any monomial of the output in the target basis is a fixed finite linear combination of $J(m)$ with coefficients in $K$. For a finite approximating sum, its image under $\iota$ lies in $\iota(\kappa\mathfrak d)\mathcal O_{\mathbb C_p}$, where $\mathfrak d=\prod_\tau(\det B_\tau)^{s'_\tau}(\det B'_\tau)^{-s_\tau}$, by the preceding calculation and the bound on the approximating scalars. The error tends to zero, by choosing the moment approximation error small enough for this finite list and these fixed coefficients. If $\kappa=0$ all the target coefficients vanish. Otherwise this scalar multiple of the valuation ring is closed. Each actual coefficient divided by $\kappa\mathfrak d$ thus has integral image under $\iota$, and belongs to the valuation ring of $K$ at $w$. Indeed the coefficients of the actual operator were in $K$ throughout. The target weight and column identities just proved put the divided output in the localized target dual Weyl lattice. This yields the claimed $G$.

### Lean correspondence

- [`ptTable`, `substAdj`, `sharp` and `WtCompat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/SubstitutionAdjoint.lean#L13) specify the table, substitution and weights.
- [`InIntClosure`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/JetSumTable.lean#L47) is the closure condition. [`subD_sharp_inDeg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SubDSharpInDeg.lean#L115) checks the degree restriction.
- [`point_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsMulOfApprox.lean#L246) computes the factor for a point. The coefficient descent is [`exists_mul_of_approx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsMulOfApprox.lean#L283), and [`closureIntegral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsMulOfApprox.lean#L313) proves the general operator statement.
- [`jetOp_of_closure`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/AdmissibleAdjointRationalPointPadicMatrix.lean#L306) uses this with an actual adjoint and its local lattice test.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
