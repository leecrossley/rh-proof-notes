# Why only the second curve jet can lose integrality

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a characteristic-zero ultrametric field and $R$ its valuation ring, with $2\in R^\times$. Let $\ell(t)=t+\cdots$ be a formal logarithm with $\ell'\in R[[t]]$, $h=\ell^{-1}$, and $F(x,y)=h(\ell(x)+\ell(y))$ an integral formal group law. Use the zero-constant curve exponent $\phi$ with the following properties. These hold for the modified sigma exponent of the good short CM curve in this application. Fix the relation $f\sim g$ meaning equality of constant terms and $\exp(f-g)$ integral. Put $C(x,y)=\phi(F(x,y))-\phi(x)-\phi(y)$. The required properties are:

- $C(F(x,x'),y)\sim C(x,y)+C(x',y)$, from the [sigma cube](from-formal-sigma-addition-to-the-curve-biextension.md), and $\phi([-1]t)\sim\phi(t)$, where $[a]t=h(a\ell(t))$.
- For a CM multiplier $a$ and its conjugate $b$, the series $[a],[b]$ are integral and $C([a]x,y)\sim C(x,[b]y)$.
- $(a-b)^2=-d\ne0$.

Use $D=(\ell')^{-1}d/dt$ and $S=(D^2\phi)(0)$. Then
$$
|S|\le|d|^{-1/2},\qquad
\exp(-\phi(h(Z)))=\exp(-S Z^2/2)J(Z)
$$
for a jet-integral series $J$ of constant $1$. If $a-b$ is a unit, then all jets of $\phi(h(Z))$, including $S$, are integral.

**Orders one and at least three.** Inversion has linear term $-t$. The coefficient of $t$ in $\exp(\phi([-1]t)-\phi(t))$ is $-2D\phi(0)$, which is integral. Since $2$ is a unit, $D\phi(0)$ is integral. Consider the difference
$$
B(x,y,z)=C(F(x,y),z)-C(x,z)-C(y,z).
$$
It vanishes upon setting any variable to zero. Its exponential is integral by the first hypothesis. In the ring of series in $x$, the coefficient of $yz$ in $\exp B$ equals the coefficient of $yz$ in $B$, because every term of $B$ has a factor $yz$. To compute it, use $Q=\phi\circ h$. In logarithmic variables $B$ is the alternating third difference of $Q$. Differentiating once each in $y,z$ at zero gives $Q''(\ell(x))-Q''(0)$, since $\ell'(0)=1$. This is $D^2\phi(x)-D^2\phi(0)$. Hence the latter is ordinary integral. The operator $D$ preserves integrality and kills constants, by [the coordinate calculation](integral-derivatives-form-a-ring-of-formal-series.md). Its iterates of positive order on this difference give $(D^n\phi)(0)\in R$ for $n\ge3$.

**Order two.** In the adjoint relation both terms vanish on the two axes, and their mixed coefficient of $xy$ is $aS$ and $bS$, respectively. Comparing that coefficient in the integral exponential gives $(a-b)S\in R$. Multiplicativity of the absolute value and the square relation give $|S|\le |d|^{-1/2}$. The series $Q(Z)-S Z^2/2$ has integral jets of all orders. By the jet exponential rule its negative exponential is jet-integral, giving the asserted $J$.

**The multiplier in the CM curve.** In the good short model take $a=(1+\sqrt{-d})/2$ under the chosen embedding, $b=(1-\sqrt{-d})/2$, at an odd prime $p\mid d$. The degree $ab=(d+1)/4$ is prime to $p$, so both scalars are units. The [prime-to-$p$ multiplication calculation](the-curve-norm-law-from-a-prime-to-p-isogeny.md), with the integral kernel points of the good model, gives integral $[a]$ and the phase norm $\phi([a]t)\sim ab\,\phi(t)$. The inverse $[a^{-1}]$ is integral by the coefficient recursion for the compositional inverse with unit linear coefficient. Since $b=1-a$, integral addition gives $[b]$ integral. Polarizing the phase norm gives $C([a]x,[a]y)\sim ab\,C(x,y)$. Now put $[a^{-1}]y$ in the second slot and use additivity to move the integer $ab$ into that slot. The resulting argument is $[b]y$. This proves the adjoint input from the same norm law. Inversion of the short parameter is $t\mapsto -t$; symmetry of the regular part of the Weierstrass function makes the phase exponent even there. Thus the inversion hypothesis in particular holds for the short model used at the discriminant prime.

**Lean correspondence.** The definition of $D$ and the statements about the jets are [`jet`, `JetOne` and `JetAdj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/JetExpShape.lean#L11). The derivative of the third difference and the exponential with its quadratic part removed are [`third_jet_integral` and `jets_shape`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/SecondCoefficientNorms/BinomialSeriesCoefficients/IntegralThirdInvariantDerivative.lean#L201). The adjoint and half-valuation deduction are [`inverse_endo_integral_holds`, `adjoint_unit_norm_holds` and `ramified_shape_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/RamifiedCurveKernels/PairedSquareJets/InverseEndoIntegralHolds.lean#L86). The CM specialization is [`ShapeCM_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/NormLeOneOfQuad.lean#L163).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
