# Brun–Titchmarsh from the missing-residue large sieve

[Chinese proof](../zh/%E7%BC%BA%E7%B1%BB%E5%A4%A7%E7%AD%9B%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BABrun%E2%80%93Titchmarsh%E7%95%8C.md)

Write $e(u)=e^{2\pi i u}$ and let $\varphi$ be Euler's totient, including $\varphi(1)=1$.

## Independent missing classes at squarefree moduli

Let $d\ge1$ be squarefree, $S\subseteq\mathbb N$ finite and $b_m\in\mathbb C$. If for each prime $\ell\mid d$ some residue class modulo $\ell$ is avoided by all of $S$, then
$$
\left|\sum_{m\in S}b_m\right|^2
\le\varphi(d)\sum_{0\le a<d,\ (a,d)=1}\left|\sum_{m\in S}b_m e(ma/d)\right|^2.
\tag{1}
$$
At $d=1$ this is equality. If $d=d'\ell$ with $(d',\ell)=1$, use induction at $d'$. For each resulting $a'$ apply the [prime missing-class bound](frequency-energy-of-a-missing-residue.md) to the coefficients $b_m e(ma'/d')$, supported on the same $S$. This adds a factor $\ell-1$ and a sum over $1\le a''<\ell$ with frequency $a'/d'+a''/\ell$. The Chinese remainder theorem sends $(a',a'')$ bijectively to the unit $a=\ell a'+d'a''\bmod d$, while $\varphi(d')(\ell-1)=\varphi(d)$. This gives (1).

## Counting a set that avoids those classes

Let $M,L$ be nonnegative integers, $Q,q\ge1$ integers, and $S\subseteq\{M+1,\ldots,M+L\}$. Suppose each prime $\ell\le Q$ with $\ell\nmid q$ has a missing class in $S$. Then
$$
|S|\,\frac{\varphi(q)}q\log Q\le Q^2+2\pi L.
\tag{2}
$$
Let $D$ be all squarefree $d\le Q$ coprime to $q$. For $F(t)=\sum_{m\in S} e(mt)$, sum (1) over $d\in D$ after dividing by $\varphi(d)$. The reduced fractions $a/d$ appearing are distinct modulo $1$ and separated by at least $Q^{-2}$, as a nonzero difference modulo $1$ has denominator dividing the product of the two denominators. The [additive large sieve](additive-large-sieve-for-spaced-frequencies.md) gives
$$
|S|^2\sum_{d\in D}\frac1{\varphi(d)}\le(Q^2+2\pi L)|S|.
$$
Group integers $u\le Q$ by the squarefree product $d$ of those prime factors of $u$ not dividing $q$. For each $d$ the sum of $1/u$ is at most $\prod_{\ell\mid d}1/(\ell-1)\prod_{\ell\mid q}(1-1/\ell)^{-1}=q/(\varphi(q)\varphi(d))$, obtained by extending each exponent range and summing its geometric series. As $\sum_{u\le Q}1/u\ge\log Q$, we have $\sum_{d\in D}1/\varphi(d)\ge(\varphi(q)/q)\log Q$. Cancel $|S|$ when nonzero to obtain (2). The empty case also holds.

## Prime counts in an interval

**Proposition.** For $q\ge1$, $a\ge0$ integers with $(a,q)=1$, $x\ge0$ and $y\ge2q$,
$$
\#\{p:x<p\le x+y,\ p\text{ prime},\ p\equiv a\bmod q\}
\le\frac{48y}{\varphi(q)\log(y/q)}.
\tag{3}
$$
Put $z=y/q$, $s=\lfloor\sqrt{\lfloor z\rfloor}\rfloor$, $Q=s+1$, $M=\lfloor x/q\rfloor$, and $L=\lfloor z\rfloor+2$. Then $z<Q^2\le4z$ and $L\le2z$. For the primes $p>Q$ being counted, let $r=a\bmod q$ and put $m=1+\lfloor p/q\rfloor$. Then $p=q(m-1)+r$, so this is injective and $M<m\le M+L$. For each prime $\ell\le Q$ not dividing $q$, one class of $m$ makes $q(m-1)+r$ divisible by $\ell$. This is excluded since $p>Q$. Thus (2), with $B$ the number of these primes, gives $B\varphi(q)\log Q/q\le Q^2+2\pi L\le20z$. Using $\log z\le2\log Q$ we get $B\varphi(q)\log z\le40y$. The remaining primes number at most $Q$ and cost $Q\varphi(q)\log z\le2qQ\log Q\le2qQ^2\le8y$. Add and divide by $\varphi(q)\log z$ to get (3).

## Lean correspondence

- `norm_sum_sq_le_totient_mul_of_avoids_classes` gives (1), with `sum_coprime_range_mul_eq_sum_sum` for the CRT pairing. `sum_inv_le_mul_sum_squarefree_inv_totient` is the reciprocal sum and `arithmetic_large_sieve_one_class` gives (2). [CRT pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L78) · [Squarefree bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L378) · [Counting](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ArithmeticLargeSieveOneResidueClassPerPrime.lean#L427)
- `card_large_primes_class_le` and `GlobalTheory.Lin.brun_titchmarsh_const` give (3), used by the fixed-modulus prime second moment. [Large primes](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BrunTitchmarshExistsConst.lean#L18) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BrunTitchmarshExistsConst.lean#L48) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BrunTitchmarshExistsConstStatement.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
