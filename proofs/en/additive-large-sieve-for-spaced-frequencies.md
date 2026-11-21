# The additive large sieve at the actual frequency spacing

[Chinese proof](../zh/%E6%8C%89%E5%AE%9E%E9%99%85%E9%A2%91%E7%8E%87%E9%97%B4%E8%B7%9D%E8%AE%A1%E8%B4%B9%E7%9A%84%E5%8A%A0%E6%B3%95%E5%A4%A7%E7%AD%9B.md)

Write $e(u)=e^{2\pi i u}$.

**Proposition.** Let $M,L\in\mathbb Z_{\ge0}$ and $a_m\in\mathbb C$ for $M<m\le M+L$. Let $X\subseteq\mathbb R$ be finite and $0<\delta\le1$. Assume $|x-y-k|\ge\delta$ for distinct $x,y\in X$ and all $k\in\mathbb Z$. For $F(t)=\sum_{M<m\le M+L}a_m e(mt)$,
$$
\sum_{x\in X}|F(x)|^2
\le(\delta^{-1}+2\pi L)\sum_{M<m\le M+L}|a_m|^2.
\tag{1}
$$

When $L=0$ or $X$ is empty the conclusion is immediate. For continuously differentiable real $f$ and continuous $h\ge|f'|$ on $[x,x+\delta]$, integrate the derivative of $(t-x-\delta)f(t)/\delta$ to obtain
$$
f(x)\le\int_x^{x+\delta}(f(t)/\delta+h(t))\,dt.
\tag{2}
$$
The two endpoint terms give $f(x)$, and the coefficient of $f'$ has modulus at most $1$.

Put $c=M+L/2$, $U(t)=e(-ct)F(t)$, and $\Omega=\pi L>0$. The derivative of $U$ has coefficients $b_m=2\pi i(m-c)a_m$ with $|b_m|\le\Omega|a_m|$. For $f=|U|^2=|F|^2$ we have $|f'|\le2|U||U'|\le\Omega |U|^2+\Omega^{-1}|U'|^2$. The integrand in (2) can therefore be taken as $g=(\delta^{-1}+\Omega)|U|^2+\Omega^{-1}|U'|^2\ge0$.

Fix $y\in X$ and let $x'=x-\lfloor x-y\rfloor\in[y,y+1)$ for each $x$. The periodicity of $F$ gives $f(x')=f(x)$. The spacing condition separates the representatives by at least $\delta$ and keeps each at distance at least $\delta$ from $y+1$, including $x'=y$. Hence the intervals $[x',x'+\delta]$ lie in $[y,y+1]$ with disjoint interiors. Summing (2) gives $\sum_{x\in X}f(x)\le\int_y^{y+1}g(t)\,dt$.

Upon expanding the squares, each cross-frequency difference is an integer, and its exponential has integral zero over $[y,y+1]$ unless the difference vanishes. Thus $\int_y^{y+1}|U|^2=\sum_m|a_m|^2$ and $\int_y^{y+1}|U'|^2=\sum_m|b_m|^2\le\Omega^2\sum_m|a_m|^2$. Substitution gives (1).

## Lean correspondence

- `gallagher_interval` is (2), `sum_intervalIntegral_le_of_spaced` sums over the intervals, and `expSum_sub_int` gives periodicity. [Local estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIntervalIntegralLeOfSpaced.lean#L6) · [Spacing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIntervalIntegralLeOfSpaced.lean#L90)
- `norm_expSum_shift` centers the frequencies, and `integral_norm_sq_expSum` gives the orthogonal integral. `additive_large_sieve` combines them. [Centering and integration](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIntervalIntegralLeOfSpaced.lean#L36) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumIntervalIntegralLeOfSpaced.lean#L125)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
