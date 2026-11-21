# The curve norm law from a prime-to-p isogeny

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Use the [short Weierstrass model](the-formal-group-and-laurent-coordinate-of-a-short-weierstrass-curve.md) over a characteristic-zero ultrametric field $K$ with $2$ of norm one. Let $\mathcal O$ be its integral ring. Keep its integral $g_2,g_3$, logarithm $\ell$, parameter $t$, and $x(t)=t^{-2}e(t)$. In the additive coordinate $z=\ell(t)$, write $W(z)=x(\ell^{-1}(z))$. Use the modified sigma series $S_*(z)=z\exp(J(z)-s_2 z^2/2)$ and the exponent $f$ with $S_*(\ell(t))=t\exp(-f(t))$ from [the first-level curve identity](from-formal-sigma-addition-to-the-curve-biextension.md). Here $s_2\in K$.

Take $\alpha\in K$ of norm one and $\alpha'\in K$. Let a finite set $I$ of size $N-1$ index integral affine points $P=(x_P,y_P)$ of the curve, with a permutation taking $P$ to $-P=(x_P,-y_P)$. Retain indices under this permutation, including when $P=-P$. Let $W_P(z)$ be the $x$-coordinate of the point with additive parameter $z$, translated by $P$ using the chord law. Assume the distribution identity, in the Laurent series field in $z$,
$$
\alpha^2 W(\alpha z)=W(z)+\sum_{P\in I}\bigl(W_P(z)-x_P\bigr),
$$
and the two scalar equalities
$$
N=\alpha\alpha',\qquad \sum_{P\in I}x_P=(\alpha^2-N)s_2.
$$
These are the isogeny and sum inputs, with the normalizing shift $b_2/12=0$ for the short curve. For $M_\alpha(t)=\ell^{-1}(\alpha\ell(t))$, we prove that $M_\alpha$ is integral and that
$$
f(M_\alpha(t))\sim N f(t).
$$
This is the short-model instance of `EndIntFromDatum` and `PhNormFromDatum` used by `curveNorm`. The hypotheses concern a formal distribution identity and integral affine points. For example in the CM application $I$ consists of the nonidentity points in the kernel of an endomorphism of degree $N$ prime to $p$. [The norm law specialized to the short curve](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/SecondLogDerivativeUnique.lean#L218)

## Integrality of the endomorphism

For a point $P$ from the hypothesis the affine slope of the chord through $(x(t),y(t))$ and $P$ is
$$
m=-\frac1t\,\frac{e(t)+y_P t^3}{e(t)-x_Pt^2}.
$$
The numerator and denominator of the fraction are integral series with constant term $1$ and linear term zero. Therefore
$$
W_P(\ell(t))=m^2-x(t)-x_P
=t^{-2}\!\left(\frac{(e(t)+y_Pt^3)^2}{(e(t)-x_Pt^2)^2}-e(t)\right)-x_P
$$
is integral: the parenthesized expression is divisible by $t^2$. Its value at zero is $x_P$, from the coefficient $2x_P$ at $t^2$ inside the parentheses. This is the integral translated coordinate in the distribution identity.

Write $M_\alpha=\alpha t G(t)$, with $G(0)=1$ since the linear term of $M_\alpha$ is $\alpha t$. Substituting $z=\ell(t)$ and multiplying the distribution identity by $t^2$ gives
$$
e(M_\alpha)=G^2 V,\qquad
V=e(t)+t^2\sum_P(W_P(\ell(t))-x_P).
$$
The series $V$ is integral with constant term $1$. In degree $n>0$, $e(\alpha tG)$ depends only on coefficients of $G$ in degrees below $n$, because each positive power of $\alpha tG$ includes a power of $t$. The degree-$n$ coefficient of $G^2V$ is $2G_n$ plus expressions in lower degrees. Induction gives $G_n\in\mathcal O$ since $2$ is a unit and $\alpha$ is integral. Thus $M_\alpha$ is integral. This is the coefficient argument for the formula from the translated $x$-coordinates. [Integral endomorphism from the translated-coordinate formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/IntegralEndomorphismFromDatum.lean#L157)

## The sigma product and its constant

We give the comparison in the additive coordinate so the second derivative is ordinary. For $X=W(z)$ and $a=x_P$, the affine chord formula for $P$ and $-P$, together with the Weierstrass equation, gives
$$
(\log(X-a))''=2X-W_P(z)-W_{-P}(z).
\tag{1}
$$
For a Laurent series the second logarithmic derivative in (1) means $((X-a)'/(X-a))'$. To verify it multiply both sides by $(X-a)^2$. The left becomes $(6X^2+2A)(X-a)-4(X^3+AX+B)$, where $A=-g_2/4,\ B=-g_3/4$. On the right the two squared slopes have sum $2((X^3+AX+B)+(a^3+Aa+B))/(X-a)^2$; the terms from subtracting $X+a$ in each reflected $x$-coordinate give $(4X+2a)(X-a)^2$. The two expressions agree by polynomial expansion.

Now $(\log S_*)''=-W-s_2$. Apply the second logarithmic derivative to
$$
\frac{S_*(\alpha z)^2}{\alpha^2 S_*(z)^{2N}\prod_{P\in I}(W(z)-x_P)} .
$$
Because the set is closed under negation, (1) contributes $2(N-1)W(z)-2\sum_P W_P(z)$ in the logarithmic derivative of the denominator. The result for the ratio is
$$
-2\alpha^2 W(\alpha z)+2W(z)+2\sum_P W_P(z)-2(\alpha^2-N)s_2=0
$$
by the distribution and sum hypotheses. The ratio itself is a power series unit of constant term $1$: the orders and leading coefficients agree by $W(z)\sim z^{-2}$ and $S_*(z)=z+O(z^3)$. It is even, since $W$ is even and $S_*$ odd. Its formal logarithm has second derivative zero, so it is linear, and evenness and the zero constant term force it to be zero. The ratio is therefore $1$. This is the squared isogeny product. The use of the sum of the $x_P$'s is exactly the cancellation of its quadratic discrepancy. [Sum condition for the squared isogeny formula](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/HasSecondLogDerivPowerSeriesExp.lean#L311)

Finally substitute $z=\ell(t)$. The squared formula, using $S_*(\ell(t))=t\exp(-f(t))$, becomes
$$
G(t)^2\exp\!\left(-2(f(M_\alpha(t))-Nf(t))\right)
=\prod_P(e(t)-x_Pt^2).
$$
Every factor on the right and $G$ is an integral unit of constant term $1$. Dividing gives an integral exponential for twice the negative discrepancy. Taking its inverse and then its formal square root preserves integrality, by the coefficient recursion for a square root of constant term $1$ with $2$ a unit. This proves the norm law for $f$. [Removing the squared factors and the factor two](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/USideB.lean#L226)

In the height-two parameter, take the integral $\theta=\ell^{-1}(\epsilon\lambda)$ and the exponent $\phi=\mathrm{phFF}$ of the first-level identity, and assume $\alpha$ is fixed by $\sigma^2$ with $\alpha'=\sigma(\alpha)$. Taking logarithms gives $\theta\circ[\alpha]=M_\alpha\circ\theta$, where $[\alpha]t=\lambda^{-1}(\alpha\lambda(t))$. Both $\theta$ and $[\alpha]$ are integral. Substitute $\theta$ in the norm law for $f$, and substitute $[\alpha]$ in the relation $\phi\sim f\circ\theta$; multiplying this relation by the integer $N$ also preserves it. It follows that $\phi([\alpha]t)\sim\alpha\sigma(\alpha)\phi(t)$, the required unit norm relation in `CurveData`. [Transport of the norm relation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/CoboundaryCommutesHomomorphism.lean#L410)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
