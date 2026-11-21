# The Siegel gap from nonnegative Dirichlet coefficients

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%B1%E9%9D%9E%E8%B4%9FDirichlet%E7%B3%BB%E6%95%B0%E5%BE%97%E5%88%B0Siegel%E9%97%B4%E9%9A%99.md)

**Proposition.** For every $\epsilon>0$ there exists $c(\epsilon)>0$ such that for every $q\ge1$ and every nonprincipal real Dirichlet character $\chi$ modulo $q$,
$$
|L(1,\chi)|\ge c(\epsilon)q^{-\epsilon}.
\tag{1}
$$
For every $\epsilon>0$ there also exists $d(\epsilon)>0$ such that every real zero $\beta$ of any such $L(s,\chi)$ satisfies $1-\beta\ge d(\epsilon)q^{-\epsilon}$.

## A product with nonnegative coefficients

Let $\chi_1,\chi_2$ be two nonprincipal real characters, with moduli $q_1,q_2$. On the units modulo $Q=q_1q_2$ set $\psi=\chi_1\chi_2$, and extend $\psi$ by zero. First suppose $\psi$ is nonprincipal. Put
$$
F(s)=\zeta(s)L(s,\chi_1)L(s,\chi_2)L(s,\psi),\qquad
\lambda=L(1,\chi_1)L(1,\chi_2)L(1,\psi).
$$
For $\Re s>1$, $F(s)=\sum_{n\ge1}a_n n^{-s}$ with $a_n\ge0$ and $a_1=1$. Indeed, at $p\nmid Q$ the character values are $a,b,ab$ for $a,b\in\{\pm1\}$. With $X=p^{-s}$ the Euler factor is either $(1-X)^{-4}$ or $(1-X^2)^{-2}$. At $p\mid Q$ the value of $\psi$ and at least one of the other two values vanish, so the factor is $(1-X)^{-1}$, $(1-X)^{-2}$, or $(1-X^2)^{-1}$. Each power series has nonnegative coefficients.

The nonprincipal $L$-functions are entire and $\zeta$ has residue $1$ at $1$. Thus $G(s)=F(s)-\lambda/(s-1)$ is holomorphic on a neighborhood of the closed disk $|s-2|\le3/2$. On the boundary, $|G(s)|\le C Q^K$ for absolute $C,K>0$. To see this, for a nonprincipal character modulo $m$ split its Dirichlet series at $m$. Complete periods sum to zero, so each partial sum of the tail is $O(m)$. Partial summation bounds the tail by $O(m|s|m^{-\Re s}/\Re s)$ when $\Re s>0$. Both the tail and the first $m$ terms are $O(m)$ for $\Re s\ge1/2$ and $|s|\le4$. The three factors give $O(q_1q_2 Q)=O(Q^2)$. On the circle $\zeta$ is bounded and $|s-1|\ge1/2$. At $s=1$ the initial segment is harmonic and the tail is $O(1)$, giving
$$
|L(1,\chi)|\ll\log(3m)\quad(\chi\ne\chi_0\bmod m).
\tag{2}
$$

## Taylor truncation at a real point near $1$

For $|z|<1$, write $F(2-z)=\sum_{j\ge0}b_j z^j$. Absolute convergence permits expanding $n^z=e^{z\log n}$ under the sum, so $b_j=\sum_n a_n n^{-2}(\log n)^j/j!\ge0$ and $b_0\ge1$. Thus the Taylor coefficients of $G(2-z)$ are $b_j-\lambda$, since every coefficient of $\lambda/(1-z)$ is $\lambda$.

Let $7/8\le\sigma<1$ and $w=2-\sigma\in(1,9/8]$. Cauchy's estimate on $|z|=3/2$ bounds the tail of $G(2-z)$ at $w$ after degree $N-1$ by $4C Q^K(3/4)^N$. Increase $C$ to at least $1$ and take $N=1+\lceil\log(8C Q^K)/\log(4/3)\rceil$. The tail is at most $1/2$ and $N=O(1+\log Q)$. Retaining the $b_0$ term and restoring the pole gives the real inequality
$$
F(\sigma)\ge \tfrac12-|\lambda|\sum_{j=0}^{N-1}w^j-\frac{|\lambda|}{w-1}
=\tfrac12-\frac{|\lambda|w^N}{1-\sigma}.
$$
Since $w^N\le e^{N(1-\sigma)}$, there are absolute constants $C_*,K_*>0$ such that
$$
F(\sigma)\ge\tfrac12-C_*\frac{|\lambda|Q^{K_*(1-\sigma)}}{1-\sigma}.
\tag{3}
$$
Taking $\sigma$ close to $1$ permits a small exponent of $Q$.

## One reference character for all moduli

Set $\sigma_0=\max(7/8,1-\epsilon/[2(K_*+1)])<1$. If some nonprincipal real character has a zero in $[\sigma_0,1)$, fix one such character $\chi_1$ and zero $\sigma$. Then $F(\sigma)=0$ for every nonprincipal real $\chi_2$ for which $\psi$ is nonprincipal. If no such zero exists, fix any nonprincipal real $\chi_1$ and take $\sigma=\sigma_0$. In this case all three $L$-factors are positive at $\sigma$. They are positive by the Euler products for $s>1$, nonzero at $1$, real on the real axis, and have no zero between $\sigma$ and $1$. Also $\zeta(\sigma)<0$ because the alternating Dirichlet series equals $(1-2^{1-\sigma})\zeta(\sigma)$ and is positive by pairing successive terms. Hence $F(\sigma)<0$ in this case.

In either case $F(\sigma)\le0$ and $K_*(1-\sigma)\le\epsilon/2$. Using (2) for $\psi$ gives $|L(1,\psi)|\ll_\epsilon Q^{\epsilon/2}$. Inequality (3) now gives $1\ll_{\epsilon,\chi_1,\sigma} Q^\epsilon|L(1,\chi_2)|$. The factor $q_1^\epsilon$ is fixed, giving (1) when $\psi$ is nonprincipal.

If $\psi$ is principal, the two characters agree on the units modulo $Q$ and their lifts to modulus $Q$ are equal. At $s=1$, lifting multiplies each original $L$-value by the factors $1-\chi_i(p)/p$ for $p\mid Q$. If $p_1<\dots<p_r$ are the distinct primes dividing $Q$, then $p_j\ge j+1$. Consequently the products of these factors lie between $1/(r+1)$ and $r+1$. Comparing the two equal lifted $L$-values yields $|L(1,\chi_2)|\ge |L(1,\chi_1)|/(r+1)^2$. Since $2^r\le Q$, the denominator is $O_\epsilon(Q^\epsilon)$, again proving (1). The constant may depend on the chosen reference character and its zero, so this argument gives existence for each $\epsilon$.

## From $L(1,\chi)$ to the gap

Every real zero satisfies $\beta<1$ by nonvanishing for $\Re s\ge1$. If $\beta\le1-1/\log(3q)$, then $1-\beta\gg_\epsilon q^{-\epsilon}$. Otherwise the derivative satisfies $|L'(s,\chi)|\ll\log^2(3q)$ throughout $[\beta,1]$. For this, split the derivative series at $q$. Since $n^{-s}\le e/n$ for $n\le q$, the first segment is $O(\log^2(3q))$. In the tail use the bound $O(q)$ for partial sums of $\chi$ and differentiate the weight $t^{-s}\log t$ in partial summation. This gives $O(q^{1-s}(\log q+1/s))=O(\log(3q))$. The derivative series converges locally uniformly for $\Re s>0$ by the same argument on compact subsets.

Integrating from $\beta$ to $1$ yields $|L(1,\chi)|\ll(1-\beta)\log^2(3q)$. Apply (1) with exponent $\epsilon/3$ and bound each logarithm by $O_\epsilon(q^{\epsilon/3})$. This gives $1-\beta\gg_\epsilon q^{-\epsilon}$. The [relative prime number theorem](relative-prime-number-theorem-two-ranges.md) uses $\epsilon=1$ to lower-bound the normalized exceptional factor by a constant times $1/M$. See also the [character-sum and derivative estimates](positive-prime-power-sum-by-hyperbola.md) for the derivative input.

## Lean correspondence

- `dirichlet_product_coefficients`, `dirichlet_product_entire` and `product_lfunction_growth_bound` support the product construction. The Lean growth estimate is finer than the coarse disk bound used above. [Coefficients](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqCoeff.lean#L34) · [Analyticity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqEntire.lean#L31) · [Growth](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqGrowth.lean#L48)
- `product_lfunction_key_inequality` gives (3). `siegel_product_character_inequality` and `siegel_theorem_of` make the reference-character choice, and `lfunction_one_same_character` treats the coincident lift. [Key inequality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/BqKeyOf.lean#L60) · [Reference choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SiegelOf.lean#L9) · [Common lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/SameCharacterLFunctionOne.lean#L98)
- `siegelLower` and `exceptional_zero_bound_of` give (1) and the real-zero gap. The proof uses analytic continuation and nonvanishing at $1$ for nonprincipal characters, and Cauchy's coefficient estimate. [Lower bound](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/FinalSiegel.lean#L17) · [Gap](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LandauZeroFreeBounds/ExceptionalZeroBounds/ExcBoundOf.lean#L26)

Status. Translation draft based on the Chinese proof and its pinned Lean references. No new Lean replay or axiom audit accompanies this note.
