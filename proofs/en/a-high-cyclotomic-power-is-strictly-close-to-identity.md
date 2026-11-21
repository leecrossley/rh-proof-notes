# A high cyclotomic power is strictly close to the identity

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E8%AE%A9%E9%AB%98%E6%AC%A1%E5%88%86%E5%9C%86%E7%94%9F%E6%88%90%E5%85%83%E7%9A%84%E7%9F%A9%E9%98%B5%E4%B8%A5%E6%A0%BC%E6%8E%A5%E8%BF%91%E5%8D%95%E4%BD%8D.md)

Let \(\ell\) be prime, \(O\) the ring of integers of a finite extension of \(\mathbb Q_\ell\), \(A=O[[U]]^n\) with \(n\ge1\), and \(I=(\ell,U)\). Let \(Y:N\to N\) be additive and semilinear for the map \(\gamma\) fixing \(O\) and each component and substituting \(1+U\mapsto(1+U)^u\) with \(u\in1+\ell\mathbb Z_\ell\). Assume \((Y-1)N\subset UN\). For each \(j\ge1\) one has
$$
(Y^{\ell^{j+1}}-1)N\subset ((\ell^2)+I^{\ell^j})N .
$$
If \(\zeta_j\) is primitive of order \(\ell^j\) and \(\eta:A\to\mathcal O_{\mathbb C_\ell}\otimes_{\mathbb Z_\ell}O\) sends \(U\) to \((\zeta_j-1)\otimes1\), then every coefficient of \(\eta(a)\) in any \(\mathbb Z_\ell\)-basis of \(O\) has absolute value \(<\rho_\ell=\ell^{-1/(\ell-1)}\) for \(a\in(\ell^2)+I^{\ell^j}\). This bounds the specialized entries of \(Y^{\ell^{j+1}}-1\) on an \(A\)-basis of \(N\).

**Proof.** We have \(\gamma(U)-U=(u-1)U+U^2c(U)\in I^2\), and \(\gamma(a)-a\in I\) for all \(a\). Apply the difference to each generator \(\ell^{k-i}U^i\) of \(I^k\), then to a coefficient times it. The difference in the generator raises the order by one because each replaced \(U\) gains a factor in \(I\); the difference of the coefficient contributes at least one power of \(I\) as well. Thus \((\gamma-1)I^k\subset I^{k+1}\). For \(\Delta=Y-1\), the equality \(\Delta(ax)=\gamma(a)\Delta(x)+(\gamma(a)-a)x\) gives \(\Delta(I^kN)\subset I^{k+1}N\), hence \(\Delta^iN\subset I^iN\).

Expand \((1+\Delta)^{\ell^{j+1}}-1\). Terms with \(i\ge\ell^j\) land in \(I^{\ell^j}N\). For \(1\le i<\ell^j\), \(v_\ell(i)\le j-1\), so \(\binom{\ell^{j+1}}i=(\ell^{j+1}/i)\binom{\ell^{j+1}-1}{i-1}\) has valuation at least two. This gives the module bound.

The Eisenstein cyclotomic polynomial gives \(v_\ell(\zeta_j-1)=1/(\ell^{j-1}(\ell-1))\), so \(\eta(I)\subset(\zeta_j-1)\). Thus \(\eta(a)=\ell^2 b+(\zeta_j-1)^{\ell^j}c\) for integral \(b,c\). Their coordinates have absolute value at most one. The two multiplying scalars have absolute values \(\ell^{-2}\) and \(\ell^{-\ell/(\ell-1)}\), both \(<\rho_\ell\). Apply the ultrametric inequality. The project takes \(j=s+n_0\) to control a finite-level change of basis.

`gamma_sub_mem_pow_succ` gives the filtration property, `semilinear_iterate_prime_pow_sub_mem` the binomial estimate, `γD_pow_sub` its application to the lattice and `norm_kap_lt_rho1_of_mem_sq_sup_pow` the coordinate estimate. [Filtration](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/GammaActionSubMemSpanPowSucc.lean#L118) · [Binomial expansion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/SemilinearIteratePrimePowSubMemFiltration.lean#L40) · [Lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsDecompletionFrameOfLattice.lean#L103) · [Norm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/NormLtRho1OfMemIdealPower.lean#L35)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
