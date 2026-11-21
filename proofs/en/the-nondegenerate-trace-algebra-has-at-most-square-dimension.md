# The nondegenerate trace algebra has at most square dimension

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%9D%9E%E9%80%80%E5%8C%96%E7%9A%84%E4%BC%AA%E8%BF%B9%E4%BB%A3%E6%95%B0%E8%87%B3%E5%A4%9A%E6%9C%89%E5%B9%B3%E6%96%B9%E7%BB%B4%E6%95%B0.md)

## Statement

Let $k$ be algebraically closed and $R$ a unital $k$-algebra. Assume every element is algebraic over $k$, that $x=0$ whenever $yx$ is nilpotent for every $y\in R$, and that every family of pairwise orthogonal nonzero idempotents has size at most $d\ge0$, with orthogonality in both multiplication orders. Then $\dim_k R\le d^2$ and $R$ is semisimple. This is used for the trace-pairing quotient in [pseudocharacter reconstruction](recovering-a-semisimple-representation-from-a-pseudocharacter.md).

## Proof

Take a largest orthogonal family $e_1,\ldots,e_s$, $s\le d$. Its sum is an idempotent and its complement is orthogonal to every member. Maximality gives $\sum_i e_i=1$. In the corner $e_iRe_i$ with identity $e_i$, a nontrivial idempotent could split $e_i$ in the family, so there are none. Every corner element is algebraic by compressing a monic relation. For a nonnilpotent corner element, a minimal polynomial with zero constant term would have a positive power of $X$ and a relatively prime nonconstant factor. The Chinese remainder theorem in $k[x]$ would give a nontrivial idempotent. Hence its constant term is nonzero and the element is invertible in the corner.

If $x\ne0$ in that corner is nilpotent, choose $y$ with $yx$ nonnilpotent. Then $z=xye_i$ is nonnilpotent in the corner since $(yx)^{m+1}=y z^m x$. It is invertible, giving a right inverse $e_i y e_i z^{-1}$ to $x$. This contradicts nilpotence by iterating the equation for a right inverse. Thus all nonzero corner elements are invertible. Over algebraically closed $k$, a root $\lambda$ of an element's minimal polynomial makes $x-\lambda e_i$ noninvertible, since otherwise cancellation gives a shorter relation. Hence $x=\lambda e_i$.

For $0\ne a\in e_iRe_j$, choose $y$ with $ya$ nonnilpotent. The same power identity gives $aye_i\ne0$ in $ke_i$. Rescale $e_jye_i$ to $b$ with $ab=e_i$. Then $ba$ is a nonzero idempotent in $ke_j$, hence $e_j$. For $c\in e_iRe_j$, write $c=(cb)a$ with $cb\in ke_i$. Thus every corner space has dimension at most one. Their sum is all $R$, so $\dim R\le s^2\le d^2$. The Jacobson radical of a finite-dimensional algebra is nilpotent. For each $x$ in it every $yx$ is nilpotent, so the radical is zero. This proves semisimplicity.

## Lean correspondence

- [`finite_and_isSemisimpleRing`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiniteAndIsSemisimpleRingOfNoNilIdealsBoundedIde.lean#L338) uses the orthogonal family, corner spaces and radical. The Chinese remainder argument displays the idempotent obtained from the minimal polynomial.
- [`finite_semisimple`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FiniteSemisimple.lean#L16) verifies these hypotheses for the trace quotient.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
