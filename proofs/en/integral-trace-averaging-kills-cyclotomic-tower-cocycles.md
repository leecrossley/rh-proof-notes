# Integral trace averaging kills cyclotomic tower cocycles

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E6%95%B4%E6%95%B0%E8%BF%B9%E5%B9%B3%E5%9D%87%E6%B6%88%E6%8E%89%E5%88%86%E5%9C%86%E5%A1%94%E9%A1%B6%E7%9A%84%E4%B8%80%E9%98%B6%E4%BD%99%E9%97%AD%E9%93%BE.md)

## Statements

Let $\ell$ be prime, $K_0/\mathbb Q_\ell$ finite unramified, $K_\infty=K_0(\mu_{\ell^\infty})$, $H=G_{K_\infty}$, $C=\mathbb C_\ell$ and $O_C$ its unit ball with the coordinatewise isometric Galois action. If $c:H\to O_C^r$ is a continuous cocycle for $r\ge0$, then for each $a\in K_\infty$ with $|a|_\ell<1$ there is $x\in O_C^r$ with $ac(h)=hx-x$ for all $h$. Also $O_C^H$ equals the closure $\widehat{\mathcal O}_\infty$ of the integers of $K_\infty$. Both use [almost surjectivity of integral trace](integral-trace-is-almost-surjective-in-the-cyclotomic-tower.md).

## Approximate averaging

Work in one coordinate with $|c(h)|\le t$. Given $\eta>0$, continuity at one gives an open normal subgroup $V\subset H$ with $|c(v)|\le\eta$ there. Take representatives $S$ of the quotient, and choose an integral $b$ in the fixed field of $V$ with $\sum_s s(b)=a$ using the trace result. Put $x_0=-\sum_s s(b)c(s)$, so $|x_0|\le t$. For $hs=\sigma_s v_s$ with $\sigma_s\in S$, $v_s\in V$, the cocycle identity gives
$$
h x_0=ac(h)+x_0-\sum_s \sigma_s(b)\sigma_s c(v_s).
$$
Indeed $h c(s)=c(hs)-c(h)$, $v_s(b)=b$, and the $\sigma_s$ permute $S$. The last sum has norm at most $\eta$. Thus $ac-\delta x_0$ has norm at most $\eta$, with $\delta x(h)=hx-x$.

For nonzero $a$ start with $x_0=0$ and residual bound $|a|$. If $|x_n|\le1$ and the residual is at most $|a|2^{-n}$, apply approximate averaging to $c-a^{-1}\delta x_n$, a cocycle of norm at most $2^{-n}$ because $a$ is fixed. At accuracy $|a|2^{-(n+1)}$ it gives correction $z_n$ of norm at most $2^{-n}$. Then $x_{n+1}=x_n+z_n$ stays integral and has the improved residual. The corrections converge by completeness and the ultrametric inequality. Passing to the limit makes the residual zero. The case $a=0$ is immediate, and coordinates give the claimed vector version.

## Fixed elements and twists

For $y\in O_C^H$ and $\eta>0$, choose algebraic $x$ with $|y-x|<|\ell|\min(\eta,1)$, in a finite normal $E/K_\infty$. Choose integral $b\in E$ of trace $\ell$, and set $w=\ell^{-1}\operatorname{Tr}(bx)\in K_\infty$. Since all embeddings fix $y$,
$$
|\ell(y-w)|=\left|\sum_s s(b)s(y-x)\right|\le|y-x|.
$$
Thus $w$ is integral and approaches $y$. Conversely $H$ fixes the whole closure by continuity.

For the cyclotomic level in the [missing-weight argument](missing-hodge-tate-weights-control-approximate-invariants.md), a fixed element of $C$ twisted by $\chi^i$ over $G_m$ can be scaled to integral and split in $O_m\oplus X_m$ by the fixed-ring calculation. Both parts are fixed by the twisted generator. On $X_m$, [injectivity in rank one with $U=I$](weight-differences-annihilate-cyclotomic-coinvariant-torsion.md) forces zero. On $O_m$ the condition is $(\chi(g)^i-1)y_0=0$. For $i\ne0$, the power valuation implies $y_0=0$. For $i=0$ the fixed field is $K_m$, after undoing the scaling.

## Lean correspondence

- [`average` and `step`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTateMaximalIdealKillsFirstCohomology.lean#L64), [`rank_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTateMaximalIdealKillsFirstCohomology.lean#L103) and [the coordinatewise result](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTateMaximalIdealKillsFirstCohomology.lean#L164) give the averaging and convergence.
- [`fixed_iff_mem_Ohat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CyclotomicTowerFixedIffMemCompletedIntegers.lean#L88) and [`invariants_twist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TateInvariantsCyclotomicTwist.lean#L54) give the fixed ring and twisted vanishing.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
