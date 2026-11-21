# Exponential decay for a single character of small modulus

[Chinese proof](../zh/%E8%BE%83%E5%B0%8F%E6%A8%A1%E6%95%B0%E7%9A%84%E5%8D%95%E7%89%B9%E5%BE%81%E7%B4%A0%E6%95%B0%E5%92%8C%E6%80%8E%E6%A0%B7%E5%8F%96%E5%BE%97%E6%8C%87%E6%95%B0%E8%A1%B0%E5%87%8F.md)

**Proposition.** For each $0<a\le1/20$ there exist $c,C>0$ depending only on $a$. Let $q\ge1$, let $\chi$ be a character modulo $q$ with principal character $\chi_0$, and let $B\subset\mathbb R$ have at most one element. Each element of $B$ must be a simple zero of the nonprincipal $L(s,\chi)$ in
$$
\mathcal R_a(q)=\{\sigma+it:\sigma\ge1-a/\log(q(|t|+2))\}.
$$
All zeros of $L(s,\chi)$ in this region belong to $B$, with the principal pole at $1$ excluded. For every $y\ge2$ and $q\le e^{c\sqrt{\log y}}$, one then has
$$
\left|\psi_\chi(y)-\mathbf1_{\chi=\chi_0}y+\sum_{\beta\in B}\frac{y^\beta}{\beta}\right|
\le C y e^{-c\sqrt{\log y}},
\qquad \psi_\chi(y)=\sum_{n\le y}\Lambda(n)\chi(n).
\tag{1}
$$
The region and the zero hypothesis are `InRegion` and `ExcZeros`. This is the smaller-modulus input in the [relative prime number theorem](relative-prime-number-theorem-two-ranges.md).

## Removing the simple poles

For nonprincipal $\chi$, write $D_\chi=-L'/L$ and $\ell=\log(q(|\Im s|+2))$. We first show that for $s\in\mathcal R_{a/2}(q)\setminus B$,
$$
\left|D_\chi(s)+\sum_{\beta\in B}\frac1{s-\beta}\right|\ll_a\ell^2.
\tag{2}
$$
If $\Re s\ge11/10$, the absolute Dirichlet series bounds $D_\chi$ and each $\beta<1$ gives $|s-\beta|^{-1}\le10$. Otherwise $\Re s\ge 26/27$ because $a\le1/20$ and $\ell\ge\log 2$. At $z_0=21/20+i\Im s$, take the outer radius $r=11/20$. The disk lies in $\Re z\ge1/2$, and $s$ lies within $r/6$ of the center. Periodic partial sums give $|L(z,\chi)|\ll q(1+|z|)$ on the disk. The inverse Euler product at $z_0$ gives $|L(z_0,\chi)|^{-1}\le\zeta(21/20)\le21$. The [disk formula](../zh/%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0.md) therefore gives $D_\chi(s)=-\sum_{\rho\in Z}m_\rho/(s-\rho)+O(\ell)$, with $Z$ the zeros in radius $r/3$ of total multiplicity $O(\ell)$.

For an ordinary zero in $Z$, $\ell_\rho=\log(q(|\Im\rho|+2))\le\ell+\log(131/120)\le6\ell/5$. Since $\rho$ lies outside $\mathcal R_a(q)$, we have $\Re(s-\rho)\ge a/\ell_\rho-a/(2\ell)\ge a/(3\ell)$. The ordinary sum is therefore $O_a(\ell^2)$. A simple zero in $B\cap Z$ cancels against the added pole. One outside $Z$ is at distance at least $r/6$ from $s$, so adding its reciprocal costs only a constant. This proves (2).

## Shift for the nonprincipal smoothed sum

Set $S_\chi(y)=\sum_{n\le y}\Lambda(n)\chi(n)(y/n-1)$ and $\sigma_0=1+1/\log y$. The inverse Mellin transform of $1/[w(w-1)]$ is $(v-1)_+$, as follows by integrating $(v-1)v^{-w-1}$ over $v\ge1$. With $v=y/n$ and the absolutely convergent Dirichlet series, this gives $S_\chi(y)$ as the integral of $D_\chi(w)y^w/[w(w-1)]$ on $\Re w=\sigma_0$, divided by $2\pi i$. The bound $|D_\chi(w)|\le-\zeta'(\sigma_0)/\zeta(\sigma_0)\ll 1+\log y$ ensures absolute convergence.

Take $T\ge1$ and put $L=\log(q(T+2))$. Of $1-a/(3L)$ and $1-a/(4L)$, at least one is at distance at least $a/(24L)$ from every element of $B$. Call it $\sigma_1$. The shift rectangle lies in $\mathcal R_{a/2}(q)$. The pole at $1$ has residue $y D_\chi(1)$, and an enclosed $\beta$ gives $-y^\beta/[\beta(\beta-1)]$. The original tail costs $O(y(1+\log y)/T)$. On the horizontals (2) bounds the log derivative by $O_a(1+L^2)$ and the denominator is at least $T^2$ in modulus. On the left, $|w|\ge1/2$, $|w-1|\ge a/(4L)$, and (2) gives $D_\chi(w)=O_a((1+L)^2)$. The integral there is $O_a(Ty^{\sigma_1}(1+L)^3)$. If an element of $B$ lies to the left of the rectangle, its residue has modulus at most $8Ly^{\sigma_1}/a$ by $\beta\ge1/2$ and $1-\beta\ge a/(4L)$. We may thus include all of $B$:
$$
S_\chi(y)=D_\chi(1)y-\sum_{\beta\in B}\frac{y^\beta}{\beta(\beta-1)}
+O_a\left(\frac{y(1+\log y)}{T}+\frac{y(1+L)^2}{T^2}+Ty^{\sigma_1}(1+L)^3\right).
\tag{3}
$$
With $u=\sqrt{\log y}$ take $T=e^{au/2}$. If $q\le e^{au/4}$, then $L\le3au/4+2$, and $4L\le u$ for $u\ge10$. Thus $Ty^{\sigma_1}\le y e^{-au/2}$. Absorbing the polynomial factors in $u$, the error is $O_a(ye^{-c_su})$ with $c_s=a/4$. For $u\le10$ all factors after dividing by $y$ are bounded in terms of $a$.

## The principal smoothed sum

For $\zeta$ the project uses `GzPNT`,
$$
S_\zeta(y)=y\log y-(1+\gamma)y+O(ye^{-c_gu})
\tag{4}
$$
with Euler's constant $\gamma$ and absolute $c_g>0$. The proof uses the classical zero-free region and the bound $|\zeta'/\zeta(s)+1/(s-1)|\ll\log^2(|\Im s|+2)$ in a suitably narrowed region. Take $b>0$ at most $1/2$ small enough for both inputs. Put $T=e^{bu/4}$, $L_\zeta=\log(T+2)$, and $\sigma_1=1-b/L_\zeta$. For $u\ge8/b$ we have $1\le L_\zeta\le u/4$. Only $1$ lies inside as a pole. In the integrand,
$$
-\frac{\zeta'(w)}{\zeta(w)}=\frac1{w-1}-\gamma+O(w-1),\qquad
\frac{y^w}{w(w-1)}=\frac{y}{w-1}+y(\log y-1)+O_y(w-1).
$$
The product has a double pole whose residue is the main term in (4). Estimate the edges as for (3), now using the pole at $1$ in the log-derivative bound. On the left $|w-1|^{-1}\le L_\zeta/b$ and $Ty^{\sigma_1}\le y e^{(b/4-4b)u}$. The right tail is $O(y(1+\log y)e^{-bu/4})$. We can take $c_g=b/8$, covering bounded $u$ by increasing the constant.

## The difference that removes the smoothing

Set $c_0=\min(c_s,c_g,1)$, $h=e^{-c_0u/2}$ and $Y=y(1+h)$. For $|f(n)|\le\Lambda(n)$ write $W_f(z)=\sum_{n\le z}f(n)(z/n-1)$. Direct subtraction gives
$$
\frac{yW_f(Y)-YW_f(y)}{Y-y}
=\sum_{n\le y} f(n)+\frac{y}{Y-y}\sum_{y<n\le Y}f(n)(Y/n-1).
\tag{5}
$$
The final sum with its coefficient is $O((yh+1)\log Y)$ since $0\le Y/n-1\le h$ and the interval contains at most $yh+1$ integers. The smoothed errors after differencing are $O_a(ye^{-c_0u}/h)=O_a(yh)$.

For a nonprincipal character the linear term in (3) cancels. Each zero term contributes
$$
-\frac{y^\beta}{\beta}(1+h)
\frac{(1+h)^{\beta-1}-1}{(\beta-1)h}.
$$
The quotient equals $(1+\theta h)^{\beta-2}$ for some $0\le\theta\le1$. Since $1/2\le\beta<1$, this gives $-y^\beta/\beta+O(yh)$. For a principal character, use (4) in (5). Its linear term cancels, and $y\log y$ contributes $y(1+h)\log(1+h)/h=y+O(yh)$. Passing from $\zeta$ to the principal character deletes powers of primes dividing $q$, of total weight at most $\omega(q)\log y$. If $q\le e^{(c_0/4)u}$ this is $O(u^3)$.

With $c=c_0/4$, the factors of $\log Y$ in (5) and the deleted prime powers are absorbed in $O_a(ye^{-cu})$. The bound on $q$ also lets us use (3) at both $y$ and $Y$. This proves (1).

## Lean correspondence

- `PsiChiBound` uses `ExcZeros` as its zero hypothesis, and `psiChiBound` assembles `smoothChi` and `gzPNT`. [Statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/SiegelWalfiszAP.lean#L16) · [Assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/SiegelWalfiszAPOfSiegelLower.lean#L23) · [Zeta input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZeroFreeRegion/LogDerivRegion.lean#L20)
- `landau_lemma_lfunction_zeros` and `log_deriv_in_zero_free_region` give (2). [Disk](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/LandauLemmaLfunctionZeros.lean#L9) · [Region](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/LogDerivRegionChiOf.lean#L10)
- `perron_formula_character`, `rectangle_contour_shift_character`, `chebyshev_character_explicit_general`, and `smoothed_character_sum_of` give (3). [Inversion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/PerronChi.lean#L283) · [Residues](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/RectShiftChi.lean#L114) · [Edge estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/ChebyshevCharacterExplicitGeneral.lean#L10) · [Choice of height](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SmoothChiOf.lean#L9)
- `laurentExpansionAtOne`, `rectangleShiftOfResidue` and `zetaPrimeSumErrorBoundOfBounds` give (4). [Expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZeroFreeRegion/ZetaLogDerivativeBounds/LaurentAtOne.lean#L50) · [Shift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZeroFreeRegion/ZetaLogDerivativeBounds/RectShiftOf.lean#L32) · [Error](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZeroFreeRegion/ZetaLogDerivativeBounds/GzPNTOf.lean#L48)
- `norm_weightedSum_sub_le` and `sum_vonMangoldt_not_coprime_le` give the errors in (5). `chebyshev_character_bound_of` completes (1). [Difference](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SumVonMangoldtNotCoprimeLe.lean#L77) · [Prime powers](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SumVonMangoldtNotCoprimeLe.lean#L83) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/PsiChiBoundOf.lean#L239)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
