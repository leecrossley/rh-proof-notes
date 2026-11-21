# Three projections give the two-fifths angle bound

[Chinese proof](../zh/%E4%B8%89%E4%B8%AA%E5%AD%90%E7%A9%BA%E9%97%B4%E7%9A%84%E6%8A%95%E5%BD%B1%E6%80%8E%E6%A0%B7%E7%BB%99%E5%87%BA%E4%BA%94%E5%88%86%E4%B9%8B%E4%BA%8C.md)

## Statement

Let $W_1,W_2,W_3$ be closed subspaces of a real Hilbert space. For each $(i,j)=(1,2),(3,1),(3,2)$ assume a closed $K_{ij}\subseteq W_i\cap W_j$ with $|\langle u,u'\rangle|\le\|u\|\|u'\|/5$ for $u\in W_i\cap K_{ij}^\perp$ and $u'\in W_j$. Put $W=W_1\cap W_2\cap W_3$. Then for $v\in W_1\cap W_2\cap W^\perp$ and $w\in W_1\cap W_3$,
$$
|\langle v,w\rangle|\le\tfrac25\|v\|\|w\|.
$$
This is `Hilb`. The pair estimates come from the [finite correlation bound](two-double-cosets-bound-correlation-by-one-fifth.md).

## Pair and triple projection errors

Let $P_i$ project onto $W_i$ and $Q_i=I-P_i$. For a pair and $x\perp K_{ij}$, set $a=P_i x,b=P_j x$, and $s=\|a\|^2+\|b\|^2$. Then $a\perp K_{ij}$, so the angle bound and $2\|a\|\|b\|\le s$ give $\|a+b\|^2\le6s/5$. Since $\langle x,a+b\rangle=s$, this gives $s\le6\|x\|^2/5$. Therefore $U=\|Q_ix\|^2+\|Q_jx\|^2\ge4\|x\|^2/5$. Also $\langle(Q_i+Q_j)x,x\rangle=U$, so $\|(Q_i+Q_j)x\|^2\ge4U/5$. This last estimate holds for every $x$ by subtracting its projection to $K_{ij}$.

Put $D=Q_1+Q_2+Q_3$. It is self-adjoint and positive, and $\ker D=W$ since $\langle Dx,x\rangle=\sum_i\|Q_ix\|^2$. Summing the pair bounds gives
$$
\|Dx\|^2=\sum_{i<j}\|(Q_i+Q_j)x\|^2-\sum_i\|Q_ix\|^2
\ge\tfrac35\langle Dx,x\rangle.
$$
The positive form $\langle Dx,y\rangle$ satisfies Cauchy–Schwarz by the discriminant of $\langle D(x+ty),x+ty\rangle$. For $y=Dx$, this gives $\|y\|^4\le(5/3)\|y\|^2\langle Dy,y\rangle$. Hence $\langle Dy,y\rangle\ge3\|y\|^2/5$ on $\operatorname{im}D$, and by continuity on its closure $W^\perp$.

## Comparing the two vectors

Subtract the projection of $w$ to $W$, preserving the inner product and decreasing its possible norm. For nonzero vectors normalize both and choose a sign with $t=\langle v,w\rangle\ge0$. On $x=v+w$ the first error $Q_1x$ is zero, $Q_2x=Q_2w$, and $Q_3x=Q_3v$. Since $v\in W_2,w\in W_3$, both $\|P_2w\|$ and $\|P_3v\|$ are at least $t$. The preceding lower bound and orthogonality give
$$
\tfrac35(2+2t)\le\|Q_2w\|^2+\|Q_3v\|^2\le2-2t^2 .
$$
This is $2(t+1)(2/5-t)\ge0$, so $t\le2/5$. Restore the original norms.

## Lean correspondence

- [`Hilb`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/AEConst.lean#L20) and [`pair_pos`, `pair_all`, `range_bound`, `closure_bound`, `upper` and `hilb_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/ClosureBound.lean) give the whole comparison.
- [`PGapAbs`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PGapAbs.lean) applies the result with the pair estimates from [`PGapAng`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PGapAng.lean).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
