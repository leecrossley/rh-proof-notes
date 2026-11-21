# Avoiding critical values gives nondegenerate common zeros

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%81%BF%E5%BC%80%E9%9B%B6%E6%B5%8B%E9%9B%86%E5%B0%B1%E8%83%BD%E5%BE%97%E5%88%B0%E9%9D%9E%E9%80%80%E5%8C%96%E7%9A%84%E5%85%B1%E5%90%8C%E9%9B%B6%E7%82%B9.md)

## Statement

Let $X$ be smooth of dimension $d$ over $\mathbb C$, $U\subseteq X$ affine, $A=\Gamma(U,\mathcal O_X)$, and $\phi_1,\ldots,\phi_d\in A$. There is a Lebesgue-null set $E\subseteq\mathbb C^d$ such that for every $c\notin E$ and every $y\in U(\mathbb C)$ with $\phi_j(y)+c_j=0$ for all $j$, the maximal ideal at $y$ satisfies
$$
\mathfrak m_y=(\phi_1+c_1,\ldots,\phi_d+c_d)+\mathfrak m_y^2.
$$
Thus the first jets are a basis. For $d=0$ take $E$ empty, with the empty determinant one.

## Proof

The map $F=(\phi_1,\ldots,\phi_d)$ is holomorphic on the complex manifold of points. The affine embedding gives second countability and hence a countable cover by analytic coordinate charts. In each chart, a complex kernel vector of the Jacobian is also a real kernel vector for the derivative of $-F$ as a map of real dimension $2d$. We need that the critical values of an equal-dimensional $C^1$ map have measure zero.

To see this directly for $G:O\subset\mathbb R^n\to\mathbb R^n$, restrict to critical points in a compact subset of $O$. The derivative is bounded and uniformly continuous on a slightly larger compact neighborhood. Cover by cubes of side $\delta$ and choose a critical point $x$ in each cube meeting the set. For any $\eta>0$ take $\delta$ small enough that $G(y)=G(x)+DG(x)(y-x)+r$ with $\|r\|\le\eta\sqrt n\,\delta$ for points $y$ of each selected cube, by integrating the derivative along segments. The linear image lies in a hyperplane with diameter $O(\delta)$, so each cube image is in a box with volume $O(\eta\delta^n)$. At most $O(\delta^{-n})$ cubes are needed. The constants can be fixed for $0<\eta\le1$. The image has outer measure at most $O(\eta)$, hence zero. Countable compact exhaustion proves the required critical-value statement.

Take $E$ as the countable union of these null sets for $-F$. If $F(y)=-c$ with $c\notin E$, the complex Jacobian is invertible at $y$. Therefore $d\phi_j(y)$ form a cotangent basis. At a smooth complex point analytic differentials identify the algebraic first jets, and shifting by $c_j$ leaves their differentials unchanged. This gives the displayed ideal identity. For the [projective fiber](prescribed-points-in-one-reduced-projective-fiber.md), apply it on $h\ne0$ with $\phi_j=g_j/h$, retaining the separate jets at the prescribed points.

## Lean correspondence

- [`countable_charts`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/AlgebraicSardShiftedFunctionsRegularZeros.lean#L22) and [`AlgSard.main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/AlgebraicSardShiftedFunctionsRegularZeros.lean#L49) assemble the chart argument.
- [`null_negEv_of_det_eq_zero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NullNegEvalOfJacobianDetEqZero.lean#L13) passes to the real critical-value theorem, proved in the needed case above. [`ker_evalComplexPoint_le_span_jacobian`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KerEvalComplexPointLeSpanJacobianStatement.lean#L11) gives cotangent generation.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
