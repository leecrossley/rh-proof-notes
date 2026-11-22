# Multiplicative shifts turn theta jets into moments

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $q$ be prime, $S(X)=\sum_{m\ge0}c_mX^m\in\mathbb C_q[[X]]$ have bounded coefficients, and let $\mu$ be the measure with these binomial moments. Let $n,k\ge0$ and $\zeta\in\mathbb C_q$ satisfy $\zeta^{q^n}=1$. Define a continuous function on $\mathbb Z_q$ by
$$
f(x)=\zeta^{\,x\bmod q^n}x^k .
$$
With $D=(1+X)d/dX$,
$$
\mu(f)=\bigl[D^k S\bigl(\zeta(1+X)-1\bigr)\bigr]_{X=0},
$$
where $D$ acts on the composed series. In particular this identity applies to transported theta series in the chart $z=\omega\log(1+X)$. If their torsion operator is the shift $X\mapsto\zeta(1+X)-1$, the right side equals $\omega^k$ times the embedded $k$-th complex derivative of the torsion-translated theta at zero.

At nonnegative integers $j$, $f(j)=\zeta^j j^k$. For the function $j\mapsto u^j$ its $m$-th forward difference at zero is $(u-1)^m$, since shifting $j$ multiplies $u^j$ by $u$. Apply $(u\,d/du)^k$ to this finite difference expression and evaluate at $u=\zeta$. The result is
$$
\Delta^m f(0)
=\left[(u\,d/du)^k(u-1)^m\right]_{u=\zeta}.
$$
A root of unity of $q$-power order reduces to $1$ in residue characteristic $q$, because $X^{q^n}-1=(X-1)^{q^n}$ there. Hence $|\zeta-1|_q<1$. The power series and the derivatives appearing in this finite iterate converge on the open unit disc for $u-1$. Differentiating term by term at $u=\zeta$ is justified by uniform convergence on closed subdiscs, since derivatives of a fixed order bring in integer factors bounded in $q$-adic norm and lower the exponent by at most that order. Now sum the finite difference formula using [the measure construction](bounded-binomial-moments-determine-a-p-adic-measure.md). Under $u=\zeta(1+X)$, $u\,d/du$ is $D$, giving the displayed identity.

For a transported analytic series $G(\omega\log(1+X))$, the formal chain rule gives $D=\omega\,d/dz$ on the composed series. Coefficient embedding commutes with differentiation because the coefficients for derivatives are integers. Iterating and evaluating at zero identifies the constant term with $\omega^k$ times the embedded derivative. This uses the torsion shift identity to replace the shifted series by the actual theta translate.

For $g$ coordinates, suppose the analytic vector is a finite sum of products of powers of one-variable theta translates, each normalized chart series of norm at most one before its scalar coefficient. The table of binomial moments is the finite sum of products of the one-variable coefficients. It is bounded since each product series is bounded and there are finitely many scalars. Applying the one-variable formula in each coordinate gives mixed monomial moments after the torsion twist. An iterated derivative in $k$ arbitrary directions distributes over all assignments of the $k$ directions to the coordinates, by the product rule. The corresponding moment function multiplies the torsion character by $k$ linear forms in the coordinates. Expansion of the product of linear forms uses the same assignments, yielding the required directional derivative moments. In the normalization $\omega=\Omega/\iota(\delta_0)$, the factors $\Omega^{-1}$ in those forms convert $\omega^k$ to the scale from differentiating in the directions divided by $\delta_0$.

### Lean correspondence

- [`twisted_measure_moments_eq_shifted_series_jets`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/TwistedMeasureMomentsEqShiftedSeriesJetsStatement.lean#L7) gives the twisted moment identity.
- [`cpTransportedTaylorSeries_multiplicativeChart`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpTransportedTaylorSeriesMultiplicativeChartStatement.lean#L7) gives the chain rule for the transported series.
- [`measure_of_products`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MeasureOfProducts.lean#L69) builds the finite product measure and obtains its directional moments by expansion over assignments of directions.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
