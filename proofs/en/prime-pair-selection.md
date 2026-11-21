# Choosing two primes that control all the required twists

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8C%91%E5%87%BA%E5%90%8C%E6%97%B6%E6%BB%A1%E8%B6%B3%E6%89%AD%E6%9B%B2%E4%BC%B0%E8%AE%A1%E7%9A%84%E7%B4%A0%E6%95%B0%E5%AF%B9.md) · [Reading and review status](../../STATUS.md)

The [pointwise estimate](translation-averaging.md) needs a prime-sum bound for each discarded character. The host construction realizes such characters as quadratic twists at auxiliary primes. The selection theorem `QH.pairEx` chooses one pair that works for all of them.

## Statement

Fix an integer $M\ge1$, $0<\varepsilon<1/52$, and $K\ge1$. At scale $Y$ put $z=Y^{\varepsilon/5}$ and $z'=z(\log Y)^2$. For a prime $p$ write $J_p(n)=(n/p)$. Say a primitive character $\chi$ realizes a function $a$ on the units modulo $L$ if $\chi(n)=a(n)$ for all $n\ge1$ coprime to $L$. The character $\chi$ is taken modulo its positive conductor. For nontrivial $\chi$, write $g_\chi(y)$ for the [corrected ramp sum](primitive-characters-from-inertia.md), with the correction $y(L'/L)(1,\chi)$.

**Claim.** There is $Y_0$ such that for every $Y\ge Y_0$ there are primes $q,d$ with
$q\equiv3\pmod8$, $d\equiv7\pmod{16}$, $\gcd(M,qd)=1$,
$z/2<\log q\le z$ and $z'/2<\log d\le z'$. The prime $q$ and every odd prime at most $z$ divide $d+1$.

For every character $\xi$ modulo $M$, every $i,j\in\{0,1\}$ with $(i,j)\ne(0,0)$, and every primitive $\chi$ realizing $\xi J_q^iJ_d^j$ on the units modulo $2Mqd$, one has throughout $Y\le y\le Y^K$

$$
|g_\chi(y)|\le y^{1/2+\varepsilon/2},\qquad
|(L'/L)(1,\chi)|\le4\log y.
$$

For every real primitive $\rho$ with conductor dividing $8M$, replacing $\xi$ by $\rho$ gives nonvanishing for every such realizing $\chi$ in $\operatorname{Re}s>1-1/400$, $|\operatorname{Im}s|\le8M\exp(z+jz')$.

## The four sieve inputs

For $0<\alpha\le1/4$, $\tau>0$, $K\ge1$, $X=Y^K$, and $Z=X^{400}$, write $\mathcal P=\{p:\sqrt U<p\le U,\ p\text{ prime},\ p\equiv a_0\pmod{m_0}\}$ with positive $m_0$. The admissible parameters have $8\mid m_0$, $\gcd(a_0,m_0)=1$, and

$$
\tfrac14(\log Y)^2\log m_0\le\log U,\qquad
Y^{\alpha/6}\le\log U\le Y^{\alpha/5}(\log Y)^2 .
$$

Use $S(y,p;\kappa)$ for the capped coefficient sum in the [mean-square note](../zh/%E5%B9%B3%E6%96%B9%E5%B9%B3%E5%9D%87%E6%80%8E%E6%A0%B7%E7%AD%9B%E6%8E%89%E5%8C%BA%E9%97%B4%E4%B8%8A%E7%9A%84%E5%9D%8F%E7%B4%A0%E6%95%B0.md).

1. For fixed $\alpha>0$ and sufficiently large $Y$, `count_a` gives $|\mathcal P|\ge U^{9/10}$ under admissibility, using the relative prime number theorem for progressions and the exceptional-zero estimate.
2. The theorem `meanSqK` supplies an absolute $C_m>0$. For fixed $0<\alpha\le1$, $K\ge1$ and sufficiently large $Y$, if every prime divisor of $m_0$ is at most $Y^{\alpha/5}$ or greater than $Z$, each $Y\le y\le X$ and each coefficient sequence $|\kappa(n)|\le1$ satisfies $\sum_{p\in\mathcal P}|S(y,p;\kappa)|^2\le C_my\log y\,|\mathcal P|$.
3. There is an absolute $C_b$ such that if $Q\ge3$ and every prime in a finite set $\mathcal B$ is greater than $F$ and has a witness $1\le f\le F$, $fp\le Q$, and a primitive character of conductor $fp$ with a zero in $\operatorname{Re}s>1-1/400$, $|\operatorname{Im}s|\le Q$, then $|\mathcal B|\le C_b Q^{1/4}$. This is `count_bad`.
4. For fixed $\alpha,\tau,K$ and sufficiently large $Y$, assume $Y^{\alpha/6}\le\log Q\le Y^{\alpha/4}$. Suppose a nontrivial character $\chi$ has modulus at most $Q$ and no zero in that rectangle, and on all natural numbers $\chi(n)=\kappa(n)J_p(n)$. If $|S(y,p;\kappa)|\le\tfrac12 y^{1/2+\tau}$ throughout $[Y,X]$, then `box_of_S` gives $|g_\chi(y)|\le y^{1/2+\tau}$ on the interval and $|(L'/L)(1,\chi)|\le C\log Y$ with absolute $C$.

## Sieve a finite family of base characters

Take a finite family $\Xi$ of at most $R$ primitive base characters, with conductor at most $F$ for each, where $R$ is fixed and $1\le F\le\sqrt U$ may vary. Assume admissibility and the prime-divisor condition above. For $p\in\mathcal P$ we have $p>F$. If $\xi$ has conductor $f$, then $\chi=\xi J_p$ is primitive of conductor $fp$ and nontrivial: the two coprime moduli give a direct product of unit groups, and each factor character uses its full conductor.

Use $Q=FU$. Then $fp\le Q$, $\log U\le\log Q\le(3/2)\log U$, and eventually $Y^{\alpha/6}\le\log Q\le Y^{\alpha/4}$ because $(3/2)(\log Y)^2\le Y^{\alpha/20}$. The primes bad for some $\xi$ because of a zero in the rectangle are at most $|C_b|Q^{1/4}\le |C_b|U^{3/8}$ by input 3. The candidate count $U^{9/10}$ implies that their proportion is at most $\eta/2$ for any fixed $\eta>0$ at sufficiently large $Y$, uniformly using $\log U\ge Y^{\alpha/6}$.

The second kind of bad prime has some $\xi\in\Xi$ for which $|S(y,p;\xi)|>\tfrac12 y^{1/2+\tau}$ at some point of the interval. With input 2, `bad_share` bounds the proportion for each $\xi$ by $\eta/[2(R+1)]$ at sufficiently large $Y$. Its union over $\Xi$ has proportion at most $\eta/2$. So a proportion at least $1-\eta$ of the candidates satisfy the hypotheses of input 4 for all their twists.

Suppose a primitive character matches $\xi J_p$ on units modulo any positive $L$. On the units of a common multiple of $L$ and both conductors, the induced characters agree. Taking the unique primitive characters that induce them shows that the original characters agree. This is the `QH.stage` argument for using the estimates with other moduli.

## Select $q$ and then $d$

For the first sieve take $\alpha=\varepsilon$, $\tau=\varepsilon/2$, $U=\exp z$, $m_0=8$, $a_0=3$. Use the primitive characters induced from all characters modulo $N_0=8M$ as the base family, with $F=N_0$ and $R$ depending only on $M$. At large $Y$, admissibility follows from $(\log Y)^2=o(z)$ and $Y^{\varepsilon/6}\le z$. The only prime factor of $m_0$ is $2$. Taking $\eta=1/2$ gives a prime $q>N_0$ for which the estimates hold on all the single $J_q$ twists.

Fix this $q$ and set $m'=q\prod_{3\le p\le z,\ p\text{ prime}}p$. The congruences $d\equiv7\pmod{16}$ and $d\equiv-1\pmod{m'}$ define a unit class modulo $16m'$. Apply the sieve with this modulus and class, $\alpha=6\varepsilon/5$, $U=\exp z'$, and still $\tau=\varepsilon/2$. The Chebyshev bound $\sum_{p\le z}\log p\le(\log4)z$ and $\log q\le z$ give $\log(16m')\le4z$ for sufficiently large $Y$. Thus the first admissibility inequality holds. The second follows from $Y^{\alpha/6}=z\le z'\le Y^{\alpha/5}(\log Y)^2$. Any prime divisor of the modulus is at most $z$ or is $q>Z$, because $\log q>z/2$ and $z/\log Y\to\infty$.

Now use the primitive characters induced by any $\xi$ or $\xi J_q$ for $\xi$ modulo $N_0$. The size of the base family at most doubles, and the conductors are at most $N_0 q$. Take $F=N_0\exp z\le\exp(z'/2)$ at sufficiently large $Y$. Again take $\eta=1/2$ to choose $d$. The first sieve covers $j=0,i=1$, and the second covers $j=1,i=0$ or $1$. Since $z'\ge2z$ at large $Y$, we have $d>q>8M$ and therefore $\gcd(M,qd)=1$.

A character modulo $M$, or a real primitive character with conductor dividing $8M$, induces a character modulo $8M$. Coprimality to $2Mqd$ is the same as coprimality to $8Mqd$. The uniqueness argument therefore applies to every realizing primitive character in the statement. The zero-free heights from $Q=FU$ are $8M\exp z$ in the first sieve and $8M\exp(z+z')$ in the second.

## The exact log-derivative bound and its use

The result `kappa4` gives $|(L'/L)(1,\chi)|\le4\log Y$ for nontrivial characters of modulus at most $Q$ with that zero-free rectangle, provided $Y$ is sufficiently large and $Y^{\varepsilon/6}\le\log Q\le A Y^{\varepsilon/5}(\log Y)^2$ with fixed $A>0$. It starts from a truncated log-derivative upper bound $1000\log\log Q+O(1)$ under nonvanishing. The inequality $1000\varepsilon/5<4$ leaves enough room to absorb the remaining terms. In the two sieves $\log Q=\log(8M)+z+jz'$ satisfies the conditions with $A=3$ for large $Y$. Since $Y\le y$, this gives the claimed $4\log y$.

In the host application, $M$ is the conductor of the fixed primitive $\psi$. The host condition `TwistForm` realizes each group character $\theta$ trivial on $H_0$ as $\xi J_q^iJ_d^j$ on units modulo $Q_Sqd$, with $\xi$ a power of $\psi$ and $\theta(1,0,0)=(-1)^j$. It also requires $M\mid Q_S$ and that each prime factor of $Q_S$ divide $2M$. A character with first sign $-1$ has $j=1$. A discarded character with first sign $1$ cannot have $i=j=0$, since then its primitive character would come from a power of $\psi$ and would be retained. Every integer coprime to $2Mqd$ is coprime to $Q_Sqd$, so the pair estimate applies. This supplies $|g_\chi(x)|\le x^{1/2+\varepsilon/2}\le x^{1/2+\varepsilon}$ and $|(L'/L)(1,\chi)|\le4\log x$ on $[Y,Y^K]$. The [character identification](primitive-characters-from-inertia.md) uses those bounds on the discarded sum.

## Lean references and review

- The sieve is [`QH.stage`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/StagePow.lean#L41). See [`MSqCount.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GL3MeanSquares/GenusMeanAsymptotics/JacobiCharacterSums/MSqCount.lean) for `bad_share` and [`CountBad.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/CountBad.lean) for zero counting.
- The inputs are [`QH.meanSqK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/meanSqK.lean#L51), [`box_of_S`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/BoxOfS.lean#L28), and [`kappa4`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/Kappa4Loglog.lean#L126). In `box_of_S` the [tail identity](../zh/%E9%9B%B6%E7%82%B9%E7%9F%A9%E5%BD%A2%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E6%88%AA%E6%96%AD%E7%B4%A0%E6%95%B0%E5%92%8C%E7%9A%84%E5%B0%BE%E9%A1%B9.md) gives $g_\chi(y)=-S(y,p;\kappa)-y\,\mathrm{tail}$, with $|y\,\mathrm{tail}|\le Y^\alpha$ absorbed by $\tfrac12 y^{1/2+\tau}$.
- The stages are [`stage1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/Stage1Succ.lean#L36) and [`stage2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/CharOf.lean#L61). [`pair_share`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/PairShare.lean#L26), [`pair_exists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/PairExists.lean#L9) and [`QH.pairEx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/MeanSquareBounds/pairEx.lean#L112) conclude existence.
- The host use is [`boundedTw`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/BoundedTw.lean#L45). The pair also enters [`winPairs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CharacterBoxes/WinPairs.lean#L5) in the [common-window argument](common-window.md) and [`supplyOfAdmOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ShortNorms/supplyOfAdmOf.lean).

English translation draft. The prime theorem, mean-square bound and zero-density bound are inputs. For their proofs see the Chinese notes on [exceptional characters in the second moment](../zh/%E5%B9%B3%E6%96%B9%E5%B9%B3%E5%9D%87%E4%B8%AD%E7%9A%84%E4%BE%8B%E5%A4%96%E7%89%B9%E5%BE%81%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%AA%E8%B4%A1%E7%8C%AE%E5%B0%91%E6%95%B0%E7%B4%A0%E6%95%B0%E5%AF%B9.md) and [counting bad twists with Dirichlet polynomials](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E7%8B%84%E5%88%A9%E5%85%8B%E9%9B%B7%E5%A4%9A%E9%A1%B9%E5%BC%8F%E6%95%B0%E5%87%BA%E5%9D%8F%E6%89%AD%E6%9B%B2.md).
