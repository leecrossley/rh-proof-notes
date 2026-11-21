# The Teichmüller parameter has a cyclotomic exponential expansion

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88Teichm%C3%BCller%E5%8F%82%E6%95%B0%E5%9C%A8%E5%90%84%E5%88%86%E5%9C%86%E5%B1%82%E6%9C%89%E6%8C%87%E6%95%B0%E5%B1%95%E5%BC%80.md)

Let \(\ell\) be prime and use the project's compatible period model `LocTied`. For a compatible cyclotomic sequence \(\varepsilon=(1,\zeta_1,\zeta_2,\ldots)\) in the tilt, let \(\mathbf t=\log[\varepsilon]\in{\rm Fil}^1 B_{\rm dR}\), with Teichmüller lift denoted by brackets. For all \(s,h,M\ge0\),
$$
[\varepsilon^{1/\ell^s}]^h-
\zeta_s^h\sum_{j=0}^{M-1}\frac{(h/\ell^s)^j}{j!}\mathbf t^j
\in {\rm Fil}^M B_{\rm dR}.
$$
[Lean statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L128)

**Proof.** For \(M=0\) this is integrality in \(B_{\rm dR}^+\). For \(M>0\), work in \({\rm Fil}^0/{\rm Fil}^M\) with the nilpotent ideal \(I\) given by \({\rm Fil}^1\). The finite exponential on \(I\) and logarithm on \(1+I\) are inverses by the characteristic-zero formal identities and \(\exp(x+y)=\exp(x)\exp(y)\). Consequently taking the \(d\)-th power on \(1+I\) is bijective for every positive integer \(d\). With \(\mu_0=[\varepsilon]-1\in I\), the period comparison gives \(\mathbf t=\sum_{j=1}^{M-1}(-1)^{j+1}\mu_0^j/j\) in this quotient. Lean uses \(M!\) to compare integrally before dividing back. Thus \([\varepsilon]=\exp(\mathbf t)\). [Truncated logarithm](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonSubExpMemHodgeFiltration.lean#L117) · [Exponential](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonSubExpMemHodgeFiltration.lean#L150)

Set \(a=[\varepsilon^{1/\ell^s}]\), \(d=\ell^s\). Fontaine specialization takes \(a\) to \(\zeta_s\), so \(a/\zeta_s\in1+I\), and its \(d\)-th power is \([\varepsilon]\) by multiplicativity of Teichmüller lifts and \(\zeta_s^d=1\). The unique root is \(\exp(\mathbf t/d)\). Taking the \(h\)-th power gives the formula. For \(f\in L[U]\) and \(\iota:L\to B_{\rm dR}\) with \(\iota(\zeta)=\zeta_s\), substitute \(U=a-1\) in the quotient. Since \(\iota(L)\subset{\rm Fil}^0\), the result is the Taylor polynomial of \(f(\zeta e^Z-1)\) at \(Z=\mathbf t/d\) modulo \({\rm Fil}^M\).

`epsT_sub_mem` identifies the root, `eq_of_pow_eq_of_nilpotent` proves uniqueness by a geometric-sum factorization, and `epsT_pow_taylor` and `poly_taylor` give the congruences. The [open-disc comparison](evaluating-open-disc-series-in-crystalline-periods.md) extends them to convergent series. [Specialization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L19) · [Uniqueness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/TeichmullerEpsilonRootPowSubZetaExpMemFiltration.lean#L120) · [Polynomials](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/PolynomialTeichmullerRootTaylorModFil.lean#L64)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
