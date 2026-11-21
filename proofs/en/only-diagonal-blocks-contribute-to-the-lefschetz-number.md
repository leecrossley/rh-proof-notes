# Only diagonal blocks contribute to the Lefschetz number

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9D%97%E5%90%8E%E5%8F%AA%E9%9C%80%E5%AF%B9%E8%A7%92%E5%9D%97%E7%9A%84Lefschetz%E6%95%B0.md)

## Statement

Let $Z$ be smooth projective over $\mathbb C$, pure of dimension $d$, and $c_1,c_2:Y\to Z$ finite étale. Suppose $F=\{y\in Y(\mathbb C):c_1(y)=c_2(y)\}$ is finite and for $z=c_1(y)=c_2(y)$, the matrix $A_y$ of $dc_2(y)\circ dc_1(y)^{-1}$ obeys $\det(I-A_y)\ne0$. In `IsTan`, local coordinates $t_l$ at $z$ give the cotangent basis $d(c_1^*t_l)$ at $y$. Row $j$ expresses $d(c_2^*t_j)$ in this basis. For $a\ge0$ define $H^{a,b}(Z)=H^b(Z,\Omega_Z^a)$. These spaces have finite dimension and with the trace $c_{1*}$ and pullback $c_2^*$,
$$
\sum_{b=0}^{d}(-1)^b\operatorname{tr}(c_{1*}c_2^*:H^{a,b}(Z)\to H^{a,b}(Z))
=\sum_{y\in F}\frac{[T^a]\det(I+TA_y)}{\det(I-A_y)}.
$$
Here the upstream theorem assumes both schemes integral, with the same smoothness, projection, fixed-point and determinant hypotheses. [Integral finite étale Lefschetz theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/HolomorphicLefschetzFiniteEtaleIntegral.lean#L74)

## Proof

Smooth schemes have regular local rings and thus local domains. Distinct irreducible components cannot meet, since at an intersection the local ring would have several minimal primes. Here quasi-compactness and Noetherianity give finitely many components, each open and closed and integral. This applies to $Z$ and to $Y$, which is smooth by étaleness and quasi-compact by finiteness. Write $Z=\coprod_j Z_j$ and $Y_{jk}=c_1^{-1}(Z_j)\cap c_2^{-1}(Z_k)$. The two restricted maps to $Z_j,Z_k$ are still finite étale.

Differentials and their cohomology split over a finite open-and-closed union. In this decomposition the $(j,k)$ block is pullback to $Y_{jk}$ followed by the trace to $Z_j$. Trace adds over open-and-closed source pieces because multiplication on a finite algebra product splits into blocks, whose traces add on affines and hence on cohomology. A linear trace on $H^{a,b}(Z)$ is the sum of the diagonal block traces. Decompose each $Y_{jj}$ into its integral components and apply the integral theorem to each with target $Z_j$. A fixed point lies in just one $Y_{jj}$ and one integral component. Open restriction leaves its tangent maps unchanged. Summing the formulas gives the two sides asserted. Smooth projective cohomology is finite dimensional on each target component even if the source is empty. For $a>d$ both sides vanish by degree.

## Lean correspondence

- [`IsTan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Divisors/IsGaloisCover.lean#L14) gives the coordinates. [Integral open-and-closed decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/ExistsIntegralClopenDecompositionOfSmooth.lean#L7) gives the components.
- [`holomorphic_lefschetz_finiteEtale_correspondence`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/HolomorphicLefschetzFiniteEtaleCorrespondence.lean#L43) decomposes the source. [`lefschetz_fixedPoint_finite_etale_correspondence`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/LefschetzFixedPointFiniteEtaleCorrespondence.lean#L255) decomposes the target and sums diagonal traces.
- [`geoOne_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/GeometricFlagBases/WeightOneGeometricRealization.lean#L11) uses the formula in weight one.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
