# Polynomial growth of L-functions from finite differences

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E6%9C%89%E9%99%90%E5%B7%AE%E5%88%86%E6%8E%A7%E5%88%B6L%E5%87%BD%E6%95%B0%E7%9A%84%E5%A2%9E%E9%95%BF.md)

**Proposition.** There are absolute constants $C,C'>0$ such that for every $q\ge1$, nonprincipal character $\chi\bmod q$, and $\Re s\ge-7/4$,
$$
|L(s,\chi)|\le Cq^4(|s|+2)^4.
$$
For $\Re s\ge-7/4$ and $s\ne1$ one also has $|(s-1)\zeta(s)|\le C'(|s|+2)^5$. These bounds cover the exterior disks in the [local zero count](local-log-derivative-from-disk-zeros.md).

## Three summations by parts

Let $a_n$, $n\ge0$, be periodic of period $q$ with zero period sum and $|a_n|\le M$. The partial sums $T(n)=\sum_{j<n}a_j$ are periodic and bounded by $qM$. Let $\mu$ be the period mean of $T(n+1)$ and let $b_n=T(n+1)-\mu$. Then the new sequence has zero period sum and $|b_n|\le 2qM$, while $|\mu|\le qM$. Summation by parts for an absolutely summable $u_n$ gives
$$
\sum_{n\ge0}a_nu_n
=\sum_{n\ge0}T(n+1)(u_n-u_{n+1})
=\mu u_0+\sum_{n\ge0}b_n(u_n-u_{n+1}).
\tag{1}
$$
The finite boundary term vanishes since $T$ is bounded and $u_n\to0$. Subtracting the mean allows (1) to be iterated.

For $x>0$, let $\Delta_s^0(x)=x^{-s}$ and $\Delta_s^{k+1}(x)=\Delta_s^k(x)-\Delta_s^k(x+1)$. Repeated integration of the derivative gives
$$
\Delta_s^k(x)=s(s+1)\cdots(s+k-1)\int_{[0,1]^k}
(x+t_1+\cdots+t_k)^{-s-k}\,dt_1\cdots dt_k .
$$
Thus if $\Re s+k\ge0$, then $|\Delta_s^k(x)|\le (|s|+k)^k x^{-\Re s-k}$. Each difference is entire in $s$ by its finite-sum expression.

On $\Re s>1$ apply (1) three times, starting with $a_n=\chi(n+1)$ and $u_n=(n+1)^{-s}$. The successive bounds for the input coefficients are $1$, $2q$, and $4q^2$. We get
$$
L(s,\chi)=\mu_1+\mu_2\Delta_s^1(1)+\mu_3\Delta_s^2(1)
+\sum_{n\ge0}b_n\Delta_s^3(n+1),
\tag{2}
$$
where $|\mu_1|\le q$, $|\mu_2|\le2q^2$, $|\mu_3|\le4q^3$, and $|b_n|\le8q^3$. For $\Re s\ge-15/8$, the last sum is dominated on $|s|\le A$ by $8q^3(A+3)^3\sum_{n\ge1} n^{-9/8}$. The identity theorem therefore gives (2) throughout $\Re s>-15/8$. On $\Re s\ge-7/4$ the terms satisfy $|\Delta_s^1(1)|=|1-2^{-s}|\le 5$, $|\Delta_s^2(1)|\le(|s|+2)^2$, and the series costs at most $8q^3(|s|+3)^3 Z$ with $Z=\sum_{n\ge1}n^{-9/8}$. Using $q\ge1$ and $|s|+3\le2(|s|+2)$ yields the first estimate, for example with $C=15+64Z$.

## The zeta factor with its pole removed

Write $w=1-s$. For $x\ge1$ define
$$
T(x,s)=x^w-\frac w2 x^{w-1}+\frac{w(w-1)}{12}x^{w-2},
\qquad E(x,s)=T(x+1,s)-T(x,s)-w x^{w-1}.
$$
For $u(t)=(x+t)^w$ take $B_1=t-1/2$, $B_2=(t^2-t+1/6)/2$, and $B_3=(t^3-3t^2/2+t/2)/6$. Their derivatives are $1,B_1,B_2$ in order. For $G=u-B_1u'+B_2u''-B_3u'''$ this gives $G'=-B_3u^{(4)}$. Also $B_3$ vanishes at both endpoints and $B_2$ equals $1/12$ there. Hence $G(1)=T(x+1,s)$ and $G(0)=T(x,s)+w x^{w-1}$. It follows that
$$
E(x,s)=-\int_0^1 B_3(t)w(w-1)(w-2)(w-3)(x+t)^{w-4}\,dt .
$$
Since $|B_3(t)|\le1$ and the four factors $|w-i|$ are at most $|s|+2$, $\Re s\ge-15/8$ gives $|E(x,s)|\le (|s|+2)^4x^{-9/8}$.

On $\Re s>1$ we have $T(N+1,s)\to0$. Telescoping the definition of $E$ gives
$$
(s-1)\zeta(s)=T(1,s)+\sum_{n\ge1} E(n,s).
$$
The estimate on $E$ gives locally uniform convergence for $\Re s>-15/8$, so the equality continues there with value $1$ at $s=1$. Finally $|T(1,s)|\le1+(|s|+2)/2+(|s|+2)^2/12$, so the bound holds with $C'=3+Z$.

## Lean correspondence

- `abel_step` and `abel_three` give (1) and (2). `norm_diffPow_le` bounds the differences, `LFunction_eq` continues the series, and `norm_LFunction_le_poly_left` gives the proposition. [Abel step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L37) · [Difference](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L83) · [Final estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SummableNinePowMulInvSqSucc.lean#L269)
- `emT` and `emE` are the zeta telescoping quantities, `norm_emE_le` bounds the remainder, and `eq_of_one_lt` and `eq_of_lt` establish the equality and its continuation. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L7) · [Continuation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L168) · [Final bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NormSubOneMulRiemannZetaLe.lean#L188)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
