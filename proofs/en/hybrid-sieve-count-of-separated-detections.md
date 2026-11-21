# Counting separated detections with the hybrid large sieve

[Chinese proof](../zh/%E6%B7%B7%E5%90%88%E5%A4%A7%E7%AD%9B%E6%80%8E%E6%A0%B7%E6%95%B0%E5%87%BA%E5%88%86%E7%A6%BB%E7%9A%84%E6%A3%80%E6%B5%8B%E7%82%B9.md)

**Proposition.** There is an absolute $C>0$ such that the following holds for every integer $Q\ge2$. Define
$$
b_Q(n)=\sum_{d\mid n,\ d\le Q^3}\mu(d),\qquad
F_\chi(s)=\sum_{Q^3<n\le Q^6}b_Q(n)\chi(n)n^{-s}.
$$
Let $\mathcal T$ be a finite set of triples $(q,\chi,\rho)$ with $1\le q\le Q$, primitive $\chi\bmod q$, $1-1/400\le\Re\rho\le1$, $|\Im\rho|\le Q$, and $|F_\chi(\rho)|\ge1/2$. For any two distinct points with the same $(q,\chi)$ assume $|\Im\rho-\Im\rho'|\ge1$. Then $|\mathcal T|\le CQ^{1/8}$. The points can be arbitrary. The [Möbius detector](mobius-truncation-detecting-zeros.md) supplies the large-value condition when the point is a zero.

## Integrating over separated windows

For entire $f$, Cauchy's formula at $\rho=\beta+i\gamma$ and Cauchy–Schwarz give $|f(\rho)|^2\le(2\pi)^{-1}\int_0^{2\pi}|f(\rho+u e^{i\theta})|^2\,d\theta$ at each radius $u>0$. Integrate against $2\pi u\,du$ for $0<u<r$ and enlarge the disk to its circumscribed square. This yields
$$
|f(\rho)|^2\le\frac1{\pi r^2}\int_{\beta-r}^{\beta+r}\int_{\gamma-r}^{\gamma+r}|f(\sigma+it)|^2\,dt\,d\sigma .
$$
Take $r=1/800$, $\sigma_0=1-3/800$, $\sigma_1=1+1/800$, and $H=Q+1$. For each point use this estimate with $f=F_\chi$ and enlarge the real interval to $[\sigma_0,\sigma_1]$. For each fixed $(q,\chi)$, the height intervals lie in $[-H,H]$ and are disjoint since their widths are $2r<1$. Summing by character and then enlarging to all primitive characters of modulus at most $Q$ gives
$$
\frac{|\mathcal T|}{4}\le
\frac1{\pi r^2}\int_{\sigma_0}^{\sigma_1}
\sum_{q\le Q}\sum_{\chi\bmod q}^{*}\int_{-H}^H|F_\chi(\sigma+it)|^2\,dt\,d\sigma.
\tag{1}
$$

## The common coefficient sequence

For fixed $\sigma$ use the [hybrid large sieve](hybrid-large-sieve-height-integration.md) on $a_n=b_Q(n)n^{-\sigma}\mathbf1_{Q^3<n\le Q^6}$. Its right side is
$$
C_{\rm H}\sum_{Q^3<n\le Q^6}(Q^2(Q+1)+n)|b_Q(n)|^2 n^{-2\sigma}.
$$
By $|\mu(d)|\le1$, $|b_Q(n)|\le\tau(n)$. For any $\eta>0$ there is $K_\eta$ such that $\tau(n)\le K_\eta n^\eta$. Indeed for $a\ge0$ and any prime $p$, $1+a\le K(1+a\eta\log2)\le K p^{a\eta}$ with $K=\max(1,1/(\eta\log2))$. For $p\ge2^{1/\eta}$ use $1+a\le2^a\le p^{a\eta}$. Multiplying over primes dividing $n$ costs a factor $K$ for only finitely many possible primes, giving the claimed $K_\eta$.

Use $\eta=1/400$ and $n>Q^3$ to bound $Q^2(Q+1)+n\le3n$. As $\sigma\ge1-3/800$, the summand is at most $3K_\eta^2 n^{-1+1/80}$. This decreasing power is integrable at zero, so $\sum_{n\le Q^6}n^{-1+1/80}\le\int_0^{Q^6} t^{-1+1/80}dt=80 Q^{3/40}\le80Q^{1/8}$. In (1) the remaining real interval has length $1/200$. This proves the proposition, and the same calculation retains the exponent $3/40$ if desired. The [unit-height counting argument](zero-density-from-unit-height-cells.md) chooses representatives satisfying the separation hypothesis.

## Lean correspondence

- `norm_sq_le_integral_square` is the point-value inequality, and `sum_integral_separated_windows_le` gives the disjoint-window sum. [Point value](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/EnormSqLeLintegralDisc.lean#L21) · [Windows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CardSpacedDetectedLe.lean#L93)
- `exists_card_divisors_le_mul_rpow` and `sum_weighted_moebius_coeff_sq_le` give the arithmetic estimates. `card_spaced_detected_le` combines these with `hybrid_large_sieve`. [Divisor bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CardSpacedDetectedLe.lean#L51) · [Weighted square sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CardSpacedDetectedLe.lean#L154) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CardSpacedDetectedLe.lean#L225) · [Hybrid large sieve](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/HybridLargeSieve.lean#L127)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
