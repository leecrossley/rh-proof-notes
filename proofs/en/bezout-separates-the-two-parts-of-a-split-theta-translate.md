# Bézout separates the two parts of a split theta translate

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be the CM coefficient field, $p=\pi\bar\pi$ a split prime with coprime factors, and $M$ the period lattice of an admitted theta pair with normalized vector $e$. Assume the Weil translates $W(z)e$ are smooth, obey the translation cocycle, are fixed for $z\in M$, and have rational cocycle arguments on the rational homomorphism space. Let $\lambda:\overline{\mathbb Q}\to\mathbb C_p$ be the coefficient embedding. Assume [the bracket-twisted moment law](bounded-p-adic-measures-give-integral-point-tables.md) with multiplier $\bar\pi/\pi$ for every translate annihilated modulo $M$ by an integer prime to $p$. Then for every rational translate $t$ with $n\pi t\in M$ for an integer $n$ prime to $p$, all normalized jets of $W(t)e$ are algebraic and their $p$-adic table is in the integral closure of the point tables $\operatorname{ptTab}(x,m)$ with $x\in M$.

Choose $\alpha,\beta\in\mathcal O_E$ with $\alpha n\bar\pi+\beta\pi=1$, and take $t'=\beta\pi t$. Then $nt'\in M$, so the moment law for $t'$ supplies $N_0$ prime to $p$. Choose $\alpha',\beta'\in\mathcal O_E$ with $\alpha'N_0+\beta'p=1$. Define
$$
m_1=\alpha'\alpha(n\pi t)\in M,\qquad
l=\beta'\bar\pi^2\alpha(n\pi t)\in M,\qquad
y=N_0(\bar\pi/\pi)m_1.
$$
Multiplying the second Bézout identity by $\alpha n\bar\pi t$ gives $y+l=\alpha n\bar\pi t$. The first identity gives $t=y+t'+l$.

Applying the translation product formula twice and using $W(l)e=e$ gives $W(t)e=\zeta\,W(y)W(t')e$ for a root of unity $\zeta$, since the two cocycle arguments are rational. Thus linearity of the jet gives algebraicity from the bracket-twisted moment law at $m_1\in M$. In that law each point table is multiplied by the bracket of $y$ and the point $x$. This bracket is again a root of unity. Its image and $\lambda(\zeta)$ have norm one, because they have finite multiplicative order. Absorb the bracket and $\lambda(\zeta)$ into the approximating weights, retaining norms at most one. The same finitely supported approximants now use the ordinary point tables, proving the claimed closure.

### Lean correspondence

- [`coc_rat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsTranslateRationalPointUnitDenominator.lean#L42) makes the cocycle rational by clearing denominators.
- [`moments_unit_translate`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MomentsTranslateRationalPointUnitDenominator.lean#L71) separates $t$ by these two Bézout identities and absorbs the root-of-unity factors.
- [`clo_comb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TranslateMomentsAll.lean#L145) passes to the new table by multiplying the coefficients of the approximants.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
