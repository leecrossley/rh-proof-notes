# Preserving nonvanishing in eigenvalue approximation

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E5%9C%A8%E6%9C%AC%E5%BE%81%E5%80%BC%E9%80%BC%E8%BF%91%E4%B8%AD%E4%BF%9D%E7%95%99%E6%8C%87%E5%AE%9A%E7%9A%84%E9%9D%9E%E6%B6%88%E5%A4%B1%E6%9D%A1%E4%BB%B6.md)

## Statement

Let $K$ have a nonarchimedean absolute value, and $S,T\subset K^J$. In the [polynomial approximation sense](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%A8%A0%E5%AF%86Frobenius%E5%8F%96%E5%80%BC%E6%9E%84%E9%80%A0%E6%9E%81%E9%99%90%E8%BF%B9.md), assume $\theta$ is approximable by $S$ and every $\eta\in S$ by $T$. Thus at every precision each approximation uses a finite linear combination with coefficients working for all integral polynomials in the coordinates. If $Q\in\mathbb Z[X_j:j\in J]$ is nonzero at every $\eta\in S$, then $\theta$ is approximable by $\{\zeta\in T:Q(\zeta)\ne0\}$. In the project the first family meets Satake tests at chosen places and the second changes the weight and type at a specified $\ell$-adic place. The polynomial is a product of eigenvalue coordinates testing the required nonvanishings.

## Proof

For fixed $\eta\in S$, approximate it by $T$ to precision $\varepsilon|Q(\eta)|$ using finite coefficients $d_\zeta$. Apply the inequalities to $PQ$ and divide by $Q(\eta)$. The new coefficient at $\zeta$ is $d_\zeta Q(\zeta)/Q(\eta)$, giving precision $\varepsilon$ for all $P$. It is zero wherever $Q(\zeta)=0$. Thus every middle point is approximable by the restricted family.

Approximate $\theta$ by $S$ to precision $\varepsilon/2$ with coefficients $c_\eta$. Put $B=\sum_\eta|c_\eta|$. Approximate each participating middle point by the restricted family to precision $\varepsilon/(2(B+1))$. Substitution adds error at most $B\varepsilon/(2(B+1))\le\varepsilon/2$, so the total is at most $\varepsilon$. Add contributions to a repeated $\zeta$ to keep one finite coefficient list independent of $P$.

The same inequalities can be used only for polynomials in a smaller set of coordinates, forgetting those used solely to define $Q$. If vectors become equal upon restriction, combine their coefficients. This transfers the nonvanishing tests back to the original target data.

## Lean correspondence

- [`polyApprox_cut`, `polyApprox_trans` and `combine_pf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/Combine.lean#L10) prove the restriction and composition.
- [`congUWG_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/CongruenceOddLevel/NotApartOfOverPair.lean#L111) adds the finite tests and retains the Frobenius and $\ell$-adic power-sum coordinates.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
