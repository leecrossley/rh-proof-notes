# The coefficient four in the log-derivative estimate

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%80%E5%A4%84%E5%AF%B9%E6%95%B0%E5%AF%BC%E6%95%B0%E7%9A%84%E7%95%8C%E5%8E%8B%E5%88%B0%E5%9B%9B%E5%80%8D%E5%AF%B9%E6%95%B0.md) · [Reading and review status](../../STATUS.md)

Let $D_\chi(s)=-L'(s,\chi)/L(s,\chi)$ for a Dirichlet character modulo $N\ge1$. The condition `GoodC(Q,χ)` means $Q>0$, $\chi$ is nonprincipal, $N\le Q$, and $L(s,\chi)\ne0$ on $\operatorname{Re}s>1-1/400$, $|\operatorname{Im}s|\le Q$.

**Claim.** For $0<\varepsilon<1/52$ and $A>0$, there is $Y_0$ such that for every real $Y\ge Y_0$ and every $\mathrm{GoodC}(Q,\chi)$ with

$$
Y^{\varepsilon/6}\le\log Q\le AY^{\varepsilon/5}(\log Y)^2,
$$

we have $|L'(1,\chi)/L(1,\chi)|\le4\log Y$.

## A short difference approximates the logarithmic derivative

Put $S_\chi(z)=\sum_{n\le z}\Lambda(n)\chi(n)(z/n-1)$ and $P_\chi(z)=\sum_{n\le z}\Lambda(n)\chi(n)/n$. For $z\ge1$ and $0<h\le z$,

$$
S_\chi(z+h)-S_\chi(z)-hP_\chi(z)=
\sum_{z<n\le z+h}\Lambda(n)\chi(n)((z+h)/n-1).
$$

There are at most $h+1$ terms of modulus at most $(h/z)\log(z+h)$, using $|\chi(n)|\le1$. Write $h=z\eta$. The [contour estimate for the same difference](contour-shift-step-size.md) gives for each $0<\delta\le1/800$ a $K\ge0$ depending only on $\delta$, such that if $Q\ge2$, $\mathrm{GoodC}(Q,\chi)$, $z\ge1$ and $0<\eta\le1$, then

$$
|S_\chi(z+h)-S_\chi(z)-hD_\chi(1)|
\le K\log Q\big((\log Q)\eta z^{1-1/400+\delta}+z^2/Q\big).
$$

Subtract and divide by $h>0$ to get

$$
|D_\chi(1)-P_\chi(z)|\le K(\log Q)^2z^{-1/400+\delta}
+K\frac{z\log Q}{\eta Q}+(\eta+1/z)\log(z+z\eta). \tag{1}
$$

Set $\delta=1/4000$, $\ell=\log Q$, $x=\ell^{5/2}$, $z=x^{400}=\ell^{1000}$, and $\eta=x^{-2}=\ell^{-5}$. For sufficiently large $\ell$ we have $\ell\ge81$ and $\ell^{1006}\le e^\ell=Q$. The first two terms of (1) are at most $K\ell^{-1/4}\le K$ and $K\ell^{1006}/Q\le K$. The last is at most $2x^{-2}\log(2x^{400})\le 2x^{-2}(1+400x)\le802$. Thus $|D_\chi(1)-P_\chi(z)|\le2K+802$, uniformly over these characters.

## A factorial bound with leading coefficient one

For every $z\ge1$,

$$
|P_\chi(z)|\le\sum_{n\le z}\frac{\Lambda(n)}n\le\log z+2. \tag{2}
$$

To show the last inequality put $m=\lfloor z\rfloor$ and $\Psi(m)=\sum_{n\le m}\Lambda(n)$. The divisor identity for $\log n$, summed to $m$, gives $\sum_{n\le m}\Lambda(n)\lfloor m/n\rfloor=\log(m!)$. It follows that $m\sum_{n\le m}\Lambda(n)/n\le\log(m!)+\Psi(m)$. Monotonicity gives $\log(m!)\le m\log m-m+1+\log m$. It remains to show $\Psi(m)+1+\log m\le3m$.

For $m\ge25$, use the Chebyshev bound $\Psi(m)\le m\log4+2\sqrt m\log m$. From $\log u\le\log4+u/4-1$ with $u=\sqrt m$, we get $\log m\le0.78+\sqrt m/2$. Thus $\Psi(m)+1+\log m\le2.39m+2.06\sqrt m+1.78\le3m$. For $3\le m\le24$, use $\Psi(m)\le\log(m!)$ and $\log m\le1.78+m/16$. The function $(m+2)(1.78+m/16)-4m+2$ is convex and nonpositive at $3,24$. It bounds the difference $\Psi(m)+1+\log m-3m$ above and is nonpositive throughout the interval. For $m=1,2$ use $\Psi(1)=0$, $\Psi(2)=\log2$. This proves the required bound. Now divide by $m$ and use $\log m\le\log z$ to obtain (2).

With $z=(\log Q)^{1000}$, (1) and (2) imply $|D_\chi(1)|\le1000\log\log Q+C$ for $C=2K+804$ at sufficiently large $Q$.

## Absorb the remaining terms

The lower bound on $\log Q$ ensures the preceding estimates apply for all sufficiently large $Y$. The upper bound gives

$$
1000\log\log Q+C\le
200\varepsilon\log Y+2000\log\log Y+1000\log A+C.
$$

Since $200\varepsilon<50/13$, the coefficient falls short of four by more than $2/13$. The other terms divided by $\log Y$ tend to zero. Hence the right side is at most $4\log Y$ beyond a threshold depending only on $\varepsilon,A$.

For the [two-prime sieve](prime-pair-selection.md), take $Q=8M\exp(Y^{\varepsilon/5})\exp(jY^{\varepsilon/5}(\log Y)^2)$ with $j=0$ or $1$. When $\log Y\ge1+\log(8M)$, this gives $Y^{\varepsilon/6}\le\log Q\le3Y^{\varepsilon/5}(\log Y)^2$. Apply the claim with $A=3$, and then use $4\log Y\le4\log y$ for window points $y\ge Y$.

## Lean references and review

- [`kappa4_num`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/Kappa4Loglog.lean#L9), [`kappa4_loglog`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/Kappa4Loglog.lean#L44) and [`QH.kappa4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/Kappa4Loglog.lean#L126) correspond to the substitution, the log-log estimate and the coefficient four. Lean writes $s^4=\log Q$ and $x=s^{10}$.
- The two difference bounds are [`tail_diff_schi`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailDiff.lean#L67) and [`tail_contour`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/TailContour.lean#L14). The estimate (2) uses [`Deduction.mertens_upper`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/DedekindLFunctions/LandauTheorems/mertensUpper.lean#L103) and its integer version.
- [`GoodC`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/PrimeSetTwoBounds.lean#L32) states the zero-free input. The application is [`pairEx.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/pairEx.lean#L112).

English translation draft. The rectangle hypothesis is supplied by the sieve, and the contour proof is treated as a separate input to this estimate.
