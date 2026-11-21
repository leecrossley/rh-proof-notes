# Operator power sums pass along the lattice tower

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%B2%BF%E9%80%BC%E8%BF%91%E6%A0%BC%E5%A1%94%E4%BC%A0%E9%80%92%E7%AE%97%E5%AD%90%E7%9A%84%E5%B9%82%E5%92%8C.md)

## Statement

Let $K$ be characteristic zero with a nonarchimedean norm $|\ell|=\ell^{-1}$. Fix a matrix $U$, vector $v$, and row $t$ with $tv=a$ for integer $a\ge1$. For every $N\ge0$ suppose there are layer matrices and vectors $U',P,v',t'_k$ of compatible sizes, coefficients $c_k$, and $T'=\sum_k c_kt'_k$. In entry maximum norm assume a uniform $B\ge1$ with $\|U\|,\|U'\|\le B$, $\|v'\|\le1$, and
$$
\|v-Pv'\|\le\ell^{-N},\quad
\|UP-PU'\|\le B\ell^{-N},\quad
\|tP-T'\|\le\ell^{-N}.
$$
Suppose fixed $S_n\in K$, $S_0=a$, satisfy $t'_k(U')^n v'=S_n$ for every layer, seed and $n\ge0$. Then $tU^n v=S_n$ for every $n\ge0$. This is `trace_pow_eq`.

## Proof

The ultrametric inequality gives $\|AB\|\le\|A\|\|B\|$ independently of dimensions. The identity
$$
U^{n+1}P-P(U')^{n+1}=U(U^nP-P(U')^n)+(UP-PU')(U')^n
$$
gives $\|U^nP-P(U')^n\|\le B^{n+1}\ell^{-N}$ by induction. For $\tau=\|t\|$, compare $tU^n v$ with $T'(U')^n v'$ by splitting the difference as
$$
tU^n(v-Pv')+t(U^nP-P(U')^n)v'+(tP-T')(U')^n v'.
$$
The bound is $K_n\ell^{-N}$ with $K_n=B^n(\tau+B\tau+1)$, uniformly in layer dimension. The seed values give $T'(U')^nv'=C_NS_n$ for $C_N=\sum_k c_k$. At $n=0$ the comparison gives $|1-C_N||a|\le K_0\ell^{-N}$. Since $a\ne0$,
$$
|tU^nv-S_n|\le(K_n+K_0|S_n|/|a|)\ell^{-N}.
$$
For fixed $n$ send $N\to\infty$.

## Recovering the weights

In `closed_of_cover` the target period basis and the layer bases supply the matrices and comparisons at an embedding. At a nonzero cyclotomic value $z$ of infinite multiplicative order, the common seed weight multiset $J$ gives $S_n=\sum_{h\in J}(z^h)^n$. The target basis gives $tU^nv$ by the same formula for its multiset $J'$. The established equalities for $n=0,\ldots,s-1$, where $h_1,\ldots,h_s$ are the distinct weights in the union, form a Vandermonde system on the multiplicity differences at the distinct $z^{h_i}$. Its nonzero determinant gives $J=J'$. The period bases, bounds and choice of $z$ are inputs in this application.

## Lean correspondence

- [`norm_comm_pow_le` and `core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TracePowEqAlongLatticeTowerCover.lean#L46) give the power comparison. [`trace_pow_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TracePowEqAlongLatticeTowerCover.lean#L145) normalizes by $n=0$.
- [`closed_of_cover`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ClosedOfCover.lean) gives the period applications. [Identification by power sums](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MultisetEqOfPowerSumsZpowEq.lean) uses independence of distinct characters, expressed as a Vandermonde calculation above.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
