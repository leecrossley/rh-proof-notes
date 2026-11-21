# Detecting zeros near one by Möbius truncation

[Chinese proof](../zh/M%C3%B6bius%E6%88%AA%E6%96%AD%E6%80%8E%E6%A0%B7%E6%A3%80%E6%B5%8B%E9%9D%A0%E8%BF%91%E4%B8%80%E7%9A%84%E9%9B%B6%E7%82%B9.md)

For an integer $Q\ge2$ and a character $\chi$ put
$$
b_Q(n)=\sum_{d\mid n,\ d\le Q^3}\mu(d),\qquad
F_{Q,\chi}(s)=\sum_{Q^3<n\le Q^6} b_Q(n)\chi(n)n^{-s}.
$$
Here $\mu$ is the Möbius function. For modulus $1$, write $F_{Q,1}$.

**Proposition.** If $Q\ge1024$, $1\le q\le Q$, $\chi\bmod q$ is nonprincipal, and $\rho=\beta+i\gamma$ satisfies $L(\rho,\chi)=0$, $\beta\ge1-1/400$, $|\gamma|\le Q$, then $|F_{Q,\chi}(\rho)|\ge1/2$. There is also an absolute integer $Q_0\ge1024$ such that if $Q\ge Q_0$, $\zeta(\rho)=0$, $1-1/400\le\beta<1$, and $Q^{1/20}\le|\gamma|\le Q$, then $|F_{Q,1}(\rho)|\ge1/2$.

## The finite convolution

For a completely multiplicative $f$ and cutoffs $D,X\ge0$, writing $n=dm$ gives
$$
\sum_{n\le X}\left(\sum_{d\mid n,\ d\le D}a_d\right) f(n)
=\sum_{d\le D} a_df(d)\sum_{m\le\lfloor X/d\rfloor}f(m),
$$
where all integer indices start at $1$. For $a_d=\mu(d)$ the initial coefficients $1\le n\le D$ are $\sum_{d\mid n}\mu(d)=\prod_{p\mid n}(1-1)$. They vanish except at $n=1$, where the product is $1$. Taking $D=Q^3,X=Q^6$ yields
$$
1+F_{Q,\chi}(s)=
\sum_{d\le Q^3}\mu(d)\chi(d)d^{-s}\sum_{m\le M_d}\chi(m)m^{-s},
\qquad M_d=\lfloor Q^6/d\rfloor .
\tag{1}
$$

## Nonprincipal characters

Let $\sigma=\Re s>0$ and $A(n)=\sum_{j\le n}\chi(j)$. The sum over a period vanishes by multiplying the residues by a unit with $\chi(u)\ne1$, so $|A(n)|\le q$. For $M\ge1$,
$$
\sum_{n\le M}\chi(n)n^{-s}
=\sum_{n=1}^M A(n)\bigl(n^{-s}-(n+1)^{-s}\bigr)+A(M)(M+1)^{-s}.
$$
The absolute difference at $n$ is at most $|s|\int_n^{n+1}t^{-\sigma-1}dt$. The difference series converges locally uniformly on $\Re s>0$, and the finite boundary term vanishes as $M\to\infty$. Agreement on $\Re s>1$ and the identity theorem give $L(s,\chi)$ there. Bounding the difference-series tail by its telescoping integral and adding the boundary term gives
$$
\left|L(s,\chi)-\sum_{n\le M}\chi(n)n^{-s}\right|
\le q(1+|s|/\sigma)(M+1)^{-\sigma}
\le2q(1+|s|/\sigma)M^{-\sigma}.
\tag{2}
$$

At $\rho$, the coefficient in the weaker bound (2) is at most $8Q^2$ since $\beta>1/2$ and $|\rho|\le\beta+Q$. For $d\le Q^3$,
$$
Q^6/2\le Q^6-d\le dM_d\le Q^6,\qquad
(dM_d)^\beta\ge(Q^6/2)^{11/12}\ge16Q^5.
$$
The second bound uses $\beta\ge11/12$ and $Q\ge1024$. Since $L(\rho,\chi)=0$, each summand in (1) has modulus at most $8Q^2(dM_d)^{-\beta}\le1/(2Q^3)$. Thus $|1+F_{Q,\chi}(\rho)|\le1/2$ and $|F_{Q,\chi}(\rho)|\ge1/2$.

## The zeta pole term

For $\Re s>1$, write $n^{-s}=s\int_n^\infty t^{-s-1}\,dt$ and interchange the absolutely convergent sum over $n>M$ with the integral. As there are $\lfloor t\rfloor-M$ such $n\le t$,
$$
\zeta(s)-\sum_{n=1}^M n^{-s}
=\frac{M^{1-s}}{s-1}-s\int_M^\infty\{t\}t^{-s-1}\,dt.
\tag{3}
$$
The fractional part is bounded by $1$. The integral and its $s$ derivative converge locally uniformly on $\Re s>0$ by comparison with $t^{-1-\delta}$ and $(\log t)t^{-1-\delta}$ on compact subsets. Thus (3) holds for $\Re s>0$, $s\ne1$. Its last term has modulus at most $(|s|/\sigma)M^{-\sigma}$.

Use (3) at a zeta zero in the proposition. With $|\rho|/\beta\le4Q$ and $|\rho-1|\ge Q^{1/20}$,
$$
\left|\sum_{m\le M_d}m^{-\rho}\right|
\le4Q M_d^{-\beta}+M_d^{1-\beta}Q^{-1/20}.
$$
In (1) the first term, after multiplying by $d^{-\beta}$ and summing, is at most $1/4$ by the bound on $(dM_d)^\beta$. The second term is $d^{-1}(dM_d)^{1-\beta}Q^{-1/20}$ per $d$, with sum at most $(1+3\log Q)Q^{6/400-1/20}=(1+3\log Q)Q^{-7/200}$. This tends to zero, and Lean also bounds it by $301Q^{-1/40}$. Take $Q_0$ such that this term is at most $1/4$. We again get $|1+F_{Q,1}(\rho)|\le1/2$, completing the proposition.

## Lean correspondence

- `sum_trunc_conv`, `sum_initial`, `rpow_bound`, and `zero_detect` give (1), the initial cancellation, the cutoff bound, and the nonprincipal conclusion. [Convolution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L9) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L108)
- `abel`, `LFunction_eq_tsum` and `norm_LFunction_sub_sum_le` give (2). [Partial summation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L127) · [Tail](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LFunctionEqTsumOfOneLt.lean#L226)
- `zeta_eq_sum` and `norm_zeta_sub_sum_le` give (3) and its remainder estimate. `pole_small` and `zeta_zero_detect` treat the pole. [Tail identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormRiemannZetaSubPartialSumLe.lean#L78) · [Pole bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L8) · [Zeta conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L38)
- The [hybrid large-sieve count](hybrid-sieve-count-of-separated-detections.md) uses the two detection inequalities as its input.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
