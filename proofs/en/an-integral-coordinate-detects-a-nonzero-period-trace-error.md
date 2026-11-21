# An integral coordinate detects a nonzero period-trace error

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E6%95%B4%E6%95%B0%E5%9D%90%E6%A0%87%E6%A3%80%E6%B5%8B%E4%B8%80%E4%B8%AA%E9%9D%9E%E9%9B%B6%E7%9A%84%E5%91%A8%E6%9C%9F%E8%BF%B9%E8%AF%AF%E5%B7%AE.md)

## Statement

Let $K=\overline{\mathbb Q}_\ell$, $F\subset K$ containing $\mathbb Q_\ell$, and $x_i,z$ finitely many elements of norm at most one. There is an $F$-linear map $\lambda:K\to F$ such that $|\lambda(x_i)|_\ell\le1$ and $|z|_\ell\le|\lambda(z)|_\ell\le1$. For the [period-trace argument](arbitrarily-small-crystalline-trace-errors-vanish.md), $F$ is the maximal unramified extension.

## Proof

Inductively represent any such finite list using an independent family $e_j$ of norm at most one and all coordinates of norm at most one. Start empty. If a new $y$ lies outside the span, append it. Otherwise write $y=\sum_j a_je_j$. If all $a_j$ are integral, the basis already works. If not, choose a maximum-norm $a_{j_0}$ of norm greater than one and replace $e_{j_0}$ by $y$. Independence remains since this coefficient is nonzero. For an old input with coordinates $c_j$, its new coordinates are $c_{j_0}/a_{j_0}$ at that position and $c_j-c_{j_0}a_j/a_{j_0}$ elsewhere. These remain integral by the maximum property and ultrametric inequality. The new vector has one unit coordinate and the rest zero.

Do this for all $x_i,z$. If $z=0$ take the zero map. Otherwise choose a largest coordinate $z_{j_0}$ of $z$ and extend its coordinate functional from the span linearly to $K$. It is bounded by one on the specified inputs, and $|z|\le\max_j|z_j|=|\lambda(z)|$ because all basis vectors had norm at most one.

## Lean correspondence

- [`intBasis_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/IntBasis.lean#L184) changes basis at the largest coordinate.
- [`func_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/ClosedPhiFunctoriality/FuncHolds.lean#L10) extends the coordinate functional.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
