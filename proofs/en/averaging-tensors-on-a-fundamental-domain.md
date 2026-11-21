# Averaging tensors on a fundamental domain

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9F%BA%E6%9C%AC%E5%9F%9F%E4%B8%8A%E7%9A%84%E5%BC%A0%E9%87%8F%E5%B9%B3%E5%9D%87%E8%83%BD%E5%BB%B6%E6%8B%93%E6%88%90%E4%B8%8D%E5%8F%98%E5%BD%A2%E5%BC%8F.md)

## Statement

Let $L$ be a number field, $N\ge1$, $j\ge0$, $G_\infty=\prod_w\mathrm{GL}_N(\mathbb C)$ and $S=\prod_w\mathrm{SL}_N(\mathbb C)$. The positive Hermitian cone $X$ uses $gI=(g^{-1})^*g^{-1}$. Let $D$ be a finite measure fundamental domain for $\Gamma_S=\mathrm{SL}_N(O_L)$ in $S$, with bi-invariant Haar measure $\mu$. If $\omega$ is a continuous $j$-form invariant under $\mathrm{GL}_N(O_L)$ and the full center, with tensor $F_\omega(s)=\omega_{sI}\circ s$ integrable on $D$, then a $G_\infty$-invariant form $\bar\omega$ satisfies
$$
F_{\bar\omega}(x)=\mu(D)^{-1}\int_D F_\omega(s)\,d\mu(s)\qquad(x\in G_\infty).
$$
Composition here applies the tangent map to every input. The Lean convention is $0^{-1}=0$ at measure zero. This is `SMean` in the [Hecke argument](hecke-iteration-represents-cycle-integrals-by-invariant-forms.md).

## Proof

Write $M$ for the average. The stabilizer at $I$ is $\prod_w U(N)$. For $u$ in it, divide $u_w$ by a unit-modulus $N$th root of its determinant to get $k\in S$ with the same tangent action. Then $F_\omega(s)\circ u=F_\omega(s)\circ k=F_\omega(sk)$ since $kI=I$. Right Haar invariance replaces the translated integral by the integral over $Dk$, which is also a fundamental domain because right translation commutes with the left $\Gamma_S$ action. The tensor is left $\Gamma_S$-invariant, so these integrals agree by partitioning one domain by its intersections with translates of the other and translating the pieces. Therefore $M\circ u=M$.

For $h=xI$, define $\bar\omega_h=M\circ x^{-1}$. Two choices of $x$ differ by right multiplication by a stabilizer element, so give the same form. Replacing $x$ by $gx$ shows invariance, and pulling back gives $M$ everywhere. It is smooth, for instance by the smooth local choice $x=h^{-1/2}$. See [closedness of invariant forms](matrix-traces-give-weights-to-cycle-values.md).

## Lean correspondence

- [`SMean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean#L131) and [`Dom`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ActLPos.lean#L157) specify the average and domain.
- [`mean_shift`, `mean_inv` and `sMean_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/MeanLatticeCounts/CountableLatS.lean) establish domain independence, stabilizer invariance, and extension.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
