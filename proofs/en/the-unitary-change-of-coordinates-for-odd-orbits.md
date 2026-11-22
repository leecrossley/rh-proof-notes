# The unitary change of coordinates for odd orbits

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix $p\ge5$ inert in the quadratic host and in class `IsResidueClassZero`. Suppose the Frobenius permutation $P:z\mapsto z^+$ on the host places has uniform positive odd orbit length $i=n_P(D,p)$. Choose one representative $r$ per orbit. Fix an admitted pair of full self-dual lattices $L,L'$ of even ranks, standard bases for them at the chosen $p$-adic embedding, and a local trace-orthonormal host frame $(b_k)_k$ of the Hom lattice. Let $j$ index a matrix entry. The [standard-basis comparison](the-standard-bases-give-integral-frobenius-dual-coordinates.md) gives vectors $g_{z,j}=(g_{z,j,k})_k$ and their bilinear dual vectors $h_{z,j}$, with integral entries in the unramified coefficient field, satisfying
$$
 \sigma g_{z,j}=h_{Pz,j},\qquad \sigma h_{z,j}=g_{Pz,j},\qquad
 h_{z,j}^{\,t}g_{w,l}=\delta_{zw}\delta_{jl}.
$$
If $\Theta$ is the raw theta combination $G$ in the orthonormal frame with scale $c$, then $\mathrm{Th}(cZ)=\Theta(\sum_{z,j}g_{z,j}Z_{z,j})$, where $\mathrm{Th}$ is the standard series.

Use the [self-dual trace basis](a-self-dual-hermitian-trace-basis-for-odd-orbits.md) $\omega_\rho\in O_i$, and put $\omega_\rho^*=\sigma^i\omega_\rho$. For $e=(r,\rho,j)$ define
$$
\gamma_e=\sum_{m=0}^{i-1}\sigma^{2m}(\omega_\rho)\,g_{P^{2m}r,j},\qquad
Y_e(Z)=\sum_{m=0}^{i-1}\sigma^{2m}(\omega_\rho^*) Z_{P^{2m}r,j}.
$$
The columns $\gamma_e$ have integral coordinates fixed by $\sigma^2$ and satisfy $\gamma^*\gamma=I$, where the star is transpose followed by $\sigma$. Moreover
$$
\sum_{z,j}g_{z,j}Z_{z,j}=\sum_e\gamma_eY_e(Z).
$$

Every summand in $\gamma_e$ is integral. Applying $\sigma^2$ moves $m$ to $m+1$ both in the coefficient and in the place. At the wrap the coefficient is fixed by $\sigma^{2i}$ and $P^{2i}r=r$. This proves the $\sigma^2$-fixed property. Applying $\sigma$ produces odd exponents and replaces $g$ by $h$. The odd exponents in $\mathbb Z/2i$ are precisely the exponents $2m+i$. They give the same places as $2m$ because $P^i=1$. Hence
$$
\sigma(\gamma_e)=\sum_{m=0}^{i-1}\sigma^{2m}(\omega_\rho^*)h_{P^{2m}r,j}.
$$
When multiplying this column against $\gamma_{e'}$, the pairings of $h$ and $g$ force the places and matrix entries to coincide. Since $2$ is invertible modulo $i$, the indices $(r,m)$ label the places once. The remaining coefficient sum is $T(\omega_{\rho'}\omega_\rho^*)=\delta_{\rho\rho'}$. This proves the unitary claim. For the substitution identity, the trace-duality equation also gives its transposed orthogonality
$$
\sum_\rho\sigma^{2m}(\omega_\rho)\sigma^{2n}(\omega_\rho^*)=\delta_{mn},
$$
by reversing the product of the two square inverse matrices. Expanding $\sum_e\gamma_eY_e$ now leaves exactly the terms with $m=n$, proving the identity.

Suppose $\Theta$ satisfies the host integrality
$$
\exp\!\left(\sum_k\phi(W_k)\right)\Theta(\lambda(W_k):k)
\ \in\ \mathcal O_{\mathbb C_p}[[W]],
$$
where $\phi,\lambda$ are the curve exponent and normalized height-two logarithm. Let $\Psi(V)=\Theta(\gamma V)$, with $V=(V_e)_e$. Then $\Psi$ has the same host integrality in the $e$-variables, and $\mathrm{Th}(cZ)=\Psi(Y_e(Z):e)$. Indeed replace each $W_k$ by the integral formal sum with logarithm $\sum_e\gamma_{k,e}\lambda(V_e)$. The phase cancellation is the same single-index and mixed-index cancellation as in [the orthonormal basis change](changing-the-orthonormal-basis-of-a-kernel.md), using the norm and adjoint laws in the height-two parameter. It applies also if the column matrix is rectangular. In the Lean route this follows by taking $Q=I-\gamma\gamma^*$ and the square matrix $\bigl(\begin{smallmatrix}Q&\gamma\\\gamma^*&0\end{smallmatrix}\bigr)$. It is unitary since $Q^*=Q=Q^2$, $Q\gamma=0$, and $Q+\gamma\gamma^*=I$. Apply the square identity to variables $(0,V)$; the new variables in the first block have the indicated logarithms and the other block contributes zero phase. An integral correction restores the sum of the phases of $V_e$.

**Lean correspondence.** [`stdSeries_orbit_coordinate_change_of_odd_inert`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/OrbitLabellings/StdSeriesOrbitCoordinateChangeOfOddInert.lean#L217) proves the trace coordinate change. The zero-padded square matrix and host integrality transport are [`unitaryInv_rect`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SubstUnitaryLogarithmicCoordinates.lean#L31) and [`HostLog.subst_unitary`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SubstUnitaryLogarithmicCoordinates.lean#L75).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
