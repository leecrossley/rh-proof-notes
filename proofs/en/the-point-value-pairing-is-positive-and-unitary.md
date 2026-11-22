# The point value pairing is positive and unitary

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E,K$ be number fields with involutions. Fix a finite set $I$, embeddings $\iota_\tau:E\to K$ for $\tau\in I$ and an embedding $\sigma:K\to\mathbb C$. The field compatibility hypothesis `FOk` says that every embedding $E\to\mathbb C$ carries the involution of $E$ to complex conjugation, and that $\iota_\tau$ and $\sigma$ respect the indicated involutions. Put $\sigma_\tau=\sigma\iota_\tau$. Fix a matrix size $n$ and dominant weights $\lambda_\tau$ of length $n$, with determinant exponents $d_\tau$ given by `shiftOf`.

The complex value space consists of functions of the form
$$
f_P(y)=\left(\prod_{\tau\in I}\det(y_\tau)^{d_\tau}\right)P((y_\tau)_\tau),
\qquad y\in\prod_{\tau\in I}\mathrm{GL}_n(\mathbb C),
$$
where $P$ belongs to the complex span of products of the dual Weyl polynomials of weights $\lambda_\tau$ in their separate matrix blocks. The construction of this polynomial space is the one used in the [complex extension of the coefficient kernel](extending-the-coefficient-kernel-to-all-complex-points.md). Write $H(f,g)$ for the point value pairing `ipVal`. On the value space it is Hermitian and positive definite, with the first variable conjugate linear.

Let $\gamma\in\mathrm{GL}_n(E)$ preserve the standard Hermitian form, so $\gamma^*\gamma=1$, where $*$ combines the involution on $E$ with transpose. Let $c\in K^\times$ have finite order. For all $f,g$ in the value space,
$$
H(T_{\gamma,c} f,T_{\gamma,c} g)=H(f,g),
\qquad
(T_{\gamma,c}f)(y)=\sigma(c)\,f((\sigma_\tau(\gamma^{-1})y_\tau)_\tau).
$$
The operators $T_{\gamma,c}$ give a representation of the product of this unitary group and the torsion subgroup of $K^\times$. In the arithmetic class model, let $S$ satisfy `GStep.Ok`, and let $C=S.\mathrm{Cl}$ be its finite class set. If $\phi$ is a nonzero class form in `S.Fi`, then
$$
\sum_{a\in C}\frac{H(\phi(a),\phi(a))}{|\operatorname{Stab}(a)|}>0.
$$
Here class values lie in the value space, and `GStep.Ok` supplies finite stabilizers.

### Proof

Let $\alpha$ run over the multi-indices in the matrix entries of all the blocks, and set $\alpha!=\prod_j\alpha_j!$. For polynomials $P,Q$ define
$$
(P,Q)_F=\sum_\alpha P_\alpha\overline{Q_\alpha}\,\alpha!.
$$
For each block let $h_\tau$ be the highest-weight polynomial `extremal`. It is a product of powers of leading minors of a matrix of indeterminates. Each minor has a diagonal monomial with coefficient $1$, hence each $h_\tau$ is nonzero. In particular
$$
N_\lambda=\prod_{\tau\in I}(h_\tau,h_\tau)_F
$$
is a positive real number. The empty product is $1$.

More generally, for a tuple of invertible frames $o_\tau$ and a polynomial $P$ write
$$
f_{o,P}(y)=
\left(\prod_\tau\det(o_\tau^{-1}y_\tau)^{d_\tau}\right)
P((o_\tau^{-1}y_\tau)_\tau).
$$
Recovering $P$ from $f_{o,P}$ is unambiguous. The determinant factor is nonzero on invertible matrices and the invertible matrices form a nonempty open set in the space of all matrices. A polynomial vanishing there vanishes identically. Lean uses a linear left inverse `polOf` of this evaluation map. The frame pairing $H_o$ of two such functions is obtained by applying this recovery to each of them and dividing the factorial pairing by $N_\lambda$:
$$
H_o(f_{o,P},f_{o,Q})=\frac{(Q,P)_F}{N_\lambda}.
$$
The standard Gram matrices and the standard frame of the point model are all identity matrices, so $H=H_1$ and $f_{1,P}=f_P$. The formula gives the claimed Hermitian symmetry and positive definiteness by summing $\lvert P_\alpha\rvert^2\alpha!$. Conjugation of $(Q,P)_F$ also proves Hermitian symmetry of `ipVal` on arbitrary functions, since the same recovery map is applied in both variables.

To compare two choices of frame, we first compute an adjoint in the factorial pairing. In variables $z_1,\ldots,z_m$ let $S_A P(z)=P(Az)$ for an arbitrary complex $m$ by $m$ matrix $A$. Then
$$
(S_A P,Q)_F=(P,S_{A^*}Q)_F .
$$
For constants this is equality of constant coefficients. The coefficient formula gives $(z_j R,Q)_F=(R,\partial_jQ)_F$ because $\alpha_j!=\alpha_j(\alpha_j-1)!$. If the adjoint formula holds for $R$ and every second argument, then
$$
\begin{aligned}
(S_A(z_iR),Q)_F
&=\sum_j A_{ij}(S_AR,\partial_jQ)_F\\
&=\sum_j A_{ij}(R,S_{A^*}\partial_jQ)_F\\
&=(R,\partial_i(S_{A^*}Q))_F
=(z_iR,S_{A^*}Q)_F.
\end{aligned}
$$
The third equality is the chain rule and conjugate linearity in the second variable. Induction on monomials followed by linearity proves the formula. For a unitary matrix $A$, the substitutions for $A$ and $A^*$ are inverse, so $(S_A P,S_A Q)_F=(P,Q)_F$. The row substitution $(y_\tau)_\tau\mapsto(u_\tau y_\tau)_\tau$ is of this form, with one block $u_\tau$ per matrix column.

Suppose that $o$ and $o'$ are both orthonormal for a tuple of Gram matrices $G$, meaning $o_\tau^*G_\tau o_\tau=(o'_\tau)^*G_\tau o'_\tau=1$. Then $u_\tau=(o'_\tau)^{-1}o_\tau$ is unitary. Writing $U(y)_\tau=u_\tau y_\tau$, we have
$$
f_{o',P}=f_{o,\zeta S_U P},
\qquad \zeta=\prod_\tau\det(u_\tau)^{d_\tau}.
$$
Unitarity gives $|\det(u_\tau)|=1$, so $|\zeta|=1$ for all integer determinant exponents. Applying the substitution identity gives
$$
H_o(f_{o',P},f_{o',Q})=(Q,P)_F/N_\lambda.
$$

Now set $o'_\tau=\sigma_\tau(\gamma)$ and $o_\tau=1$. The compatibility of the embeddings with the involution makes each $o'_\tau$ unitary. In these frames $T_{\gamma,c}f_P=\sigma(c) f_{o',P}$. This function lies in the same complex value space because the dual Weyl polynomial space is invariant under the block row action and the determinant factor acts by a scalar. It defines a representation since inverse substitutions compose in the opposite order to the matrices inside the arguments, and the scalars multiply. Since $c$ has finite order, $\sigma(c)$ is a complex root of unity. Thus the two scalar factors in the pairing multiply to $|\sigma(c)|^2=1$, and the frame identity proves invariance.

Finally, each stabilizer is finite and contains its identity, so its reciprocal order is a positive real number. Each summand in the class sum is nonnegative. A nonzero class form has a nonzero value in some class, giving a strictly positive summand there.

### Lean correspondence

- [`nfAll`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/HermitianForms/IsLocBasis.lean#L19) is the normalized factorial pairing. [`polOf_fnOf` and `ipFr_apply`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/PolyFn.lean#L351) recover the polynomials and identify the order of the two arguments.
- [`LFocks_subAdj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/FockSubAdj.lean#L10) proves the substitution adjoint. [`fockF_blockAct`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/PolyFnLemmas.lean#L77) applies it block by block. [`nfAll_blockAct` and `ipFr_fnOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/PolyFnLemmas.lean#L628) cancel the substitution and twist in orthonormal frames.
- [`trFr_mem`, `actV` and `ipVal_trFr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevelPrimePointModelRealisation.lean#L39) give the action and its invariance. [`ipVal_pos`, `ipVal_herm` and `classSum_pos_herm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/ClassSumPosHerm.lean#L10) prove positivity and symmetry at the value and class levels.

Status. Source-based reconstruction draft. The action uses the field compatibility hypothesis, and the positive class sum uses the finite class set and stabilizers. Together with the [point quotient](constructing-the-point-model-by-a-torsion-quotient.md) and [residue readouts](reducing-lattice-moves-to-finite-residue-data.md), this gives the Hermitian point model used for the kernel laws. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
