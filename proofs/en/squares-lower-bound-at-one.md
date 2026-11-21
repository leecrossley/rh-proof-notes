# A lower bound at one from square terms of a Lambert series

[Chinese proof](../zh/%E5%B9%B3%E6%96%B9%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E5%AE%9E%E7%89%B9%E5%BE%81%E5%9C%A8%E4%B8%80%E5%A4%84%E7%9A%84%E4%B8%8B%E7%95%8C.md)

**Proposition.** Let $q\ge1$ and let $\chi$ be a nonprincipal real Dirichlet character modulo $q$. Then
$$
|L(1,\chi)|\ge \frac1{36q}.
\tag{1}
$$
In particular the weaker bound $(1/36)q^{-3/2}$ holds. The [low-height gap proof](effective-low-height-zero-gap.md) uses this weaker form.

Put $A_\chi(n)=\sum_{d\mid n}\chi(d)$. This multiplicative function takes the value $\sum_{i=0}^j \chi(p)^i$ at $p^j$. According as $\chi(p)$ is $0$, $1$, or $-1$, this sum is $1$, $j+1$, or $\mathbf1_{2\mid j}$. Thus $A_\chi(n)\ge0$ and $A_\chi(m^2)\ge1$ for every $m\ge1$. For $\alpha>0$ regroup the absolutely summable double series to get
$$
F(\alpha)=\sum_{n\ge1}A_\chi(n)e^{-\alpha n}
=\sum_{d,k\ge1}\chi(d)e^{-\alpha dk}
=\sum_{d\ge1}\frac{\chi(d)}{e^{\alpha d}-1}.
$$
Indeed the absolute sum is at most $\sum_{d\ge1}e^{-\alpha d}/(1-e^{-\alpha})$. For an integer $J\ge1$ and $\alpha=J^{-2}$, the $J$ squares of $1,\ldots,J$ have weights at least $e^{-1}>1/3$. Consequently $F(J^{-2})\ge J/3$.

A complete period of $\chi$ sums to zero. Multiplication of the residues by a unit $u$ with $\chi(u)\ne1$ proves this by multiplying the sum by $\chi(u)$ while preserving it. Hence $B(N)=\sum_{n\le N}\chi(n)$ satisfies $|B(N)|\le q$. For nonnegative nonincreasing $b_n$, partial summation gives
$$
\sum_{n=1}^N\chi(n)b_n=B(N)b_N+\sum_{n=1}^{N-1}B(n)(b_n-b_{n+1}).
$$
The nonnegative weights on the right add to $b_1$, so the absolute value is at most $qb_1$.

The function $w(x)=x^{-1}-(e^x-1)^{-1}$ on $x>0$ takes values in $[0,1]$. The lower bound follows from $e^x\ge1+x$, and the upper bound from $x\ge1-e^{-x}$. It is nonincreasing: $w'(x)=-1/x^2+e^x/(e^x-1)^2\le0$ follows from $e^{x/2}-e^{-x/2}\ge x$. The latter inequality follows by integration of the derivative, which is at least $1$.

For $\epsilon>0$ we may subtract two absolutely convergent series:
$$
\alpha^{-1}L(1+\epsilon,\chi)-\sum_{n\ge1}\frac{\chi(n)n^{-\epsilon}}{e^{\alpha n}-1}
=\sum_{n\ge1}\chi(n)n^{-\epsilon}w(\alpha n).
$$
On the right the weight is nonnegative and nonincreasing with first term at most $1$, so the modulus is at most $q$. Let $\epsilon\downarrow0$. The first term on the left converges by continuity of $L$, and the other by domination by $(e^{\alpha n}-1)^{-1}$. We obtain $|\alpha^{-1}L(1,\chi)-F(\alpha)|\le q$.

Choose $J=6q$. Then $F(J^{-2})\ge2q$ and the last inequality gives $\alpha^{-1}|L(1,\chi)|\ge q$. Multiplying by $\alpha=(6q)^{-2}$ proves (1).

## Lean correspondence

- `abel_bound` and `char_sum_bound` give the partial-summation and period bounds. The weight properties are in the same file. [Partial summation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L8) · [Weight](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L76)
- `one_le_zetaMul_sq`, `lambert` and `lambert_lower` give the square contribution, and `compare_right` and `compare_one` bound the Lambert-series error. [Squares](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L121) · [Lambert series](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L140) · [Comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L256)
- `inv_le_norm_LFunction_one` proves (1) and `exists_le_norm_LFunction_one` gives the weaker exponent. [Exact bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L339) · [Weaker form](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLeNormLFunctionOne.lean#L354)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
