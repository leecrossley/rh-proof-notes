# The modified sigma has the canonical period multiplier

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $\Lambda=\mathbb Zw_1+\mathbb Zw_2\subset\mathbb C$ be a full lattice, with the basis oriented so that $\mathscr A=\operatorname{Im}(\overline{w_1}w_2)>0$. Write $H(z,w)=z\bar w/\mathscr A$ and let $\epsilon(w)=1$ for $w\in2\Lambda$ and $-1$ for $w\in\Lambda\setminus2\Lambda$. Define the Weierstrass sigma by
$$
\sigma(z)=z\prod_{\lambda\in\Lambda\setminus\{0\}}
(1-z/\lambda)\exp\!\left(z/\lambda+z^2/(2\lambda^2)\right).
$$
Then there is a unique $s_2\in\mathbb C$ such that $S(z)=e^{-s_2z^2/2}\sigma(z)$ satisfies, for every $w\in\Lambda$,
$$
S(z+w)=\epsilon(w)\exp\!\left(\pi H(z,w)+\pi H(w,w)/2\right)S(z)
\qquad(z\in\mathbb C).
$$
It is entire and has simple zeros precisely at $\Lambda$. In addition, with $g_2=60\sum_{\lambda\ne0}\lambda^{-4}$ and $g_3=140\sum_{\lambda\ne0}\lambda^{-6}$, the lattice discriminant $g_2^3-27g_3^2$ is nonzero. These properties supply the entire scalar theta used in the [fourfold average](a-fourfold-average-generates-the-standard-theta-line.md) and show that a period lattice scaled by a twelfth root of the original discriminant has nonzero scaling.

**The product and the logarithmic derivative.** A lattice has $O(R^2)$ elements of absolute value at most $R$, by comparing with an integer square in the basis $w_1,w_2$. In dyadic annuli this gives $\sum_{\lambda\ne0}|\lambda|^{-3}<\infty$. For $|z|\le r$, the logarithm of the factor for $|\lambda|>2r$ is given by the power series $-\sum_{n\ge3}(z/\lambda)^n/n$, bounded in absolute value by $2r^3|\lambda|^{-3}$. The tail therefore converges locally uniformly to a nonvanishing holomorphic function. The finitely many remaining factors give exactly the asserted zeros, all simple, and $\sigma'(0)=1$. Reindexing by $\lambda\mapsto-\lambda$ also gives $\sigma(-z)=-\sigma(z)$.

Away from the lattice, termwise differentiation gives the zeta function $\zeta=\sigma'/\sigma$ and the Weierstrass function $\wp=-\zeta'$. The formulas are
$$
\zeta(z)=\frac1z+\sum_{\lambda\ne0}
  \left(\frac1{z-\lambda}+\frac1\lambda+\frac z{\lambda^2}\right),
\qquad
\wp(z)=\frac1{z^2}+\sum_{\lambda\ne0}
  \left(\frac1{(z-\lambda)^2}-\frac1{\lambda^2}\right).
$$
The subtracted terms make both sums locally uniformly convergent off the lattice by the same $|\lambda|^{-3}$ bound. The derivative $\wp'(z)=-2\sum_{\lambda\in\Lambda}(z-\lambda)^{-3}$ is periodic by absolute convergence and reindexing. Thus $\wp(z+w_j)-\wp(z)$ is constant for either basis period $w_j$. Since $\wp$ is even, evaluation at $-w_j/2$ gives zero. Hence $\wp$ is periodic for all periods, and $\zeta(z+w)-\zeta(z)=\eta(w)$ is constant in $z$. Combining two translations shows that $\eta$ is additive on $\Lambda$.

**The sign and Hermitian correction.** For each $w\in\Lambda$, the function
$$
\frac{\sigma(z+w)}{\sigma(z)}\exp(-\eta(w)(z+w/2))
$$
extends through the lattice and has logarithmic derivative zero, so equals a nonzero constant $c(w)$. At $z$ and $-z-w$ the displayed values are reciprocal by oddness, so $c(w)=\pm1$. For $w\notin2\Lambda$, evaluate at $-w/2$ to get $c(w)=-1$. For $w=2u,\ u\in\Lambda$, compose the formula twice with period $u$. Additivity of $\eta$ combines the exponents and the sign is $c(u)^2=1$. Thus $c=\epsilon$.

Integrate $\zeta$ along the positively oriented boundary of a translated fundamental parallelogram avoiding the lattice. It encloses one pole of residue $1$. Grouping opposite sides using the constant differences gives
$$
\eta(w_1)w_2-\eta(w_2)w_1=2\pi i.
$$
The map $w\mapsto\pi\bar w/\mathscr A$ has exactly the same alternating difference on the basis. Therefore the two quotients
$$
\frac{\eta(w_j)-\pi\bar w_j/\mathscr A}{w_j},\qquad j=1,2,
$$
coincide. Denote their common value by $s_2$. Additivity now gives $\eta(w)=s_2w+\pi\bar w/\mathscr A$ on all periods. Substituting this into the transformation law of $\sigma$ and multiplying by $e^{-s_2(z+w)^2/2}$ cancels the quadratic correction. This is the required formula for $S$. Any other correction would add a factor $e^{c w z+c w^2/2}$ to that formula for every $z$, which forces $c=0$ for any nonzero period $w$. The modification leaves the zeros and their orders unchanged.

**Discriminant.** Expansion at the origin gives
$$
\wp(z)=z^{-2}+(g_2/20)z^2+(g_3/28)z^4+O(z^6).
$$
This follows by expanding $(z-\lambda)^{-2}$ and pairing $\lambda$ and $-\lambda$. Thus the elliptic function $(\wp')^2-4\wp^3+g_2\wp+g_3$ has no pole at zero and vanishes there. By periodicity it has no poles anywhere. It is bounded on a fundamental parallelogram and hence constant, proving $(\wp')^2=4\wp^3-g_2\wp-g_3$. At each of the three nonzero half-periods modulo $\Lambda$, periodicity and oddness of $\wp'$ give $\wp'=0$. The three values of $\wp$ there are distinct. Indeed, for any finite $a$, the function $\wp-a$ has exactly two zeros counted with multiplicity per period cell, by the argument principle and its one double pole there. At a half-period where $\wp=a$, the zero has multiplicity at least two. Two such half-periods would give at least four zeros. The three distinct values are roots of $4x^3-g_2x-g_3$, whose discriminant is $16(g_2^3-27g_3^2)$. This proves the nonvanishing.

**Lean correspondence.** Product convergence, the zero set and the logarithmic derivative are [`sigma_product_locally_uniform`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/SigmaConv.lean#L121), [`sigmaZero_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/SigmaBasic.lean#L58) and [`sigmaLogDeriv_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/SigmaLog.lean#L55). Quasi-period relation, Legendre relation and the correction use [`sigmaQuasi_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/SigmaQuasi.lean#L245), [`legendre_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/Legendre.lean#L188), [`etaSplit_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/QuasiPeriodConstUniqueOf.lean#L93) and [`sgStarQuasi_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/AnalyticIdentityTheorems/SgStar.lean#L24). The contour calculation above gives the Legendre relation from the pole of $\zeta$, where the source derives it from its Eisenstein formula. The discriminant result is [`discNeZero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/EisensteinTranslationProducts/EllipticOnePole.lean#L22) and its use for the host ideal is [`discrNZ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/PairingIndexBounds/HalvesRecursion/RecursiveLatticeMembership/MemLamOfIff.lean#L155). The distinct-value argument above uses the zero count of $\wp-a$ to obtain the corresponding injectivity assertion at the three half-periods.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
