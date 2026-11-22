# A split CM isogeny forces integrality of the even theta series

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $d$ be prime with $d\equiv7\bmod16$, let $q$ be split in the imaginary quadratic maximal order $\mathcal O$ of discriminant $-d$, and let $M$ be its good Weierstrass model with embedding $\iota:\mathbb C\to\mathbb C_q$ and multiplicative chart of scale $\omega$. Let $\theta$ be the normalized even theta of that order, with $\theta(0)=1$. Then the Taylor series of $\theta$, embedded by $\iota$ and composed with $\omega\log(1+X)$, is integral.

Choose a nonzero $\alpha\in\mathcal O$ that is congruent to $1$ at the chosen place above $q$ and to $0$ at its conjugate. These choices follow from the two relatively prime ideals. In the chosen embedding its image $a$ lies in $\mathbb Z_q^\times$ because the place is split. The integer $m=\alpha\bar\alpha>0$ is divisible by $q$ and hence $m\ge2$. The CM isogeny quotient theorem for the even theta supplies an elliptic quotient
$$
\theta(\alpha z)=\theta(z)^m\,\varepsilon(z)
$$
near zero, where $\varepsilon$ is analytic there and has integral chart series. This is the geometric input. The quotient at zero is one by the normalization.

Write $S(X)$ for the chart series of $\theta$, $E(X)$ for that of $\varepsilon$, and $P_a(X)=(1+X)^a-1$. The chart identity for scaling by $\alpha$ gives
$$
S(P_a(X))=S(X)^mE(X).
$$
Here $P_a$ has integral coefficients, zero constant term and linear coefficient $a$. The series $S,E$ have constant term $1$. Suppose by induction that the coefficients of $S$ below degree $n\ge1$ are integral. In degree $n$, the only contribution involving $s_n$ on the left comes from $s_nP_a(X)^n$, giving $a^n s_n$. On the right it arises by choosing $s_n$ from one of the $m$ factors and constants everywhere else, giving $ms_n$. All other contributions in this degree use integral coefficients of $E,P_a$ and earlier coefficients of $S$. Thus $(a^n-m)s_n$ is integral. The difference $a^n-m$ is a unit because $|a^n|_q=1$ and $|m|_q<1$. Dividing proves integrality in degree $n$, and induction proves the assertion. This supplies the base series bound used in [the simultaneous theta translation inequality](an-elliptic-quotient-keeps-cancellations-in-a-theta-translate-sum.md).

### Lean correspondence

- [`theta_series_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CmEvenThetaSeriesChartCoeffIntegral.lean#L15) chooses $\alpha$, gets the norm comparison on $m$, and applies coefficient uniqueness to the functional equation.
- [the integral isogeny quotient](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ThetaNormQuotientEllipticUnitSeriesStatement.lean#L7) supplies $\varepsilon$.
- [the multiplicative scaling law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/CpTransportedTaylorSeriesMultiplicativeChartStatement.lean#L7) gives substitution by $P_a$.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
