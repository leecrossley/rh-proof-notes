# The de Rham filtration determines each expansion monomial

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%B1%95%E5%BC%80%E7%9A%84%E5%8D%95%E9%A1%B9%E7%94%B1deRham%E8%BF%87%E6%BB%A4%E5%86%B3%E5%AE%9A.md)

Let \(B\) be a field containing \(L\), with an integer-indexed decreasing, separated, exhaustive multiplicative filtration \(\operatorname{Fil}^aB=t_B^a B^+\), \(B^+=\operatorname{Fil}^0 B\), \(L\subset B^+\), and \(t_B\in B^\times\). Assume a ring map \(e:L[[t]]\to B^+\) evaluates \(t\) at \(t_B\) and has \(e(a)\in t_B^mB^+\) if and only if \(a\in t^mL[[t]]\) for all \(m\ge0\).

Let \(V\) be finite dimensional over \(L\) and \(p:V\to B^n\) be \(L\)-linear. For \(r\le n\), let \(g_1,\dots,g_r\in V((t))\) and \(\Lambda=\sum_j L[[t]]g_j\). Assume \(\psi_j\in(B^+)^n\) generate \((B^+)^n\) and satisfy the following comparison. Whenever \(f=\sum_j a_jg_j\) with \(a_j\in L[[t]]\), the vector \(\sum_j e(a_j)\psi_j\) has \(t_B\)-expansion with coefficients \(p(f_k)\). This means agreement with every finite truncation modulo the corresponding power of \(t_B\), after multiplying by a sufficient fixed power of \(t_B\) to shift all degrees to nonnegative ones. Suppose \(\Lambda\) contains \(t^m V[[t]]\) for some \(m\in\mathbb Z\). Then
$$
dt^k\in\Lambda\quad\Longleftrightarrow\quad p(d)\in(\operatorname{Fil}^{-k}B)^n
\qquad(d\in V,\ k\in\mathbb Z).
$$

**Proof.** For \(dt^k=\sum_j a_jg_j\), the truncation comparison and separatedness imply the equality \(t_B^kp(d)=\sum_j e(a_j)\psi_j\). The right side is integral, proving one implication. Conversely, if \(t_B^kp(d)\) is integral, write it as \(\sum_j b_j\psi_j\), \(b_j\in B^+\). These \(r\) vectors span \(B^n\) and \(r\le n\), so they form a basis. Choose \(h\ge0\) with \(k+h\ge m\). The tail hypothesis gives \(dt^{k+h}=\sum_j a_jg_j\) with \(a_j\in L[[t]]\). Applying the comparison,
$$
\sum_j e(a_j)\psi_j=t_B^{k+h}p(d)=\sum_j t_B^h b_j\psi_j .
$$
Independence gives \(e(a_j)=t_B^hb_j\). Order preservation for \(e\) makes each \(a_j\) divisible by \(t^h\). Divide the formal series equality by \(t^h\) to recover \(dt^k\in\Lambda\).

In the application \(V\) is a fixed coefficient component of crystalline periods. The map \(p\) compares them with de Rham periods using the chosen embedding \(\iota:L\hookrightarrow B_{\rm dR}\). For the original \(L\)-representation \(V_0\), imposing \(cv\otimes b=v\otimes\iota(c)b\) on \(V_0\otimes_{\mathbb Q_\ell}B_{\rm dR}\) gives \(V_0\otimes_{L,\iota}B_{\rm dR}\). Coordinates in an \(L\)-basis of \(V_0\) identify filtration degree \(a\) with all coordinates in \(\operatorname{Fil}^aB_{\rm dR}\). This defines the project's `FilAt` on the crystalline component. The comparison at the current level gives the \(\psi_j\) from the Wach basis. The common tail bound and [degree-by-degree criterion](checking-cyclotomic-expansion-lattices-degree-by-degree.md) now identify the whole expansion lattice with the bounded-below series satisfying \(f_k\in\operatorname{Fil}^{-k}\) for every \(k\).

`single_mem_iff` uses `Rep.unique` and the basis comparison. `mem_sup_iff` proves the coordinate test, and `lat_eq_fil` applies the monomial result with the cyclotomic de Rham comparison. The comparison itself is an input here. [Monomial argument](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L80) · [Truncation uniqueness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L180) · [Coordinate test](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L404) · [Expanded lattice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeEqFiltrationSumAtLevel.lean#L423)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
