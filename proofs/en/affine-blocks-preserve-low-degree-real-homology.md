# Affine blocks preserve low-degree real homology

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%BB%BF%E5%B0%84%E7%9F%A9%E9%98%B5%E5%9D%97%E4%B8%8D%E6%94%B9%E5%8F%98%E4%BD%8E%E9%98%B6%E5%AE%9E%E5%90%8C%E8%B0%83.md)

## Statement

Let $L$ be totally imaginary, $R=O_L$, and $1\le j<r_2(L)$. For $n,d\ge0$, a group $H$, and two representations $f$ and $f_0$ over $R$ with
$$
f(h)=\begin{pmatrix}f_0(h)&B(h)\\0&I_d\end{pmatrix},
$$
the pushforward of every real $j$-cycle under $f$ agrees modulo boundaries with its pushforward under stabilization of $f_0$. This is `SAff` used in the [Hecke coset comparison](two-contributions-to-the-hecke-period-average.md).

## A unit acting on the upper block

Put $Q=\mathrm{GL}_n(R)$, $A=M_{n,d}(R)$ additively, and $P=A\rtimes Q$ via left multiplication. The section $s:Q\to P$ sets the upper-right block to zero and $\mathrm{pr}:P\to Q$ takes the upper-left block. Choose $u\in R^\times$ such that $\prod_w|w(u)|^{a_w}\ne1$ for all nonnegative integer $a_w$ with $0<\sum_w a_w\le j$. The Dirichlet unit lattice is full in the hyperplane of coordinate sum zero. Each indicated functional there is nonzero because some $a_w$ is zero and another positive, using $j<r_2(L)$. To avoid finitely many kernels, substitute integer $t$ into $b_1+t b_2+\cdots+t^{r-1}b_r$ for a lattice basis. Each nonzero linear condition excludes only finitely many $t$.

Multiplication $\chi$ by $u$ on $A$ induces eigenvalues $\sigma(u)$ on $H^1(A,\mathbb C)$ from the complex embeddings on all entries, since $L\otimes_\mathbb Q\mathbb C$ splits over them. For the free abelian lattice $A$, degree-$b$ cohomology is the $b$th exterior power. For $1\le b\le j$ none of the eigenvalue products is one, by taking absolute values and grouping by infinite place. There is therefore a real polynomial $f_b$ annihilating $\chi^*$ on $H^b(A,\mathbb R)$ with $f_b(1)\ne0$. Take the product of linear factors over the eigenvalues and their conjugates.

## Where the block directions vanish

Use $c=u^{-1}I_n$ in $Q$. The inner conjugation $p\mapsto s(c)^{-1}ps(c)$ is identity on $Q$ and $\chi$ on $A$. In Hochschild–Serre for $1\to A\to P\to Q\to1$, the second page is $H^a(Q,H^b(A,\mathbb R))$. For $b>0$, $a+b\le j$, $f_b$ annihilates this term since the action commutes with $Q$ and vanishes by the coefficient polynomial. It continues to annihilate the successive subquotients. The same automorphism acts by identity on total cohomology by the inner-conjugation chain homotopy, so on the limit graded piece the polynomial is multiplication by $f_b(1)$. Consequently that graded piece vanishes. Only $b=0$ contributes in degree $j$, so pullback from $Q$ is onto, and it is injective by the section. This makes $(s\circ\mathrm{pr})^*$ the identity in degree $j$.

The source implements the same step on an explicit double complex. To transfer the polynomial from the kernel, the retraction $\rho(p)=p s(\mathrm{pr}(p))^{-1}$ to $A$ is left $A$-equivariant and commutes with the conjugation. A kernel-invariant homogeneous cocycle on $P$ differs from its restriction pulled back along $\rho$ by a coboundary by the prism. Thus applying $f_b$ yields a coboundary. The column descent `Core` shows that a $P$-invariant cocycle restricting to zero on $s(Q)$ is a coboundary, which is the filtration conclusion used here.

For a cycle on $P$, if its difference from its image under $s\circ\mathrm{pr}$ has nonzero class, a real functional on homology detecting it extends to a cocycle on chains. The two evaluations must be equal by the cohomology calculation, a contradiction. Push this identity from $P$ to the matrix group for the claimed result.

## Lean correspondence

- [`SAff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean), [`sAff_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/SAffOf.lean#L11) and [`sAff_of_parts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/SAffOfParts.lean#L131) state and assemble the result.
- [`Unit`, `Span`, `Eigen`, `ColPoly` and `Core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/Transfer.lean) specify the pieces. [Unit selection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/LcharKerNotFiniteIndex.lean#L102), [embedding products](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/ProdEmbNeOne.lean) and [cup-product spanning](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/SpanForSubsingleton.lean#L102) give the polynomial.
- [Transfer from the kernel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/TransferAlt.lean#L68) and [column descent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/AffineSplittingSpan/CoreMain.lean#L149) give the source version of the filtration argument.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
