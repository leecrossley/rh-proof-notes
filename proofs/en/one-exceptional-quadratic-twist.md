# Why at most one quadratic twist can inherit the exceptional zero

[Chinese proof](../zh/%E9%9B%B6%E7%82%B9%E4%BE%8B%E5%A4%96%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%80%E5%A4%9A%E5%BD%B1%E5%93%8D%E4%B8%80%E4%B8%AA%E4%BA%8C%E6%AC%A1%E6%89%AD%E6%9B%B2.md) · [Reading and review status](../../STATUS.md)

## Statement

Fix $\varepsilon,A,D>0$. For all $Y$ above a threshold depending only on these constants, take integers $m>0,a$ with $8\mid m$ and $\gcd(a,m)=1$, and real $U$ satisfying

$$
\tfrac14(\log Y)^2\log m\le\log U,\qquad
Y^{\varepsilon/6}\le\log U\le Y^{\varepsilon/5}(\log Y)^2.
$$

Let $P$ be the primes $q$ with $\sqrt U<q\le U$ and $q\equiv a\pmod m$. There is a natural number $s_*$ such that every odd squarefree $1<s\le Y^A$ coprime to $m$ with $s\ne s_*$ satisfies

$$
\left|\sum_{q\in P}(q/s)\right|\le Y^{-D}|P|.
$$

The symbol is the Jacobi symbol. With the real operations used in Lean, if $U\le0$ the candidate set is empty. We take $U>0$ below. This is the cancellation input `twistK` for the [mean square](exceptional-quadratic-mean-square.md).

## The three analytic inputs

Write $\operatorname{Li}(X)=\int_2^X dt/\log t$ and $\pi(X;M,b)=\#\{p\le X:p\equiv b\bmod M\}$. The relative prime number theorem `PNTAPRelW` supplies $c_3>0,C_0,A_0$, all absolute. For each positive $8\mid M$, choose an exceptional pair $(\xi,\beta)$ if one exists, with nonprincipal quadratic $\xi$ modulo $M$, $L(\beta,\xi)=0$, and $1-1/(8\log M)<\beta<1$. Put

$$
A_M(b,X)=\frac{\operatorname{Li}(X)-\operatorname{Re}\xi(b)\operatorname{Li}(X^\beta)}{\varphi(M)},
$$

omitting the second term of the numerator if there is no pair. For $X\ge2$, $\gcd(b,M)=1$ and $\log X\ge C_0\log M\log(\log M+2)$, the error in replacing $\pi(X;M,b)$ by $A_M(b,X)$ is bounded in modulus by
$|A_0|\big(\exp(-c_3\log X/\log M)+\exp(-\sqrt{c_3\log X})\big)A_M(b,X)$.

See the [relative prime number theorem](relative-prime-number-theorem-two-ranges.md) for the proof of this input. The effective bound `ExcBound` gives $1-\beta\ge c/M$ for such real zeros with absolute $0<c\le1$. The comparison `page_across` gives an absolute $c_0>0$ such that for two nonprincipal quadratic characters of moduli $M_1,M_2\le Z$, $Z\ge3$, if both have a real zero in $(1-c_0/\log Z,1)$, then they agree on the units modulo $M_1M_2$. This follows by inducing to modulus $M_1M_2\le Z^2$ and using uniqueness there, with $c_0$ one third of the constant from the same-modulus statement. The real zeros survive the change of modulus.

## Which twists can retain an exceptional main term?

Fix $s$ as in the statement and put $M=ms$. The reduced classes $b$ modulo $M$ with $b\equiv a\bmod m$ form a coset $B$ of $H=\{u\bmod M:u\equiv1\bmod m,\ \gcd(u,M)=1\}$, with $|B|=\varphi(s)$. The character $j_s(b)=(b/s)$ is nontrivial on $H$. Indeed for a prime divisor $p$ of $s$, use the Chinese remainder theorem to choose a unit non-square modulo $p$ and congruent to one modulo $m$ and $s/p$. That unit is in $H$ and has $j_s=-1$. Multiplying by it permutes $B$, so $\sum_{b\in B}j_s(b)=0$.

Consequently the $\operatorname{Li}(U)$ main term vanishes in $\sum_{b\in B}j_s(b)A_M(b,U)$. If an exceptional pair exists, its term contains $\sum_{b\in B}j_s(b)\xi(b)$. The same coset cancellation shows that this too vanishes unless $\xi|_H=j_s|_H$. In that last case its absolute contribution is at most $|B|\operatorname{Li}(U^\beta)/\varphi(M)$.

Set $Z=mY^A$. Call $s$ exceptional if the chosen pair has $\xi|_H=j_s|_H$ and $1-\beta<c_0/\log Z$. For two exceptional indices $s_1,s_2$, both moduli are at most $Z$. By `page_across`, their Jacobi symbols agree on integers congruent to one modulo $m$ and coprime to $s_1s_2$. If $s_1\ne s_2$, choose a prime dividing exactly one of the two squarefree indices, and use the Chinese remainder theorem to choose a non-square unit there and one at all other prime factors and modulo $m$. The two symbols are opposite, a contradiction. Thus there is at most one exceptional index. Use it for $s_*$ if it exists and use zero otherwise.

## The remaining relative error is small on the required interval

Let $L=\log Y$, $u=\log U$. For large $Y$ the scale conditions yield $u\ge L^2(\log m+AL)/8$, hence $u/\log M\ge u/\log Z\ge L^2/8$. Also $\log m\le4Y^{\varepsilon/5}$, so $\log(\log M+2)=O(L)$. Thus the relative theorem applies at $U$ and its relative error coefficient $\delta$ is at most $Y^{-D}/16$, uniformly in $s$.

For nonexceptional $s$ with a surviving term, $1-\beta\ge c_0/\log Z$. Write $r=\operatorname{Li}(U^\beta)/\operatorname{Li}(U)$. Using $\operatorname{Li}(U^\beta)\le U^\beta/\log2$ and $\operatorname{Li}(U)\ge(U-2)/\log U$ gives $r\le4u\exp(-c_0u/\log Z)\le Y^{-D}/32$ for large $Y$, since $\log u=O(L)$. Here $U^\beta\ge2$ for large $Y$ because $\beta>1/2$. Each $A_M(b,U)\ge(1-r)\operatorname{Li}(U)/\varphi(M)$. Hence the possibly surviving twisted main term is at most $2r\sum_{b\in B}A_M(b,U)$ in modulus. When it cancels take $r=0$ in this comparison.

The primes $q\equiv a\bmod m$ that are nonunits modulo $ms$ divide $s$, and their Jacobi symbols vanish. Adding the class errors gives a bound $(2r+\delta)\sum_{b\in B}A_M(b,U)$ for the twisted sum up to $U$. The main terms are positive, and the relative error is at most $1/2$. Thus $\sum_{b\in B}A_M(b,U)\le2\pi(U;m,a)$ and the twisted sum is at most $(Y^{-D}/4)\pi(U;m,a)$ in modulus.

To discard $q\le\sqrt U$, first get a lower bound on the full count. In modulus $m$, the effective gap $1-\beta\ge c/m$ implies $U-U^\beta\ge U(1-e^{-c/m})\ge cU/(2m)$ for $u\ge1$. Integrating over $[U^\beta,U]$ gives $\operatorname{Li}(U)-\operatorname{Li}(U^\beta)\ge cU/(2m\log U)$, valid at large $Y$. After dividing by $\varphi(m)\le m$, the class main term is at least $cU/(2m^2\log U)$. The same lower bound follows directly from $\operatorname{Li}(U)$ when there is no exceptional term. Since $\log m/u\le4/L^2$ and $\log u/u\to0$, the relative theorem gives $\pi(U;m,a)\ge2U^{9/10}$ at large $Y$. Removing at most $\sqrt U$ primes gives $|P|\ge U^{9/10}$ and $\sqrt U\le U^{-2/5}|P|\le(Y^{-D}/4)|P|$. Use $\pi(U;m,a)\le |P|+\sqrt U$ in the bound for the full sum and add the discarded contribution. This proves the claim.

## Lean references and review

- [`twistK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/twistK.lean#L148) combines the relative errors, the comparison of zeros and the half-power cutoff. [`MSqTwistB.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqTwistB.lean) controls the twisted main term by coset summation.
- [`page_across`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqPage.lean#L37) compares the induced characters, and [`jacobi_separate`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqOrth.lean#L133) distinguishes different squarefree indices.
- [`count_a`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqCount.lean) gives the count used after discarding small primes. The relative theorem is supplied via [`MeanSquareHypWIff.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MeanSquareHypWIff.lean) and [`PNTFinal.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/PNTFinal.lean).

English translation draft. The three analytic inputs carry the deeper prime-distribution argument.
