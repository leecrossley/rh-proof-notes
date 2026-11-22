# The unit CM multiplier preserves the formal kernel at two

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Use the [ordinary good model at two](a-chain-of-two-isogenies-gives-the-ordinary-cm-model.md), with complex lattice $L$, coefficient isomorphism $\iota$, integral coefficients, unit discriminant, and $a_1$ a unit. Write $x(z)=\iota(\wp_L(z))-b_2/12$ for the affine coordinate of a nonidentity point. Uniformization identifies the transported complex points modulo $L$ with points of the model. The formal kernel $\mathcal F$ is the subgroup of points reducing to the identity. A nonidentity point is in $\mathcal F$ exactly when its $x$-coordinate has norm $>1$, by the integral chart at infinity and good reduction. Let $\alpha\in\mathbb C^\times$ preserve $L$, and suppose $\iota(\alpha)\in\mathbb Z_2^\times$.

**Claim.** No nonidentity point killed by $\alpha$ is in $\mathcal F$, and multiplication by $\alpha$ carries $\mathcal F$ into itself.

**The $x$-coordinates of $2$-primary torsion.** For a nonidentity point of order two, $2y+a_1x+a_3=0$, so
$$
4x^3+b_2x^2+2b_4x+b_6=0.
$$
All the $b_i$ are integral and $|b_2|=1$, since $b_2=a_1^2+4a_2$. If such an $x$ has norm $>1$, then $u=1/x$ has norm $<1$ and satisfies $4+b_2u+2b_4u^2+b_6u^3=0$. The terms of degree at least two in $u$ have strictly smaller norm than $b_2u$. Thus $|u|=1/4$ and $|x|=4$. Two roots $u,u'$ of norm $<1$ must coincide: subtract the equations and divide by $u-u'$ if it is nonzero. The linear term gives the unit $b_2$, while the other terms give elements of norm $<1$, which is impossible. The affine $y$-coordinate is determined by the order-two equation. Hence at most one nonzero point of order two lies in $\mathcal F$. The same cubic shows there is no order-two point with norm $>4$.

For a point $P$ with $2P\ne0$ the duplication formula is
$$
x(2P)=\frac{x^4-b_4x^2-2b_6x-b_8}{4x^3+b_2x^2+2b_4x+b_6}.
$$
If $|x|\ge4$, the numerator has norm $|x|^4$, and the denominator has norm at most $|x|^3/4$. This gives $|x(2P)|\ge4|x|>4$. Repeating the calculation would preclude any subsequent doubling from reaching order two. Thus every $2$-primary torsion point of order greater than two has $|x|<4$. The formula follows by substituting the tangent slope in the Weierstrass addition law.

**No kernel point lies in $\mathcal F$.** The $\alpha$-kernel modulo $L$ is finite, and all of its classes are killed by the positive integer $n=\alpha\bar\alpha$. A point of that kernel in $\mathcal F$ must have $2$-power order: the odd part of $n$ acts invertibly in the integral formal law by its unit linear coefficient. A nonidentity such point would therefore supply a point $P_*$ of order two in that kernel and in $\mathcal F$. Choose one representative $P$ per nonidentity kernel point. The coefficient of $Z^2$ in the [Weierstrass distribution law](the-lattice-isogeny-and-its-weight-two-constant.md) gives
$$
\sum_P (3\wp_L(P)^2-g_2(L)/4)=(\alpha^4-1)g_2(L)/20 .
$$
Indeed $\wp_L(Z)=Z^{-2}+(g_2/20)Z^2+\cdots$ and $\tfrac12\wp_L''(P)=3\wp_L(P)^2-g_2/4$. On transporting to the integral model, the summand at $x=x(P)$ is
$$
3(x+b_2/12)^2-g_2(W)/4=3x^2+(b_2/2)x+b_4/2 ,
$$
using $12g_2(W)=c_4=b_2^2-24b_4$. The norm at $P_*$ is $16$; for every other point it is strictly less than $16$. This follows from the $x$-bounds just proved and $|x|\le1$ outside $\mathcal F$. The sum has norm $16$ by strict dominance. However $\iota(\alpha)$ is an odd $2$-adic integer, so $\iota(\alpha)^4\equiv1\bmod16$, by the congruence on odd integers and continuity. Also $|g_2|\le4$ from integral $c_4$. The right side has norm at most $16^{-1}\cdot4\cdot4=1$, a contradiction.

**Stability of $\mathcal F$.** Let $z$ represent a nonidentity point in $\mathcal F$. Its image under $\alpha$ is nonidentity by the preceding argument. For every nonidentity kernel point $P$, both $P$ and $z+P$ are outside $\mathcal F$, since it is a subgroup and $z\in\mathcal F$. Apply the full distribution law at $z$, again using $x=\wp-b_2/12$ after transport. In
$$
\iota(\alpha)^2 x(\alpha z)
=x(z)+(1-\iota(\alpha)^2)b_2/12+\sum_P(x(z+P)-x(P)),
$$
the sum is integral. The scalar shift is integral too because the square of an odd $2$-adic integer is $1\bmod8$ and $|b_2/12|\le4$. The $x(z)$-term, of norm $>1$, strictly dominates all the rest. As $\iota(\alpha)$ has norm one, $|x(\alpha z)|=|x(z)|>1$. This is the asserted stability.

**Lean correspondence.** The two-torsion and duplication bounds are [`two_torsion_kernel_unique_holds`, `torsion_norm_bound_holds` and `kappa_norm_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/TwoTorsionKernelUniqueHolds.lean#L348). The coefficient identity is [`kappa_sum_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/CoeffTwoPSeries.lean#L51). The argument using the unique dominant summand is [`KernelIntegral_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/NotInKernelOfMultiplierTorsion.lean#L303). Stability is [`kernel_stable_of_integral_kernel`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/LatticePointInKernelSubgroup.lean#L129).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
