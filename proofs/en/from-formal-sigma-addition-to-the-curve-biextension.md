# From formal sigma addition to the curve biextension

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $K$ be a characteristic-zero ultrametric normed field with $p$ an odd prime and $\lVert p\rVert=p^{-1}$, and let $\mathcal O$ be its unit ball. Take $g_2,g_3\in\mathcal O$, $s_2\in K$, and a scalar $\epsilon$ of norm one. On the short Weierstrass curve of the [formal curve calculation](the-formal-group-and-laurent-coordinate-of-a-short-weierstrass-curve.md), use the identity parameter, the law $F_E$, the logarithm $\ell$ and the regular part $P$ of $x(\ell^{-1}(z))$. Define $J$ by $J''(z)=-P(z)$, $J(0)=J'(0)=0$. Use the height-two logarithm $\lambda(t)=\sum_{j\ge0}p^{-j}t^{p^{2j}}$ and assume $F(x,y)=\lambda^{-1}(\lambda(x)+\lambda(y))$ is integral. Assume the zero-constant series $\theta(t)=\ell^{-1}(\epsilon\lambda(t))$ has integral coefficients. Define the one-variable exponent
$$
\phi(t)=-J(\epsilon\lambda(t))+\frac{s_2}{2}\bigl(\epsilon\lambda(t)\bigr)^2-\log(\lambda(t)/t).
$$
Lean calls this `phFF`, and its input condition on $\theta$ is integrality of `thetaS`. Then $b_0(x,y)=\phi(F(x,y))-\phi(x)-\phi(y)$ is divisible by $xy$, is symmetric, and is additive in each argument for $F$ modulo $\sim$, where $A\sim B$ means equal constant terms and integral $\exp(A-B)$. This is `F1` for the curve exponent in `first_level_on_curve`. [The local curve exponent and its first-level statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/StatementE.lean#L19)

## Derive the formal sigma addition identity

This calculation only uses the Weierstrass differential equation over $K$. Put $W(z)=z^{-2}+P(z)$, so $W'^2=4W^3-g_2W-g_3$ and $W''=6W^2-g_2/2$ by differentiation. The latter follows by cancellation of $W'$, whose leading term is $-2z^{-3}$. The formal sigma series is $S(z)=z\exp(J(z))$. Since $P$ is even, $P(u)-P(v)$ is divisible by $u^2-v^2$ in $K[[u,v]]$. Thus
$$
N(u,v)=\frac{u^2v^2\bigl(W(v)-W(u)\bigr)}{u^2-v^2}
=1-u^2v^2\frac{P(u)-P(v)}{u^2-v^2}
$$
is a well-defined series of constant term $1$. We prove
$$
J(u+v)+J(u-v)-2J(u)-2J(v)=\log N(u,v).
\tag{1}
$$

Use the differential operator $\Box=\partial_u^2-\partial_v^2$. For $D=W(v)-W(u)$, the difference of its second logarithmic derivatives in the fraction field is
$$
-\frac{W''(u)+W''(v)}{D}
+\frac{W'(v)^2-W'(u)^2}{D^2}
=-2D.
$$
In the last step substitute the differential equations and use $W(v)^3-W(u)^3=D\bigl(W(v)^2+W(v)W(u)+W(u)^2\bigr)$. By second logarithmic derivative of a nonzero element $A$ we mean $\partial_i((\partial_i A)/A)$; this requires no logarithm of $D$. The expression for $N$ uses the product $u^2v^2D/(u^2-v^2)$. The two factors $u-v,u+v$ of the denominator each have difference of second logarithmic derivatives zero. The factor $u^2v^2$ contributes $-2/u^2+2/v^2$. Thus $\Box\log N=2(P(u)-P(v))$. The left side of (1) has the same image under $\Box$, since the terms in $u\pm v$ are killed and $J''=-P$. Both sides and their first $v$-derivatives vanish at $v=0$: on the right $N-1$ is divisible by $v^2$, and on the left the first derivatives of the terms $J(u+v)$ and $J(u-v)$ cancel, with $J'(0)=0$. If $H$ is their difference, the equation $\partial_v^2 H=\partial_u^2 H$ determines its coefficient of $v^{k+2}$ from its coefficient of $v^k$ by dividing by $(k+1)(k+2)$. Both initial coefficients are zero, so $H=0$. [Proof by the formal wave equation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/PderivZeroZeroWeierstrassDifference.lean#L301)

Exponentiate (1) and multiply by the factors $u\pm v,u,v$ in the sigma definition to obtain
$$
\frac{S(u+v)S(u-v)}{S(u)^2S(v)^2}=W(v)-W(u).
$$
The same equality holds with $S_*(z)=S(z)\exp(-s_2z^2/2)$, because the corresponding quadratic parallelogram is zero. In Lean these are `AddSigma` and `AddSgStar`, with all denominators cleared. [The sigma and modified-sigma addition formulas](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/StatementA.lean#L87)

## A parallelogram with integral exponential in the identity parameter

Define
$$
f(t)=-J(\ell(t))+\frac{s_2}{2}\ell(t)^2-\log(\ell(t)/t).
$$
It has zero constant term and $S_*(\ell(t))=t\exp(-f(t))$. Write $x+y$ and $x-y$ in this paragraph for $F_E(x,y)$ and $F_E(x,-y)$. Substituting $u=\ell(x)$, $v=\ell(y)$ in sigma addition gives
$$
(x+y)(x-y)\exp\bigl(-f(x+y)-f(x-y)+2f(x)+2f(y)\bigr)
=x^2 e(y)-y^2 e(x).
$$
Here we used $W(\ell(t))=t^{-2}e(t)$. By the integral two-point factorization, the right hand side equals $-C(x,y)(x+y)(x-y)$, where $-C$ is integral of constant term $1$. Cancel the common nonzero product. Thus the parallelogram $P_f(x,y)=f(x+y)+f(x-y)-2f(x)-2f(y)$ satisfies $P_f\sim0$. [Integrality of the parallelogram exponential](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/InVarAddInVarNeZero.lean#L305)

To deduce additivity of $b_E(x,y)=f(x+y)-f(x)-f(y)$, keep all sums and differences in the law $F_E$. Halving $[1/2]_E=\ell^{-1}(\ell/2)$ is integral because it is the inverse of the integral zero-constant doubling series with linear coefficient $2$, a unit. For three variables $x,y,z$, put $b=(y+z)/2,\ c=(y-z)/2,\ a=x+b$ in the group law. Each of $a,b,c$ is an integral point. Expand the expression
$$
P_f(a,b)-P_f(a,c)+P_f(b,c)-P_f(b,b).
$$
Since $b+c=y,\ b-c=z,\ a-b=x$ and $f(0)=0$, it equals
$$
f(x+y+z)-f(x+y)-f(x+z)-f(y+z)+f(x)+f(y)+f(z).
$$
This is $b_E(x+y,z)-b_E(x,z)-b_E(y,z)$. Every parallelogram on the first display is equivalent to zero by integral substitution, so this defect is equivalent to zero. The second additivity follows by symmetry of $b_E$; vanishing along each axis follows from $f(0)=0$. This is the step from the parallelogram to the cube identity in `f1O`. [The combination of four parallelograms](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/ConstantCoeffEqZeroOfParallelogram.lean#L115) · [The first-level curve cocycle](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/FinalB.lean#L49)

## Transport to the height-two law

The identity $\ell(\theta(t))=\epsilon\lambda(t)$ makes $\theta$ a homomorphism from $F$ to $F_E$, by taking logarithms. On the level of exponents,
$$
\phi(t)-f(\theta(t))=-\log\!\left(\frac{\theta(t)}{\epsilon t}\right).
$$
Indeed the $J$ and quadratic terms of $f(\theta(t))$ agree with those of $\phi$, and $\ell(\theta(t))/\theta(t)=\epsilon\lambda(t)/\theta(t)$. The ratio $\theta(t)/(\epsilon t)$ is integral with constant term $1$ from the assumption on $\theta$ and its linear term. Its logarithm has integral exponential, as does its negative. Thus $\phi\sim f\circ\theta$. Taking coboundaries and then the two additivity defects preserves equivalence, since all the substitutions use integral zero-constant series. The defects for $f\circ\theta$ are the already integral defects for $f$ evaluated at $\theta$ of each variable, by the homomorphism property. The resulting $b_0$ has the asserted additivity, vanishes on both axes and is symmetric. This proves the first-level input used in constructing the mean. The norm of $\theta$ and the one-variable norm law for $\phi$ at scalar units are supplied by further CM arguments. [Comparison of the two exponents and transport of the first-level identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussSumParity/KummerThetaLogarithms/LubinTateLogIsArtinHasse.lean#L223)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
