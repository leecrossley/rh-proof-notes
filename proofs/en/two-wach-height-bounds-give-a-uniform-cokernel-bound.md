# Two Wach height bounds give a uniform cokernel bound

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%A4%E4%BE%A7%E7%9A%84Wach%E9%AB%98%E5%BA%A6%E7%95%8C%E8%BD%AC%E6%88%90%E4%BD%99%E6%A0%B8%E7%9A%84%E7%BB%9F%E4%B8%80%E7%95%8C.md)

Let \(\ell\) be prime, \(O\) a complete discrete valuation ring of mixed characteristic \((0,\ell)\), and \(R=O[[U]]\). For \(n\ge1\) let \(A=\prod_{i\in\mathbb Z/n\mathbb Z}R\). Frobenius sends component \(i-1\) to component \(i\) by the ring map \(\phi\) fixing \(O\) and taking \(U\) to \((1+U)^\ell-1\). At level \(s\ge1\) put \(X=(1+U)^{\ell^{s-1}}-1\) and \(Q=\phi(X)/X\).

Let \(D_1,D_2\) be \(A\)-modules with Frobenius-semilinear operators \(\Phi_1,\Phi_2\) and Wach submodules \(N_1,N_2\). Let \(F:D_1\to D_2\) be \(A\)-linear, commute with Frobenius, and map \(N_1\) into \(N_2\). Write \(N_{a,i}\) for component \(i\) of \(N_a\). Assume:

1. \(N_2\) is finite free over \(A\). For every \(i\), \(N_{2,i}\) and the \(R\)-span of \(\Phi_2(N_{2,i-1})\) coincide after inverting \(Q\).
2. For integers \(M_i,h_i\ge0\), \(Q^{M_i}\Phi_2(N_{2,i-1})\subset N_{2,i}\) and \(Q^{h_i} N_{1,i}\subset\operatorname{span}_R\Phi_1(N_{1,i-1})\).
3. For some integer \(c\ge0\), \(U^cN_{2,i}\subset F(N_{1,i})\) for every \(i\).

Then \(X^H N_{2,i}\subset F(N_{1,i})\) for every \(i\), with \(H=\max_i(M_i+h_i)\). In the project \(M_i,h_i\) are the left and right widths of the window of Hodge filtration jumps.

**Proof.** Let \(\mathfrak a_i\) be the annihilator of \(N_{2,i}/F(N_{1,i})\). We have \(U^c\in\mathfrak a_i\). For \(g\in\mathfrak a_i\), use the [Frobenius basis](integral-power-series-basis-for-frobenius.md) to write \(Q^Hg=\sum_j (1+U)^j\phi(z_j)\). For \(y\in N_{2,i-1}\) the target height implies \(Q^{M_i}\Phi_2(y)\in N_{2,i}\). Consequently \(gQ^{M_i}\Phi_2(y)=F(x)\) for some \(x\in N_{1,i}\). The source height places \(Q^{h_i}x\) in the span of \(\Phi_1(N_{1,i-1})\). Multiply by \(Q^{H-M_i-h_i}\) and apply \(F\). The result is
$$
Q^Hg\,\Phi_2(y)\in\operatorname{span}_R\Phi_2(F(N_{1,i-1})).
$$
Expand the coefficients of the right-hand combination in the Frobenius basis. Semilinearity moves each \(\phi(b)\) inside \(\Phi_2\), giving an expression \(\sum_j(1+U)^j\Phi_2(y_j)\) with \(y_j\in F(N_{1,i-1})\). The left side is \(\sum_j(1+U)^j\Phi_2(z_jy)\).

To compare the two expressions, take a basis \(b_1,\dots,b_r\) of \(N_{2,i-1}\). The \(r\) vectors \(\Phi_2(b_a)\) span a space of dimension \(r\) over \(\operatorname{Frac}(R)\) by assumption 1, so they are independent there. For each \(a\), comparing its coefficient in the two expressions and then using uniqueness of Frobenius coordinates shows \(z_jy=y_j\). Since this holds for all \(y\), \(z_j\in\mathfrak a_{i-1}\), establishing \(Q^H\mathfrak a_i\subset R\phi(\mathfrak a_{i-1})\). The [recursion on ideals](frobenius-recursion-reduces-the-cokernel-exponent.md) now proves the result.

At level \(s=1\), \(X=U\). In the application with odd \(\ell\) and unramified \(K_w/\mathbb Q_\ell\), this leads to the [prime-power bound](from-a-parameter-power-to-a-prime-power-in-the-wach-cokernel.md).

The two height conditions and final exponent appear in `p5` and `wachLengthLatticeMap`. The coordinate comparison is `indep_of_commensurable`, `decomp_unique`, and `key_inclusion`. [Height conditions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L146) · [Exponent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/DeltaInvariantLattices.lean#L334) · [Independence](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L25) · [Uniqueness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L85) · [Inclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L233)

For actual crystalline quotients `X_pow_kills_coker` first obtains the qualitative \(U^c\) bound. The source filtration window also bounds the quotient's jumps, so both heights come from that window. [Crystalline application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/CokernelCrystallineSurjectionKilledByXPow.lean#L411) · [Height from jumps](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachLatticeHeightsFromHodgeJumps.lean#L382)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
