# The half-period phase has an integral third difference at two

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use a good integral Weierstrass model $W$ in residue characteristic $2$, over a characteristic-zero ultrametric field with integral ring $R$. Let $T\ne0$ be a point of order two with integral affine coordinates $(x_T,y_T)$. In the formal parameter $t=-x/y$, write $x(t)=e(t)/t^2$ with $e\in1+tR[[t]]$. Use the normalized logarithm $\ell$ and formal law $F$. In additive coordinates $Z$, the Weierstrass function is $\wp(Z)=x(\ell^{-1}Z)+b_2/12$. Put $E=\wp(T)=x_T+b_2/12$, $k=3E^2-g_2/4$, $g(t)=e(t)-x_Tt^2$, and
$$
w(Z)=\frac1{\wp(Z)-E},\qquad w(\ell(t))=\frac{t^2}{g(t)}.
$$
Here $k=3x_T^2+(b_2/2)x_T+b_4/2$ is integral for this order-two point. Indeed $2y_T+a_1x_T+a_3=0$, and $b_2x_T+b_4=4a_2x_T+2a_4+a_1(a_1x_T+a_3)$ is divisible by $2$ in $R$. Also $g$ and its inverse are integral with constant $1$.

Let $\phi_O$ be the phase of the modified sigma series with its simple zero at the origin, normalized by $\Sigma_O(\ell(t))=t\exp(-\phi_O(t))$. Let $\Sigma_E$ be the normalized even half-period theta, with constant $1$, and set $\Sigma_E(\ell(t))=\exp(-\phi_E(t))$. The half-period addition identity is
$\Sigma_E(Z)^2=\Sigma_O(Z)^2(\wp(Z)-E)$;
equivalently $2(\phi_E-\phi_O)=-\log g$. Both phases have zero constant term. We prove that the additive defect of $\phi_E$,
$B_E(x,y)=\phi_E(F(x,y))-\phi_E(x)-\phi_E(y)$,
is biadditive modulo the subgroup of zero-constant exponents with integral exponential. We use [the third-difference identity for $\phi_O$](the-three-point-sigma-identity-gives-the-odd-cube-at-two.md), which follows from the two- and three-point sigma identities over the integral Weierstrass law. For the even phase the proof below avoids dividing an integral exponent congruence by $2$.

Define $\eta(t)=(e(t)+y_Tt^3)/g(t)$ and $L(x,y)=y\eta(x)+x\eta(y)-a_1xy$. With $D(x,y)=1-k\,w(\ell(x))w(\ell(y))$ the addition calculation gives
$$
g(F(x,y))L(x,y)^2=g(x)g(y)F(x,y)^2 D(x,y)^2. \tag{1}
$$
Here is the calculation. The differential equation for $\wp$ and $4E^3-g_2 E-g_3=0$ give
$(w')^2=4w(1+3Ew+kw^2)$.
For the square root $s=\sqrt w=Z+\cdots$,
$$
s(U+V)(1-ks(U)^2s(V)^2)=s(U)s'(V)+s(V)s'(U).
$$
This formal addition identity follows by verifying the equation in $V$ for the quotient of the right side by $1-ks(U)^2s(V)^2$. On differentiating and squaring, use $s'^2=1+3Es^2+ks^4$ and $s''=3Es+2ks^3$; the result is $s'^2=1+3Es^2+ks^4$ for that quotient as well. Its value at $V=0$ is $s(U)$ and its derivative there is $s'(U)$. Successive formal coefficients are unique because $s'(U)$ is a unit in the characteristic-zero series ring in $U$. Squaring yields the corresponding addition formula for $w$. In the parameter $t$, differentiation of $w=(\wp-E)^{-1}$ and $\wp'(\ell(t))=2y(t)+a_1x(t)+a_3$ gives
$$
 t w'(\ell(t))=w(\ell(t))(2\eta(t)-a_1t).
$$
In this equality use $y(t)=-x(t)/t$ and $2y_T+a_1x_T+a_3=0$ to combine the constant terms. Substituting this derivative and $w(\ell(t))=t^2/g(t)$ into the squared addition identity, and cancelling the common $4x^2y^2$, gives (1).

We claim $L=F\nu$ with $\nu\in1+(x,y)R[[x,y]]$. Put the formal inverse $[-1]x$ in place of $y$ in (1). It annihilates $F$, and the factor $g(F)$ becomes $1$, so $L(x,[-1]x)=0$. The integral substitution $y\mapsto F([-1]x,y)$ is undone by $y\mapsto F(x,y)$. It transforms $L$ into a series that vanishes at $y=0$, so is divisible by $y$ over $R$. Undo the substitution to obtain the factorization by $F$. Since $L$ and $F$ have the same degree-one part $x+y$, $\nu$ has constant $1$. Also $D$ is an integral unit with constant $1$. Cancel $F^2$ in (1) and take formal logarithms. Using $2(\phi_E-\phi_O)=-\log g$, the result is the exact equality
$$
B_E(x,y)-B_O(x,y)=\log\nu(x,y)-\log D(x,y).
$$
Cancellation of $2$ occurs in an equality over the characteristic-zero coefficient field. The right side is a logarithm of an integral unit, hence an exponent congruent to zero. The same is true after inserting any integral formal group sum into either slot. Therefore the additivity of $B_O$ modulo integral exponentials supplies it for $B_E$, as claimed.

**Lean correspondence.** The addition and derivative identities are [`GCob_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/AtVariableWeierstrassDerivative.lean#L224) and its inputs. The integral division is [`div_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/DivLaw.lean#L19) and `LDiv_of`. The exact coboundary comparison, then third-difference transport, are [`BeESim_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/CocycleDiffExpEquiv.lean#L78) and [`CubeE_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/CocycleDiffExpEquiv.lean#L166).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
