# Division quotients determine the conjugate of a sigma translate

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be the imaginary quadratic field of the host. Let $\Lambda,\Lambda'\subset\mathbb C$ be full lattices stable under $\mathcal O_K$, with algebraic Weierstrass invariants. Let $\rho:\overline{\mathbb Q}\to\mathbb C$ fix $K$ and send the invariants of $\Lambda$ to those of $\Lambda'$. Write $S,\widetilde S$ for the [modified sigmas](the-modified-sigma-has-the-canonical-period-multiplier.md) of the two lattices. Use the translation $U_x$ for the normalized form of the relevant lattice. The Weierstrass uniformization sends a class $[v]$ modulo $\Lambda$ to the point at infinity if $v\in\Lambda$, and otherwise to $(\wp_\Lambda(v),\wp_\Lambda'(v)/2)$ on the short cubic. Transport the algebraic torsion points of this cubic by applying $\rho$ to their coordinates, to obtain the corresponding classes modulo $\Lambda'$.

Fix $m\ge1$ and $x,x'\in\mathbb C$ with $mx/2\in\Lambda$. Suppose $u=x/(2m)$ and $u'=x'/(2m)$ represent corresponding torsion classes. This is the adapted condition `Adp1` of level $2m$. Then the Taylor series of $U_xS$ has algebraic coefficients and applying $\rho$ to its coefficients gives the Taylor series of $U_{x'}\widetilde S$. In particular, in the host setting, an embedding of any subfield containing the specified Taylor coefficients and the torsion data gives the same identity by extending the embedding to algebraic coefficients.

**The canonical sigma series.** The correspondence of torsion points uses the algebraic group law on the conjugate curves. It is additive and commutes with multiplication by each $\alpha\in\mathcal O_K$ when $\rho$ fixes $K$. For $\alpha\ne0$, the [isogeny distribution identity](the-lattice-isogeny-and-its-weight-two-constant.md) expresses $\wp_\Lambda(\alpha z)$ as a sum of translated $\wp$ functions at the kernel points and an algebraic constant, times $\alpha^{-2}$. The kernel is killed by the positive integer $\alpha\bar\alpha$. Its points have algebraic coordinates, as they belong to the torsion of the algebraic curve. Each translate is rational in $\wp_\Lambda(z),\wp_\Lambda'(z)$ by the chord formula. Differentiation and division by $\alpha$ give the analogous expression for $\wp_\Lambda'(\alpha z)$. Thus the endomorphism is algebraic over $\overline{\mathbb Q}$. Its conjugate has tangent multiplier $\rho(\alpha)=\alpha$ for the invariant differential $dx/(2y)$, which pulls back to $dz$. A complex group endomorphism is determined by that multiplier because it lifts to a linear map on the complex universal cover. This proves the claimed commutation. The same isogeny calculation computes the modified sigma constant $s_2$ of either lattice as
$$
s_2=\frac{\sum_{P\in\ker(\alpha),\,P\ne0}x(P)}
                 {\alpha^2-\alpha\bar\alpha}
$$
using a nonreal $\alpha\in\mathcal O_K$. The denominator is nonzero. The correspondence of the kernel points shows that $s_2$ is algebraic and goes to the modified sigma constant for $\Lambda'$. The regular expansion $S(z)=z\exp(J(z)-s_2z^2/2)$, with $J''=-(\wp_\Lambda(z)-z^{-2})$ and $J(0)=J'(0)=0$, now gives the conjugate of $S$ coefficient by coefficient. The Laurent coefficients of $\wp_\Lambda$ are determined by its Weierstrass equation and the invariants, and formal integration and exponential preserve the coefficient identities. This is the canonical odd theta calculation.

**The division quotients.** If $u\notin\Lambda$, define the germs near zero
$$
D_n(z)=\frac{S(n(z+u))}{S(z+u)^{n^2}},\qquad n\ge0.
$$
They correspond under $\rho$ to the analogous germs $D'_n$ at $u'$. To see this, the initial terms are $D_0=0,\ D_1=1,\ D_2=-\wp_\Lambda'(z+u)$. The last identity is obtained by differentiating the sigma addition identity in its second variable at the first variable, using $S(0)=0,\ S'(0)=1$. The Taylor series of $\wp_\Lambda(z+u)$ is determined by the differential equation $\wp''=6\wp^2-g_2/2$, with initial values $\wp_\Lambda(u),\wp_\Lambda'(u)$. These initial data go to the corresponding data at $u'$. Thus the quotient series correspond for $n=0,1,2$.

Put $W(F)=FF''-(F')^2$, with derivatives in the local variable. The addition formula for $S$ can be written
$$
S(v+w)S(v-w)=W(S)(v)S(w)^2-W(S)(w)S(v)^2,
$$
since $W(S)(v)=-(\wp_\Lambda(v)+s_2)S(v)^2$. Use $w=z+u,\ v=(n+1)w$. The identities
$$
 W(FG)=W(F)G^2+F^2W(G),\qquad
 W(G^r)=rG^{2r-2}W(G)
$$
and the chain rule show that the terms involving $W(S)(w)$ cancel after inserting $S((n+1)w)=D_{n+1}(z)S(w)^{(n+1)^2}$. Dividing by the remaining power of $S(w)$ gives
$$
(n+1)^2 D_{n+2}D_n=W(D_{n+1}).
$$
For $n\ge1$, $D_n$ is a nonzero germ because $S$ is not identically zero and the argument $n(z+u)$ is nonconstant. Therefore division in the field of formal Laurent series yields the next Taylor series from the two previous ones. The recurrence is rational in their coefficients and proves that all the quotient germs correspond.

**Fixing the root's constant.** If $u\in\Lambda$, then $x=2mu$ lies in $2\Lambda$. The corresponding period condition holds for $u'$ as well, so both translations fix the canonical sigma. Otherwise $u,u'$ are both nonperiods. Write $F_v=U_v S$ on the first lattice. Inserting the exponent defining $U_v$ gives
$$
F_{n u}(n z)=F_u(z)^{n^2}D_n(z).
$$
The equality holds as germs, and the same equality holds on the second lattice. Set $A(z)=F_u(z)^{(2m)^2}$. Because $m^2u=mx/2\in\Lambda$, the shift $2m^2u$ lies in $2\Lambda$, and
$$
A(z)^{m^2}=S(2m^2 z)/D_{2m^2}(z).
$$
Thus the $m^2$-th power corresponds by the preceding arguments. To fix the root, put $k=m^2-1$. The period law at $m^2u$ and oddness give $F_{(k+2)u}(0)=-F_{ku}(0)$. Indeed both are $\epsilon(m^2u)e^{-\pi H(u,u)/2}$ times $S(u)$ and $S(-u)$ respectively, as the cross terms cancel against the translation exponent. Both values are nonzero because $(m^2\pm1)u$ are nonperiods. Using the displayed multiplication law at zero,
$$
A(0)=-\frac{D_k(0)}{D_{k+2}(0)},
$$
by $(k+2)^2-k^2=(2m)^2$. Thus the constants at the two lattices correspond exactly. In characteristic zero, a nonzero-constant formal series is determined by its $m^2$-th power and its constant. Indeed the coefficient of degree $j\ge1$ in the power has a linear term $m^2A(0)^{m^2-1}[z^j]A$, plus a polynomial in earlier coefficients. Induction proves conjugation of $A$. Finally $F_x(2mz)=A(z)D_{2m}(z)$, which gives the claimed Taylor correspondence by division of the coefficient of degree $j$ by $(2m)^j$. This method uses only algebraic coefficients, so it also gives the agreement for any smaller field over which the input coefficients are defined.

**Lean correspondence.** The adapted point condition at a chosen division level is [`StarPt` and `Adp1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/StandardLatticesGL3.lean#L35). Torsion transport and preservation of the CM action use [`galStar_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/GalStarComplexMultiplicationPoints.lean#L286), and the canonical odd theta coefficient theorem is [`galSg_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/GaloisTaylorSeriesCanonicalOddThetaAll.lean#L623). The quotient recurrences are [`IsSigmaLike.divQuot_rec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/SecondDerivSigmaProductAtZero.lean#L127) and [`jetRel_divQuot`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/SecondDerivSigmaProductAtZero.lean#L173). The power identity and its fixed constant are [`translate_facts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/GaloisConjTaylorThetaTranslate.lean#L77), combined in [`galois_translate_sgStar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/GaloisConjTaylorThetaTranslate.lean#L181).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
