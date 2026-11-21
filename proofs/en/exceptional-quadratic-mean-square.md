# The contribution of an exceptional quadratic character to the mean square

[Chinese proof](../zh/%E5%B9%B3%E6%96%B9%E5%B9%B3%E5%9D%87%E4%B8%AD%E7%9A%84%E4%BE%8B%E5%A4%96%E7%89%B9%E5%BE%81%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%AA%E8%B4%A1%E7%8C%AE%E5%B0%91%E6%95%B0%E7%B4%A0%E6%95%B0%E5%AF%B9.md) · [Reading and review status](../../STATUS.md)

## A bound with one exceptional squarefree index

Fix integers $m\ge1$ with $8\mid m$ and $a$ with $\gcd(a,m)=1$. Take $Z,B\in\mathbb R$, $y,\eta\ge0$, and a sequence $|\kappa(n)|\le1$. Put $N=\max(0,\lfloor Z\rfloor)$. Let $P$ be a finite set of primes $q\equiv a\pmod m$ with $q>N^2$. For $n\ge1$ set $c(n)=\Lambda(n)\min(1,y/n)$ and define

$$
S(q)=\sum_{1\le n\le N}c(n)\kappa(n)(n/q),\qquad
b_p=\sum_{\substack{k\ge1\\p^k\le N}}c(p^k),\qquad
L=\sum_{1\le n\le N}c(n).
$$

Let $R$ be the sum of $c(p^k)$ for the prime powers $p^k\le N$ with $k$ even or $p\mid m$. Assume $b_p\le B$ for every prime and that for one given natural $s_*$ all odd squarefree $1<s\le N^2$ coprime to $m$ with $s\ne s_*$ satisfy

$$
\left|\sum_{q\in P}(q/s)\right|\le\eta|P|.
$$

The symbols in these formulas are Jacobi symbols. Then

$$
\sum_{q\in P}|S(q)|^2\le
|P|\left(\sum_{p\le N}b_p^2+R^2+2B^2+2BR+\eta L^2\right), \tag{1}
$$

with $p$ restricted to primes. This is `QH.meanSq_abs`.

## Only odd exponents outside the modulus are relevant

Expand the square, interchange the sums, and use the reality of $(n/q)$ and $|\kappa(n)\overline{\kappa(n')}|\le1$. The left side of (1) is at most

$$
\sum_{1\le n,n'\le N}c(n)c(n')\left|\sum_{q\in P}(nn'/q)\right|.
$$

For the pair $(n,n')$ let $s=\prod_{p\nmid m,\ v_p(nn')\text{ odd}}p$. Since $q>N^2$, no candidate divides $nn'$, and square factors drop out of the symbol. For $p\mid m$, the symbol $(p/q)$ is fixed by the congruence class of $q$ modulo $m$, by quadratic reciprocity and the supplement at $2$. For $p\nmid m$, $p$ is odd, and reciprocity changes $(p/q)$ to $(q/p)$ times a fixed sign, since $q\bmod4$ is fixed. Multiplying gives $(nn'/q)=\sigma(q/s)$ with one sign $\sigma$ for all $q\in P$.

For $s>1$ with $s\ne s_*$ the sum has modulus at most $\eta|P|$, contributing at most $\eta|P|L^2$ in all. For the remaining pairs use the bound $|P|$. The source labels them by $s=1$ and $s=\max(s_*,2)$. The latter class is empty if $\max(s_*,2)=2$ because $s$ is odd.

## Count the pairs with a fixed exceptional index

Only $n=p^k,n'=r^j$ contribute since $\Lambda$ vanishes otherwise. Call a prime power special when its exponent is even or its base divides $m$. The sum of the special weights is $R$.

For $s=1$, pairs with the same prime base have total weight at most $\sum_p b_p^2$. A pair with different bases must consist of two special powers, so those pairs have total weight at most $R^2$. For a fixed $s=r>1$ that is prime, same-base pairs have base $r$ and total at most $b_r^2$. Different-base pairs have one base $r$ and the other power special, so both orders contribute at most $2b_rR$. If $s>1$ is composite, it must be a product of two distinct primes $p,r$ and those must be the two bases. The total is at most $2b_pb_r$. The weight of the possible exceptional class is therefore at most $2B^2+2BR$. Multiplying by $|P|$ and including the other classes proves (1).

## Application at the sieve scales

There is an absolute $C>0$ such that for each $0<\varepsilon\le1$ and $K\ge1$, the following holds for all $Y$ above a threshold depending on them. Use the modulus and residue hypotheses above, and assume

$$
(\log Y)^2\log m/4\le\log U,\qquad
Y^{\varepsilon/6}\le\log U\le Y^{\varepsilon/5}(\log Y)^2.
$$

Every prime divisor of $m$ is to be at most $Y^{\varepsilon/5}$ or greater than $Y^{400K}$. Let $Z=Y^{400K}$ and $P=\{q:\sqrt U<q\le U,\ q\text{ prime},\ q\equiv a\pmod m\}$. For every $Y\le y\le Y^K$ and every coefficient sequence bounded by one, the conclusion is $\sum_{q\in P}|S(q)|^2\le C y\log y\,|P|$. When $U\le0$ the candidate set is empty.

The analytic input `twistK` gives, for fixed $\varepsilon,A,D>0$ and all sufficiently large $Y$, cancellation with $\eta=Y^{-D}$ for all odd squarefree $1<s\le Y^A$ coprime to $m$, apart from one possible exception. It uses the same three bounds on $U,m,a$. Take $A=800K$ and $D=K+1$ to cover $s\le N^2$. The inequality $\log U\ge Y^{\varepsilon/6}$ gives $Z^2\le\sqrt U$ at large $Y$, so all candidates satisfy $q>N^2$.

For the remaining quantities use $\sum_{n\le t}\Lambda(n)\ll t$ with an absolute constant. For $p\le y$, the part of $b_p$ below $y$ is at most $\log y$, and the geometric tail is at most $2\log p\le2\log y$. For $p>y\ge3$, the geometric tail gives $b_p\le2y\log p/p\le2\log y$, since $\log t/t$ decreases for $t\ge3$. Thus $B=3\log y$ works.

For $p\le y$, the elementary bound $\pi(y)\le\sqrt y+2\sum_{n\le y}\Lambda(n)/\log y$ gives $\sum b_p^2=O(y\log y)$ on that range. For $p>y$, separate $2^j y<p\le2^{j+1}y$. The bound on $b_p$ and $\sum_{p\le t}\log p\ll t$ give contribution $O(y2^{-j}\log(2^{j+1}y))$ on each block. Summing gives $O(y\log y)$.

For the even powers in $R$ write $n=u^2$ and use $\Lambda(u^2)=\Lambda(u)$. The sum to $\sqrt y$ is $O(\sqrt y)$, and the weight $y/u^2$ makes each doubling block above it cost $O(2^{-j}\sqrt y)$. For the bases dividing $m$, only primes $\le Y^{\varepsilon/5}\le y^{1/5}$ can occur below $Z$, so these contribute at most $3y^{1/5}\log y\ll\sqrt y$. Thus $R^2+2B^2+2BR\ll y\log y$. Finally $L\le y\sum_{n\le N}\Lambda(n)/n\ll y\log Z$. Increasing the threshold so that $400K\log Y\le\sqrt Y$, we get $\eta L^2\ll Y^{-(K+1)}y^2Y\le y$. Substitution into (1) proves the uniform mean-square estimate. The [interval sieve](mean-square-good-primes.md) uses this at every $y$ and for every bounded coefficient sequence.

## Lean references and review

- [`jacobi_class`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqJac.lean#L141) fixes the signs; `abs_pair_sum_eq` in [`MSqMain.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqMain.lean) gives the transformed symbol sum.
- [`pairs_one`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqPairs.lean#L255) and [`pairs_r`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqPairs.lean#L307) give the two special contributions, assembled by [`QH.meanSq_abs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/MeanSqAbs.lean).
- [`meanSqK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/meanSqK.lean) applies [`twistK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/twistK.lean#L148) and the estimates in [`SPsqLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/SPsqLe.lean), [`RRLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/RRLe.lean), and [`SumCNLe.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/SumCNLe.lean).

English translation draft. The cancellation input is proved in the note on [why only one quadratic twist can be exceptional](one-exceptional-quadratic-twist.md).
