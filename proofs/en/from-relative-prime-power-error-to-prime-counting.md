# From relative prime-power error to prime counting

[Chinese proof](../zh/%E7%9B%B8%E5%AF%B9%E8%AF%AF%E5%B7%AE%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%B4%A0%E6%95%B0%E5%B9%82%E4%BC%A0%E5%88%B0%E7%B4%A0%E6%95%B0%E8%AE%A1%E6%95%B0.md)

## Abel summation with an exceptional term

Let $X\ge16$, $0\le K\le1$, $|\theta|\le1$, $1/2\le\beta\le1$, and $D\ge0$. Let $0\le c(n)\le\Lambda(n)$ for all positive integers, and write $\Psi(t)=\sum_{n\le t}c(n)$ and $F(t)=K(t-\theta t^\beta/\beta)$. Assume $|\Psi(t)-F(t)|\le Dt$ for all $t\in[\sqrt X,X]$. With $\mathrm{Li}(Y)=\int_2^Y dt/\log t$, `abel_core` gives
$$
\left|\sum_{2\le n\le X}\frac{c(n)}{\log n}
-K\bigl(\mathrm{Li}(X)-\theta\mathrm{Li}(X^\beta)\bigr)\right|
\le 5DX/\log X+40\sqrt X.
$$

Set $s=\sqrt X$ and $M(t)=K(\mathrm{Li}(t)-\theta\mathrm{Li}(t^\beta))$. Abel summation gives
$$
\sum_{s<n\le X}\frac{c(n)}{\log n}
=\frac{\Psi(X)}{\log X}-\frac{\Psi(s)}{\log s}
+\int_s^X\frac{\Psi(t)}{t\log^2 t}\,dt.
$$
Since $M'(t)=F'(t)/\log t$, integration by parts gives the same expression for $M(X)-M(s)$ with $F$ in place of $\Psi$. The error at $X$ is at most $DX/\log X$, and the integral costs at most $4DX/(\log X)^2\le4DX/\log X$. At the smaller endpoint use $\sum_{n\le s}\Lambda(n)\le6s$ and $\log2\ge1/2$. The sum for $n\le s$ costs at most $12s$, $|M(s)|\le2\mathrm{Li}(s)\le4s$ since $s^\beta\ge2$, and the endpoint difference costs at most $9s$ by $|F(s)|\le3s$ and $\log s\ge1$. Together these give the bound. [The Abel calculation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTPiB.lean)

## A lower bound for the actual main term

Take modulus $M_0\ge8$ divisible by $8$ and $b$ coprime to $M_0$. Put $c(n)=\Lambda(n)\mathbf1_{n\equiv b\bmod M_0}$. Character orthogonality expresses $\Psi$ as the weighted average of twisted Chebyshev sums. Its main term has $K=1/\varphi(M_0)$, and $\theta=\xi(b)$ for the optional exceptional real character $\xi$ of zero $\beta$. Without such a character use $\theta=0,\beta=1$. Write $L=\log X$ and assume $L\ge16\log M_0$. The relative Chebyshev bound uses $\eta=1$ without exception and $\eta=\min(1,(1-\beta)\log M_0)$ with one. In this setting `etaOf_lower` supplies $\eta\ge c_1/M_0$ for an effective absolute $c_1>0$. The actual main term satisfies
$$
\mathrm{Li}(X)-\theta\mathrm{Li}(X^\beta)\ge\eta X/(2L).
$$
When $\theta\le0$, the left is at least $\mathrm{Li}(X)\ge(X-2)/L\ge X/(2L)$. When $\theta>0$, use $\eta\le(1-\beta)L$ and $1-e^{-\eta}\ge\eta/2$ for $0\le\eta\le1$ to get $X-X^\beta\ge\eta X/2$. Integrating over $[X^\beta,X]$ and using $\theta\le1$ gives the bound. [Lower bound on the main term](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTPiC.lean)

## Transfer the relative error

The analytic input `PsiRel` says that for each such $M_0$ and its optional exceptional pair there are absolute constants $A,c>0,C_0$ giving
$$
\sum_{\chi\bmod M_0}|\Psi_\chi(t)-A_\chi(t)|
\le At\eta\left(e^{-c\log t/\log M_0}+e^{-c\sqrt{\log t}}\right)
$$
when $t\ge2$ and $\log t\ge C_0\log M_0\log(\log M_0+2)$. Here $\Psi_\chi(t)=\sum_{n\le t}\Lambda(n)\chi(n)$ and $A_\chi(t)$ equals $t$ for the principal character, $-t^\beta/\beta$ for the exceptional one, and zero otherwise. The project glues two estimates according to the relative sizes of the modulus and the height. [Relative Chebyshev bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/DeuringHeilbronnM.lean) · [Gluing the two ranges](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTFinal.lean)

Assume $L\ge\max(16,2C_0)\log M_0\log(\log M_0+2)$, which puts all of $[\sqrt X,X]$ in range. Set $c'=\min(c/2,c^2/2)$ and $E(X)=e^{-c'L/\log M_0}+e^{-\sqrt{c'L}}$. Orthogonality bounds the progression error by $At\eta E(X)/\varphi(M_0)$, so the Abel estimate applies with $D=A\eta E(X)/\varphi(M_0)$. To count primes, drop prime powers with exponent $k\ge2$. Each contributes at most $1/k$, and there are at most $\sqrt X\log X/\log2$ such powers. The source allows an error $4\sqrt X L$. With the Abel estimate, this gives the main-term error $5A\eta E(X)X/(\varphi(M_0)L)$ plus a remainder at most $44\sqrt X L$.

By the lower bound on the actual main term, the first error is at most $10AE(X)$ times the main term. For the remainder, divide by both the main-term lower bound and $E(X)$. Use $\eta\ge c_1/M_0$, $\varphi(M_0)\le M_0$, $M_0^2\le X^{1/8}$ and $E(X)\ge e^{-\sqrt{c'L}}$. The ratio is bounded by a constant times $L^2 e^{-3L/8+\sqrt{c'L}}$, which is uniformly bounded. This completes the relative prime-count estimate `PNTAPRelW`. [Dropping prime powers](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTPiA.lean) · [Relative prime count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PrimeCountOfPsi.lean) · [Application to quadratic twists](one-exceptional-quadratic-twist.md)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
