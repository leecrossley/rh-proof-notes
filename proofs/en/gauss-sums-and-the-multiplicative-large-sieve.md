# Gauss sums and the multiplicative large sieve

[Chinese proof](../zh/%E9%AB%98%E6%96%AF%E5%92%8C%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%8A%A0%E6%B3%95%E5%A4%A7%E7%AD%9B%E5%8F%98%E6%88%90%E4%B9%98%E6%B3%95%E5%A4%A7%E7%AD%9B.md)

Write $e(u)=e^{2\pi i u}$.

**Proposition.** For integer $Q\ge1$, $M,L\ge0$ integers, and complex coefficients $a_n$ on $M<n\le M+L$,
$$
\sum_{q=1}^Q\sum_{\chi\bmod q}^{*}\left|\sum_{M<n\le M+L}a_n\chi(n)\right|^2
\le(Q^2+2\pi L)\sum_{M<n\le M+L}|a_n|^2 .
\tag{1}
$$
The star ranges over primitive characters, meaning the characters of the unit group that do not descend to a proper divisor of $q$. Their values off the units are zero, and the unique character modulo $1$ is primitive.

## The shifted Gauss sum

For a primitive $\chi\bmod q$, let $\tau(\chi)=\sum_{b\bmod q}\chi(b)e(b/q)$. The shifted sum obeys
$$
\sum_{b\bmod q}\chi(b)e(nb/q)=\chi^{-1}(n)\tau(\chi).
\tag{2}
$$
On the units this is the change of variable $b\mapsto nb$. If $g=\gcd(n,q)>1$, write $d=q/g$. Reduction from the units modulo $q$ to those modulo $d$ is onto. For a lift use the Chinese remainder theorem to make its value $1$ at primes dividing $q$ and coprime to $d$. Primitivity gives a unit $u\equiv1\bmod d$ with $\chi(u)\ne1$, otherwise the character would descend. Multiplication by $u$ preserves the additive phase since $q\mid n(u-1)$, so it multiplies the sum by $\chi(u)$ without changing it. Thus both sides of (2) vanish.

The same argument works over a field $K$ with a primitive $K$-valued multiplicative character $\chi$ and a primitive additive character $\psi:\mathbb Z/q\mathbb Z\to K^\times$. Additive primitivity means for each nonzero $c\bmod q$ that $b\mapsto\psi(bc)$ is nontrivial. Define $\tau(\chi,\psi)=\sum_a\chi(a)\psi(a)$. The shift identity gives
$$
\tau(\chi,\psi)\tau(\chi^{-1},\psi^{-1})
=\sum_a\chi(a)\sum_b\psi(b(a-1))=q
$$
in $K$. Indeed for $a\ne1$ the inner sum vanishes by translation by a $b_0$ on which $\psi(b_0(a-1))\ne1$, and for $a=1$ it is $q$. Over $\mathbb C$ with $\psi(b)=e(b/q)$ this gives $|\tau(\chi)|^2=q$.

## From characters to separated frequencies

Character orthogonality on the unit group gives, for any $F$ on the residue classes,
$$
\sum_{\chi\bmod q}\left|\sum_b \chi^{-1}(b)F(b)\right|^2
=\varphi(q)\sum_{(b,q)=1}|F(b)|^2 .
$$
Expanding the squares reduces to $\sum_\chi\chi(cb^{-1})$, which is $\varphi(q)$ at the identity and zero otherwise by geometric sums on the cyclic factors of the finite unit group.

Put $A(t)=\sum_{M<n\le M+L}a_n e(nt)$ and $F(b)=A(b/q)$. Inversion preserves primitivity, so (2) for $\chi^{-1}$ gives $\sum_b \chi^{-1}(b)F(b)=\tau(\chi^{-1})\sum_n a_n\chi(n)$. Squaring, summing, and extending the orthogonality sum from primitive to all characters gives
$$
q\sum_{\chi\bmod q}^{*}\left|\sum_n a_n\chi(n)\right|^2
\le\varphi(q)\sum_{0\le b<q,\ (b,q)=1}|A(b/q)|^2.
\tag{3}
$$
All reduced fractions $b/q$ here, for $1\le q\le Q$, are distinct. For two of them and $k\in\mathbb Z$, their difference minus $k$ is a nonzero integer divided by $qr$, so its modulus is at least $Q^{-2}$. Apply the [additive large sieve](additive-large-sieve-for-spaced-frequencies.md) with $\delta=Q^{-2}$, and sum (3) using $\varphi(q)/q\le1$. This proves (1). Dividing (3) by $\varphi(q)$ gives the weighted version with $q/\varphi(q)$ on the left of (1).

## Lean correspondence

- Mathlib gives `gaussSum_mulShift_of_isPrimitive`. The project proves the field-valued Gauss identity and its norm specialization. [Shift](https://github.com/leanprover-community/mathlib4/blob/0df444a360eaa60ab8c11dca51a86af692955474/Mathlib/NumberTheory/DirichletCharacter/GaussSum.lean#L57) · [Field identity](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/GaussSumMulGaussSumInvOfIsPrimitive.lean#L11) · [Norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieve.lean#L8)
- `sum_norm_sq_char` and `sum_primitive_le` give (3). `farey_spaced` and `reduced_inj` give the spacing and `multiplicative_large_sieve` applies the additive bound. [Orthogonality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieve.lean#L16) · [Comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieve.lean#L47) · [Spacing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieve.lean#L98) · [Conclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MultiplicativeLargeSieve.lean#L142)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
