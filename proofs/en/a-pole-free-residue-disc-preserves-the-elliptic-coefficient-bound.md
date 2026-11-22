# A pole-free residue disc preserves the elliptic coefficient bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the good Weierstrass model $M$ of a complex period lattice after a field embedding into $\mathbb C_q$, and an integral chart $\ell(X)$ at its origin. Write $\widehat\phi$ for the embedded analytic Taylor series composed with $\ell$. A small point means one in the residue disc of the curve identity. Let $\phi$ be meromorphic and elliptic for the period lattice, analytic at $0$ and at $t$, with no poles that are small. Suppose $t$ is outside the small disc. If $\widehat\phi$ has coefficient bound $B\ge0$ and $\widehat{\phi(\,\cdot+t)}$ has some finite coefficient bound, then every coefficient of $\widehat{\phi(\,\cdot+t)}$ has norm at most $B$.

The elliptic function representation gives
$$
\phi(z)D(x(z))=A(x(z))+C(x(z))y(z),\qquad
D(Z)=\prod_i(Z-x(P_i)),
$$
where the $P_i$ are poles of $\phi$ away from the period lattice, listed with repetitions as needed, and $A,C$ are polynomials. By the small-point test, $|\iota(x(P_i))|_q\le1$, so the embedded coefficients of $D$ have norm at most one. At zero the Weierstrass chart has Laurent expansions $x=X^{-2}x_0(X)$ and $y=X^{-3}y_0(X)$ after embedding, with $x_0,y_0$ integral and unit constant terms. Multiplying the identity by enough powers of $X$ to clear the poles and then dropping any common powers of $X$ shows that for $k=\max(\deg A,\deg C,0)$, the series
$$
\sum_{i=0}^k
  \left(
     \iota(A_i)X^{2(k-i)+3}x_0^i+
     \iota(C_i)X^{2(k-i)}x_0^i y_0
  \right)
$$
has coefficient bound $B$: its product by a power of $X$ is the product of $\widehat\phi$ and an integral series with the poles of $D(x)$ cleared.

The leading degrees in this finite sum are all distinct, the $A_i$ giving odd and the $C_i$ even degrees. Read them in increasing order. At the next leading degree the contributions already read have norm at most $B$ by integrality of their tails, while the new coefficient is multiplied by a unit. Subtract the known contributions from the total coefficient. This proves $|\iota(A_i)|_q,|\iota(C_i)|_q\le B$ for every $i$.

At $t$ the model's translated-coordinate law gives integral chart series $x_t,y_t$ for $x(z+t),y(z+t)$. It also says that the supremum of the norms of the positive-degree coefficients of $x_t$ is one. Thus each denominator factor $x_t-\iota(x(P_i))$ has coefficient norm exactly one. The translated numerator $A^\iota(x_t)+C^\iota(x_t)y_t$ has coefficient norm at most $B$. To cancel the denominator, the supremum norm on bounded power series is multiplicative. One way to see this is to use the norm $\max_j |a_j|_q\rho^j$ for $0<\rho<1$. In each factor take the smallest index attaining its maximum. Their sum gives a unique maximal contribution at that product coefficient, so the weighted norm is multiplicative. As $\rho\uparrow1$, these norms increase to the coefficient supremum. Therefore the denominator product also has coefficient norm one, and the identity at $t$ proves the desired bound on the already bounded translated series.

The elliptic-function representation, the translated-coordinate law, and the Laurent expansions of the chart are the geometric inputs. The cancellation uses the full coefficient norm of the denominator.

### Lean correspondence

- [the elliptic numerator and denominator representation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsEllipticFunctionMulProdEqXyStatement.lean#L7) and [the integral pole expansions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/IntegralWeierstrassChartXyUnitSeriesStatement.lean#L7) are the inputs at zero.
- [`norm_le_of_distinct`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NormLeOfDistinct.lean#L29) gives the leading-degree extraction, with the even and odd orders in `coeff_norm_le`.
- [`chart_hat_coeff_bounds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ChartHatCoeffBoundsStatement.lean#L7) bounds the translated coordinates and gives the denominator norm.
- [`translate_norm_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpTransportedTaylorSeriesTranslateNormLe.lean#L137) combines these steps.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
