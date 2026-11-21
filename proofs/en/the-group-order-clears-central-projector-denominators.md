# The group order clears central projector denominators

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E9%99%90%E7%BE%A4%E7%9A%84%E9%98%B6%E8%83%BD%E6%B8%85%E6%8E%89%E4%B8%AD%E5%BF%83%E6%8A%95%E5%BD%B1%E7%9A%84%E5%88%86%E6%AF%8D.md)

## Statement

Let $\Gamma$ be finite of order $n\ge1$ and $\zeta\in\mathbb C$ primitive of order $n$. If $e=\sum_g e_g[g]\in\mathbb C[\Gamma]$ is a central idempotent, then $ne_g\in\mathbb Z[\zeta]$ for all $g$. For a domain $O$ embedded in $\mathbb C$ with image containing $\zeta$, $ne$ lifts uniquely to the center of $O[\Gamma]$. In the [Hecke cut](central-idempotents-select-comparable-hecke-summands.md), $\Gamma$ is the product of the finite groups at the places over two prescribed primes and `Pend` supplies the root.

## Proof

For left multiplication $L_x$ on $\mathbb C[\Gamma]$, each diagonal coefficient in the group basis is $x_1$, since $gh=h$ exactly when $g=1$. Thus $\operatorname{tr}L_x=nx_1$. Given $u\in\Gamma$, take $x=[u^{-1}]e$, so $x_1=e_u$. Centrality, $e^2=e$, and $u^n=1$ give $x^{n+1}=x$. Hence each eigenvalue of $L_x$ is zero or an $n$th root of unity. Their sum with algebraic multiplicities is $ne_u$ and belongs to $\mathbb Z[\zeta]$, also for $n=1$.

The image of $O$ contains $\mathbb Z[\zeta]$, so lift the coefficients. The lift is central because each commutator is zero after the injective base change, and uniqueness is coefficientwise. Products of local central idempotents are central idempotents since they commute. Apply the bound to every such product and add the lifts for the good tuples. One factor of the group order suffices for the operator that acts by that order on the retained types and by zero on the others.

## Lean correspondence

- [`trace_lmul`, `trace_mem_adjoin` and `centralIdemCoeff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TraceMemAdjoin.lean) compute the trace and integral coefficients.
- [`card_mul_idem_from_center`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CardMulIdemFromCenter.lean#L34) lifts coefficients, and [`CentralStep.main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CentralElementsFromIdempotentCoeffs.lean#L13) applies this to a product of local projectors.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
