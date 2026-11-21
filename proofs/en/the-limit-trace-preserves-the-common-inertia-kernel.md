# The limit trace preserves the common inertia kernel

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9E%81%E9%99%90%E8%BF%B9%E4%BF%9D%E7%95%99%E6%89%80%E6%9C%89%E7%A7%8D%E5%AD%90%E5%85%B1%E6%9C%89%E7%9A%84%E6%83%AF%E6%80%A7%E6%A0%B8.md)

## Statement

Let $K$ be algebraically closed of characteristic zero with an absolute value, and $r:G\to\mathrm{GL}_a(K)$ semisimple. Let $\mathcal C$ consist of $a$-dimensional representations. Suppose for every $\varepsilon>0$ a finite coefficient family satisfies
$$
\left|\operatorname{tr}r(g)-\sum_{\rho\in\mathcal C} c_\rho\operatorname{tr}\rho(g)\right|\le\varepsilon
\qquad(g\in G).
$$
If $\rho(s)=I$ for every $\rho\in\mathcal C$, then $r(s)=I$. This applies element by element to an inertia group.

## Proof

Each seed trace agrees at $sg$ and $g$. Subtract the two approximations using the same coefficients, so the trace of $r(sg)$ differs from that of $r(g)$ by at most $2\varepsilon$. Let $\varepsilon\to0$. This gives $\operatorname{tr}((r(s)-I)r(g))=0$ for every $g$.

The span $B$ of $r(G)$ is an algebra containing $r(s)-I$. It acts faithfully and semisimply on the representation, so is semisimple. By Artin–Wedderburn the trace on it is the sum of ordinary matrix traces on the simple blocks with their positive integer multiplicities. These are nonzero in characteristic zero, and the ordinary trace pairing on each matrix algebra is nondegenerate. Thus $r(s)-I=0$. In the application choose for each $w\nmid\ell$ a subfamily known unramified at $w$ that still approximates the target. The assertion kills $I_w$. Matching traces at Frobenius powers then determines the full Frobenius polynomial by [the limit-trace comparison](constructing-the-limit-trace-from-dense-frobenius-values.md).

## Lean correspondence

- [`ker_of_linApprox`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/KerOfLinApprox.lean#L10) uses [nondegeneracy of the semisimple trace pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/EqZeroOfTraceMulEqZeroSemisimpleRepStatement.lean).
- [`limWU4_of` outside $\ell$](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/LimFinOddOf.lean#L134) chooses the place-specific seed families.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
