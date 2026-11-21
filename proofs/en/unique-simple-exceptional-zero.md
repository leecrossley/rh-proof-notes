# Uniqueness and simplicity of the real exceptional zero

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%9D%A0%E8%BF%91%E4%B8%80%E7%9A%84%E5%AE%9E%E4%BE%8B%E5%A4%96%E9%9B%B6%E7%82%B9%E5%94%AF%E4%B8%80%E4%B8%94%E7%AE%80%E5%8D%95.md)

**Proposition.** There is an absolute constant $c_{\rm R}>0$ with the following property. Let $q\ge1$ and let $\chi,\psi$ be nonprincipal Dirichlet characters modulo $q$ such that $\chi^2=\psi^2=\chi_0$, where $\chi_0$ is the principal character modulo $q$. If $\beta,\beta'$ are real, both at least $1-c_{\rm R}/\log(2q)$, and $L(\beta,\chi)=L(\beta',\psi)=0$, then $\chi=\psi$, $\beta=\beta'$, and $L'(\beta,\chi)\ne0$.

## The real zeros

Write $D_\chi(\sigma,t)=-\Re(L'/L)(\sigma+it,\chi)$ and $L_0=\log(2q)>1/2$. We use the [one-sided log-derivative bounds](three-four-one-zero-free-region.md). For $1<\sigma\le2$ they give absolute constants $C_0,C_1>0$ such that
$$
D_{\chi_0}(\sigma,0)\le\frac1{\sigma-1}+C_0 L_0,\qquad
D_\chi(\sigma,0)\le C_1 L_0-\sum_{\beta\in S}\frac{m_\beta}{\sigma-\beta}\quad(\chi\ne\chi_0),
\tag{1}
$$
where $S$ can be any collection of distinct real zeros in $[2/3,1)$, and $m_\beta$ is the analytic multiplicity. Every such $\beta$ lies within distance $5/6$ of $3/2$. The other zeros in the local log-derivative formula contribute reciprocal terms with nonnegative real part before the overall minus sign, so dropping those terms gives an upper bound.

Put $K=C_0+3C_1$, $\varepsilon=\min(1/2,1/(4K))$, and $c_{\rm R}=\varepsilon/8$. Take $\sigma=1+\varepsilon/L_0$. Then $1<\sigma\le2$, and both zeros are at least $2/3$. Nonvanishing for $\Re s\ge1$ puts them strictly below $1$.

If $\chi\ne\psi$, the product $\chi\psi$ is nonprincipal. The Euler series at $\sigma$ shows that $D_{\chi_0}+D_\chi+D_\psi+D_{\chi\psi}\ge0$. On integers coprime to $q$ the coefficient of $\Lambda(n)n^{-\sigma}$ is $(1+\chi(n))(1+\psi(n))\ge0$, and on the remaining integers it is zero. Apply (1), keeping one zero in each of the middle two terms and none in the last. This gives
$$
\frac1{\sigma-\beta}+\frac1{\sigma-\beta'}\le\frac1{\sigma-1}+K L_0.
\tag{2}
$$
If $\chi=\psi$ but $\beta\ne\beta'$, the positivity of $D_{\chi_0}+D_\chi$ gives (2) by keeping both zeros in $D_\chi$. If both zeros are the same and $L'(\beta,\chi)=0$, their common zero has multiplicity at least two, so the same positivity again gives (2).

In every case $(\sigma-\beta)L_0,(\sigma-\beta')L_0\le9\varepsilon/8$. The left side of (2) is at least $16L_0/(9\varepsilon)$, and the right side is at most $5L_0/(4\varepsilon)$. The strict inequality $16/9>5/4$ rules out all three cases.

## The zero-free region used in the project

Set
$$
\mathcal R_q(c)=\left\{s:\Re s\ge1-\frac{c}{\log(q(|\Im s|+2))}\right\}.
$$
The project predicate `ZFRDirichlet` asserts that one $c>0$ works for every modulus $q\ge1$. Any zero in $\mathcal R_q(c)$, with $s=1$ excluded for the principal character, must belong to a nonprincipal quadratic character and must be real and simple. Moreover every pair of character and zero in the region for the same modulus coincides with that one.

Choose $c$ to be the minimum of $c_{\rm R}$ and the principal and nonprincipal region constants in the upstream proof. Shrinking $c$ shrinks the region because the denominator is positive. The principal region excludes the principal character, and the nonprincipal region restricts all remaining zeros to the real axis and to quadratic characters. On the real axis the denominator is $\log(2q)$, so the proposition completes the proof.

For $q\ge3$ the project also uses $M=\max(q,q|\Im s|)$. Then $q(|\Im s|+2)\le3M\le M^2$, so $\Re s\ge1-(c/2)/\log M$ puts $s$ in $\mathcal R_q(c)$. For $\zeta$, use the principal character modulo $1$ and $\log(|t|+2)\le2\log(|t|+3)$. Every nontrivial zero $\rho$ of $\zeta$ therefore has $\Re\rho\le1-(c/2)/\log(|\Im\rho|+3)$. The project packages these two regions with the [multiplicity-sensitive density bound](../zh/%E6%80%8E%E6%A0%B7%E7%94%B1%E5%8D%95%E4%BD%8D%E9%AB%98%E5%BA%A6%E6%A0%BC%E5%AD%90%E6%95%B0%E5%87%BA%E5%B8%A6%E9%87%8D%E6%95%B0%E7%9A%84%E9%9B%B6%E7%82%B9.md) to select the only possible exceptional term in the truncated explicit formula.

## Lean correspondence

- The local bound and three cases of the proposition are `GlobalTheory.RealZeroNearOne.exists_bound` and `GlobalTheory.RealZeroNearOne.main`. The Euler-series positivity is `neg_sum_logDeriv_nonneg`. [Local bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/OrderNeTop.lean#L33) · [Main argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/OrderNeTop.lean#L89) · [Positivity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NegSumLogDerivNonneg.lean#L42)
- `ZFRDirichlet` and `GlobalTheory.LandauPageRegion.main` state and prove the combined region. [Definition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/Statement.lean#L15) · [Assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/InRegionMono.lean#L54)
- `inRegion_of_max` and `main` change the Dirichlet denominator, and `density_and_regions` packages the bounds. [Change of variables](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NeOneOfIsPrimitive.lean#L8) · [Package](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DensityAndRegions.lean#L10) · [Corresponding fields of `adm6`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/ShortIntervalPrimes.lean#L128)

Status. Translation draft based on the Chinese proof and its pinned Lean references. No new Lean replay or axiom audit accompanies this note.
