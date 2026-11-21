# A selected root gives a spectral operator on one character block

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%80%89%E5%AE%9A%E6%A0%B9%E7%9A%84%E8%B0%B1%E6%8A%95%E5%BD%B1%E5%8F%AA%E5%9C%A8%E4%B8%80%E4%B8%AA%E5%AD%97%E7%AC%A6%E5%9D%97%E6%9C%89%E5%80%BC.md)

**Proposition.** Let $e_B$ be an idempotent on a finite-dimensional $K$-space $V$, and let $X_0=e_BX_0e_B$. Suppose $X_0$ on $e_BV$ has characteristic polynomial $\prod_{0\le j<t}(T-\lambda_j)$ with $t\ge1$ and distinct $\lambda_j\in K$. Define
$$
E=e_B\prod_{1\le j<t}(X_0-\lambda_j e_B),\qquad
\delta=\prod_{1\le j<t}(\lambda_0-\lambda_j).
$$
Then $E$ acts by $\delta\ne0$ on the $\lambda_0$ line and by zero on every other eigenline and on $(1-e_B)V$. Thus $E$ has rank one and $E^2=\delta E$.

The idempotent gives the direct sum of its image and kernel. On its image the eigenlines give a basis because there are $t$ distinct eigenvalues in a $t$-dimensional space. The factor on the $\lambda_a$ line has product $\prod_{1\le j<t}(\lambda_a-\lambda_j)$, which equals $\delta$ for $a=0$ and vanishes otherwise. The outside factor $e_B$ kills the complement, including when the product is empty. The corner polynomial is $\det(Te_B-X_0+(1-e_B))$ because this operator is the identity on the complement. If the matrices are integral over a DVR $\mathcal O$, that monic polynomial has integral coefficients, and its roots in $K=\operatorname{Frac}\mathcal O$ belong to $\mathcal O$ by integral closedness.

At the good point $\pi$ the order of the roots is $\lambda_j=\chi_1(g_0)\epsilon(g_0)^{-j}$, matching character blocks $1,\ldots,t$. Thus $E$ acts only on block one with $\Delta=\delta(\pi)$. In the block-ring relation $E=\sum_g a_g r(g)$, evaluate on block one to get $\sum_g a_g(\pi)\chi_1(g)=\Delta$. These are the equal scalars used in the [coboundary calculation](coboundary-cost-of-two-denominators.md). Their valuation is computed in the [denominator lemma](valuation-of-the-denominator-between-blocks.md).

The other idempotent $e_1(\pi)$ is integral and rank one in the zero block. The image lattice $L=e_1\mathcal O^r$ is a direct summand and free of rank one. Hence the image of $e_1$ on $(K/\mathcal O)^r$ is $KL/L\simeq K/\mathcal O$, giving the one-coordinate cost for each zero-block column generator.

## Lean correspondence

- `eMat` computes the operator and `rootsInt` gives integral roots. `ring_objects_of_matrix_data` checks the good-point scalars. [Operator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/IdemFactor.lean#L123) · [Roots](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/IdempotentImageSurjective.lean#L108) · [Scalar comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/RingObjectsOfMatrixData.lean#L109)
- `idemKO` identifies the quotient-lattice image of $e_1$. [Quotient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/IdemKO.lean#L12)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
