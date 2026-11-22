# The split CM isogeny makes the half-period series integral

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $L\subset\mathbb C$ be a complex multiplication lattice with maximal order of discriminant $-d$, with $d\equiv7\bmod8$. Let $T$ be half of a period and put $\omega=(1+\sqrt{-d})/2$. Assume $\omega T,\bar\omega T$ are both nonzero in $\mathbb C/L$. Transport the curve and its affine coordinates into $\mathbb C_2$ using the uniformization on a good integral model with $a_1$ a unit, as in [the construction of the ordinary CM model](a-chain-of-two-isogenies-gives-the-ordinary-cm-model.md). We show that the normalized, Gaussian-modified even theta at $T$, evaluated at the formal logarithm $\ell(t)$, belongs to $1+tR[[t]]$ for $R=\mathcal O_{\mathbb C_2}$. Its logarithm in the additive coordinate $Z$ has constant and linear coefficient zero and second derivative $-\wp(T+Z)-s_2$. The quasi-period constant $s_2$ is normalized by the [isogeny coefficient identity](the-lattice-isogeny-and-its-weight-two-constant.md) below.

The two roots of $X^2-X+(d+1)/4$ are congruent to $1$ and $0\bmod2$ by simple-root lifting. Choose $\alpha$ from $\omega,\bar\omega$ with unit image $a$, and write $b\in2\mathbb Z_2$ for the image of the conjugate multiplier. Thus $\alpha\bar\alpha=N$, where $N$ is a positive even integer and $ab=N$. Use [the integral kernel and stability theorem](the-unit-cm-multiplier-preserves-the-formal-kernel-at-two.md). It says that the reduction kernel $E_1$ is preserved by $\alpha$, that $E_1\cap\ker\alpha=0$, and that $E_1$ has exactly one nonidentity point of order two. If $T$ belonged to $E_1$, then $\alpha T$ would be a nonidentity point of order two in $E_1$. Uniqueness would give $\alpha T=T$, and hence $\bar\alpha T=NT=0$, a contradiction. For every $Q$ with $\alpha Q=T$, stability also gives $Q\notin E_1$, and $2Q=0$ would imply $\bar\alpha T=NQ=0$. Thus $T$ and the members of the fibre have integral affine coordinates. Because $T=-T$ and the fibre has no points fixed by negation, its $N=2m$ members form $m$ pairs $\{\pm Q\}$.

Write $H(Z)$ for the normalized even series and, for $P=T$ or a fibre representative, put $W_P(Z)=Z^2(\wp(Z)-\wp(P))$. Both have constant $1$ and zero linear term. By differentiating the logarithm of the two-point sigma identity twice,
$$
(\log W_P)''=2(\wp(Z)-Z^{-2})-\wp(Z+P)-\wp(Z-P).
$$
Let $S=\sum_{P\in\ker\alpha\setminus\{0\}}\wp(P)$. The isogeny distribution and its quasi-period condition give
$$
a^2\wp(aZ+T)=\sum_{\{\pm Q\}}\bigl(\wp(Z+Q)+\wp(Z-Q)\bigr)-S,
\qquad
(a^2-2m)s_2=S.
$$
Combine the displayed equations with $(\log H)''=-\wp(T+Z)-s_2$. The second logarithmic derivatives on the two sides of
$$
H(aZ)\,W_T(Z)^m=H(Z)^{2m}\prod_{\{\pm Q\}}W_Q(Z)
$$
agree. The constant and linear logarithmic coefficients agree as well, proving the identity over the characteristic-zero coefficient field.

In the coordinate $t$, put $x(t)=e(t)/t^2$ with $e\in1+tR[[t]]$. Each $W_P(\ell(t))$ is $(\ell(t)/t)^2(e(t)-x(P)t^2)$. The powers of $\ell(t)/t$ cancel, and all factors $e(t)-x(P)t^2$ are integral units. Define $\phi$ by $H(\ell(t))=\exp(-\phi(t))$, and write $f\sim g$ if $\exp(f-g)$ is an integral unit with constant $1$. The identity proves
$$
\phi([a]t)\sim ab\,\phi(t),\qquad [c]t=\ell^{-1}(c\ell(t)).
\tag{1}
$$

By [the even-phase cube identity](the-half-period-phase-has-an-integral-third-difference-at-two.md), the defect $B(x,y)=\phi(x\oplus y)-\phi(x)-\phi(y)$ is biadditive modulo $\sim$. All $[c]$ with $c\in\mathbb Z_2$ have integral coefficients: the claim holds for integers by the formal group law, the coefficients depend polynomially on $c$, and $R$ is closed. The same argument shows that $f\sim0$ implies $cf\sim0$ for $c\in\mathbb Z_2$, since $\exp(nf)=\exp(f)^n$ is integral for all integers $n$ and each coefficient depends polynomially on $n$. We can therefore pass the two integer additivity identities for $B$ to $a$ by coefficientwise continuity. They give $B([a]x,[a]y)\sim a^2 B(x,y)$, while (1) and the homomorphism law for $[a]$ give $B([a]x,[a]y)\sim ab B(x,y)$. Since $a(a-b)\in\mathbb Z_2^\times$, multiply the difference by its inverse to obtain $B\sim0$.

Now $\phi$ itself is additive modulo $\sim$. It follows for all integers $n$ that $\phi([n]t)\sim n\phi(t)$, by adding $t$ repeatedly and using the formal inverse for negative $n$. By the same continuity argument this holds at $n=a$. Comparing with (1) gives $a(1-b)\phi\sim0$. The coefficient $a(1-b)$ is a unit and its inverse is again a $2$-adic integer, so $\phi\sim0$. This proves the claimed integral expansion.

**Lean correspondence.** The fibre is controlled by [`PointsTwoFinal_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/LatticePointInKernelSubgroup.lean#L190). The logarithmic norm calculation and its integral quotient are [`theta_zero_isogeny_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/LinearCoeffLogShiftedWeierstrass.lean#L131) and [`PhENorm_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/PhENormOf.lean#L14). The continuity and scalar argument is [`two_adic_scalar_conditions`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/TwoAdicScalarConditions.lean#L98) followed by [`split_vanishing_at_two`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/BiextensionFormalMulMul.lean#L101). The combined conclusion on the actual theta series is [`Th0TwoFinal_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/FrobeniusFibreCurves/LogarithmicSubstitution/LatticePointInKernelSubgroup.lean#L269).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
