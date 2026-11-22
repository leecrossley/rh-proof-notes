# Coefficient kernel bounds pass to all word-prime points

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a true adjacent step $i\to i+1$ and a place $w$ over its word prime $T$. Suppose the point models at both layers are realized by the arithmetic charts with the following data. Every point can be written $g_\zeta P_{b,d}$ for a representative $P_{b,d}$ attached to a class $b$ and a decorated lattice $d$, where $\zeta$ is a root of unity in the coefficient field. The ordinary point value lattice at a representative is the embedded arithmetic lattice on $L^\sharp$. On the selected side the point value lattice with all kernel conditions at a target representative is the embedded arithmetic lattice on $L'$. These identifications and covariance under the actions $g_\zeta$ are the value-chart hypotheses. Assume the point entry $\mathcal K(P,P')$ equals the embedded arithmetic coefficient kernel entry at representatives, is contravariant in source moves and covariant in target moves, and is linear in the input value. If the coefficient kernels satisfy [the two local bounds](the-two-split-sides-give-the-word-prime-kernel-bounds.md), the same bounds hold for the point kernel on every point pair.

More precisely, with $B_i(w,V,P)$ denoting the value lattice with kernel conditions at $V$, $P,P'$ arbitrary, and $Y\in B_i(w,\varnothing,P)$, the bounds are
$$
\begin{aligned}
T^{fN_i+\sum_\tau s_{i,\tau}}\mathcal K(P,P')Y
    &\in B_{i+1}(w,V_{\rm all},P') &\quad&\text{on the selected side},\\
\mathcal K(P,P')Y
    &\in T^{f(t+1)/2}B_{i+1}(w,\varnothing,P') &&\text{on the conjugate side}.
\end{aligned}
$$
The powers of $T$ act through the coefficient-field embedding in the point model. Here $s_{i,\tau}$ is the degree correction, equal to the negative target determinant shift, $N_i$ is the source rank, $f$ counts the embeddings, and the adjacent ranks differ by $t+1$.

Write $P=g_\zeta P_0$ and $P'=g_{\zeta'}P'_0$. Undo the source move by putting $Y_0=g_\zeta^{-1}Y$ in the value representation. It lies in the ordinary lattice at $P_0$ by the value-chart hypothesis. On the conjugate side the source formalization uses the additional description that the torsion move leaves the coordinates of the point lattice unchanged and acts on its represented values by a power of the root of unity. Each such power is a unit in every finite valuation ring, since both it and its inverse are algebraic integers. Thus it preserves the lattice. Choose a localized coefficient vector $F$ mapping to $Y_0$, using the ordinary value-lattice identification at $P_0$.

Apply the coefficient bounds to $F$. On the selected side, the scaled coefficient value belongs to the target lattice on $L'$. Its embedding therefore belongs to $B_{i+1}(w,V_{\rm all},P'_0)$. On the conjugate side the entry is $T^{f(t+1)/2}$ times an integral coefficient vector at $P'_0$, whose image is an ordinary integral point value there. The entry identification carries these assertions to the point kernel for $(P_0,P'_0)$; it commutes with the powers of $T$. Finally $g_{\zeta'}$ sends the represented target value into the corresponding lattice at $P'$. Source and target covariance identifies that transported value with $\mathcal K(P,P')Y$, with the same scale. As $P,P',Y$ were arbitrary, this gives the two point-kernel laws used in [the word-prime lattice proof](restoring-the-word-prime-value-lattice-after-one-lift.md).

### Lean correspondence

- [`KerBar` and `KerP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/KerIsTerm.lean#L105) state the coefficient bounds.
- [`intP_of_kerP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IntPOfKerP.lean#L17) passes to selected-side point coordinates.
- [`isIntegral_torsion` and `act_zeta_mem`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ConjugatePrimeBoundPointKernelOfCoefficientKerne.lean#L33) give the unit action, and [`intBar_of_kerBar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ConjugatePrimeBoundPointKernelOfCoefficientKerne.lean#L48) passes to conjugate-side point coordinates.
- [`KerPt.IntBar` and `KerPt.IntP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/FormsStable.lean#L220) state the resulting pointwise laws.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
