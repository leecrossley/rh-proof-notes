# Height from a lattice and its inverse transpose form

[Chinese proof](../zh/%E6%A0%BC%E4%B8%8E%E5%AF%B9%E5%81%B6%E6%A0%BC%E7%9A%84%E6%9C%80%E7%9F%AD%E5%90%91%E9%87%8F%E6%80%8E%E6%A0%B7%E5%AE%9A%E4%B9%89%E9%AB%98%E5%BA%A6.md)

## Statement

Let $L$ be totally imaginary, $R=O_L$, $N\ge1$, and $G_\infty=\prod_w\mathrm{GL}_N(\mathbb C)$. The embedded $R^N$ is a full real lattice $\Lambda$. For invertible matrices $B=(B_w)_w$ set
$$
m(B)=\inf_{0\ne y\in R^N}\sum_w\|B_w w(y)\|_2^2,\qquad
\mathrm{ht}(x)=\big(m(x^{-1})m(x^\mathsf{T})\big)^{-1}.
$$
The height is continuous, left $\mathrm{GL}_N(R)$-invariant, and has a uniform positive lower bound. For every compact $K\subset G_\infty$ there is $C_K$ with $\mathrm{ht}(xg)\le C_K\mathrm{ht}(x)$ for all $x$ and $g\in K$. This is `SHt`.

## Proof

The action sends $I$ to $(x^{-1})^*x^{-1}$, so the first minimum is its least squared length on the lattice. Its inverse transpose is $(x^\mathsf{T})^*x^\mathsf{T}$, giving the second minimum on the same lattice. Both are positive by discreteness. For $\gamma\in\mathrm{GL}_N(R)$ the two matrices become $x^{-1}\gamma^{-1}$ and $x^\mathsf{T}\gamma^\mathsf{T}$. The right factors permute nonzero lattice points, proving left invariance.

Write $n=[L:\mathbb Q]$, $r=r_2(L)$, $d=nN$, $D=|\operatorname{disc}L|$ and $I_0=D^Nd^d$. The [Hermitian lattice volume bound](hermitian-forms-bound-matrix-group-torsion.md) says $1\le I_0\prod_w\det h_w$ for minimum squared length at least one. Apply it to $B^*B/m(B)$ to get $m(B)^{Nr}\le I_0\prod_w|\det B_w|^2$. For $B=x^{-1},x^\mathsf T$, the determinant factors cancel, so the product of the two minima to power $Nr$ is at most $I_0^2$. This gives a uniform positive height lower bound.

Use operator norms maximized over places. The comparisons for every vector yield
$$
m(x^{-1})\le\|g\|_{\mathrm{op}}^2m((xg)^{-1}),\qquad
m(x^\mathsf T)\le\|(g^\mathsf T)^{-1}\|_{\mathrm{op}}^2m((xg)^\mathsf T).
$$
Thus $\mathrm{ht}(xg)\le B(g)\mathrm{ht}(x)$ with $B(g)=\|g\|_{\mathrm{op}}^2\|(g^\mathsf T)^{-1}\|_{\mathrm{op}}^2$. Similarly the lower bound is $\mathrm{ht}(x)/B(g^{-1})$. Since $B$ is continuous and $B(1)=1$, this proves continuity. Taking the supremum on a compact $K$ gives the other assertion.

## Lean correspondence

- [`ht`, `lam` and `dualH`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ActLPos.lean#L143) and [`ht_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeightContinuity/MatrixTupleDistortionPos.lean#L193) relate forms and minima.
- [Continuity, invariance and distortion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeightContinuity/ContinuousHt.lean#L127) use [`detlow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Detlow.lean#L36) for the lower bound. [`sHt_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeightContinuity/SHtOf.lean#L6) assembles them.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
