# From a mean square at a fixed point to good primes on an interval

[Chinese proof](../zh/%E5%B9%B3%E6%96%B9%E5%B9%B3%E5%9D%87%E6%80%8E%E6%A0%B7%E7%AD%9B%E6%8E%89%E5%8C%BA%E9%97%B4%E4%B8%8A%E7%9A%84%E5%9D%8F%E7%B4%A0%E6%95%B0.md) · [Reading and review status](../../STATUS.md)

The mean-square estimate holds for a common argument $y$. A bad prime can fail the desired bound at an argument that depends on the prime. This lemma handles these varying arguments by controlling the derivative on dyadic intervals.

## Statement

Let $Z\in\mathbb R$, let $\kappa:\mathbb N\to\mathbb C$, and write $J_q(n)=(n/q)$ for the quadratic symbol used in the source, applied to odd primes in the sieve. Put

$$
S(y,q;\kappa)=\sum_{1\le n\le\lfloor Z\rfloor}
\Lambda(n)\kappa(n)J_q(n)\min(1,y/n),
$$

where the sum is empty if the upper cutoff is below one. For a finite set $P\subseteq\mathbb N$, the mean-square input `MeanSq` requires, for each $y\in[Y,X]$ and every sequence $a$ with $|a(n)|\le1$,

$$
\sum_{q\in P}|S(y,q;a)|^2\le Cy\log y\,|P|. \tag{1}
$$

**Claim.** For $C\ge0$, $\tau>0$ and $\eta>0$, there is $Y_0\ge2$ with the following property. Take reals $Y\ge Y_0,X,Z$, finite sets $B\subseteq P\subseteq\mathbb N$, and a coefficient sequence $\kappa$ bounded by one. If (1) holds and for every $q\in B$ there is $y\in[Y,X]$ with $|S(y,q;\kappa)|>\tfrac12 y^{1/2+\tau}$, then $|B|\le\eta|P|$. The threshold is independent of $X,Z,P,B,\kappa$.

## Control within one dyadic block

For each $q$, the capped function $\min(1,v/n)$ is continuous piecewise linear with derivative $1/n$ for $v<n$ and zero for $v>n$. Put

$$
D(v,q)=\sum_{\substack{1\le n\le\lfloor Z\rfloor\\n>v}}
\Lambda(n)\kappa(n)J_q(n)/n.
$$

A finite sum of the integrated piecewise linear formulas gives $S(y,q;\kappa)=S(A,q;\kappa)+\int_A^y D(v,q)\,dv$. At the finitely many breakpoints either value of the derivative gives the same integral.

For fixed $v\in[Y,X]$, let $\kappa_v(n)=\mathbf1_{n>v}\kappa(n)$. Then $vD(v,q)=S(v,q;\kappa_v)$ because $\min(1,v/n)=v/n$ on the surviving terms. The coefficients $\kappa_v$ are still bounded by one and have the same truncation for all $q$. By (1),

$$
\sum_{q\in P}|D(v,q)|^2\le C\frac{\log v}{v}|P|. \tag{2}
$$

Take $[A,W]\subseteq[Y,X]$ with $A\le W\le2A$. Choose any $w(q)\in[A,W]$ for each $q\in P$. By the squared triangle bound and Cauchy–Schwarz for the integral,

$$
|S(w(q),q;\kappa)|^2
\le2|S(A,q;\kappa)|^2+2A\int_A^W|D(v,q)|^2\,dv .
$$

All terms on the right now use a common endpoint and interval. Sum in $q$ and use (1) at $A$ and (2) under the integral. Since $\log v/v\le\log(2A)/A$ and the interval length is at most $A$, this gives

$$
\sum_{q\in P}|S(w(q),q;\kappa)|^2\le4CA\log(2A)|P|. \tag{3}
$$

## Count the bad primes on the whole interval

On one block let $B'$ be the primes with a bad point. Choose a bad $w(q)$ for $q\in B'$ and choose $A$ otherwise. For $q\in B'$ the square in (3) exceeds $A^{1+2\tau}/4$. Hence

$$
|B'|\le16C A^{-2\tau}\log(2A)|P|
\le(32C/\tau)A^{-\tau}|P|,
$$

using $A\ge2$ and $\log(2A)\le2\log A\le2A^\tau/\tau$. If $X<Y$ there are no bad points. Otherwise cover $[Y,X]$ by the blocks $[2^iY,\min(2^{i+1}Y,X)]$ with $i\ge0$ and $2^iY\le X$. Each prime in $B$ is counted in at least one block. The sum of the bounds is at most

$$
\frac{32C}{\tau(1-2^{-\tau})}Y^{-\tau}|P|.
$$

Since $\tau>0$, the coefficient is at most $\eta$ for $Y\ge Y_0$ with $Y_0$ sufficiently large. This proves the claim.

For the [two-prime sieve](prime-pair-selection.md), take the permitted bad proportion to be $\eta/[2(R+1)]$ for each of at most $R$ base characters, and sum their bad proportions. The primes discarded for their capped sums number at most $\eta|P|/2$. A separate zero-density bound handles zeros in the required rectangle. The remaining primes satisfy the hypotheses of `box_of_S`, which converts the capped-sum estimate into a bound on the corrected ramp sum. The construction uses this argument once for $q$ and again in a congruence class depending on $q$ for $d$.

## Lean references and review

- [`QH.S`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/PrimeSetTwoBounds.lean#L13) and [`MeanSq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/PrimeSetTwoBounds.lean#L26) define the sum and input.
- [`bs_S_sub_S`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BadShare.lean#L76), [`bs_mul_D_eq_S`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BadShare.lean#L83), and [`bs_sum_D_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BadShare.lean#L146) give the integral formula, the truncation and (2). [`bs_block`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BadShare.lean#L163) gives (3).
- [`bs_markov`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BadShare.lean#L207) counts one block, [`QH.bad_share`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BadShare.lean#L251) combines the blocks, and [`QH.stage`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/StagePow.lean#L41) applies the result. The application obtains (1) from [`meanSqK.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/meanSqK.lean).

English translation draft. The mean square is a hypothesis of this argument.
