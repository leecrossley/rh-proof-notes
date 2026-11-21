# Lattice isomorphisms with prescribed determinant

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%BB%99%E6%A0%BC%E5%90%8C%E6%9E%84%E6%8C%87%E5%AE%9A%E8%A1%8C%E5%88%97%E5%BC%8F.md)

## Statement

Let $F$ be a number field with $R=O_F$, $J$ a finite set, and $A_j,B_j$ integral finitely supported divisors. Put $I(D)=\prod_\mathfrak p\mathfrak p^{D_\mathfrak p}$, a fractional ideal. Suppose $\beta\in F^\times$ with $\mathrm{div}(\beta)=\sum_j(B_j-A_j)$, with $\beta=1$ required when $J$ is empty. Then some $g\in\mathrm{GL}(F^J)$ has
$$
\det g=\beta,\qquad
g\big(\bigoplus_j I(A_j)\big)=\bigoplus_j I(B_j).
$$
This is `SStein`, used to set determinants of blocks in the [global cycle](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E6%89%AD%E6%9B%B2%E4%B8%BB%E5%9B%A0%E5%AD%90%E5%8F%98%E6%88%90%E4%B8%80%E4%B8%AA%E5%85%A8%E5%B1%80%E5%91%A8%E6%9C%9F.md).

## A two-coordinate move

For any nonzero fractional ideals $C,D$ choose $p\in C\setminus\{0\}$ and $q\in D$ whose images in $D/\mathfrak pD$ are nonzero for all prime divisors $\mathfrak p$ of $pC^{-1}$. Such a $q$ exists by the Chinese remainder theorem, since each quotient is one-dimensional over $R/\mathfrak p$. Then the integral ideals $pC^{-1},qD^{-1}$ are coprime, so $ps-qr=1$ for some $s\in C^{-1}$ and $r\in D^{-1}$.

To add divisor $D_0$ to position $i$ and subtract it from position $j\ne i$, take $C=I(D_0)$ and $D=I(A_i+D_0-A_j)$. Apply $\begin{pmatrix}p&q\\r&s\end{pmatrix}$ in those positions and the identity elsewhere. The first output lies in $I(A_i+D_0)$ and the second in $I(A_j-D_0)$ by adding the input ideal exponents to those of the entries. The inverse $\begin{pmatrix}s&-q\\-r&p\end{pmatrix}$ has the reverse inclusions by the same computation, so this carries the source onto the target lattice with determinant one.

## Assembling the isomorphism

If $J$ is nonempty, fix $j_0$ and multiply that coordinate by $\beta$. This adds $\mathrm{div}(\beta)$ and makes the total divisor equal to the target total. For each $i\ne j_0$ use the two-coordinate move with $D_0$ the required change at $i$, taking the opposite change at $j_0$. This preserves the total and all already completed coordinates. The last coordinate then agrees by equality of totals. The composition has determinant $\beta$. In dimension zero the identity has determinant one.

## Lean correspondence

- [`SStein`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L79), with [`val_eq_count` and `exists_frac`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SSteinTPf.lean#L17), gives the valuation statement.
- [`exists_sl2_with_valuation_bounds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SSteinTPf.lean#L47) and [`rel_move`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SSteinTPf.lean#L125) give the move. [The assembly](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SSteinTPf.lean#L164) is used through [the final interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/FinSStein.lean#L6).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
