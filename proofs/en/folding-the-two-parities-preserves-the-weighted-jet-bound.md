# Folding the two parities preserves the weighted jet bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p$ be odd and $v(p)=1$ in the characteristic-zero ultrametric coefficient field. Let $A$ be a finite set of places with an action $z\mapsto P^ez$ of a cyclic group of order $d\ge1$, and $J$ a finite set of matrix-entry indices. Put $I=A\times J$. On $I$ use the multivariable logarithm
$$
\mathscr L_{z,j}(X)=\sum_{k\ge0}p^{-k}X_{P^{-2k}z,j}^{p^{2k}} .
$$
Take a finite set $R\subseteq A$. For each $r\in R$ take a power series $b_r$ on the doubled cyclic set $\mathbb Z/(2d)\mathbb Z$, satisfying the full hypotheses of [the local two-parity coefficient lemma](prime-powers-in-the-jet-coefficient-bound.md) for length $2d$, with signs $\epsilon_r\in\{\pm1\}$. Define the folded exponent by
$$
B(X)=\sum_{r\in R}\frac{\epsilon_r}{2}\sum_{j\in J}
 b_r\bigl((X_{P^sr,j})_{s\bmod 2d}\bigr).
$$
Suppose for an integral series $U$ and a unit $\eta$ that $\Theta(\eta\mathscr L(X))=U(X)\exp(B(\mathscr L(X)))$. This is the product-form hypothesis used for the ordinary, non-signal inert orbits.

Let $\sigma_z\ge0$ satisfy $p^e\sigma_z+\sigma_{P^ez}\ge1$ for every $z$ and every positive odd $e$. Set $\rho=1/(p^2-1)$, $c=1/(p-1)$, and $\gamma=c-\rho$. We claim that for every multi-index $m$ with $m_i\le H$, $H\ge1$,
$$
v(m![X^m]\Theta)\ \ge\
\sum_{(z,j)\in I}m_{z,j}(\gamma-\sigma_z)-|I|(\log_p H+1). \tag{1}
$$

We assign variable $X_{z,j}$ the weight $\rho+\sigma_z$, so that a coefficient $b_n$ of $X^n$ has weighted valuation $v(b_n)+\sum n_{z,j}(\rho+\sigma_z)$. In $b_r$ at uniform weight $\rho$ the bound is $c$, except for monomials $X_s^{p^\alpha}X_{s'}^{p^\beta}$ with opposite parities and $s+\alpha=s'+\beta\bmod 2d$. Those have lower bound $c-1$. Suppose first $\alpha\ge\beta$. Then $e=\alpha-\beta$ is odd, because the representatives have opposite parities modulo the even modulus $2d$, and $P^{s'}r=P^e(P^sr)$. The added weight on the folded monomial is
$$
p^\alpha\sigma_{P^sr}+p^\beta\sigma_{P^{s'}r}
=p^\beta(p^e\sigma_{P^sr}+\sigma_{P^{s'}r})\ge1.
$$
The case $\alpha<\beta$ follows by interchanging the labels. This reasoning includes the case $P^sr=P^{s'}r$: both powers then contribute to the same variable. The ordinary monomials retain their lower bound $c$ because $\sigma\ge0$. Each folded coefficient is a finite sum in its degree, so its weighted valuation is at least $c$. The factors $\epsilon_r/2$ are units because $p$ is odd. It follows that $B$ has weighted valuation at least $c$ and vanishing constant term.

Let $g$ be the formal inverse of $\mathscr L$, which exists by the identity linear term. The recursive inverse calculation in the coefficient lemma works for the shift $z\mapsto P^{-2}z$: each $g_{z,j}$ has weighted valuation at least $\rho$ at uniform variable weight $\rho$, since $(p^{2k}-1)\rho\ge k$. This also holds at our larger weights. Substituting the inverse gives $\Theta(\eta X)=U(g(X))\exp B(X)$. The first factor has weighted valuation at least zero, since $U$ is integral. In $\exp B$ the $k$-th term has weighted valuation at least $kc-v_p(k!)\ge0$. Therefore the product has weighted valuation at least zero, and $\eta$ has no effect on valuations. For each $m_i\le H$, the digit form of Legendre's formula gives $v_p(m_i!)\ge cm_i-(\log_p H+1)$, also when $m_i=0$. Adding these bounds to $v([X^m]\Theta)\ge-\sum_i m_i(\rho+\sigma_i)$ proves (1).

**Lean correspondence.** The folded exponent and product form are [`beS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ColDefs.lean#L23) and [`HasThetaProductForm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/ColDefs.lean#L34). The doubled-orbit parity argument and its weighted bound are [`radii_sum_ge_one_opposite_parity`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/BeSConstantCoeffEqZeroAndWtGe.lean#L19) and [`beS_constantCoeff_eq_zero_and_wtGe`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/BeSConstantCoeffEqZeroAndWtGe.lean#L39). The inverse substitution, multiplication and factorial loss are combined in [`norm_mfact_mul_coeff_le_of_B0S`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/NormMfactMulCoeffLeOfB0S.lean#L69).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
