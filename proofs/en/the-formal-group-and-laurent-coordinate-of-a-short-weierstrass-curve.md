# The formal group and Laurent coordinate of a short Weierstrass curve

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $K$ be a characteristic-zero ultrametric normed field, $\mathcal O$ its integral ring, and $2$ a unit of $\mathcal O$. For $g_2,g_3\in\mathcal O$ put $A=-g_2/4,\ B=-g_3/4$ and use the short Weierstrass model $y^2=x^3+Ax+B$. At its identity use the parameter $t=-x/y$. There is a formal group law $F_E(t,s)\in\mathcal O[[t,s]]$ whose inverse is $-t$, given by addition of points near the identity. Its logarithm $\ell$ has $\ell(0)=0,\ \ell'(0)=1$ and $\ell(F_E(t,s))=\ell(t)+\ell(s)$. If $z=\ell(t)$, one has
$$
x(t)=t^{-2}e(t),\qquad e(t)\in1+t^4\mathcal O[[t^2]],\qquad
x(\ell^{-1}(z))=z^{-2}+P(z),
$$
where $P$ is even with $P(0)=0$. With $W(z)=z^{-2}+P(z)$ one has
$$
(W')^2=4W^3-g_2W-g_3.
$$
Also, the regular coefficient $e$ satisfies the integral factorization
$$
s^2e(t)-t^2e(s)=C(t,s)F_E(t,s)F_E(t,-s),\qquad
C\in\mathcal O[[t,s]],\quad C(0,0)=-1 .
$$
These are the short-model instances of the law, Weierstrass equation and coordinate factorization used by `bridgeLaw`, `bridgeWp` and `bridgeCurve`. The statements at the cited Lean declarations also cover general Weierstrass coefficients. [The three formal curve inputs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/StatementJ.lean#L13) · [Assembly of the curve inputs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/TwoTorsionU.lean#L14)

## Chords in a regular chart

In the projective chart $[t:-1:w]$ at the identity, the curve equation becomes
$$
w=t^3+Atw^2+Bw^3 .
$$
It has a unique solution $w(t)$ with zero constant term, by solving one coefficient at a time. The terms on the right after $t^3$ use only lower degrees. The solution is integral, is odd by uniqueness, and has $w(t)=t^3+O(t^7)$. Thus $x=t/w(t)=t^{-2}e(t)$, $y=-1/w(t)$, with $e(t)=(w(t)/t^3)^{-1}$ integral, even, and $1+O(t^4)$.

To add the points with parameters $t,s$, form the chord in this chart. Its slope $\Lambda=(w(t)-w(s))/(t-s)$ and intercept $N=w(t)-\Lambda t$ are integral formal series, since each difference quotient of a monomial is a polynomial. The slope begins at degree two and the intercept at degree three. Substitution $w=\Lambda u+N$ in $u^3+Auw^2+Bw^3-w=0$ yields a cubic in $u$ with leading coefficient $c_3=1+A\Lambda^2+B\Lambda^3$ and coefficient $c_2=2A\Lambda N+3B\Lambda^2N$ at $u^2$. Two roots are $t,s$. The third is $-t-s-c_2/c_3$, by comparing the sum of the roots. Reflection $y\mapsto-y$ sends the parameter to its negative, so the addition law is $F_E=t+s+c_2/c_3$. The denominator has constant term $1$, proving integral coefficients. For $s=0$, the intercept is zero, so $F_E(t,0)=t$. For $s=-t$ the intercept is again zero since $w$ is odd, so $F_E(t,-t)=0$. [The chart, chord, and third intersection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/CompInv.lean#L36)

## The logarithm and the Weierstrass equation

The invariant differential in the parameter is
$$
\frac{dx(t)}{2y(t)}=\left(1-\frac{t e'(t)}{2e(t)}\right)dt.
$$
Its coefficient is $1+O(t^4)$. Integrating with constant term zero defines $\ell$. This is the logarithm `logSer`. Indeed the coefficient of $dt$ is $1/(1-2Atw-3Bw^2)$, as follows by differentiating $w=t^3+Atw^2+Bw^3$ and substituting $x=t/w,\ y=-1/w$. The denominator is `fw` in the short model. [Logarithm in the identity parameter](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/CompInv.lean#L103)

For additivity, in the affine chart fix a second point $(a,b)$, so the slope of the chord with $(x,y)$ is $m=(y-b)/(x-a)$. The reflected third point has
$$
x_3=m^2-x-a,\qquad y_3=-y+m(x-x_3).
$$
Write $L(X)=y+m(X-x)$. The polynomial $X^3+AX+B-L(X)^2$ equals $(X-x)(X-a)(X-x_3)$. Differentiating in $X$ at $x$ gives $3x^2+A-2ym=(x-a)(x-x_3)$. Also $2y\,dy/dx=3x^2+A$. Since $dm/dx=(dy/dx-m)/(x-a)$, these identities give $2y\,dm/dx=x-x_3$. Now $y\,dx_3/dx=2ym\,dm/dx-y=y_3$. Hence $dx_3/(2y_3)=dx/(2y)$ with the second point held fixed. The affine and regular-chart chord formulas use the same line and the same third intersection, so this identity holds when the branches at $t,s$ are substituted. Calculations with the affine slope can take place in the fraction field of $K[[t,s]]$, and the resulting differential equality is one between regular series. It gives $\partial_t\bigl(\ell(F_E(t,s))-\ell(t)\bigr)=0$. In characteristic zero this difference is independent of $t$; at $t=0$ it is $\ell(s)$. This proves the logarithm identity. All group law identities then follow by inversion of $\ell$. [Formal group logarithm and group law](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/FglInvariant.lean#L14)

Let $t=\ell^{-1}(z)$. The coefficient of $dt$ in the differential is even, so $\ell$ and its inverse are odd. Since the inverse has $t=z+O(z^5)$ and $e(t)=1+O(t^4)$, $x(t)$ has the form $z^{-2}+P(z)$ with $P$ even and zero constant term. The differential identity gives $W'(z)=2y(t)$. The equation of the curve therefore gives $(W')^2=4W^3-g_2W-g_3$, which is `IsWp` after multiplication by $z^6$.

## Factor the two-point difference

Because $e$ is even, $s^2e(t)-t^2e(s)$ is divisible by $s^2-t^2$ over $\mathcal O[[t,s]]$. To see this write it in $t^2,s^2$ and set them equal. Its quotient has constant term $1$, from the terms $s^2-t^2$. Likewise $F_E(t,s)$ is divisible by $t+s$ over $\mathcal O$, because $F_E(t,-t)=0$; apply the integral change of variables from $t,s$ to $t,t+s$. Its quotient has constant term $1$, by the linear part of $F_E$. The same argument gives $F_E(t,-s)/(t-s)$ of constant term $1$. These two quotients have integral inverses, so dividing the difference by their product and using $s^2-t^2=-(t+s)(t-s)$ gives $C$ as asserted. For this model the shift $b_2/12$ used in `CurveHyp` is zero. [The curve identity in the formal chart](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/WeierstrassTwoTorsion/WeierstrassSubstitution/BridgeJ.lean#L82)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
