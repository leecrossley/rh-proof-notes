# Counting and detecting zeros in a small disk

[Chinese proof](../zh/%E5%B0%8F%E5%9C%86%E7%9B%98%E9%87%8C%E7%9A%84%E9%9B%B6%E7%82%B9%E6%80%8E%E6%A0%B7%E4%BA%A7%E7%94%9F%E5%A4%A7%E5%AF%BC%E6%95%B0.md)

Let $\chi$ be a character modulo $q\ge1$ and let $\tau\in\mathbb R$. Assume that $\chi$ is nonprincipal or $|\tau|\ge2$. Let $D_k(\chi;s)=k!^{-1}\sum_{n\ge1}\Lambda(n)\chi(n)(\log n)^k n^{-s}$ for $\Re s>1$.

**Proposition.** There is an absolute $C>0$ such that for $0<r\le1/2$, the disk $|w-(1+i\tau)|\le r$ contains finitely many zeros of $L(s,\chi)$, of total multiplicity at most $C(1+r\log(q(|\tau|+2)))$. There are also absolute $A\ge1$, $C_*,r_0>0$ such that if
$$
L\ge\log(q(|\tau|+2)),\quad 1/L\le r\le r_0,\quad
K\ge C_*rL,\quad |\rho-(1+i\tau)|\le r,
$$
where $K$ is a nonnegative integer and $\rho$ is a zero, then some integer $K\le k\le2K$ has $|D_k(\chi;1+r+i\tau)|\ge(Ar)^{-(k+1)}$.

## First powers and the reciprocal square sum

Put $s=1+r+i\tau$ and let $Z$ be the zero set in $|w-(2+i\tau)|\le3$, excluding the principal pole. The [high log-derivative formula](high-log-derivatives-from-nearby-zeros.md) with constant $C_1$ gives, for $j\ge1$,
$$
\left|\sum_{w\in Z}m_\chi(w)(s-w)^{-j}\right|
\le |D_{j-1}(\chi;s)|+C_1 L+1 .
\tag{1}
$$
The pole term is at most $1$ because $|s-1|\ge2$ for a principal character. Also $|D_0(\chi;s)|\le G(r)=\sum_n\Lambda(n)n^{-1-r}\le1/r+C_1$. For the last bound apply the disk formula to $\zeta$ at $1+r$, where the zero fractions have nonnegative real parts.

For each $w\in Z$, $\Re(s-w)\ge r$, so $\Re(1/(s-w))\ge r/|s-w|^2$. On the small disk $|s-w|\le2r$, so each copy contributes at least $1/(4r)$. With $L=\log(q(|\tau|+2))$, (1) at $j=1$ gives the asserted count. If $L\ge1/r\ge2$, the same estimate also gives
$$
\sum_{w\in Z}\frac{m_\chi(w)}{|s-w|^2}\le(2C_1+2)L/r.
\tag{2}
$$

## A large power near the target

Use [Turán's second theorem](turan-power-sums-by-exterior-interpolation.md) with constant $D=16e^2$: among powers $M+1,\ldots,M+N$ of a list of $N$ complex numbers, one power sum has modulus at least $(N/[D(M+N)])^N$ times that power of the modulus of a specified entry. Set $A=8D$, $r_0=1/A$, $C_*=4A^2(2C_1+2)$, and $Z_{\rm in}=\{w\in Z:|s-w|\le Ar\}$. By (2),
$$
(Ar)^2\sum_{w\in Z}m_\chi(w)|s-w|^{-2}\le K/4.
$$
Thus there are at most $K$ near zeros with multiplicity. They include $\rho$, since $|\rho-(2+i\tau)|\le1+r$ and $|s-\rho|\le2r$. The point cannot be the principal pole by the height condition.

List the reciprocals for $Z_{\rm in}$ with multiplicity and pad with zeros to length $K$. Apply Turán with $M=N=K$ and the entry from $\rho$. Some $K+1\le j\le2K$ has near-sum modulus at least $(1/(2D))^K(1/(2r))^j\ge X^j$, with $X=1/(4Dr)$. For a far zero the $j$th reciprocal power in modulus is bounded by $(Ar)^{2-j}|s-w|^{-2}$, since $j\ge2$. Summing gives at most $(Ar)^{-j}K/4\le X^j/4$ by $K\le2^j$. The total power sum has modulus at least $3X^j/4$.

Finally set $k=j-1$. Since $X\ge2$, $X^k\ge K$ and $X^j\ge KX\ge128D(1+C_1)L$. Thus (1) gives $|D_k(\chi;s)|\ge3X^j/4-(1+C_1)L\ge X^j/2\ge(X/2)^j=(Ar)^{-(k+1)}$.

## Lean correspondence

- `few_zeros` gives the small-disk count. [Count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DirichletLFewZerosSmallDisc.lean#L98)
- `power_sum_mult`, `power_sum_large` and `exists_large_derSeries` implement the padding, near and far comparison, and derivative conclusion. [Padding](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLargeVonMangoldtLogPowerSeriesNearZero.lean#L11) · [Power sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLargeVonMangoldtLogPowerSeriesNearZero.lean#L39) · [Derivative](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLargeVonMangoldtLogPowerSeriesNearZero.lean#L159)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
