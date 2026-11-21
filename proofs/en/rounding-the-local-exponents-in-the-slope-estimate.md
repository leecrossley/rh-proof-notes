# Rounding the local exponents in the slope estimate

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E6%8C%87%E6%95%B0%E5%8F%96%E6%95%B4%E7%9A%84%E8%AF%AF%E5%B7%AE%E4%B8%BA%E4%BD%95%E5%8F%AF%E6%8E%A7.md)

## Statement

Let $K$ be totally imaginary, $S$ a finite set of primes of $K$, and $p_w,e_w,f_w$ the residue characteristic, ramification index and residue degree of $w\in S$. Put $\lambda_w=\log(\mathrm Nw)/[K:\mathbb Q]=f_w\log p_w/[K:\mathbb Q]$. For real $g_w$ and a nonzero finitely generated lattice $M$, set
$$
I=\prod_{w\in S}w^{-\lfloor e_wg_w\rfloor},\qquad U=2\sum_{w\in S}\lambda_w e_wg_w,\qquad
E=|\mu(IM)-\mu(M)-U|.
$$
Keep the metric fixed and use the project's slope normalization. Let $X''\ge0$, let $T,g_0,g_1,d$ be primes, and let $D_\Gamma$ be a positive integer. Assume every $w$ with $g_w\ne0$ lies over a rational prime $p_w$ that is at most $X''$, is one of $T,g_0,g_1,d$, or divides $D_\Gamma$. Then
$$
E\le2\bigl(X''\log4+\log T+\log g_0+\log g_1+\log d+\log D_\Gamma\bigr).
$$
If $\log g_0,\log g_1,\log d\le X''$, $\log T\le C_T X''$ and $\log D_\Gamma\le C_\Gamma X''$, this gives $E\le2(\log4+3+C_T+C_\Gamma)X''$.

## Group the rounding errors by rational prime

The fractional ideal scaling formula gives $\mu(IM)-\mu(M)=2\sum_w\lambda_w\lfloor e_wg_w\rfloor$. Rounding has error in $(-1,0]$ and makes no difference at $g_w=0$. Therefore $E\le2\sum_{w:g_w\ne0}\lambda_w$. At each rational prime $p$, $\sum_{w\mid p} e_w f_w=[K:\mathbb Q]$ and $e_w\ge1$, so the sum over selected places above $p$ is at most $\log p$. [Exact slope change](local-lengths-and-lattice-slopes.md)

The elementary bound $\prod_{p\le N}p\le4^N$ follows by induction. At $N=2k$, the primes in $(k,2k]$ divide $\binom{2k}{k}\le4^k$. At $N=2k+1$ with $k\ge1$, those in $(k+1,2k+1]$ divide $\binom{2k+1}{k}\le4^k$, since this coefficient and the adjacent equal coefficient both occur in the sum $2^{2k+1}$. The bases $N=0,1$ are immediate. This proves $\sum_{p\le X''}\log p\le X''\log4$ by taking the integer part. The four special primes cost their individual logarithms, and the product of the distinct primes dividing $D_\Gamma$ divides $D_\Gamma$. Summing these bounds gives the first inequality and substituting the size conditions gives the second.

## Uniformity on the window

The project takes $g_w=\mathrm{sg}(u,w)$ for each word $u$, summing increment plus correction minus loss over lift indices. Outside the specified support, `ZeroAbove` kills the increments and losses, and `F_above` kills the corrections. This is the support condition obtained from `LinkDIV`. [Local increment support](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/DataParams%E2%82%82.lean)

Here $x>1$, $0<\varepsilon<1/52$, $X'=\exp(x^{\varepsilon/3})$, $X''=X'xn_H$, where $n_H\ge1$ is the group order, and $f=2n_H$. The size conditions give $\log g_i\le x^{\varepsilon+\varepsilon/100}$ and $\log d\le x^{\varepsilon/5+\varepsilon/100}$, each at most $X''$. Also $\log T\le C_T^0 m x^\varepsilon$. At a sufficiently large uniform threshold, $C_T^0\le x^{\varepsilon/100}$, so $m\le2n_H$ yields $\log T\le2xn_H\le2X''$.

For the denominator, $\log D_\Gamma\le C fN(m)\log(fN(m))$ with $N(m)=k+m(t+1)$. We have $N(m)\le\eta_{\mathrm{sz}}\le\exp(x^{\varepsilon/4})\le X'$ and $n_H\le x^3$. Hence $\log(fN(m))\le\log2+3\log x+x\le4x$, so $fN(m)\log(fN(m))\le8X''$. The source uses the looser bound $\log D_\Gamma\le10|C|X''$. Taking the maximum of the thresholds for length vanishing, full rank, finite generation and the family bounds makes the rounding estimate uniform in $x$, the candidate, and the word. It bounds the quotient slope's rounding contribution $R_d$ by a constant times $X''$. [Rounding in the quotient estimate](quotient-slope-bounds.md) · [Place in the common family](joint-family-selection.md)

- `mu_diff` and `round_le` give the change and local rounding bound. `sum_lwP_le` and `sum_lwP_le_primes` group by rational prime. `sg_eq_zero` and `nprimeMu_at` give the support and first estimate. `nprimeMuR_at` and `linkMu` handle the uniform bound. [Rounding estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/SumLogPrimeFactorsLe.lean)
- `muTu_of_tuSize` and `muDGam_of_fact` give the special size bounds. `linkMu_of_linkDIV` obtains the support from the global divisibility data. [Size inputs](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/MuTuOfTuSize.lean) · [Application to global divisibility](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/AdmissibleParameterJoins/SumLogPrimeFactorsLe.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
