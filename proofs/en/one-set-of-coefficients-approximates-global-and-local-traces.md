# One set of coefficients approximates global and local traces

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%90%8C%E4%B8%80%E7%BB%84%E7%B3%BB%E6%95%B0%E8%83%BD%E9%80%BC%E8%BF%91%E5%85%A8%E5%B1%80%E8%BF%B9%E5%92%8C%E5%B1%80%E9%83%A8Frobenius%E5%B9%82%E5%92%8C.md)

## Statement

Let $K$ be nonarchimedean, $\Gamma$ a group, and $r,\rho_i:\Gamma\to\mathrm{GL}_a(K)$ for $i\in A$. There are target coordinates $\theta:J\to K$, $\theta':J'\to K$ and seed coordinates $\eta_i,\eta_i'$ on the respective sets. Assume $(\theta,\theta')$ is [polynomially approximable](constructing-the-limit-trace-from-dense-frobenius-values.md) by the seed pairs on $J\sqcup J'$. Assume any finite combination with error at most $\varepsilon$ on all polynomials in $J$ has error at most $\varepsilon$ on $\operatorname{tr}r(g)$ uniformly in $g$. Let sequences satisfy $S_n=u_n\theta'_{p(n)}$ and $s(\rho_i)_n=u_n\eta'_{i,p(n)}$ for $p:\mathbb N\to J'$ and common $u_n\in K$. For every $N\ge0$ and $\varepsilon>0$, one finite coefficient family gives both
$$
\left|\operatorname{tr}r(g)-\sum_i c_i\operatorname{tr}\rho_i(g)\right|\le\varepsilon
\quad(g\in\Gamma),\qquad
\left|S_n-\sum_i c_i s(\rho_i)_n\right|\le\varepsilon\quad(0\le n\le N).
$$

## Proof

Set $M=\max(1,|u_0|,\ldots,|u_N|)$ and choose the joint polynomial approximation to error $\varepsilon/M$. Restrict to polynomials in $J$ and apply the assumed transfer to get the first bound. Use $X_{p(n)}$ in the second coordinate set and multiply by $u_n$ to get the second. Both use the same coefficients. Repeated seed representations can have their coefficients combined because both evaluated functions depend only on the representation.

For each $w\mid\ell$, the application uses seeds crystalline at $w$ with a common Hodge–Tate weight list. The first coordinates are spherical Hecke eigenvalues and their uniform trace bound is the limit-trace result. The second coordinates are Satake power sums scaled to correspond to integral operators. At a local Weil element $\sigma$ use exponent $-n\deg\sigma$ because the algebraic normalization raises Satake parameters to power $-\deg\sigma$. The $u_n$ undo the integral scales. This gives `JointApprox` for the [crystalline trace argument](arbitrarily-small-crystalline-trace-errors-vanish.md).

## Lean correspondence

- [`joint`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/SlopeTestRemainingChoices.lean#L50) makes the two errors simultaneous. [`phiSum_satWD`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/SlopeTestRemainingChoices.lean#L91) gives the exponents.
- [`limWU4_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/TraceLimits/LimFinOddOf.lean#L172) supplies the shared coordinates at the place.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
