# Even copies fix the two standard unitary theta constants

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $a,b$ be even ranks in the host CM construction, and let $\Lambda_0$ be the complex period lattice for the standard pair $L_0=\mathcal O_{E_0}^a$, $L'_0=\mathcal O_{E_0}^b$. Assume the standard theta data: $\Lambda_0$ is a full self-dual lattice with the host semicharacter, the host theta $\theta_0$ is a nonzero entire generator of its theta space, and after a unitary change of either standard lattice the new period lattice is commensurable and has the transported semicharacter. Assume the [standard-side triangle laws](two-orthogonal-halves-make-the-standard-theta-triangles-compose.md). The standard period lattice consists of matrices with entries independently in the same complex period module, and its Hermitian form and character split by individual rows or columns. In the notation of [the host path equations](square-and-triangle-paths-give-the-host-theta-equations.md), we prove for every unitary source $g$ and target $g'$ that
$$
\begin{aligned}
P_{g,1}\theta_0
 &=\left(\prod_\tau \sigma_\tau(\overline{\det g})\right)^{b/2}
   T_{(L_0,L'_0),(gL_0,L'_0)}\theta_0,\\
P_{1,g'}\theta_0
 &=\left(\prod_\tau \sigma_\tau(\det g')\right)^{a/2}
   T_{(L_0,L'_0),(L_0,g'L'_0)}\theta_0.
\end{aligned}
\tag{1}
$$
These are the two standard constants needed for unitary covariance of the natural theta.

### A source unitary without fixed vectors

If $\det(1-g)\ne0$, right multiplication of a row by $g_\tau^*$ has no nonzero fixed vector in each complex block. Denote this one-row action by $\delta_1$ and the action on the whole matrix space by $\delta$. The whole space is the product of $b$ identical rows, $\delta$ is block diagonal with $b$ copies of $\delta_1$, and its determinant is the corresponding product. The row dimension is $a$ times the number of complex embeddings, so it is even. Put $A_1=1-\delta_1^{-1}$ and $A=1-\delta^{-1}$. They are invertible.

The standard period lattice is a product over rows because maps between the standard lattices are exactly the integral matrices, and the same period scalar module applies in each slot. The common Hermitian form is the sum of the row forms. The sign on the product is the product of the signs on those rows: the diagonal form splits as a sum of integral diagonal phases. Thus the intersection of the standard period lattice with its $\delta$-image, and also its $A$-image, are products across rows. The finite quotient and the Cayley phase factor across these products. If its normalized Gauss sum on one row is $G_1$, that on the whole space is $G_1^b$. The [one-row norm congruence argument](the-norm-congruence-makes-the-one-row-cayley-gauss-sum-real.md) gives $G_1^2=1$, so $G_1^b=1$.

By the [unitary comparison](the-unitary-theta-scalar-from-a-cayley-gaussian.md#compare-and-take-the-eighth-power), the scalar relating $P_{g,1}\theta_0$ to the normalized lattice average is
$$
\frac{|\det A|}{\det A}G_1^b
 =\left(\frac{|\det A_1|}{\det A_1}\right)^b .
$$
For an invertible $A_1$, the square of $|\det A_1|/\det A_1$ is $\overline{\det A_1}/\det A_1$. Since $A_1^*=1-\delta_1=-\delta_1 A_1$ and the row dimension is even, this quotient is $\det\delta_1$. Thus the scalar is $(\det\delta_1)^{b/2}$. The determinant of right multiplication on a row by $g_\tau^*$ is $\overline{\sigma_\tau(\det g)}$, so $\det\delta_1=\prod_\tau\sigma_\tau(\overline{\det g})$. This is the first constant of (1). When $b=0$ the space has dimension zero, and the equality holds with the empty product and the identity average.

### The target unitary without fixed vectors

If $\det(1-g')\ne0$, use the $a$ independent columns instead. A column is acted on by left multiplication by $g'_\tau$; when written as a row by transposing, this is exactly the one-row action of the conjugate unitary $\overline{g'}$, since $(\overline{g'})^*=(g')^t$. Thus the real one-row Gauss sum statement applies. Its determinant on one column is $\prod_\tau\sigma_\tau(\det g')$ and the column dimension $b$ times the number of embeddings is even. The same product calculation raises this determinant to $a/2$. This gives the second identity of (1). The case $a=0$ again has the identity average.

### Remove the fixed-vector restriction

Let $s\in E_0$ be a nonzero element with $\bar s=-s$. For example one of the imaginary quadratic generators works. The scalars
$$
\lambda_t=\frac{1+ts}{1-ts},\qquad t=0,1,2,\ldots,
$$
are defined, have unitary norm, and are pairwise distinct by cross multiplication, since the field has characteristic zero. Given $g$ choose one with $\lambda_t\ne1$ and $\det(\lambda_t1-g)\ne0$, avoiding only finitely many roots of the characteristic polynomial. Then $g=g_1g_2$ with $g_1=\lambda_t1,\ g_2=\lambda_t^{-1}g$, both unitary and neither having eigenvalue $1$. Apply the first proved identity to each. Pullbacks compose as $P_{g_1,1}P_{g_2,1}=P_{g,1}$. Moving $P_{g_1,1}$ through the average for $g_2$ transports that average to the one from $g_1L_0$ to $g_1g_2L_0$, with the target standard throughout. The input for this new average is the direct move from $L_0$ to $g_1L_0$ of $\theta_0$, multiplied by its scalar. The source triangle compresses the two moves into the one from $L_0$ to $gL_0$. Since the determinant factors multiply, this gives the first formula for all $g$.

For $g'$, take a scalar factorization of the same kind. The target pullbacks compose in the same order because $(g'_1g'_2)^*=(g'_2)^*(g'_1)^*$. Use the target triangle, keeping the source standard, to obtain the second formula for arbitrary $g'$. This proves both of the host standard formulas.

### Lean correspondence

- [`const_copies`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/ConstCopies.lean#L59) multiplies the one-row phases, applies evenness and computes the determinant power. [`mem_standardThetaLattice_iff_adelicIdeal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/MemStandardThetaLatticeIffAdelicIdeal.lean#L89) gives the entrywise period description, and [`map_row` and `map_col`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/FinrankRow.lean#L29) compares the two coordinate actions.
- [`J1at_of_ne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/LineOfSpans.lean#L67) and [`J2at_of_ne`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/LineOfSpans.lean#L92) handle the fixed-vector-free maps. [`split_unitary`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/NormOne.lean#L63) gives the scalar factorization.
- [`J1at_mul` and `J2at_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/PullMulRight.lean#L51) use the two triangles for multiplication. [`first_constant_of_triangles_data` and `second_constant_of_triangles_data`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/SplitPairEquations/IntegralSquareRoots/SecondConstantOfTrianglesData.lean#L15) give (1), the `J1` and `J2` inputs.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
