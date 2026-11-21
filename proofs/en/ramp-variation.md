# Varying the argument and the weight of a ramp prime sum

[Chinese proof](../zh/%E6%96%9C%E5%9D%A1%E7%B4%A0%E6%95%B0%E5%92%8C%E4%B8%BA%E4%BD%95%E8%83%BD%E7%A7%BB%E5%8A%A8%E5%B0%BA%E5%BA%A6%E5%92%8C%E6%9D%83%E9%87%8D.md) · [Reading and review status](../../STATUS.md)

The [translation-average estimate](translation-averaging.md) first replaces many different weights with a common weight. It then moves all the arguments of the prime sums to a common value. The two operations use the following separate estimates.

Let $H$ be a finite abelian group, $A=(\mathbb Z/2\mathbb Z)^2\times H$, and let $\widehat A$ denote its complex characters. For each prime $p$ choose any subgroup $I_p\le A$ and element $F_p\in A$. Define $P_\psi(n)$ by the product of inertia-coset averages in the [Fourier identity](finite-fourier-balance.md#data-and-statement). Fix any function $\ell:\widehat A\to\mathbb C$. Write $c_\psi(n)=\Lambda(n)P_\psi(n)$ and $x_+=\max(x,0)$. For $y>0$ put

$$
\begin{aligned}
U_\psi(y)&=\sum_{n\ge1}c_\psi(n)(y/n-1)_+,\\
G_\psi(y)&=U_\psi(y)+y\ell(\psi) &&(\psi\ne1),\\
G_1(y)&=U_1(y)-y\log y+(1+\gamma_E)y.
\end{aligned}
$$

The sums have no nonzero terms beyond $\lfloor y\rfloor$. The claims hold for every choice of these data.

**Weight estimate.** For every $\psi$ and all $a,w,w'>0$,

$$
\big|wG_\psi(a/w)-w'G_\psi(a/w')\big|
\le 3a\,\frac{|w-w'|}{\min(w,w')}. \tag{1}
$$

**Argument estimate.** There is an absolute constant $C_d\ge0$ such that for all $y,z\ge1$,

$$
\begin{aligned}
|G_\psi(y)-G_\psi(z)|&\le|y-z|\big(\log\max(y,z)+C_d+|\ell(\psi)|\big)
&&(\psi\ne1),\\
|G_1(y)-G_1(z)|&\le C_d|y-z|.
\end{aligned} \tag{2}
$$

## Two bounds for sums of von Mangoldt coefficients

Write $\Psi(Y)=\sum_{1\le n\le Y}\Lambda(n)$. We use $\Psi(Y)\le3Y$ for $Y\ge0$. In Lean this follows from the Chebyshev estimate $\Psi(Y)\le(\log4)Y+2\sqrt Y\log Y$ for $Y\ge1$. With $u=\sqrt Y$, the inequality $\log u\le u/e$ gives $2\sqrt Y\log Y\le4Y/e$ and $\log4+4/e<3$.

Here is also an elementary derivation of the needed bound. For an integer $m\ge1$, the $p$-adic valuation of $\binom{2m}{m}$ is

$$
\sum_{j\ge1}\left(\left\lfloor\frac{2m}{p^j}\right\rfloor
-2\left\lfloor\frac m{p^j}\right\rfloor\right).
$$

Each summand is nonnegative and equals one when $m<p^j\le2m$. Therefore $\Psi(2m)-\Psi(m)\le\log\binom{2m}{m}\le2m\log2$, since all the binomial coefficients in row $2m$ sum to $2^{2m}$. Summing for $m=1,2,4,\ldots,2^{k-1}$ gives $\Psi(2^k)\le(2^{k+1}-2)\log2$. For $Y\ge1$ the least power of two at least $Y$ is at most $2Y$, so $\Psi(Y)\le4Y\log2\le3Y$. For $0\le Y<1$ the sum vanishes.

Now put $A(k)=\sum_{1\le n\le k}\Lambda(n)/n$ for integer $k\ge1$. From prime factorization, $\log n=\sum_{d\mid n}\Lambda(d)$. Sum over $n\le k$ and interchange the finite sums, obtaining

$$
\log(k!)=\sum_{1\le d\le k}\Lambda(d)\lfloor k/d\rfloor.
$$

Hence $0\le kA(k)-\log(k!)\le\Psi(k)$. Monotonicity of the logarithm gives $\int_1^k\log u\,du\le\log(k!)\le k\log k$. Division by $k$ therefore gives

$$
\log k-1\le A(k)\le\log k+\log4+4. \tag{3}
$$

For the upper bound we have used the weaker constant $\log4+4$ in place of $3$.

## Proof of the argument estimate

Every group-character value has modulus one, so $|P_\psi(n)|\le1$ by the definition as a product of averages. Thus $|c_\psi(n)|\le\Lambda(n)$. The positive-part function is $1$-Lipschitz, giving $|(y/n-1)_+-(z/n-1)_+|\le|y-z|/n$. For $\psi\ne1$, use the common cutoff $k=\lfloor\max(y,z)\rfloor$. Summing the bound and adding the linear correction gives $|G_\psi(y)-G_\psi(z)|\le|y-z|\big(A(k)+|\ell(\psi)|\big)$. Equation (3) yields the first part of (2).

For the trivial character, on any closed interval $[k,k+1]$ with $k\ge1$ one can sum just through $n=k$. The next term is zero even at the right endpoint. On this interval,

$$
G_1(y)=yA(k)-\sum_{n\le k}\Lambda(n)-y\log y+(1+\gamma_E)y.
$$

Its derivative in the interior is $A(k)-\log y+\gamma_E$. By (3), $k\le y\le2k$, and $1/2<\gamma_E<2/3$, its absolute value is at most $K_0=\log4+7$. Splitting any interval between $y,z\ge1$ at its integers and summing the bounds from the mean value theorem gives $|G_1(y)-G_1(z)|\le K_0|y-z|$. Taking $C_d\ge\max(\log4+4,K_0)$ works for both types of character. Lean also uses a version extending to $y\ge1/2$. On $[1/2,1]$ the ramp part vanishes, so the extra estimate follows by differentiating the main term directly.

## Proof of the weight estimate

By symmetry suppose $w\le w'$. From $w(a/(wn)-1)_+=(a/n-w)_+$, the difference of the weighted ramp sums is

$$
B=\sum_{n\le a/w}c_\psi(n)\big((a/n-w)_+-(a/n-w')_+\big).
$$

Each bracket is between $0$ and $w'-w$. The coefficient bound and Chebyshev estimate give $|B|\le\Psi(a/w)(w'-w)\le3(a/w)(w'-w)$. For a nontrivial character the correction $a\ell(\psi)$ is the same at both weights and cancels. For the trivial character each $c_1(n)=\Lambda(n)$ is nonnegative, so $B\ge0$. The linear main terms cancel and the full difference is $B-a\log(w'/w)$. Since $0\le a\log(w'/w)\le(a/w)(w'-w)$, the absolute difference is at most $3(a/w)(w'-w)$. This proves (1).

## Lean references and review

- The factorial identity and the two estimates in (3) are [`sum_log_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L37), [`mertens_upper`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L55) and [`mertens_lower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L86). The trivial-character derivative and gluing are [`deriv_bound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L139), [`lip_piece`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L165) and [`lip_upto`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L185), leading to [`Formalism.zetaPrimeSumErrorLipschitz`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ZetaNonvanishing/GzLipschitz.lean#L220).
- See [`norm_coef_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L764) and [`deriv_char`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L778) for nontrivial characters in (2). The weight cases are [`lip_char`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L852) and [`lip_triv_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L901). The final statements are [`lipschitz_weight_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L957) and [`derivative_integral_all`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/LipschitzWeightAndMinimum.lean#L966).

English translation draft. The binomial coefficient argument is the elementary alternative included in the Chinese exposition.
