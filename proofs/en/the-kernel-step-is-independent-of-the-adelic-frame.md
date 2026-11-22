# The kernel step is independent of the adelic frame

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a tied joint model at an inert site, with the dictionary between adelic and local lattice tuples ($\mathrm{Dict}$), admissible source and target lattice pairs ($\mathrm{Pair}$), the positive labelling of embeddings ($\mathrm{Pos}$), and the analytic kernel law ($\mathrm{Law}$). Fix a step $0\le j<m$ and any field embedding $\iota:\mathbb C\to\mathbb C_p$ agreeing on algebraic numbers with the site's prescribed embedding. For every admitted source and target lattice tuple $L,L'$, and rational input column $x$ at layer $j$, let $\phi$ be the corresponding arithmetic class-kernel summand. The local reading of $\phi$ at $L'$ equals
$$
c_K\,\mathcal D_j\bigl(c_j(x)(L),\,r_j(L,L')\bigr).
$$
Here $c_j(x)(L)$ is the first local chart reading at $L$, $r_j(L,L')$ is the normalized local kernel series, and $\mathcal D_j$ is the differential pairing of the local model. The scalar $c_K$ has $|c_K|_p=1$ and depends on the site, the embedding and the layer, uniformly over all $L,L'$ and $x$. This is the compatibility called `Del`.

### The determinant factor and a common complex polynomial

If either layer has no components there are no pairs to test, and $c_K=1$ suffices. Otherwise the frame change gives $c_K$ as the product of a power of the local coordinate scale with
$$
\iota\!\left(\frac{k_T}{k_S c_{\rm op}}\right).
$$
Here $k_S,k_T$ are products of determinant powers from the orthonormal chart bases and rational unitary changes, and $c_{\rm op}$ is a product of reversal signs and integer powers of the differential generators. For the chart determinants the individual embedded norms are one. For the rational unitary changes the exponent is constant over the CM type, and the product of the CM embeddings of a norm-one determinant is a unit at this inert site. Each differential generator and the coordinate scale is a unit. This proves the unit assertion and shows that the denominator is nonzero. The chosen orthonormal bases in a given layer have the same determinant factors in every component, so the formula is independent of the components.

For the input $x$ choose the polynomial $Q$ in sharp coordinates supplied by the joint model. At the source class of $L$ it has the prescribed weights. Apply its associated differential operator to the natural theta kernel for the two classes and multiply by the source and target character factors. Denote the resulting target frame polynomial by $P$. The operator-on-frame identity gives, for every target point $y$ of the class of $L'$,
$$
\phi(y)=\left(\prod_\tau d_\tau(y)^{s_\tau}\right)^{-1}P(\operatorname{frame}(y)).
$$
Here $d_\tau(y)$ is the frame determinant factor in embedding $\tau$ and $s_\tau$ is the prescribed degree correction. The weight identity for differentiation puts $P$ in the target weight space.

### Passing through the frame changes and reading the value

A decomposition $d$ of the adelic lattice tuple chooses a rational frame change and an element of the level group. Transport $P$ through this change and include the determinant correction above. This gives a complex polynomial $V_d$ which realizes $\phi$ on the resulting chart. More specifically, the transported-polynomial identity gives
$$
\iota_* V_d=\operatorname{sc}_T(d,L')\,\tau_{d,L'}\!\left(\Phi_j P\right),
$$
where $\iota_*$ acts on coefficients, $\Phi_j$ changes to the local coordinates with the required slot reversals, and $\tau_{d,L'}$ is the target frame substitution. The local contraction identity has the following inputs at $d$: the input polynomial after the source frame move equals the chart reading in the moved coordinates; the same transformation identifies the differential operator with the prescribed local one, including its degree; the target frame substitution matches the local target move; and the product of the source scalar and the two moving characters times $c_K$ equals $\operatorname{sc}_T(d,L')$. With these identities the displayed formula becomes
$$
\iota_*V_d=c_K\,\mathcal D_j(c_j(x)(L),r_j(L,L')).
$$
The right hand side is independent of $d$. Since $\iota$ is injective, coefficient comparison makes all $V_d$ one polynomial $V$. Such a decomposition exists by the dictionary. To recover the local readout, take any representative used to test the evaluation at the lattice tuple. The level-group comparison moves it to one of the decompositions by multiplying by a stabilizing element whose character value is one. Thus $V$, which realizes $\phi$ on every decomposition, realizes the same evaluations on all these representatives. The uniqueness of polynomial readout now gives the stated identity.

This proves the passage from the frame identities to the single step of the actual chain. The differential contraction identity and the coordinate, character and frame-move identities supplying it are the local inputs to this passage.

### Lean correspondence

- [`GlobalTheory.TwV.DelA.tieDel_all_steps`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KernelSiteFrameValuesAllStepsLtM.lean#L23) gives the step comparison.
- [`cKs_unit_indep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/StepDeterminantConstantUnitIndependent.lean#L16) proves the unit norm and component independence.
- [`entQFrame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/OperatorOnFrameAndClassSummandPolynomial.lean#L46) gives the formula for the class summand.
- [`transported_frame_realAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/TransportedFramePolynomialComplexValuesAtPoint.lean#L38) transports $P$. The local identities combine in [`delPolAt_site`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KernelSiteContractionIdentityOperatorHalf.lean#L14).
- [`rdJ_eq_of_realAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/LatticeTupleReadingEqOfRealisingPolynomial.lean#L33) compares representatives and gives the polynomial readout.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
