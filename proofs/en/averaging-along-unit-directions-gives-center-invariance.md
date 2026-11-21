# Averaging along unit directions gives center invariance

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%B2%BF%E5%8D%95%E4%BD%8D%E6%96%B9%E5%90%91%E5%B9%B3%E5%9D%87%E5%87%BA%E4%B8%AD%E5%BF%83%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)

## Statement

Let $L$ be a number field, $N,j\ge1$, $\Gamma=\mathrm{GL}_N(O_L)$ and $G_\infty=\prod_w\mathrm{GL}_N(\mathbb C)$. Suppose $\omega$ is a continuous $j$-form on the positive Hermitian cone $X$ whose integration cochain on tuples of vertices of $X$ is closed. Assume invariance under $\Gamma$ and central scalars with equal absolute values at all places. For the pulled-back tensor $F_\omega(x)$ at $I$, suppose $\|F_\omega(x)\|\le B(x)$ with $B(xg)\le C_KB(x)$ uniformly for $g$ in each compact $K\subset G_\infty$. Then a continuous form $\omega'$ has closed integration cochain, is invariant under $\Gamma$ and the full center, agrees on every $\Gamma$-cycle with $\omega$, and satisfies $\|F_{\omega'}(x)\|\le CB(x)$. This is `SCen` in [Hecke reconstruction](hecke-iteration-represents-cycle-integrals-by-invariant-forms.md).

## Turning integer periods into real directions

For $v\in\mathbb R^{\{w\}}$, let $s(v)$ be the scalars $e^{v_w}$ at the places. A unit $u\in O_L^\times$ gives $\ell(u)=(\log|w(u)|)_w$, with $s(\ell(u))$ acting on forms like $uI_N$ because phases cancel in congruence. The form is invariant under these scalars and all $s(t\mathbf1)$. For a form $\eta$ invariant under $s(v)$, set
$$
\operatorname{Av}_v\eta=\int_0^1 s(tv)^*\eta\,dt.
$$
The integral of tensor evaluations depends continuously on the point, by continuity on compact parameter intervals. Pullback by $s(\tau v)$ shifts the parameter of a period-one integrand, preserving the integral. All other previous center invariances and arithmetic invariance persist by commutation. The unit logarithms span the weighted sum-zero hyperplane, with weights one at real and two at complex places, by Dirichlet's unit theorem. Choose a finite spanning set and average in these directions, which with $\mathbf1$ span the full space. Phases act trivially, so this gives full center invariance.

## Retaining periods and bounds

The effect of a central pullback on a simplex with vertices $\gamma_i I$ is to replace the base point $I$ by $s(tv)I$ because the actions commute. The equivariant prism connects the two choices. Closedness of the integration cochain gives equal values on cycles. Each pullback also has closed integration cochain, as does the average. Continuity on compact simplices and the parameter interval gives the interchange of integrals. Thus each averaging step preserves all cycle values.

For the growth bound, the pulled-back tensor of the average is $\int_0^1 F_\eta(s(tv)x)\,dt$. If $\eta$ obeys $C_0B(x)$, the center commutes, so the bound for $s(tv)x=x s(tv)$ is at most $C_0C_K B(x)$ for the compact parameter set $K$. The finite sequence of averages multiplies finitely many constants. This gives the asserted form and growth bound.

## Lean correspondence

- [`SCen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean#L104) and [`TSpan`, `TScal` and `TAv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CentralPositiveSemidefinite/TSpan.lean) specify the construction.
- [`span_units`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CentralPositiveSemidefinite/LamSApply.lean#L65), [`tAv_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CentralPositiveSemidefinite/ContinuousOnPullbackCentralScalingSimplexParam.lean#L213), and [`join`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CentralPositiveSemidefinite/AvCongr.lean#L193) give the directions, averaging and iteration. [`sCen_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/CentralPositiveSemidefinite/SCenOf.lean) assembles the result.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
