# A prescribed local abelian extension can be globalized with CM disjointness

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a CM number field \(E\) in an algebraic closure \(\Omega\), its maximal real subfield \(F\), a finite place \(w\) of \(E\), and a prolongation to \(\Omega\) whose restriction to \(F\) lies over \(v\). Write \(D_E\subset D_F\) for the resulting decomposition groups and \(G_L=\operatorname{Gal}(\Omega/L)\) for subfields \(L\). Let \(N\) be an open subgroup of \(G_E\). There are two conclusions.

1. Some finite solvable Galois CM extension \(M_0/E\) satisfies \(G_E=G_{M_0}N\), \(D_E\subseteq G_{M_0}\), and \(D_{M_0^+}\subseteq G_{M_0}\) for the same prolongation. The last condition says that the place of \(M_0^+\) splits in \(M_0/M_0^+\).
2. If \(D_F=D_E\) and \(V\) is an open subgroup of \(D_E\) containing \([D_E,D_E]\), there is a finite solvable Galois CM extension \(M/E\) with \(G_E=G_MN\) and \(D_E\cap G_M=V\).

The parameter \(N\) is used to preserve cuspidality in the solvable base change. [First statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsSolvableCmExtensionSplitPlace.lean#L30) · [Second statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsSolvableCmExtensionAbelianCompletion.lean#L85) · [Cuspidality argument](a-nonvanishing-trace-keeps-a-solvable-base-change-cuspidal.md)

## Forcing the required global disjointness

The subgroup \(N\) is also open in \(G_F\) because \(G_E\) has finite index. Choose an open normal subgroup \(U\) of \(G_F\) contained in \(N\). For each element of \(G_F/U\), Čebotarev furnishes a finite place other than \(v\) and a Frobenius element representing that element of the quotient. One can choose the prolongation to \(\Omega\) to get the element itself from its conjugacy class. Let \(T\) be the finite set of chosen places. Every \(g\in G_F\) can then be written \(g=xn\) with \(x\) in a decomposition group over a place of \(T\) and \(n\in N\). [Covering an open quotient by decomposition groups](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/FiniteDecompositionGroupsCoverOpenQuotient.lean#L17)

If \(F_1/F\) is a finite solvable Galois totally real extension split at \(T\), take \(M=EF_1\). This is CM because it is the quadratic totally imaginary extension of the real field \(F_1\) obtained by adjoining \(E\). The extension \(M/E\) is Galois and solvable since its group embeds by restriction in \(\operatorname{Gal}(F_1/F)\). If \(g\in G_E\) and \(g=xn\) is the above decomposition, then \(x\in G_E\) as \(n\in N\subset G_E\). It fixes \(F_1\) by the splitting at \(T\), so \(x\in G_M\). This proves \(G_E=G_MN\). For any \(g\in G_E\), fixing \(M\) is equivalent to fixing \(F_1\). [Compositum and disjointness](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsCmFieldLiftDisjointOfRealSolvable.lean#L35)

## Making the two local choices

For the first assertion, \(D_E=D_F\cap G_E\) is open in \(D_F\) and contains the commutator subgroup because \(E/F\) is quadratic. Globalize this open subgroup using the [character construction](finite-order-local-characters-globalize-with-trivial-infinite-components.md). It produces a totally real abelian \(F_1/F\), split at \(T\), such that
\[
D_F\cap G_{F_1}=D_E.
\]
Then \(M_0=EF_1\) has \(M_0^+=F_1\). Every element of \(D_E\) fixes \(F_1\) and therefore \(M_0\). Conversely \(D_{M_0^+}=D_F\cap G_{F_1}=D_E\), so it also fixes \(M_0\). This proves both local conditions in the first assertion. [Matching the quadratic decomposition subgroup](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsSolvableCmExtensionSplitPlace.lean#L30)

For the second assertion, identify \(D_E\) with \(D_F\) by the assumed splitting. Globalize \(V\) by the same character construction to get \(F_1/F\), split at \(T\), with \(D_F\cap G_{F_1}=V\). For \(M=EF_1\), the identity for fixing \(M\) now reads \(D_E\cap G_M=D_E\cap G_{F_1}=V\). This proves the second assertion. [Prescribed abelian completion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsSolvableCmExtensionAbelianCompletion.lean#L85)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
