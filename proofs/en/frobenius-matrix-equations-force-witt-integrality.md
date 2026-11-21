# Frobenius matrix equations force Witt integrality

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88Frobenius%E7%9F%A9%E9%98%B5%E6%96%B9%E7%A8%8B%E8%BF%AB%E4%BD%BFWitt%E7%B3%BB%E6%95%B0%E6%95%B4%E5%8C%96.md)

Let $\ell$ be prime, $k$ a perfect valued field of characteristic $\ell$ with valuation ring $R$, and $B=W(k)$, $B^+=W(R)$ the $\ell$-typical Witt rings. Let $\Phi$ be Witt Frobenius, acting entrywise. For finite sizes $d,e$, assume
$$
Z\in M_{d,e}(B),\quad P\in M_d(B^+),\quad P'\in M_e(B^+),\quad
Y\in M_{d,e}(B^+),\qquad \Phi(Z)=PZP'+Y.
$$
Then $Z\in M_{d,e}(B^+)$. The result holds after tensoring the rings with any finite free $\mathbb Z_\ell$-algebra $O$, using Frobenius on the Witt factor.

**Proof.** Reduce modulo $\ell$ and use lower-case names for the images. An entry of $z$ of maximal absolute value $M>1$ would give absolute value $M^\ell$ on the left. The right-hand sum has absolute value at most $M$ by the ultrametric inequality: each product contains at most one factor from $z$ and all other factors have absolute value at most one. Thus $z$ is integral.

Lift $z$ to the matrix $Z_0$ of Teichmüller representatives over $B^+$ and write $Z=Z_0+\ell Z_1$. The ring $R$ is perfect because an $\ell$-th root of an integral element is integral. Hence $W(R)/\ell=R\hookrightarrow k=W(k)/\ell$. In
$$
\ell(\Phi(Z_1)-PZ_1P')=PZ_0P'+Y-\Phi(Z_0)
$$
the right side belongs to $B^+$ and is divisible by $\ell$ in $B$. By the injection of residue rings it is divisible in $B^+$ as well. Cancel $\ell$, which is regular in $B$, to get an equation of the same type for $Z_1$. Iterating shows each finite Witt truncation of $Z$ is integral, so each Witt coordinate is in $R$. Empty matrices satisfy the conclusion directly.

For coefficients in $O$, use a $\mathbb Z_\ell$-basis of $O$ to replace each scalar by its block of multiplication on $O\otimes B$. This preserves the equation and commutes with Frobenius. The proved case gives integral blocks, and applying a block to the coordinate vector of $1$ recovers the scalar in $O\otimes B^+$. The application is $k=\mathbb C_\ell^\flat$, where the lemma checks the matrix and its inverse in a Wach comparison.

The tilt valuation ring is `valuationRing_tilt`. The maximum argument is `residue_integral`, the lift is `step` and the iteration is `integral_of_frobenius`. `eq_sum_regRep` and `integrality_baseChange` handle the coefficient extension in `frobenius_integrality_coeff`. [Tilt](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L92) · [Residue calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L102) · [Lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L144) · [Iteration](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityWittTiltAinf.lean#L239) · [Base change](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/FrobeniusIntegralityTensorAinfCoefficients.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
