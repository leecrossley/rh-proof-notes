# A prime mean-square lower bound from a large derivative

[Chinese proof](../zh/%E5%A4%A7%E5%AF%BC%E6%95%B0%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E6%88%AA%E6%96%AD%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E5%9D%87%E6%96%B9%E4%B8%8B%E7%95%8C.md)

For coefficients $c_n$ with $|c_n|\le1$, let $D_k(c;s)=k!^{-1}\sum_{n\ge1}\Lambda(n)c_n(\log n)^k n^{-s}$ on $\Re s>1$.

**Proposition.** For each $A\ge1$ there are $0<a<b$, $C,r_0>0$ and $K_0$ such that for $0<r\le r_0$ and integers $K,k$ with $K_0\le K\le k\le2K$, if $|D_k(c;1+r)|\ge(Ar)^{-(k+1)}$ then
$$
\int_N^M \left|\sum_{N<p\le y}\frac{\log p}{p}c_p\right|^2\frac{dy}{y}
\ge r^{-3}e^{-CK},\qquad N=e^{aK/r},\quad M=e^{bK/r}.
\tag{1}
$$

Let $P_k(u)=u^ke^{-u}/k!$, the weight `pw k u`. Then $r^kD_k(c;1+r)=\sum_n(\Lambda(n)/n)c_n P_k(r\log n)$. From one term of the exponential series,
$$
0\le P_k(u)\le \vartheta^k e^{u/\vartheta-u}\quad(u\ge0,\ \vartheta>0).
\tag{2}
$$
In particular $P_k\le1$. Fix a small $d>0$ and use $a=d/3$, $b=32/d$. For $u\le aK$ use $\vartheta=d/3$ and $u/\vartheta\le k$, $e<3$, to get $P_k(u)\le d^k e^{-u/2}$. For $u\ge bK$ use $\vartheta=4$ and $u/4\ge (4/d)k$, which gives the same bound. Keep prime terms $N<p\le M$ with modified weights $P_k(r\log p)-P_k(r\log M)$. Outside the window the omitted weights satisfy the tail bounds. Inside it, the subtracted weight is at most $d^k p^{-r/2}$. Thus the total prime error is at most $d^k\sum_n\Lambda(n)n^{-1-r/2}$.

For $n=p^j$, $j\ge2$, (2) with $\vartheta=4r$ gives $P_k(r\log n)\le(4r)^k n^{1/4}$. These terms cost at most $(4r)^k B$, where $B=\sum_p\sum_{j\ge2}(\log p)p^{-3j/4}$ is finite by summing the geometric series and comparing with $\sum_{n\ge2}(\log n)n^{-3/2}$. Choose an absolute $C_0\ge1$ so that $\sum_n\Lambda(n)n^{-1-s}\le C_0/s$ for $0<s\le1$. This follows from the log derivative of $\zeta$ since subtracting its pole $1/s$ leaves a bounded function on this interval.

Write $S(y)=\sum_{N<p\le y}(\log p)c_p/p$ and $f(y)=P_k(r\log y)$. For $k\ge1$, $P'_k=P_{k-1}-P_k$, hence $|f'(y)|\le r/y$. Since $f(p)-f(M)=-\int_p^M f'(y)dy$, the modified prime sum is $-\int_N^M S(y)f'(y)dy$. The estimates give
$$
r^k|D_k(c;1+r)|\le r\int_N^M|S(y)|\,dy/y
+d^k\sum_n\Lambda(n)n^{-1-r/2}+(4r)^k B.
$$
Take $\eta=(16C_0 A)^{-1}$, $d=\eta/A$, $r_0=(8A(B+1))^{-1}$, and $K_0=1$. Let $Q=A^{-k-1}/r$, the lower bound for the left side. The prime error is at most $A^{-k}\eta^k 2C_0/r\le Q/8$. The prime-power error is at most $Q/8$ by $4r\le1/A$ and $B\le1/(8Ar)$. Thus $\int_N^M|S(y)|dy/y\ge Q/(2r)$.

Cauchy–Schwarz and $\log(M/N)\le bK/r$ give a square integral at least $1/(4bK A^{2(k+1)}r^3)$. Since $2(k+1)\le6K$ and $4bK\le e^{4bK}$, this proves (1) with $C=6\log A+4b$.

## Lean correspondence

- `pw_le`, `pw_small`, `pw_large` and `pw_pp` give the three tail estimates. `abel_pw` converts the truncated prime sum to an integral and `large_mean_of_large_derivative` concludes. [Tail estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LargeMeanOfLargeDerivative.lean#L19) · [Abel summation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LargeMeanOfLargeDerivative.lean#L218) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LargeMeanOfLargeDerivative.lean#L247)
- The $\zeta$ estimate and higher prime-power summability have separate proofs. [Zeta bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsTsumVonMangoldtDivRpowLeDiv.lean#L12) · [Higher powers](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNonPrimeVonMangoldtDivRpow.lean#L107)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
