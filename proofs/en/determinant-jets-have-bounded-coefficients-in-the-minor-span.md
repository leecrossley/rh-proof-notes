# Determinant jets have bounded coefficients in the minor span

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $A$ be a finite set of places, with one Young diagram $\nu_z$ at each place $z$. At that place $X$ has rows indexed by the nonnegative integers and $N_0$ columns, and $Y$ is an $N_0\times N_1$ matrix of formal variables. For a column of $\nu_z$ of height $h$, choose $h$ increasing indices $I$ of columns of $Y$, and use the minor of $XY$ with its first $h$ rows and columns $I$. Multiply over all diagram columns and places, obtaining $G_I(X,Y)$. Let $\Theta(Y)$ be an arbitrary formal power series over $\mathbb C_p$, and apply the linear functional $Y^m\mapsto m![Y^m]\Theta$ to obtain $Q_I(X)$. Assume each monomial coefficient of $Q_I$ has norm at most $p^{-B}$.

The conclusion is that $Q_I$ can be written as a finite sum of products of the corresponding initial-row minors of $X$, with coefficients of norm at most $p^{-B}$. This is the implication from `KvalGe` to `ExpansionCoeffValuationGe`. We use the same norm bound on every coefficient of the expansion. Any bound on the coefficients of such an expansion also implies the original bound, since the minors have integer coefficients.

For one minor, the Cauchy–Binet formula gives
$$
\det(XY)_{[1,h],I}=\sum_{J\subseteq[1,N_0],\ |J|=h}
 \det X_{[1,h],J}\det Y_{J,I}.
$$
This follows by expanding the determinant multilinearly. An index list with repetition gives zero, and, for a fixed increasing $J$, summing its permutations gives the second determinant. It also covers $h>N_0$ by the empty sum. Taking products and applying the coefficient functional writes $Q_I$ in the $\mathbb C_p$-span of the products $M_J(X)$ of initial-row minors, without a bound yet on the coefficients in this expression.

For each place $z$, the span of its minor products has a projection $T_z$ over $\mathbb Z$, by [the monic-basis proof](initial-minors-have-an-integral-monic-basis.md) after transposing the variables. Its image is the integral span of those products, and it fixes each product. The full polynomial ring has the monomials $X^m=\prod_z X_z^{m_z}$ as a basis. Define $T(X^m)=\prod_z T_z(X_z^{m_z})$ and extend linearly. This is an integral map whose image is in the span of the $M_J$. Each $M_J$ factors over the places, so the map fixes it. Extending scalars to $\mathbb C_p$, $T$ fixes $Q_I$ as well.

For each $m$ occurring in $Q_I$, expand $T(X^m)=\sum_J a_{m,J}M_J$ with $a_{m,J}\in\mathbb Z$. By applying $T$ to $Q_I$ in its monomial expression, we obtain the desired expansion with coefficients
$$
c_J=\sum_{m} [X^m]Q_I\ a_{m,J}.
$$
Every term has norm at most $p^{-B}$ and the sum is finite, so this same bound holds for $c_J$. This argument avoids making any independence assumption on the full generating list $(M_J)$.

**Lean correspondence.** Span membership is [`minorXZ_expand`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MonomialFrameSpan/BasisMonomialsApply.lean#L93) and [`stepSpan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MonomialFrameSpan/BasisMonomialsApply.lean#L159). The projection across the places is [`projZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MonomialFrameSpan/SatProj.lean#L194). Extending it to the coefficient field and keeping the norm bound is [`stepSat_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MonomialFrameSpan/SatFin.lean#L12). The implication in both directions is assembled in [`genFrameSB_of_span`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/MonomialFrameSpan/GenFrameSBOfSpan.lean#L10) and used by the [kernel form theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/Divisibility/OrbitPlaces.lean#L1621).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
