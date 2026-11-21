# Two double cosets bound correlation by one fifth

[Chinese proof](../zh/%E4%B8%A4%E7%B1%BB%E9%99%AA%E9%9B%86%E6%80%8E%E6%A0%B7%E6%8A%8A%E7%9B%B8%E5%85%B3%E6%80%A7%E5%8E%8B%E5%88%B0%E4%BA%94%E5%88%86%E4%B9%8B%E4%B8%80.md)

## Statement

Let $G$ be finite, $E,E'\le G$, with $G\setminus E$ empty or one $E$ double coset. Let $f,g:G\to\mathbb R$ be left invariant under $E,E'$, respectively, with $\sum_xf(x)=0$. Then
$$
[E':E\cap E']\left|\sum_x f(x)g(x)\right|^2
\le\left(\sum_x f(x)^2\right)\left(\sum_x g(x)^2\right).
$$
Thus index at least $25$ gives an angle bound $1/5$ between the normalized functions. This is the finite-group estimate in `PDesign.core`.

## The correlation estimate

Take $C(a)=\sum_x f(ax)f(x)$. On $E$ it equals $\|f\|_2^2$. It is constant on $E$ double cosets by left invariance and change of variables, and $\sum_a C(a)=(\sum_x f(x))^2=0$. Thus $C$ is nonpositive outside $E$. If the outside is empty then $f=0$. Set $F(x)=\sum_{a\in E'}f(ax)$. By $E'$-invariance of $g$, $\sum_x F(x)g(x)=|E'|\sum_x f(x)g(x)$. Expanding the square and substituting $bx$ gives
$$
\sum_xF(x)^2=|E'|\sum_{a\in E'}C(a)
\le |E'||E\cap E'|\|f\|_2^2.
$$
Apply Cauchy–Schwarz to the sum against $g$ and divide by the positive orders.

## Finite-index averaging and $L^2$

In `Design` take subgroups $E,E'$ of $K$ with $B=E\cap E'$ finite index, $K\setminus E$ at most one double coset, and $[E':B]\ge25$. For each $x$ apply the finite result to $f(k)=a(kx)$ and $g(k)=b(kx)$, where $a,b$ are invariant under the indicated subgroups and the $B\backslash K$ average of $a(kx)$ is zero. They descend to the finite quotient by the core of $B$, the kernel of the action on cosets. Its fibers over $B\backslash K$ have equal size. Thus pointwise
$$
|\operatorname{Avg}_{B\backslash K}(ab)(x)|
\le\tfrac15\sqrt{\operatorname{Avg}_{B\backslash K}(a^2)(x)}
             \sqrt{\operatorname{Avg}_{B\backslash K}(b^2)(x)} .
$$
For left multiplication with Haar measure, let $D_B,D_K$ be fundamental domains. Unfolding the domain expresses an integral on $D_B$ as $[K:B]$ times the integral of the average on $D_K$. Cauchy–Schwarz on $D_K$ now gives $|\langle a,b\rangle_{D_B}|\le\|a\|_{D_B}\|b\|_{D_B}/5$.

For $B\le H\le K$, the projection to $H$-invariant classes in $L^2(D_B)$ is the finite coset average. It has that invariant image, fixes it, and preserves pairing with every invariant class by unfolding, so is orthogonal. For an $E$-invariant class orthogonal to the $K$-invariants, take an invariant representative and subtract its pointwise $K$-average, which is zero as a class. Now apply the estimate to any $E'$-invariant class. This gives the hypothesis of the [three-subspace angle bound](three-projections-yield-the-two-fifths-angle.md).

## Lean correspondence

- [`Design` and `Unfold`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/AEConst.lean#L29) specify the finite-index setting. [`core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PDesign.lean#L25) and [`design_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PDesign.lean#L237) prove the finite estimate and descent.
- [`core` and `angle`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ArithmeticGapBounds/PGapAng.lean#L41) pass from pointwise averaging to the Hilbert space estimate.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
