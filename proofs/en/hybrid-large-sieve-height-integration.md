# The height integral in the hybrid large sieve

[Chinese proof](../zh/%E6%B7%B7%E5%90%88%E5%A4%A7%E7%AD%9B%E7%9A%84%E7%A7%AF%E5%88%86%E5%9B%A0%E5%AD%90%E4%BB%8E%E5%93%AA%E9%87%8C%E6%9D%A5.md)

**Proposition.** There is an absolute $C>0$ such that for any integer $Q\ge1$, integer $N\ge0$, complex $a_1,\ldots,a_N$, and real $T\ge1$,
$$
\sum_{q\le Q}\sum_{\chi\bmod q}^{*}\int_{-T}^T
\left|\sum_{1\le n\le N}a_n\chi(n)n^{-it}\right|^2dt
\le C\sum_{n=1}^N(Q^2T+n)|a_n|^2.
\tag{1}
$$
The sum is over primitive characters. The case $N=0$ has both sides zero.

Set $h=1/T$. For fixed $\chi$, write $D(t)=\sum_n a_n\chi(n)n^{-it}$ and $f(v)=\sum_n a_n\chi(n)\mathbf1_{[\log n-h,\log n)}(v)$. With the Fourier convention $\widehat f(w)=\int f(v)e^{-2\pi i wv}dv$, substituting $v=\log n-u$ gives $\widehat f(w)=D(2\pi w)\int_0^h e^{2\pi i w u}du$. For $|t|\le T$, the kernel $\int_0^h e^{itu}du$ has real part at least $h/2$ by $|tu|\le1$ and $\cos(tu)\ge1-(tu)^2/2$. Change variables $t=2\pi w$ and apply Plancherel for the step function. Then with $x=e^v$,
$$
\int_{-T}^T|D(t)|^2dt\le8\pi T^2\int_0^\infty |W_\chi(x)|^2 dx/x,
\quad W_\chi(x)=\sum_{n\in I_x}a_n\chi(n),\quad
I_x=\{1\le n\le N:x<n\le xe^{1/T}\}.
\tag{2}
$$
The [prime mean-value proof](fixed-modulus-prime-second-moment.md) gives a Gaussian proof of this form of Plancherel.

For each $x$ the window lies in an integer interval of length $L=\lfloor xe^{1/T}\rfloor-\lfloor x\rfloor$. The inequality $e^{1/T}-1\le2/T$ gives $L\le2x/T+1$, so $2\pi L\le8(2n/T+1)$ for each $n\in I_x$. Apply the [multiplicative large sieve](gauss-sums-and-the-multiplicative-large-sieve.md) with coefficients zero outside $I_x$ to obtain
$$
\sum_{q\le Q}\sum_\chi^* |W_\chi(x)|^2
\le \sum_{n\in I_x}(Q^2+8(2n/T+1))|a_n|^2.
$$
Each $n$ is present for $ne^{-1/T}\le x<n$, of $dx/x$ measure $1/T$. Summing and integrating in (2) thus bounds the left side of (1) by $8\pi\sum_n(Q^2T+16n+8T)|a_n|^2$. This is bounded by (1) with $C=128\pi$. The factor $T^2$ in (2) and the occurrence length $1/T$ leave the factor $T$ multiplying $Q^2$, while the term $n/T$ from the window length becomes $n$.

## Lean correspondence

- `plancherel`, `exp_sum` and `gallagher` give (2). [Plancherel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IntegralNormSqLp.lean#L41) · [Window inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IntegralNormSqLp.lean#L163)
- `window` applies `sum_norm_sq_primitive_char_sum_le`, `kernel_integral` gives $1/T$, and `hybrid_large_sieve` combines them. [Multiplicative input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieveStatement.lean#L6) · [Occurrence length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/HybridLargeSieve.lean#L32) · [Sieve conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/HybridLargeSieve.lean#L127)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
