# Transporting the quadratic theta phase through four copies

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a characteristic-zero ultrametric field, $R$ its valuation ring, and $\ell(t)=t+\cdots$ a formal logarithm with integral derivative. Write $h=\ell^{-1}$. Assume a zero-constant phase $\phi$ in the integral formal parameter satisfies
$$
\exp(-\phi(h(Z)))=\exp(-S Z^2/2)J(Z),
\qquad J\text{ jet-integral}.
$$
This is the [quadratic curve phase](why-only-the-second-curve-jet-can-lose-integrality.md). The [jet ring rules](integral-derivatives-form-a-ring-of-formal-series.md) will be used below. For $T\in K[[Z_1,\ldots,Z_n]]$, write $T^{\otimes4}$ for the product of four copies with disjoint variables. Assume the theta model gives
$$
T^{\otimes4}(\gamma Z)=
 \exp\!\left(-\sum_w\phi(h(Z_w))\right)G(h(Z_w):w),
\qquad G\in R[[t_w:w]]
$$
for some matrix $\gamma$ on the four blocks, where $w$ ranges over their $4n$ coordinates. This is the exact identity provided by `TensStd` after the ordinary local model estimate. If $C$ is an integral matrix with $4n$ rows and $\gamma C=\operatorname{diag}_4(M)$, the following conclusions hold.

**The ramified case.** Suppose $2$ is a unit, the variables in a single target block are $X^\pm_{t,a,b}$ as in [the paired minors](why-high-mixed-derivatives-vanish-on-paired-minors.md), and $C^t C$ is the direct sum of four matrices of a paired form, up to $\theta Q$ for an integral matrix $Q$ with $|S\theta|\le1$. More precisely, the leading Gram entry is $u_t$ between two coordinates in the same block and with the same $t,a,b$ and opposite sign, and is zero otherwise. Assume $|u_t|\le1$. Then
$$
T(MX)=\exp\!\left(-S\sum_{t,a,b}u_t X^-_{t,a,b}X^+_{t,a,b}\right)U(X),
\quad U\text{ jet-integral}.
$$

Indeed, $G(h(Z_w):w)$ is jet-integral by invariant differentiation in the separate variables, since $\ell'$ has an integral inverse. Multiplying it by the product of $J(Z_w)$ gives a jet-integral remainder, leaving $\exp(-S\sum_w Z_w^2/2)$. Substitute $Z=CX^{(4)}$, where $X^{(4)}$ lists the four blocks. The left is $T(MX)^{\otimes4}$ by the matrix equation. Integral linear substitution preserves the remainder. The transformed quadratic polynomial is the sum of the four paired polynomials, with coefficient $-S$, plus a quadratic error with matrix $-S\theta Q/2$. Its coefficients are integral because $2$ is a unit and $S\theta Q$ is integral. By the jet exponential rule its exponential can be absorbed into the remainder. Thus the fourfold tensor of $T(MX)\exp(S\sum_{t,a,b}u_t X^-_{t,a,b}X^+_{t,a,b})$ is jet-integral. Extract the fourth power of each repeated jet and take its norm, proving that the corrected single factor is jet-integral. This factor is the required $U$.

For a finite linear combination of series with this same $M,S,u_t$, and scalars of norm at most one, factor out the common exponential. The sum of the remaining jet-integral series is jet-integral. In particular the common exponent must be determined by the chart and the directions before choosing the theta translate to which the argument applies.

**The unramified odd-prime case.** If instead all jets of $\phi\circ h$ are integral, its exponential and the right-hand side of the fourfold identity are already jet-integral. Substitution by $C$ and extraction from the independent four blocks give $T(MX)$ jet-integral, using only $\gamma C=\operatorname{diag}_4(M)$ and the integrality of $C$. No paired Gram hypothesis is needed for this conclusion.

**Lean correspondence.** The fourfold identity is the conclusion of [`ShapeToZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussianEigenFrames/StatementA.lean#L14), used by `TensStd`. The ramified output and the odd-prime output are [`ShapeLin_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussianEigenFrames/GramFrameComposition/GramFrameCompositionMvExpFact.lean#L266) and [`JetsLin_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussianEigenFrames/GramFrameComposition/JetsLin.lean#L144). [`shape_paired_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/FourthPowerTheta.lean#L63) combines the local tensor model, the Gram matrix and the ramified phase. For the full `ShapeD` assertion at (p=d), the remaining chart condition is (B) equal to the paired form modulo (sqrt{-d}), and the local tensor identity must hold for each translate.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
