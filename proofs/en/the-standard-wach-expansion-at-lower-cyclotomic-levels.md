# The standard Wach expansion at lower cyclotomic levels

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E8%BE%83%E4%BD%8E%E5%88%86%E5%9C%86%E5%B1%82%E7%9A%84%E5%B1%95%E5%BC%80%E6%A0%BC%E6%B2%A1%E6%9C%89%E8%B4%9F%E6%AC%A1%E9%A1%B9.md)

Let \(\ell\) be prime and \(s\ge1\). Let \(L/\mathbb Q_\ell\) be a finite extension containing the \(\ell^s\)-th roots of unity and put \(Q=\Phi_{\ell^s}(1+U)\). Let \(N\) be a Wach lattice with \(n\ge1\) coefficient components, indexed cyclically. Write \(e_{i,\zeta}(x)\in V_i((t))\) for the expansion of \(x\in N\) at component \(i\) and root \(\zeta\), with \(V_i\) finite dimensional over \(L\), and \(\Lambda_{i,\zeta}\) for the \(L[[t]]\)-span of these expansions. Assume:

1. At \(\zeta=1\) the expansions have a common lower degree bound, and \(\Lambda_{i,1}\) contains \(t^mV_i[[t]]\) for some \(m\). The cyclotomic operator \(\gamma\) multiplies degree \(k\) by \(u^k\), where \(u\in L^\times\) has infinite order. Also \(\gamma(x)-x\in UN\) and \(E_1(U)\) has zero constant term.
2. The Frobenius comparison, whenever \(Q^a\Phi x\in N\), is
   $$
   e_{i,\zeta}(Q^a\Phi x)
   = E_\zeta(Q)^a\Phi_i\!\left(e_{i-1,\zeta^\ell}(x)(\ell t)\right)
   $$
   with \(\Phi_i:V_{i-1}\to V_i\) an \(L\)-linear isomorphism. Each \(\Phi x\) enters \(N\) after multiplication by some power of \(Q\), and each \(y\in N\) enters the integral scalar span of \(\Phi(N)\) after multiplication by some power of \(Q\). Integral scalars act on expansions by multiplication by their scalar expansions.

Then \(\Lambda_{i,\zeta}=V_i[[t]]\) for every \(\zeta\) with \(\zeta^{\ell^{s-1}}=1\) and every \(i\).

**Proof.** At \(\zeta=1\), omit \(i\) and put \(e(x)=\sum_k d_k(x)t^k\). For \(\gamma(x)-x=Uy\), \(y\in N\), the degree-\(k\) equality is
$$
(u^k-1)d_k(x)=\sum_{j\ge1} E_1(U)_j\,d_{k-j}(y).
$$
Start below the common support bound. For negative \(k\), once the coefficients below \(k\) vanish for all elements of \(N\), the right side is zero for all \(x\). Since \(u^k\ne1\), the degree \(k\) coefficients vanish as well. This proves the absence of negative degrees. Let \(S\) be the span of the \(d_0(x)\). For \(k\ge1\) the same equality puts all \(d_k(x)\) in \(S\) inductively. Because the span of the expansions contains \(t^mV_i[[t]]\), it follows that \(S=V_i\). The [degree-by-degree result](checking-cyclotomic-expansion-lattices-degree-by-degree.md) puts each constant \(d_0(x)\) in \(\Lambda_{i,1}\). They span \(V_i\), giving equality with \(V_i[[t]]\).

For the induction step assume the result at \(\zeta^\ell\). The condition \(\zeta^{\ell^{s-1}}=1\) implies \(Q(\zeta-1)\ne0\), so \(E_\zeta(Q)\) is a unit. For each \(x\), bring \(\Phi x\) into \(N\) by a power of \(Q\), use the comparison, then cancel the unit in the expansion. Thus \(f(t)\mapsto\Phi_i(f(\ell t))\) sends the span at \(\zeta^\ell\) into the span at \(\zeta\). It takes \(V_{i-1}[[t]]\) onto \(V_i[[t]]\), since substitution \(t\mapsto\ell t\) is an automorphism over \(L\). Conversely, multiply any \(y\in N\) by a sufficient power of \(Q\) to write it as a combination of Frobenius images. By the comparison, the scalar expansions and the induction hypothesis this expands in nonnegative degrees. Cancelling the unit \(E_\zeta(Q)^a\) keeps the expansion in nonnegative degrees. Induction on the order of \(\zeta\) completes the proof.

The start at \(1\) uses `uniform_supp`, `lower`, `std_of_lower` and `lat_one_std`. The lower-level step is `std_step` and `lat_low`. [Common support](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqStdPowerSeriesAtZero.lean#L110) · [Recurrence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqStdPowerSeriesAtZero.lean#L153) · [Standard lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqStdPowerSeriesAtZero.lean#L40) · [At \(1\)](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqStdPowerSeriesAtZero.lean#L184) · [Step](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeExpansionsStdBelowLevel.lean#L84) · [Induction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeExpansionsStdBelowLevel.lean#L186)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
