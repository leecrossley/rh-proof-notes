# Homogeneous forms interpolate first jets at finitely many points

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E9%BD%90%E6%AC%A1%E5%BC%8F%E5%90%8C%E6%97%B6%E6%8F%92%E5%80%BC%E6%9C%89%E9%99%90%E7%82%B9%E7%9A%84%E4%B8%80%E9%98%B6%E6%95%B0%E6%8D%AE.md)

## Statement

Let $X\hookrightarrow\mathbb P^N_{\mathbb C}$ be integral smooth of dimension $d$ and $S\subset X(\mathbb C)$ finite. Put $m=|S|+1$ and $n=2m$. There are homogeneous degree-$n$ forms $h,g_1,\ldots,g_d$ with each $g_j$ generically nonzero and zero on $S$, all common zeros belonging to $S$, and at each $y\in S$ the following properties. For any degree-$n$ form $a$ nonzero at $y$, $h/a$ belongs to $\mathfrak m_y^2$ and the first jets of $g_j/a$ form a basis of $\mathfrak m_y/\mathfrak m_y^2$. This supplies the interpolation in [the prescribed reduced fiber](prescribed-points-in-one-reduced-projective-fiber.md).

## Separating points and jets

For any scheme point $z\notin S$ and each $y\in S$, choose a linear form vanishing at $y$ with nonzero value at $z$. Such a form exists because the linear equations of the closed point $y$ cut out just $y$. Multiply and pad the degree by a nonvanishing linear form at $z$ to obtain degree $m$ vanishing on $S$ and nonzero at $z$. Its square also separates at degree $n$.

For $y\in S$ choose a linear form $a_0$ nonzero throughout $S$ by avoiding a finite union of proper subspaces. On this chart the coordinate differences span the cotangent space of $X$ by closed immersion. So any first jet at $y$ is that of $\ell/a_0$ with $\ell(y)=0$ linear. Choose $p_y$ of degree $n-1$ vanishing on $S\setminus\{y\}$ and nonzero at $y$ by the separating construction. The form $\ell p_y$ has the required first jet after rescaling, because $\ell p_y/a_0^n=(\ell/a_0)(p_y/a_0^{n-1})$ multiplies the jet by the nonzero second value. Thus the space $V_n$ of degree-$n$ forms vanishing on $S$ maps onto each cotangent space. Changing the local trivialization only rescales the jets there.

## Choosing all $g_j$ and $h$

Induct on $k$ with $g_1,\ldots,g_k$ generically nonzero, independent first jets at each $y\in S$, and common zeros outside $S$ of codimension at least $k$. Start with $k=0$. If $k<d$, require $g_{k+1}$ to be nonzero at the generic point of $X$ and of each component of the old zero locus whose generic point is outside $S$. These are finitely many proper-subspace exclusions by separation. At each $y\in S$, require its jet outside the span of the first $k$, which also excludes a proper subspace by surjectivity. Choose a form outside the finite union. A new zero outside $S$ must be a strict specialization from one of the old components' generic points, increasing codimension by at least one.

At $k=d$ the extra zeros are finitely many closed points, all on zero-dimensional components. Choose a degree-$m$ form $p$ vanishing on $S$ and nonzero at all extra points by the same separation and finite-union argument. With $h=p^2$ all conditions hold, including the basis condition by dimension. For $d=0$ there are no $g_j$ and the last selection applies directly.

## Lean correspondence

- [`exists_sep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFormsVanishingComplexPointsFullJets.lean#L233) and [`exists_form_jet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFormsVanishingComplexPointsFullJets.lean#L318) give separating forms and prescribed jets.
- [`exists_jet_forms`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFormsVanishingComplexPointsFullJets.lean#L440) uses specialization chains for codimension and the square to remove extra points.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
