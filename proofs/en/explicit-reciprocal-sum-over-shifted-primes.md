# An explicit bound for the reciprocal sum over shifted primes

[Chinese proof](../zh/%E7%B4%A0%E6%95%B0%E7%A7%BB%E4%BD%8D%E5%80%92%E6%95%B0%E5%92%8C%E7%9A%84%E6%98%BE%E5%BC%8F%E4%B8%8A%E7%95%8C.md)

**Proposition.** For every integer $y\ge3$,
$$
S(y)=\sum_{p\le y,\ p\text{ prime}}\frac1{p-1}\le7\log\log y+6.
\tag{1}
$$

## The weighted estimate

For every nonnegative integer $N$,
$$
B(N)=\sum_{p\le N}\frac{\log p}{p-1}\le\log N+2.2,
\tag{2}
$$
with $\log0=0$ in Lean. The cases $N\le3$ follow by direct evaluation. For $N\ge4$, write $P_n=\prod_{p\le n}p$. We have $P_n\le4^n$ by induction. For even $n\ge4$ use $P_n=P_{n-1}$. For odd $n=2m+1\ge3$, every prime $m+1<p\le2m+1$ divides $\binom{2m+1}m$. The product of these primes divides it, and $\binom{2m+1}m\le2^{2m}$ since the two central coefficients are equal. Thus $P_n\le P_{m+1}4^m\le4^n$.

From $v_p(N!)\ge\lfloor N/p\rfloor$, summing gives $N\sum_{p\le N}(\log p)/p\le\log(N!)+N\log4$. Concavity of $\log$ yields $\int_k^{k+1}\log t\,dt\ge(\log k+\log(k+1))/2$. Summing gives
$$
N^{-1}\log(N!)\le\log N-1+1/N+(\log N)/(2N).
$$
For $N\ge4$ the last terms are at most $0.45$, using $\log N\le N/e\le0.4N$. Therefore $\sum_{p\le N}(\log p)/p\le\log N-0.55+\log4$.

The difference when replacing $p$ by $p-1$ is bounded by $\sum_{n=2}^N(\log n)/(n(n-1))$. Put $g(x)=(\log x+4/3)/x$. For $n\ge3$, $(n+1)(\log(n+1)-\log n)\le(n+1)/n\le4/3$ yields $g(n)-g(n+1)\ge\log(n+1)/(n(n+1))$. Thus the difference is at most $(\log2)/2+(\log3)/6+g(3)-g(N)\le(\log2+\log3)/2+4/9$. Combining, the added constant above $\log N$ is less than $2.2$ by $\log2<0.7$ and $\log3<1.11$. These follow by lower-bounding the exponential series at $0.7$ and at $1.11$. This proves (2).

## Removing the weight

For $3\le y\le8$ the sum is at most $23/12$ and $\log\log y>0$. For $y\ge9$ use strong induction at $s=\lfloor\sqrt y\rfloor$. Every $p>s$ has $\log p>(\log y)/2$. By (2) and $\log y>2$ the contribution above $s$ is at most $2+4.4/\log y\le4.2$. Also $\log\log s\le\log\log y-\log2$. Since $7\log2\ge4.2$, induction proves (1). The inequality $\log2\ge2/3$ follows by integrating $1/t\ge4/3-4t/9$ on $[1,2]$.

A sharper corollary of (2) follows by partial summation. For $t\ge2$ set $B(t)=B(\lfloor t\rfloor)$. The formula $1/\log p=1/\log y+\int_p^y dt/(t\log^2t)$ gives
$$
S(y)=B(y)/\log y+\int_2^y B(t)\frac{dt}{t\log^2t}
\le\log\log y+1-\log\log2+\frac{2.2}{\log2}\le\log\log y+5
$$
for $y\ge2$. The last step uses $\log2\ge2/3$. The project statement is (1).

## Lean correspondence

- `sum_log_div_pred_le` is (2). The Lean proof uses Mathlib's primorial bound and Stirling monotonicity, which give the product and factorial estimates above. [Weighted sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/SumPrimeLogDivPredLeLogAdd.lean#L131)
- `sum_inv_pred_small` and `inv_pred_le_of_sqrt_lt` give the induction base and the term bound, combined by `sum_inv_pred_le`. The project later uses (1) to bound the total reciprocal weight over selected primes in `primeSum_eOf`. [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/SumPrimesInvPredLeLoglog.lean#L41) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/SumPrimesInvPredLeLoglogStatement.lean#L5) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/WeightedPrimeLogSumOscillationBoundLe.lean#L145)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
