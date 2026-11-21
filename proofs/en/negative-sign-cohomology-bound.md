# Valuations and annihilators in the negative-sign cohomology bound

[Chinese proof](../zh/%E8%B4%9F%E5%8F%B7%E4%B8%8A%E5%90%8C%E8%B0%83%E9%95%BF%E5%BA%A6%E6%80%8E%E6%A0%B7%E7%94%B1%E8%B5%8B%E5%80%BC%E5%92%8C%E6%B6%88%E5%8E%BB%E5%85%83%E6%8E%A7%E5%88%B6.md) · [Reading and review status](../../STATUS.md)

## Setting and conclusion

Fix an abelian field datum $A$ with positive modulus $m$ and subgroup $H_A\le(\mathbb Z/m\mathbb Z)^\times$, and put $d_A=[(\mathbb Z/m\mathbb Z)^\times:H_A]$. Let $u,t\ge2$, and let $q,d$ be primes with $q\equiv3\pmod8$, $d\equiv7\pmod{16}$ and $\gcd(qd,m)=1$. Let $E$ be a CM field in the cyclotomic fixed-field class for $(A,u,q,d)$ from the [cohomological window](cohomological-window.md). In particular the defining subgroup has image in $H_A$ modulo $m$, in $\{\pm1\}$ modulo $2^{u+2}$ and in the squares modulo $q$ and $d$. Put $n=[E:\mathbb Q]$ and let $F$ be the least positive conductor of a cyclotomic field into which $E$ embeds.

For odd prime $\ell$ and $a\ge1$, let $L^-_{\ell,a}$ be the $\mathbb Z_\ell$-length of the $(-1)^{a+1}$ eigenspace of complex conjugation in the kernel of localization at all places over $\ell$. The global cohomology uses $\mathbb Q_\ell/\mathbb Z_\ell(-a)$ and allows ramification only over $\ell$ at the finite places.

Under the local inputs stated below, these lengths are finite, and there is an absolute $C\ge0$ such that for every finite set $S$ of odd primes,

$$
\sum_{\ell\in S}\log\ell\sum_{1\le a<t}L^-_{\ell,a}
\le 3nt^2\log(tF)+C\sum_{\substack{\ell\mid d_A\\\ell\text{ odd prime}}}
\ell n^2t^2\log^2(t\ell F). \tag{1}
$$

All estimates quantify over every allowed local model. This is the conclusion of `ThmBcFree`, the negative-sign part of the total length estimate.

## The bound from an annihilating power of $\ell$

For every odd $\ell$ and $a\ge1$, `killPow` supplies a nonnegative integer $r$ such that $\ell^r$ kills the entire negative eigenspace and $r\log\ell\le C_0n(a+1)\log(a\ell F)$ for an absolute $C_0\ge0$. The extra condition for the dyadic case does not occur here. The other input, `gen`, gives length at most $8\ell n\log(\ell F)$ for the submodule of global $H^1$ killed by $\ell$.

Filter the negative eigenspace $P$ by $P[\ell^i]$ for $0\le i\le r$. On $P[\ell^i]$, multiplication by $\ell^{i-1}$ has kernel $P[\ell^{i-1}]$ and image in the $\ell$-torsion of global $H^1$, so each successive quotient injects into that torsion. Every quotient therefore has finite length at most $8\ell n\log(\ell F)$. Add the lengths, multiply by $\log\ell$, and use the bound on $r$ and $\log(\ell F)\le\log(a\ell F)$. This gives `StickBound`:

$$
\log\ell\cdot L^-_{\ell,a}\le 8C_0\ell n^2(a+1)\log^2(a\ell F). \tag{2}
$$

## The bound from an integer shared by all good primes

Let $k=a+1$. Write $T_k$ for the characters modulo $F$ factoring through $\operatorname{Gal}(E/\mathbb Q)$ with $\xi(-1)=(-1)^k$. They can be realized over $\mathbb C$ or over an algebraic closure of $\mathbb Q_\ell$. Set $A_k(\xi)=F(\prod_{p\le k+1}p)B_{k,\xi^*}$ with the product over primes and $\xi^*$ the inducing primitive character. The generalized Bernoulli number of a primitive character $\xi^*$ of conductor $f$ is $B_{k,\xi^*}=f^{k-1}\sum_{b\bmod f}\xi^*(b)B_k(b/f)$, with $B_k$ the Bernoulli polynomial. Use $|\ell|_\ell=1/\ell$.

For $\ell\nmid n$, the conclusion `atPrime` obtained from `PsiBound` gives finiteness of $L^-_{\ell,a}$ and a subset $T'_{k,\ell}\subseteq T_k$ satisfying

$$
\log\ell\cdot L^-_{\ell,a}
\le \sum_{\xi\in T'_{k,\ell}}-\log|A_k(\xi)|_\ell .
$$

The Bernoulli input `b_prodint` says that all the $A_k(\xi)$ are algebraic integers, their full product is a common nonzero rational integer $D$ in every chosen algebraic closure, and $\log|D|\le|T_k|\log(16F^{k+1}k!)$. Each summand is therefore nonnegative, so we may extend $T'_{k,\ell}$ to $T_k$. By multiplicativity of the absolute value, the full sum is $v_\ell(D)\log\ell$. Adding over any finite set of primes not dividing $n$ costs at most $\log|D|$, by factorization of the same integer $D$. As $E/\mathbb Q$ is abelian, $|T_k|\le n$. Thus the sum over these primes for each $a$ is at most $n\log(16F^{k+1}k!)$.

## Which exceptional primes can occur

The Galois group $\operatorname{Gal}(E/\mathbb Q)$ is a quotient of the unit group of the defining cyclotomic field. Let $D_0=2^{u+1}d_A$. For every such unit $b$, Euler's theorem gives $b^{D_0}\equiv1\pmod{2^{u+2}}$. Its image in $(\mathbb Z/m\mathbb Z)^\times/H_A$ is one after taking the same power because that quotient has order $d_A$. Since $D_0$ is even the powers modulo $q,d$ are automatically squares. Thus the $D_0$th power of every automorphism fixes $E$. If an odd prime $\ell$ divides $n$, Cauchy's theorem gives an element of order $\ell$ in $\operatorname{Gal}(E/\mathbb Q)$, so $\ell\mid D_0$ and hence $\ell\mid d_A$.

For primes not dividing $n$ sum the integer bound over $1\le a<t$. Since $k=a+1\le t$, one has $16F^{k+1}k!\le(tF)^{2t+5}$ by bounding the factors by $(tF)^4,(tF)^{t+1},(tF)^t$. Since $(t-1)(2t+5)\le3t^2$, this gives the first term in (1). For primes dividing $n$ apply (2) and use $a+1\le t$, $\log(a\ell F)\le\log(t\ell F)$. Summing over fewer than $t$ values of $a$ and over the odd prime divisors of $d_A$ gives the second term with $C=8C_0$. Both parts also give the required finiteness.

## Lean references and review

- [`thmBc_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ThmBcOfPsiBound.lean#L147) splits the primes and sums in $a$. The degree restriction is [`DegExistsLift.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/DegExistsLift.lean).
- In [`ThmBcOfPsiBound.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ThmBcOfPsiBound.lean), `stick_of` combines [`killPow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/KillPow.lean), `gen` and `lenPow`. See also the [imports](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/Imports.lean).
- [`primeBound_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ThmBcOfPsiBound.lean#L293) uses [`atPrime`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/AtPrime.lean) and the common integer via [`prodVal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ProdVal.lean). The Bernoulli numbers are in [`MapGenBChar.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/BernoulliNumbers/MapGenBChar.lean).
- [`thmBcFree_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/ThmBcOfPsiBound.lean#L295) assumes `PsiBound`, supplied by `ML.iv` in [`HVCore.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ThresholdArguments/DenseThresholdCases/HVCore.lean).

English translation draft. The Chinese notes continue into the [Bernoulli character bound](../zh/%E5%B9%BF%E4%B9%89Bernoulli%E6%95%B0%E6%80%8E%E6%A0%B7%E7%95%8C%E5%AE%9A%E8%B4%9F%E5%8F%B7%E7%89%B9%E5%BE%81%E5%88%86%E9%87%8F%E7%9A%84%E9%95%BF%E5%BA%A6.md), its [local cup-product input](../zh/%E5%B1%80%E9%83%A8%E6%9D%AF%E7%A7%AF%E6%80%8E%E6%A0%B7%E8%BF%AB%E4%BD%BF%E6%83%AF%E6%80%A7%E4%B8%8A%E7%9A%84%E5%8F%96%E5%80%BC%E4%B9%98%E7%A7%AF%E6%B6%88%E5%A4%B1.md), the [annihilating prime power](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E7%BE%A4%E7%8E%AF%E6%B6%88%E5%8E%BB%E7%AE%97%E5%AD%90%E8%83%BD%E7%BB%99%E5%87%BA%E4%B8%80%E4%B8%AA%E7%B4%A0%E6%95%B0%E5%B9%82.md) and the [bound for one layer of torsion](../zh/%E5%8A%A0%E4%B8%80%E5%B1%82%E5%8D%95%E4%BD%8D%E6%A0%B9%E6%80%8E%E6%A0%B7%E6%95%B0%E5%87%BA%E8%A2%AB%E7%B4%A0%E6%95%B0%E6%B6%88%E5%8E%BB%E7%9A%84%E4%B8%8A%E5%90%8C%E8%B0%83%E7%B1%BB.md).
