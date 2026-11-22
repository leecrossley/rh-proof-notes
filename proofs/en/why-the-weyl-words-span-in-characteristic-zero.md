# Why the Weyl words span in characteristic zero

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $r\ge n\ge 0$, let $k$ be a field of characteristic zero and let $\nu_1\ge\cdots\ge\nu_n\ge 0$ be integers. Put $\nu_{n+1}=0$. In the polynomial ring of an $r$ by $n$ matrix $Y$ over $k$, let $\nabla_\nu(k)$ be the space of polynomials of column multidegree $\nu$ invariant under adding any scalar multiple of an earlier column to a later column. Invariance means a polynomial identity in the added scalar and all the matrix entries. Let $\Delta_\nu(k)$ be the span of all finite words of row divided operators $D_{ab}^{(m)}$ applied to
$$
h_\nu(Y)=\prod_{j=1}^n\det(Y_{[1,j],[1,j]})^{\nu_j-\nu_{j+1}}.
$$
Here $D_{ab}^{(m)}$ extracts the coefficient of $u^m$ after adding $u$ times row $a$ to row $b$. Then
$$
\Delta_\nu(k)=\nabla_\nu(k).
$$
In particular, if $f$ has integer coefficients and belongs to the integral version $\nabla_\nu(\mathbb Z)$ of this space, there is a nonzero integer $d$ with $df\in\Delta_\nu(\mathbb Z)$. This is the spanning input for the [local value lattice](a-local-frame-identifies-the-weyl-value-lattice.md).

### The highest-weight line

Each leading minor is invariant under adding an earlier column to a later column. If the later column is among the first $j$, both columns are included and the operation does not change its determinant. If it is outside the first $j$, the operation leaves the minor untouched. The analogous argument for rows gives invariance under adding an earlier row to a later row. The product $h_\nu$ has degree $\nu_j$ in column $j$ by telescoping. It is nonzero, taking value $1$ on the rectangular matrix with diagonal entries $1$ and other entries $0$. Row operations commute with the column operations, and preserve column degrees. Taking coefficients of the row parameter shows that $\nabla_\nu(k)$ is stable under every divided row operator. In particular $\Delta_\nu(k)\subseteq\nabla_\nu(k)$.

Suppose $f\in\nabla_\nu(k)$ is killed by $D_{ab}^{(m)}$ for all $a<b$ and $m\ge 1$. Then it is also invariant under adding an earlier row to a later row, because all positive coefficients of the added scalar vanish. On the matrices where every leading principal minor is nonzero, we may apply exactly these row and column operations to reach a diagonal rectangular matrix. At the current diagonal pivot first clear the entries below it using that row, and then clear the entries to its right using that column. The preceding rows and columns stay cleared. Every leading principal minor is unchanged by the allowed operations. After completing the previous pivots, the leading minor through the current pivot is the product of the previous pivots times the current one, so the current pivot is nonzero. The procedure therefore continues through column $n$, also clearing the entries below row $n$.

On a diagonal matrix with entries $t_j$, the only possible surviving monomial of column multidegree $\nu$ is $\prod_jt_j^{\nu_j}$. Its coefficient in $f$ is a fixed scalar $c$. The corresponding value of $h_\nu$ is precisely $\prod_jt_j^{\nu_j}$. Invariance under the operations now gives $f(Y)=c h_\nu(Y)$ at every matrix with all leading minors nonzero. Over an infinite field this implies polynomial equality. Indeed, multiplying $f-c h_\nu$ by the product of the leading minors gives a polynomial vanishing on every matrix. The polynomial ring is a domain and the product of these minors is nonzero, so $f-c h_\nu=0$.

### Every nonzero stable subspace contains this line

Work over $\mathbb Q$. All polynomials concerned lie in the finite-dimensional space of column multidegree $\nu$. For the operator $D_{aa}^{(1)}$, scaling row $a$ by $1+u$ shows that a monomial of row degree $\mu_a$ is an eigenvector of eigenvalue $\mu_a$. In any subspace stable under all divided row operators, the row-degree components of a polynomial remain in the subspace. To obtain one component, for each row apply the Lagrange interpolation polynomial in $D_{aa}^{(1)}$ which is $1$ at the desired degree and $0$ at all other degrees from $0$ to $\sum_j\nu_j$.

Suppose a nonzero subspace of $\nabla_\nu(\mathbb Q)$ is stable under all these operators. Among the row weight vectors $\mu$ occurring nontrivially in it, choose one minimizing $\sum_{a=1}^r a\mu_a$, and take a nonzero homogeneous vector of that row weight. When $a<b$, the image under $D_{ab}^{(m)}$, if nonzero, has row degree $m$ greater at $a$ and $m$ less at $b$. For $m\ge1$ its score drops by $m(b-a)$, contrary to minimality. Therefore the vector is killed by all the raising operators. The preceding argument makes it a nonzero scalar multiple of $h_\nu$, so the subspace contains $h_\nu$.

### Factorial orthogonality forces the span

On rational polynomials use the symmetric bilinear form
$$
(f,g)_F=\sum_\alpha f_\alpha g_\alpha\,\alpha!,
$$
where $\alpha$ runs through monomial exponents. This is positive definite over $\mathbb Q$. The substitution adjoint in the [point value pairing](the-point-value-pairing-is-positive-and-unitary.md), restricted to rational coefficients, identifies substitution by a rational row matrix with the adjoint substitution by its transpose. For the matrix adding $u$ times row $a$ to row $b$, the transpose adds $u$ times row $b$ to row $a$. Comparing coefficients of $u^m$ gives
$$
(D_{ab}^{(m)}f,g)_F=(f,D_{ba}^{(m)}g)_F.
$$

Let $M=\Delta_\nu(\mathbb Q)$. It is stable under every divided row operator by its definition. The orthogonal complement of $M$ inside $\nabla_\nu(\mathbb Q)$ is also stable, by the adjoint formula and stability of $\nabla_\nu(\mathbb Q)$. If this complement were nonzero it would contain $h_\nu$. But $h_\nu\in M$ and $(h_\nu,h_\nu)_F>0$. The complement is therefore zero. The restriction of the pairing to $M$ is nondegenerate by positivity, so any element of $\nabla_\nu(\mathbb Q)$ can be written as a vector in $M$ plus one orthogonal to $M$: solve the linear equations against a rational basis of $M$ using its invertible Gram matrix. Hence $M=\nabla_\nu(\mathbb Q)$.

### Denominators and other coefficient fields

The generators of $M$ are words on $h_\nu$ with integer coefficients. Writing an integral $f$ in their rational span uses only finitely many rational coefficients. A common nonzero integer denominator gives the asserted integral multiple.

Over any characteristic-zero field, the condition of fixed column multidegree restricts to finitely many monomials. The remaining column invariance equations come from the coefficients in the extra scalar of each triangular column addition and have integer entries. Gaussian elimination over $\mathbb Q$ thus gives a rational basis of their kernel that remains a basis over $k$. The word generators also commute with coefficient extension, so the proved equality extends from $\mathbb Q$ to $k$. Lean performs this last step using a semistandard basis of the dual Weyl space whose elements are integral bideterminants. For each basis element its nonzero integer multiple belongs to the integral Weyl lattice by the rational argument. That integer becomes invertible in $k$, giving the same equality after coefficient extension.

### Lean correspondence

- [`dualWeyl` and `weyl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/StatementA.lean#L24) define the two spaces. [`dualWeylModuleRowDividedPowerStable`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/RowDivStable.lean#L143) is stability under the row operators.
- [`highest_weight_line`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/HWLine.lean#L11) identifies the joint kernel. [`lhwline_elim_cleared` and `lhwline_vanish`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/LHwlineLemmas.lean#L321) perform elimination on the matrices with nonzero leading minors.
- [`row_divided_closed_graded`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/RowDivClosedGraded.lean#L10) extracts row components. [`lhwin_exists_killed`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/LHwinLemmas.lean#L133) obtains a vector killed by the raising operators. [`hwInClosed_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/HWInClosed.lean#L10) puts the highest-weight vector in any nonzero stable rational subspace.
- [`fock_space_row_divided_adjoint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/FockQRowDivAdj.lean#L169) is the adjoint formula. [`closedEqNabla_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FockSpaceTableaux/ClosedEqNabla.lean#L55) is the orthogonal-complement argument.
- [`weylEqNablaQ` and `weylRational`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FinalB.lean#L23) give rational spanning and the denominator result. [`dualWeyl_eq_weyl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/PolyFnLemmas.lean#L416) uses [`sSBasis`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FinalD.lean#L18) to extend the result to characteristic zero.

Status. Source-based reconstruction draft. The final extension of scalars above uses the finite column-invariance equations. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
