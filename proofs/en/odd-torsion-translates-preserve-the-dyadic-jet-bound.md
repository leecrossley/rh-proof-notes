# Odd torsion translates preserve the dyadic jet bound

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Keep the hypotheses of [the split CM half-period calculation](the-split-cm-isogeny-makes-the-half-period-series-integral.md), including the good integral model over $\mathbb C_2$ with unit $a_1$. For finite sets $I,J$, choose $s_{ji}\in\mathbb C$ with $Ns_{ji}\in L$ for a common positive odd integer $N$, and $r_j\in R=\mathcal O_{\mathbb C_2}$. Let $H_T$ be the normalized even theta at $T$. On an entire function define the translation
$$
(U_s f)(Z)=f(Z+s)\exp\left(-\frac{\pi}{\operatorname{area}(L)}\left(Z\overline s+s\overline s/2\right)\right).
$$
Transport the Taylor coefficients into $\mathbb C_2$, and set $\Theta(Z)=\sum_{j\in J}r_j\prod_{i\in I}(U_{s_{ji}}H_T)(Z_i)$, with transported factors understood. The assertion is that $m![Z^m]\Theta$ is integral for every multi-index $m$, where $m!=\prod_i m_i!$. In particular $\sum_m P_m m![Z^m]\Theta$ is integral whenever $P=\sum_m P_m Z^m$ is an integral polynomial.

Fix one of the shifts and let $A$ be the cyclic group of its torsion point. It has odd order. Reduction is injective on $A$, as the formal group has no nonzero torsion of odd order. The reduction of $T$ is nonzero of order two by the half-period calculation. Thus $T+P$ has nonidentity reduction for every $P\in A$, and its reduction differs from both $Q$ and $-Q$ for each nonzero $Q\in A$. On a Weierstrass curve, a given affine $x$-coordinate specifies a point up to negation, including in characteristic two. Hence $x(Q)-x(T+P)$ is a unit. The translated function $x(T+P+\cdot)$ has integral expansion at the formal identity. Indeed translation by the integral point $T+P$ on the smooth Weierstrass model maps the formal identity to the affine chart of its reduction. The regular affine coordinate can be expanded there over $R$; equivalently the integral chord formula gives its expansion after cancelling any powers of $t$. Thus
$$
x(Q)-x(T+P+t)\in R[[t]]^\times
$$
in the formal coordinate, with unit constant term. Here $T+P+t$ uses the formal group parameter for the final variable.

Choose representatives of $A$ killed by $N$ modulo $L$, with representative $0$ at the identity. For $P\in A$, let $H_P(t)$ be the transported $U_s H_T$ for its representative, evaluated at $Z=\ell(t)$. The sigma addition identity gives, for $Q\ne0$,
$$
H_{P+Q}H_{P-Q}
=\rho(P,Q)c(Q)^2\bigl(x(Q)-x(T+P+t)\bigr)H_P^2 ,
\tag{1}
$$
where $c(Q)\ne0$ is the value at zero of the translate by the representative of $Q$ of the Gaussian-modified odd sigma series. The identity before choosing representatives uses exactly the sums and differences of representatives. Replacing them by the chosen representatives and composing the translations changes the two sides by powers of the torsion translation characters. Those values are roots of unity, since the shifts and $T$ are of finite order on $L$ and the alternating pairing of periods has integer values. Hence $|\rho(P,Q)|_2=1$. This is the same translation product used in [the finite-cycle calculation at odd primes](closing-the-torsion-translation-recurrence.md), with the simple zero at the origin replaced by $H_0(0)=1$.

Equation (1) at $P=0$ shows that $H_Q(0)$ and $H_{-Q}(0)$ are nonzero for every $Q$. Write $h(P)=\log |H_P(0)|_2$. Taking the logarithm of the norms at $t=0$ yields
$$
h(P+Q)+h(P-Q)-2h(P)=2\log|c(Q)|_2 .
$$
Summing over $P\in A$ gives $|c(Q)|_2=1$. The left side now vanishes, so $h$ has constant successive differences on every cyclic orbit of translation by $Q$. A constant difference on a finite cycle is zero. Starting at $0$ yields $h(Q)=0$, since $h(0)=0$.

For any $Q$ of order $m>1$, normalize $F_j=H_{jQ}/H_{jQ}(0)$. Divide (1) by its constant terms to get $F_{j+1}F_{j-1}=D_jF_j^2$, with $D_j\in1+tR[[t]]$. In characteristic zero all $F_j$ have inverses with constant $1$. The recurrence gives
$$
F_m=F_1^mF_0^{-(m-1)}\prod_{j=1}^{m-1}D_j^{\,m-j}.
$$
Since $F_m=F_0$ and $F_0\in1+tR[[t]]$ by the half-period result, $F_1^m$ is integral. Here $m$ is odd, so the coefficient in degree $k$ of the $m$-th power has the form $m[t^k]F_1$ plus an integral polynomial in earlier coefficients. Induction using that $m$ is a unit proves $F_1$ integral. Together with the unit constant term, this gives $H_Q\in R[[t]]^\times$. The identity case is $H_0$; any other representative of a fixed torsion class changes the series by a scalar unit.

Substituting $Z_i=\ell(t_i)$ now makes every factor of $\Theta$ integral. The invariant derivative in $Z_i$ acts after substitution as $\ell'(t_i)^{-1}d/dt_i$. The series $\ell'(t_i)$ is the integral invariant differential of the Weierstrass model, with constant $1$. Its inverse and formal differentiation preserve integrality. Apply each derivative $m_i$ times and evaluate at zero. This yields the asserted jet $m![Z^m]\Theta$. The polynomial pairing is a finite sum of products of integral elements.

**Lean correspondence.** The analytic translation product is used in [`shiftCase`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/TransW.lean#L489) and assembled in [`shift_analytic_model`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/TransW.lean#L614). Integral constants and normalized translates are proved in [`shift_unit'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/OneLtNormXOfInKernel.lean#L146). The finite-product statement and jet pairing are [`IntOpTwoOrth_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/IntegralOperatorTwoOrthogonal.lean#L15) and the ensuing theorem.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
