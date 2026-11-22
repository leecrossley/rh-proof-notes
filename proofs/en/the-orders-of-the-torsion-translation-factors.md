# The orders of the torsion translation factors

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be prime, $R=\mathcal O_{\mathbb C_p}$, and $W:y^2=x^3+Ax+B$ with $A,B\in R$ and unit discriminant. Let $P,Q\ne O$ lie in a finite subgroup killed by an integer prime to $p$. In the formal identity chart at $O$, write $x(t),y(t)$ for the Laurent coordinates with $t=-x/y$. Let $x_P(t)$ be the formal expansion of the $x$-coordinate of the point obtained by adding $P$ to the chart point $t$. Then $x_Q-x_P(t)$ is $t^e$ times an integral power series with unit constant term, with
$$
e=\begin{cases}
0,&P\ne Q,\ P\ne-Q,\\
1,&P=\pm Q,\ [2]Q\ne O,\\
2,&P=\pm Q,\ [2]Q=O.
\end{cases}
$$
This is the short-model version of `FacShape`. At $P=O$ the corresponding statement is that $t^2(x_Q-x(t))$ is integral with unit constant term.

**Integrality and the first coefficients.** The finite nonzero points have integral coordinates by the [prime-to-$p$ torsion argument](why-prime-to-p-torsion-has-integral-unramified-coordinates.md). The chart expansion gives $x(t)=t^{-2}a(t)$ with $a(t)\in1+t^4R[[t]]$, and $y(t)=-t^{-3}a(t)$. If $x_P,y_P$ denote the constant affine coordinates of $P$, the chord slope is
$$
m=-t^{-1}\frac{a(t)+y_Pt^3}{a(t)-x_Pt^2}.
$$
The denominator has constant $1$, and $x_P(t)=m^2-x(t)-x_P$. Thus the terms $t^{-2}$ cancel and all remaining coefficients are integral. The relation $x(t)=t^{-2}-A/x(t)-B/x(t)^2$ gives $x(t)=t^{-2}-At^2+O(t^4)$. Expansion of the slope square then gives
$$
x_P(t)=x_P+2y_Pt+(3x_P^2+A)t^2+O(t^3).
$$
At $P=O$, $t^2(x_Q-x(t))=x_Qt^2-a(t)$ gives the stated unit directly.

**The units.** Suppose $P\ne\pm Q$. Their $x$-coordinates are different by the curve equation. If the difference had norm less than $1$, then the two $y$-coordinates would be congruent or opposite modulo the maximal ideal. If at least one of the $y$-coordinates has unit norm, one of the two numerators $y_P-y_Q,\ y_P+y_Q$ is a unit, since $2$ is a unit. The corresponding slope for $P+Q$ or $P-Q$ has norm greater than $1$, giving a nonintegral $x$-coordinate of the sum or difference. This contradicts the torsion bound, since both sums are nonzero. If neither $y$ is a unit, the common residue of the $x$-coordinates is a simple root of the cubic, because the discriminant is a unit. Subtract the equations:
$$
(y_P-y_Q)(y_P+y_Q)=(x_P-x_Q)(x_P^2+x_P x_Q+x_Q^2+A).
$$
Both slopes $(y_P\pm y_Q)/(x_P-x_Q)$ must be integral by the same torsion bound. Hence the second factor on the right equals their product times $x_P-x_Q$, of norm less than $1$. This contradicts the nonzero derivative at the common residue. Thus $x_Q-x_P$ is a unit.

For $P=\pm Q$, the constant term vanishes. If $[2]Q\ne O$, then $y_P$ is a unit: if it had norm less than $1$ the cubic derivative at $x_P$ would be a unit and the duplication slope $(3x_P^2+A)/(2y_P)$ would have norm greater than $1$. This would give a nonintegral $x$-coordinate of $[2]P$. Now $2y_P$ is a unit, so the linear term gives $e=1$. If $[2]Q=O$, then $y_P=0$ and $3x_P^2+A$ is a unit by the good discriminant. The quadratic term gives $e=2$.

**Lean correspondence.** The general Weierstrass statements of the factor shapes are [`XTShape` and `FacShape`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/StatementT.lean#L9). The addition-series proof of the first coefficients is used in [`xTShape` and `facShape`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/FacShapeZero.lean#L20). The unit checks, including the versions for general Weierstrass models, are in [`nonsingular_norm` and the following three lemmas](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/NonsingularNorm.lean#L132) and are combined in [`FacShape_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/ConstantCoeffInvTDen.lean#L53). This argument supplies the factor valuations in the torsion recurrence.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
