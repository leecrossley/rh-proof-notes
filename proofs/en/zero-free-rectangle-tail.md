# From the zero-free rectangle to the tail of a truncated prime sum

[Chinese proof](../zh/%E9%9B%B6%E7%82%B9%E7%9F%A9%E5%BD%A2%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E6%88%AA%E6%96%AD%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E5%B0%BE%E9%A1%B9.md) · [Reading and review status](../../STATUS.md)

Let $\Lambda$ be the von Mangoldt function, $\chi$ a Dirichlet character modulo $N\ge1$, and $y>0$. Put $A_\chi(y)=\sum_{1\le n\le y}\Lambda(n)\chi(n)(y/n-1)$ and $g_\chi(y)=A_\chi(y)+y(L'/L)(1,\chi)$. For $q\in\mathbb N$ write $J_q(n)$ for the Jacobi symbol used in the source. For odd prime $q$ it is the Legendre symbol. Define the capped sum

$$
S(Z,y,q,\kappa)=\sum_{1\le n\le Z}\Lambda(n)\kappa(n)J_q(n)\min(1,y/n).
$$

**Claim.** There is an absolute $C>0$ such that for every $0<\varepsilon\le1/4$, $\tau>0$ and $K\ge1$, some threshold $Y_0$ has the following property. For each real $Y\ge Y_0$, take $X=Y^K$, $Z=X^{400}$, and a real $Q$ with $Y^{\varepsilon/6}\le\log Q\le Y^{\varepsilon/4}$. Let $\chi$ be nonprincipal of modulus $N\le Q$ with $L(s,\chi)\ne0$ throughout $\operatorname{Re}s>1-1/400$, $|\operatorname{Im}s|\le Q$. Suppose $\chi(n)=\kappa(n)J_q(n)$ for all natural numbers $n$ and $|S(Z,y,q,\kappa)|\le\tfrac12 y^{1/2+\tau}$ for every $y\in[Y,X]$. Then $|(L'/L)(1,\chi)|\le C\log Y$ and $|g_\chi(y)|\le y^{1/2+\tau}$ for all $y$ in the interval.

This is the result `QH.box_of_S` used in the [auxiliary-prime sieve](prime-pair-selection.md).

## Estimate the tail by two descriptions of one difference

Set $D_\chi=-(L'/L)(1,\chi)$, $P(z)=\sum_{1\le n\le z}\Lambda(n)\chi(n)/n$, and $R(z)=D_\chi-P(z)$. The last quantity is `tailL`.

The contour input `tail_contour` states the following. For each $0<\delta\le1/800$ there is $B\ge0$ such that if $Q\ge2$, $1\le N\le Q$, $\chi$ is nonprincipal and nonvanishing in the specified rectangle, $z\ge1$ and $0<\eta\le1$, then for $h=z\eta$,

$$
|A_\chi(z+h)-A_\chi(z)-hD_\chi|
\le B\log Q\left[(\log Q)\eta z^{1-1/400+\delta}+z^2/Q\right]. \tag{1}
$$

Nonvanishing allows the Perron integral, truncated at height $Q/2$, to move left to $\operatorname{Re}s=1-1/400+\delta$. On this line the difference kernel contains $(1+\eta)^s-1$, which accounts for the factor $\eta$. The horizontal edges and the tails on the starting line contribute the term with $z^2/Q$. This quantitative bound is an input here. See the Chinese proof of the [contour shift for the smooth difference](../zh/%E5%B9%B3%E6%BB%91%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E5%B7%AE%E5%88%86%E5%9C%A8%E7%A7%BB%E7%BA%BF%E6%97%B6%E6%80%8E%E6%A0%B7%E4%BF%9D%E7%95%99%E6%AD%A5%E9%95%BF.md).

Directly in the finite sums, the terms at $n\le z$ contribute exactly $hP(z)$ to the difference, since their weights increase by $h/n$. At $z<n\le z+h$, the new ramp is bounded by $h/z$, the von Mangoldt coefficient is at most $\log(z+h)$, and there are at most $h+1$ integers. Thus

$$
|A_\chi(z+h)-A_\chi(z)-hP(z)|\le h(h+1)\log(z+h)/z . \tag{2}
$$

Subtracting the two expressions and using (1) and (2), then dividing by $h>0$, gives a bound on $R(z)$.

## The cutoff at the power $400$

For the tail estimate allow $0<\varepsilon\le1$ and $K\ge1$. Take $x=Y^K$, $z=x^{400}$, $\eta=x^{-2}$, $\delta=\varepsilon/(1600K)$ and hence $h=x^{398}$. For $Y\ge3$ we have $Q\ge\exp(Y^{\varepsilon/6})\ge2$, and $\eta,\delta$ are in the contour range. Multiplying the preceding bound for $R$ by $x$ gives

$$
x|R(z)|\le B(\log Q)^2Y^{\varepsilon/4}
 + B(\log Q)x^{403}/Q
 +(x^{-1}+x^{-399})\log(z+h).
$$

In the first term we used $xz^{-1/400+\delta}=x^{400\delta}=Y^{\varepsilon/4}$. By $\log Q\le Y^{\varepsilon/4}$ it is at most $BY^{3\varepsilon/4}$, which is eventually at most $Y^\varepsilon/3$. The second term is at most $BY^{404K}\exp(-Y^{\varepsilon/6})$ since $\log Q\le x$. Substituting $Y^{\varepsilon/6}$ as the variable shows it tends to zero, so it is eventually at most $Y^\varepsilon/3$. In the third term $z+h\le2x^{400}\le x^{401}$ and $x^{-399}\le x^{-1}$, so it is bounded by $802(\log x)/x\le802$, also eventually at most $Y^\varepsilon/3$. The resulting threshold can depend on $\varepsilon,K$ and the corresponding contour constant. It is uniform in $Q,N,\chi$. We obtain `tailK`:

$$
x\,|R(x^{400})|\le Y^\varepsilon. \tag{3}
$$

## Return to the corrected ramp

For the log derivative, first apply (3) with $K=1$ to get $|R(Y^{400})|\le Y^{\varepsilon-1}\le1$. Partial summation of the elementary Chebyshev bound $\sum_{n\le z}\Lambda(n)=O(z)$, or the [factorial calculation](ramp-variation.md), gives an absolute $C_0$ with $\sum_{n\le z}\Lambda(n)/n\le C_0\log z$ for $z\ge2$. Since $|\chi(n)|\le1$, we have $|D_\chi|\le400C_0\log Y+1\le(400C_0+1)\log Y$ for $Y\ge3$. This constant is independent of $\varepsilon,\tau,K$.

Now use the specified $K$ and $Z=X^{400}$. For each $y\in[Y,X]$, the identity $(y/n-1)_++\min(1,y/n)=y/n$ gives, after summing through $Z$,

$$
A_\chi(y)+S(Z,y,q,\kappa)=yP(Z),
\qquad g_\chi(y)=-S(Z,y,q,\kappa)-yR(Z).
$$

Here $Z\ge y$ and the hypothesis $\chi=\kappa J_q$ identifies the coefficients. The capped sum has modulus at most $\tfrac12 y^{1/2+\tau}$ by hypothesis. Equation (3) bounds $|yR(Z)|$ by $Y^\varepsilon$. For $Y\ge16$ and $\varepsilon\le1/4$, $Y^\varepsilon\le Y^{1/4}\le\tfrac12 Y^{1/2}\le\tfrac12 y^{1/2+\tau}$. Adding gives the claim.

## Lean references and review

- The capped sum and the rectangle are in [`PrimeSetTwoBounds.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/PrimeSetTwoBounds.lean). The ramp error, finite sum, and tail are in [`SecondEstimateOfIntervalHypothesis.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/SecondEstimateOfIntervalHypothesis.lean).
- Compare [`tail_contour`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailContour.lean#L14), [`tail_diff_schi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailDiff.lean#L67), [`tailK_num`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/TailKExp.lean#L23), and [`QH.tailK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/TailKExp.lean#L92).
- [`tail_mertens`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailMertens.lean#L61) and [`kappaC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/kappaC.lean#L9) give the log-derivative control. The finite splitting is [`finite_splitting_of_group`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/HookFormulaTorsion/WeightedVonMangoldtSumIdentity.lean#L52), and [`QH.box_of_S`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BoxOfS.lean#L28) assembles the estimates.

English translation draft. The same contour input is used in the separate derivation of the [exact constant $4$](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%80%E5%A4%84%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0%E7%9A%84%E7%95%8C%E5%8E%8B%E5%88%B0%E5%9B%9B%E5%80%8D%E5%AF%B9%E6%95%B0.md), where the cutoff is $(\log Q)^{1000}$ instead of $X^{400}$.
