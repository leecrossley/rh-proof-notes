# Checking cyclotomic expansion lattices degree by degree

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%B1%95%E5%BC%80%E6%A0%BC%E5%8F%AF%E4%BB%A5%E9%80%90%E4%B8%AA%E6%AC%A1%E6%95%B0%E6%A3%80%E6%9F%A5.md)

Let $V$ be a finite-dimensional vector space over a field $L$, and $\Lambda\subset V((t))$ an $L[[t]]$-submodule of the Laurent series bounded below in degree. Assume $t^mV[[t]]\subset\Lambda$ for some integer $m$, and that $\Lambda$ is stable under $\gamma$ acting in degree $k$ by $u^k$, with $u\in L^\times$ of infinite order. Then for each $f=\sum_k d_kt^k$ in $V((t))$,
$$
f\in\Lambda\quad\Longleftrightarrow\quad d_kt^k\in\Lambda\quad\text{for every }k .
$$

**Proof.** Split $f$ into its finite part below degree $m$ and its tail. The tail always belongs to $\Lambda$. If $f\in\Lambda$, its finite part $f_{<m}$ does too. Let $I$ be its finite support. For $b\in I$ the polynomial
$$
P_b(T)=\prod_{k\in I,\ k\ne b}\frac{T-u^k}{u^b-u^k}
$$
is well defined by the infinite order assumption. Then $P_b(\gamma)f_{<m}=d_bt^b$ belongs to $\Lambda$ by stability. The other degrees are either zero or already belong to the tail. Conversely, add the finitely many low-degree monomials and the single tail, all of which belong to $\Lambda$.

In the Wach setting the expansion matrix of a basis has nonzero Laurent determinant. Its inverse has a common finite pole bound $m$ on its entries; hence $t^mV[[t]]$ belongs to the span. The formal proof uses the adjugate and obtains the nonzero determinant from the full-rank de Rham comparison. An identically zero determinant would map to zero under the coefficient comparison. [`full_of_det`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachExpansionsSpanFullLattice.lean#L38) · [`full_lat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachExpansionsSpanFullLattice.lean#L245)

The cyclotomic operator fixes the chosen root and substitutes $t\mapsto ut$, which also preserves $L[[t]]$-linear generation. Here $u=1+\ell^sv$ for a unit $v$, with $s\ge2$ when $\ell=2$; the valuation formula for $u^k-1$ ensures it is nonzero for $k\ne0$. The finite projection argument is `graded_of_full` and stability of the span is `latSpan_stable`. The application in `lat_eq_fil` combines this with [the de Rham criterion for monomials](de-rham-filtration-determines-each-expansion-monomial.md). [Projection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachExpansionLatticeGradedOfLevelLe.lean#L131) · [Stability](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachExpansionLatticeGradedOfLevelLe.lean#L186) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L423)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
