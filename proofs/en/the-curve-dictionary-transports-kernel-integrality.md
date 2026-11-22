# The curve dictionary transports kernel integrality

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be prime, $R=\mathcal O_{\mathbb C_p}$, and $\iota:\overline{\mathbb Q}\hookrightarrow\mathbb C_p$. Let $\Lambda$ be the complex period lattice of the imaginary quadratic ideal in the host data. Assume its normalized discriminant is $1$. Let $W$ be a Weierstrass model obtained from the transported lattice curve by a change of variables $C$, with coefficients in the unramified valuation ring and with unit discriminant. Write $a=(C.u)^{-1}$ for the scalar on logarithmic coordinates. Assume the chosen height-two comparison gives $v\in TR[[T]]$ and a unit $e$ such that
$$
\ell_W(v(T))=e^{-1}L(T), \qquad v'(0)=e^{-1},
$$
where $\ell_W$ is the normalized curve logarithm for the identity parameter $-x/y$ and $L(T)=\sum_{m\ge0}T^{p^{2m}}/p^m$. The existence of this integral comparison for the inert CM curve is the [height-two parameter theorem](normalizing-the-height-two-logarithm.md).

Write $S_\Lambda$ for the formal Taylor series of the modified sigma function after applying $\iota$ to its algebraic coefficients. Let $g_2,g_3,s_2$ denote the two invariants and the modified sigma constant on $W$, and put $\epsilon=e^{-1}$. For any finite column list $b_1,\ldots,b_r$ of rectangular host matrices, write $B$ for the matrix whose $i$-th column lists their embedded entries. Let $G$ be any formal series in the entry variables over $\mathbb C_p$. If the corrected pullback of $G$ on a discriminant-one model chosen below is integral, then
$$
G\big(a\epsilon B(L(T_i))_i\big)\exp\!\left(\sum_{i=1}^r\phi(T_i)\right)\in R[[T_1,\ldots,T_r]].
$$
Here $\phi=\text{`phFF`}(p,g_2,g_3,s_2,\epsilon)$ is the common phase in the $L$-coordinate. This is the implication in `DictInt`, applicable to every size and list for the same curve.

**The phase comparison.** In logarithmic coordinate $z$ the regular part of the Weierstrass function is the series $P(z)=\wp_W(z)-z^{-2}$ for $g_2,g_3$. For a general model, the Laurent $x$-coordinate is shifted by $b_2/12$, with $b_2=a_1^2+4a_2$, to obtain $\wp_W$. Completing the square and putting $x_s=x+b_2/12$ gives the short curve with the same invariant differential and hence the same $P$. In particular
$$
J(z)=-\int_0^z\int_0^w P(u)\,du\,dw
$$
has zero constant and linear terms, and is the regular sigma exponent for both models. Indeed $\log(S_W(z)/z)=J(z)-s_2z^2/2$, by the [sigma construction](from-formal-sigma-addition-to-the-curve-biextension.md). The Taylor coefficients used here are algebraic: $g_2,g_3$ follow from the CM singular modulus and the discriminant normalization, and the isogeny formula for $s_2$ expresses it as a rational multiple of a finite sum of algebraic torsion coordinates. The formal differential equation for $P$ and integration then give the remaining coefficients. [Algebraicity of the modified sigma constant](the-lattice-isogeny-and-its-weight-two-constant.md)

The invariants scale by $a^4,a^6$, and $s_2$ by $a^2$, when passing from the transported lattice model to $W$. Uniqueness of $P$ under this scaling and the normalization $S'_W(0)=1$ give $S_\Lambda(az)=aS_W(z)$. Thus the single-coordinate factor in the original correction on $W$ is
$$
A_W(t)=\frac{S_\Lambda(a\ell_W(t))}{at}
      =\exp(-f_W(t)),\qquad
f_W(t)=-J(\ell_W(t))+\frac{s_2}{2}\ell_W(t)^2-\log\!\frac{\ell_W(t)}t.
$$
The normalized height-two phase has the same first two terms at $z=\epsilon L(T)$ and last term $-\log(L(T)/T)$. With $\psi(T)=f_W(v(T))$ this gives
$$
\psi-\phi=\log\!\frac{L(T)/T}{(\ell_W(t)/t)|_{t=v(T)}}=\log\!\frac{e v(T)}T .
$$
Consequently $V=\exp(\phi-\psi)=T/(e v(T))$ has integral coefficients and constant $1$. This follows by inverting the integral series $e v(T)/T$, whose constant is $1$. There is no need for either exponential $\exp(\psi)$ or $\exp(\phi)$ to be integral on its own.

The same comparison identifies the short theta parameter in the curve datum. Directly on $W$ the short parameter is
$$
\frac{-x_s}{y_s}
=t\,\frac{x_0(t)+b_2t^2/12}
{x_0(t)-(a_1/2)t x_0(t)-(a_3/2)t^3},
\qquad
x_0(t)=t^2x(t),\quad y_s=y+(a_1x+a_3)/2.
$$
The chart recursion gives $x_0\in R[[t]]$ with constant $1$. Since $2,3$ are units, the denominator is a unit over $R$; substitution of $v$ proves integrality of the short parameter at $z=\epsilon L$. This is the theta integrality assertion used with the norm law.

**The integral substitution.** Choose $\nu$ with $\nu^{12}=\Delta(W)$. It is a unit. Scale $W$ to $W'$ by dividing every coefficient $a_j$ by $\nu^j$; the new discriminant is $1$. The identity parameter scales from $t$ to $\nu t$, so $\ell_{W'}(\nu t)=\nu\ell_W(t)$, as also follows from the normalized invariant differential. The logarithmic scalar $a'$ for $W'$ is $a/\nu$. Thus $A_{W'}(\nu t)=A_W(t)$. Set $h(T)=\nu v(T)\in TR[[T]]$. The hypothesis for `DictInt` is exactly
$$
G\big(a' B(\ell_{W'}(X_i))_i\big)
\prod_i A_{W'}(X_i)^{-1}\in R[[X_1,\ldots,X_r]].
$$
At $p\ge5$ the correction `ePh` is this product of the single-coordinate inverses. Substituting $X_i=h(T_i)$ preserves integrality, because at any fixed total degree only finitely many input coefficients are involved. The logarithmic argument becomes $a\epsilon B(L(T_i))_i$, and the correction becomes $\exp(\sum_i\psi(T_i))$. Multiplying by $\prod_i V(T_i)$ gives the claimed series. Finally $\Delta(W)=a^{12}$, since the lattice equation has discriminant $1$. Hence $c=a\epsilon$ has norm $1$ and is independent of the rank and of the basis list.

**Lean correspondence.** The statement with the model, the chart series and the quantifier over all lists is [`DictInt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/DefsRep.lean#L78). The sigma factor is [`ePhi1_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/FormalExponentialAgree.lean#L153). The signed phase comparison is [`phase_compatibility`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/ExistsWittSeriesInverseFormalGroupIso.lean#L327), with [an explicit coefficient proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhEquivShortWeierstrassModel.lean#L100). The parameter quotient is [`shortIso_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ThetaUnitFunctionShortModelIntegral.lean#L62). The scaling and substitution are [`flog_scale`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PadicNormTwoHundredSixteenEqOneOfFiveLe.lean#L153) and [`dict_core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PadicNormTwoHundredSixteenEqOneOfFiveLe.lean#L237). The production dictionary is [`rdictMain`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/RepDict.lean#L301). Its additional biextension comparison as a coboundary is a separate assertion, beyond this implication.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
