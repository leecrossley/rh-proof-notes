# Interpolating torsion characters builds the height-one isomorphism

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a complete algebraically closed nonarchimedean field of characteristic zero, with valuation ring $\mathcal O$, and let $p$ be prime. Let $F(X,Y)$ be a one-dimensional formal group law over $\mathcal O$. Assume the coefficients of $[p]_F(X)$ in degrees below $p$ have norm $<1$, and the degree-$p$ coefficient has norm one. Then there is an integral series $f(X)$, with $f(0)=0$ and unit linear coefficient, satisfying
$$
1+f(F(X,Y))=(1+f(X))(1+f(Y)).
$$
Thus $f$ is an integral formal isomorphism to the multiplicative law in the parameter $z-1$.

### Integral finite character polynomials

[The height-one torsion calculation](the-height-one-torsion-tower-has-a-controlled-product-of-norms.md) supplies compatible $t_n$ in the open unit disc with $t_0=0$ and $[p]t_{n+1}=t_n$. Each $t_n$ has exact order $p^n$. Write $G_n$ for its nonzero multiples. These sets are increasing, satisfy $r\le|x|<1$ with $r=|t_1|>0$, and obey
$$
r^{p-1}=|p|,\qquad \prod_{x\in G_n}|x|=|p|^n,\qquad |p|<1.
$$
These precise torsion facts are the inputs used below. Choose compatible primitive roots $\zeta_n$ of order $p^n$. On the $p^n$ points $x_j=[j]t_n$ assign the intended character $\chi(x_j)=\zeta_n^j$.

Interpolate this character by the unique $g_n\in K[X]$ of degree below $h=p^n$. To see its coefficients are integral, let $P_n(X)=\prod_j(X-x_j)$. It is monic with integral coefficients. Reducing $F(X,Y)^k$ modulo $P_n(X),P_n(Y)$ preserves integrality for each $k<h$, even for the convergent formal series: the lower coefficients of $P_n$ have norm $<1$, so reducing $X^m$ into degrees below $h$ gains a norm factor $<1$ for every block of $h$ reductions. Thus the infinitely many reduced coefficient contributions converge, and the reduced polynomial agrees with $F(x_i,x_j)^k$ on the grid. Denote its coefficients by $c_{kab}$. If $g_n(X)=\sum_a g_aX^a$, the character identity and uniqueness of two-variable interpolation give
$$
g_a g_b=\sum_k g_k c_{kab}.
$$
Taking $a=b$ with $|g_a|$ maximal yields $\max_a|g_a|^2\le\max_a|g_a|$, hence the required integrality.

### A coefficient limit determined by all torsion levels

For an integral series $H(X)=\sum_j h_jX^j$ vanishing at $x$ with $|x|<1$, divide by $X-x$. The quotient has coefficients $\sum_{j\ge k+1}h_j x^{j-k-1}$ in degree $k$, all integral. Repeating at distinct zeros in $G_n$ shows that $H$ is the product of the corresponding linear factors times an integral series. The factor polynomial's coefficient of degree $k$ is a sum of products formed by omitting $k$ zeros, so its norm is at most $r^{-k}\prod_{x\in G_n}|x|$. The same bound holds for $|h_k|$, since $r\le1$ and convolution with an integral quotient can only use lower degrees of the factor polynomial.

The compatibility of $t_n,\zeta_n$ makes $g_{n+1}-g_n$ vanish on $G_n$. For every fixed coefficient, the bound just proved tends to zero. By the ultrametric inequality the coefficients form Cauchy sequences, and their limits give an integral series $\Phi$ with $\Phi(0)=1$. At any fixed small torsion point evaluation commutes with this limit, because the coefficient bound gives uniform geometric tails there. Hence $\Phi([j]t_n)=\zeta_n^j$ for every $j,n$.

The integral two-variable series $\Phi(F(X,Y))-\Phi(X)\Phi(Y)$ vanishes on all grids $G_n\times G_n$. To prove it vanishes identically, fix any $y$ in the union of the $G_n$ and apply the same coefficient bound in the first coordinate on all sufficiently large $G_n$. This gives the zero series in $X$ at that $y$. Its coefficients are integral series in $Y$ and vanish on the union, so the bound applied again makes them all zero.

Finally let $f=\Phi-1$. If the linear coefficient of $f$ were nonunit, then the constant term zero and the integral higher terms would give $|f(t_1)|<|t_1|$. But $f(t_1)=\zeta_1-1$, and $|\zeta_1-1|^{p-1}\ge|p|$ by the product $\prod_{j=1}^{p-1}(1-\zeta_1^j)=p$ and the bound $|1-\zeta_1^j|\le|1-\zeta_1|$. This contradicts $r^{p-1}=|p|$. The coefficient is a unit, completing the isomorphism proof.

### Lean correspondence

- [`exists_torsion_tower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsFormalGroupHeightOneTorsionTower.lean#L33) constructs $t_n$, and [`tower_norm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NormFormalGroupHeightOneTorsionTower.lean#L118) proves the norm identities.
- [`exists_integral_poly_of_character`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsIntegralPolyOfCharacter.lean#L8) uses the maximal coefficient argument, applied in [`exists_intg_polynomial_level`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsIntegralPolynomialTorsionCharacterLevel.lean#L24).
- [`exists_limit_of_agree_on_points`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsLimitPowerSeriesAgreeOnAnnulusPoints.lean#L41) takes the limit, and [`eq_zero_of_ev_vanish`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/IntegralMvPowerSeriesTwoEqZeroOfVanishOnSquares.lean#L38) proves uniqueness on the grids.
- [`exists_iso_multiplicative`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsIsoMultiplicative.lean#L65) combines the steps and proves the unit linear coefficient.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
