# Counting zeros with multiplicity using unit-height cells

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%B1%E5%8D%95%E4%BD%8D%E9%AB%98%E5%BA%A6%E6%A0%BC%E5%AD%90%E6%95%B0%E5%87%BA%E5%B8%A6%E9%87%8D%E6%95%B0%E7%9A%84%E9%9B%B6%E7%82%B9.md)

**Proposition.** There are absolute constants $C_0,C_1>0$ with the following property. For any real $Q\ge3$, let $\mathcal T$ be a finite set of triples $(q,\chi,\rho)$ with $q$ a positive integer at most $Q$, $\chi$ primitive modulo $q$, and
$$
L(\rho,\chi)=0,\qquad 1-1/400\le\Re\rho,\qquad |\Im\rho|\le Q.
\tag{1}
$$
The number of occupied cells $(q,\chi,\lfloor\Im\rho\rfloor)$ is at most $C_0Q^{1/8}$. In addition,
$$
\sum_{(q,\chi,\rho)\in\mathcal T}\operatorname{ord}_{\rho} L(\cdot,\chi)
\le C_1Q^{1/4}.
$$
The order is the analytic order of vanishing. A primitive principal character has modulus $1$ and yields $\zeta$. By the nonvanishing input on $\Re s\ge1$, all the zeros here have $\Re\rho<1$. In Mathlib the total-function value at the pole of $\zeta$ is nonzero as well. [Mathlib nonvanishing](https://github.com/leanprover-community/mathlib4/blob/0df444a360eaa60ab8c11dca51a86af692955474/Mathlib/NumberTheory/LSeries/Nonvanishing.lean)

## The occupied cells

Let $P=\max(Q_{\rm D},Q_\zeta,\lceil Q\rceil)$, where the first two integers are the absolute thresholds in the [Dirichlet and zeta detectors](mobius-truncation-detecting-zeros.md). Then $P\ge3$ and $P\ll Q$. The modulus-$1$ cells with a point $|\Im\rho|<P^{1/20}$ have indices in $[-\lceil P^{1/20}\rceil,\lceil P^{1/20}\rceil]$, so they number at most $5P^{1/8}$.

Every other point has a nonprincipal primitive character or comes from a zeta zero with $|\Im\rho|\ge P^{1/20}$. The corresponding detector in either case gives
$$
\left|
\sum_{P^3<n\le P^6}
\left(\sum_{d\mid n,\ d\le P^3}\mu(d)\right)\chi(n)n^{-\rho}
\right|\ge\tfrac12.
\tag{2}
$$
Select one remaining point in each occupied cell, splitting the representatives by the parity of $j=\lfloor\Im\rho\rfloor$. Two different cells for the same $(q,\chi)$ of the same parity have indices $j<k$ with $k\ge j+2$. Their heights differ by more than $1$ since the lower one is below $j+1$ and the upper one is at least $k$. Thus each parity class meets the hypotheses of the [hybrid large-sieve count](hybrid-sieve-count-of-separated-detections.md) for points satisfying (2). Each class contributes at most $C_{\rm s} P^{1/8}$ cells. Including the low-height zeta cells gives $(2C_{\rm s}+5)P^{1/8}=O(Q^{1/8})$.

## Multiplicities within a cell

For every $q\ge1$, primitive $\chi\bmod q$, and real $t$, the zeros with $0<\Re\rho<1$ and $|\Im\rho-t|\le1$ have total multiplicity at most $C_{\rm w}\log(q(|t|+2))$. Indeed, they lie at distance at most $3$ from $2+it$ and hence in the radius-$7/2$ disk in the [local log-derivative proof](local-log-derivative-from-disk-zeros.md). The center is in the Euler half-plane, so the disk count applies there. Use the Dirichlet disk for nonprincipal $\chi$ and the pole-removed zeta disk for $q=1$.

In a cell $(q,\chi,j)$ the bound with $t=j$ applies because all heights belong to $[j,j+1)$ and (1) puts the real parts in $(0,1)$. Using $|j|\le Q+1$ yields $q(|j|+2)\le Q(Q+3)\le Q^3$. Hence the cell weight is at most $3C_{\rm w}\log Q\le24C_{\rm w}Q^{1/8}$, where the last step uses $\log u\le u-1$ at $u=Q^{1/8}$. Multiply by the occupied-cell count to get $O(Q^{1/4})$. Keeping the logarithm separately gives $O(Q^{1/8}\log Q)$. Keeping the sharper separated-point exponent $3/40$ as well gives $O(Q^{3/40}\log Q)$, which also absorbs the $O(Q^{1/20})$ low-height cell count.

## Lean correspondence

- `one_le_abs_sub_of_floor` gives the separation and `exists_subset_injOn_card_image` selects the representatives for `ncard_cells_le`. [Separation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NcardUnitCellsDirichletLZerosNearOneLe.lean#L10) · [Selection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NcardUnitCellsDirichletLZerosNearOneLe.lean#L35) · [Cell count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NcardUnitCellsDirichletLZerosNearOneLe.lean#L60) · [Forwarding theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/NcardUnitCellsDirichletLZerosNearOneLeStatement.lean#L6)
- `zero_detect`, `zeta_zero_detect` and `card_spaced_detected_le` provide (2) and the separated-point count. [Dirichlet detector](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SumTruncConv.lean#L108) · [Zeta detector](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ZetaZeroDetect.lean#L38) · [Separated count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CardSpacedDetectedLe.lean#L225)
- `count_zeros_window` provides the cell weight, which `zero_density_mult` sums using `re_lt_one_of_zero`. The result is included in `density_and_regions` for bounding bad characters. [Window count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FinsumMemLeOfSubset.lean#L43) · [Sum](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ReLtOneOfZero.lean#L37) · [Package](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DensityAndRegions.lean#L10)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
