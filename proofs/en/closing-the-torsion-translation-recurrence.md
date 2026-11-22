# Closing the torsion translation recurrence

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be prime, $\Lambda\subset\mathbb C$ a lattice, and $\iota:\mathbb C\cong\mathbb C_p$ an abstract field isomorphism. Suppose the short model obtained by transporting its invariants,
$$
W:y^2=x^3-\iota(g_2(\Lambda))x/4-\iota(g_3(\Lambda))/4,
$$
is integral with unit discriminant. Write $S$ for the modified sigma function on $\Lambda$, normalized by $S'(0)=1$. For $s\in\mathbb C$, let $G_s(T)$ be the Taylor series of $U_s S$ transported by $\iota$ and evaluated at the normalized logarithm $\ell_W(T)$, times the universal normalization
$$
A(T)^{-1},\qquad A(T)=\iota(\operatorname{Tay}S)(\ell_W(T))/T.
$$
Here $U_s$ is the degree-one translation on the complex torus, with Hermitian form $H(z,s)=z\bar s/\operatorname{area}(\Lambda)$. If $Ns\in\Lambda$ for an integer $N>0$ prime to $p$, then:

- If $s\in\Lambda$, $G_s(T)=uT$ for a scalar $u$ of norm $1$.
- Otherwise $G_s(0)$ has norm $1$ and $G_s(T)/G_s(0)\in 1+TR[[T]]$, where $R=\mathcal O_{\mathbb C_p}$.

This implies the integral translation bound for half-period theta and the height-two coordinate, proved below.

**The addition formula.** For $\eta\notin\Lambda$, the sigma product formula gives
$$
S(z+\eta)S(z-\eta)=S(z)^2S(\eta)^2(\wp(\eta)-\wp(z)).
$$
Changing $z$ to $z+\xi$, inserting the factors from $U_{\xi+\eta},U_{\xi-\eta}$, and using
$H(\xi+\eta,\xi+\eta)+H(\xi-\eta,\xi-\eta)=2H(\xi,\xi)+2H(\eta,\eta)$
gives the identity with $(U_\xi S)^2(U_\eta S)(0)^2$ on the right. The modified-sigma quadratic factors cancel in the product formula. For a lattice shift, the period formula of $S$ gives $U_s S=\pm S$, and so $G_s=\pm T$. For a nonlattice shift its constant is the transported value of $U_s S$ at zero, which is nonzero since the zeros of $S$ are the periods.

The map from complex shifts to points of $W$ is obtained by transporting $\wp,\wp'/2$. It preserves addition by the Weierstrass chord identities. In particular the Taylor series of $\wp(z+\xi)$ in the formal chart is the translated coordinate $x_P(T)$ where $P$ is the point of $\xi$. This follows by substituting the Laurent coordinates of the moving point in the chord formula. Consequently, when neither $\xi$ nor $\eta$ is a period,
$$
G_{\xi+\eta}G_{\xi-\eta}
=G_\xi^2\,G_\eta(0)^2\big(x_Q-x_P(T)\big),
$$
where $Q$ corresponds to $\eta$. No extra power of $T$ is needed in this case, because the difference has a power series expansion without a pole.

**A cycle of length $m$.** Suppose $s\notin\Lambda$ and let $m\ge2$ be its exact order. Put $G_j=G_{js}$, $P_j$ the corresponding point of $W$, and $c=G_1(0)\ne0$. For $1\le j<m$, set $D_j=x_{P_1}-x_{P_j}(T)$. Addition gives $G_{j+1}G_{j-1}=G_j^2c^2D_j$. Inductively, cancelling the nonzero series from successive equations yields
$$
G_mG_0^{m-1}=G_1^m\prod_{j=1}^{m-1}(c^2D_j)^{m-j}.
$$
For instance, the ratios $G_{j+1}/G_j$ and $G_j/G_{j-1}$, in the field of formal Laurent series, differ by the factor $c^2D_j$; multiply the successive ratios to get the formula. Each $D_j$ is $T$ to a nonnegative power times an integral unit by [the torsion factor lemma](the-orders-of-the-torsion-translation-factors.md). Thus the right hand side is $G_1^m c^{m(m-1)} T^h V(T)$ for an integral unit $V$, and the left hand side is a scalar unit times $T^m$. Comparing orders gives $h=m$. Comparing leading coefficients then gives $|c|^{m^2}=1$, hence $|c|=1$. After dividing by the leading coefficient and cancelling $T^m$, $(G_1/c)^m$ is the inverse of $V/V(0)$, so it is integral. A series $F=1+\sum_{j\ge1}b_jT^j$ whose $m$-th power is integral is itself integral when $p\nmid m$: the coefficient of $T^j$ is $m b_j$ plus a polynomial with integer coefficients in earlier $b_i$. Since $m\mid N$, induction proves the claim.

**From sigma to half-period theta.** Put $s_0=\omega_0/2$ with $\omega_0\in\Lambda$, $s_0\notin\Lambda$, and let $f_0=U_{s_0}S/(U_{s_0}S)(0)$. For any $t$ killed by $N$ prime to $p$, $U_t f_0$ is a root of unity times $U_{t+s_0}S/(U_{s_0}S)(0)$ by the translation cocycle. The cocycle is a root of unity because $2N t,2N s_0\in\Lambda$, whose alternating form is integral. The denominator has norm $1$ by the result for $s_0$, and $2N(t+s_0)\in\Lambda$. Both cases of the sigma result now show
$$
A(T)^{-1}\,\iota(\operatorname{Tay}(U_t f_0))(\ell_W(T))\in R[[T]] .
$$
If $h\in TR[[T]]$ is the integral short parameter with $\ell_W(h(T))=\epsilon L(T)$ and $|\epsilon|=1$, the sigma identity gives $A(h(T))=(\epsilon T/h(T))\exp(-\phi(T))$. Consequently the height-two corrected translate $\exp(\phi(T))\,\iota(\operatorname{Tay}(U_t f_0))(\epsilon L(T))$ equals the preceding integral expression after substituting $h$, multiplied by $\epsilon T/h(T)$. That factor is integral with constant $1$. The lattice can also be normalized so that the logarithmic argument is $L(T)$: multiplying the periods and $t$ by $\iota^{-1}(\epsilon)$ rescales their invariants by weights $-4,-6,-2$, and the Taylor series of the normalized half-period function changes by the inverse argument scaling. This is the bound used in [the finite product expansion](four-theta-copies-as-a-finite-sum-of-one-variable-translates.md).

**Lean correspondence.** The addition law for the translated series is [`IsTransSys`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/IsTransSys.lean#L60), with [`AnalyticSys_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/AnaSys.lean#L387). The finite-cycle identity and its integrality consequence are [`translate_power`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/ScaledXEqOffOrigin.lean#L96) and [`TransUnit_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/ScaledXOffOrigin.lean#L65). The normalized theta result is [`Th0Analytic_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/Taylor0ConstMul.lean#L195). The change to height two and homothety are [`v_integral_nonsingular_jet_norms`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/TorsionTranslationPowers/NonsingularJetNorms/VIntegral.lean#L46) and [`lubin_tate_transfer_integral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/ThetaKappaShapeOfTransferIntegrality.lean#L69).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
