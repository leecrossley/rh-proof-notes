# A norm-one ideal twist restores the conjugated period lattice

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/K$ be the host CM extension and let $\mathfrak b$ be the nonzero integral half-different in its host data. Thus the relative different is $\mathfrak D_{E/K}=\mathfrak b\bar{\mathfrak b}$ and the scalar fractional ideal of the host is $J_0=\mathfrak b^{-1}$. Take $\sigma\in\operatorname{Gal}(E/K)$, which commutes with CM conjugation. Let $L\subset E^a$ and $L'\subset E^b$ be any full self-dual $\mathcal O_E$-lattices in the coordinate Hermitian forms. In this assertion the ranks can be any nonnegative integers. Put
$$
Y(L,L')=J_0\operatorname{Hom}_{\mathcal O_E}(L,L'),
$$
where each homomorphism is regarded as its $E$-linear matrix. There are full self-dual lattices $L_1,L_1'$ of the same respective ranks such that
$$
\sigma\bigl(Y(L,L')\bigr)=Y(L_1,L_1').
\tag{1}
$$
Here $\sigma$ on a lattice or a matrix applies $\sigma$ to every entry. In particular, for any scalar period lattice $\Lambda_c=\delta I$ as in the [host lattice proof](the-host-period-lattices-are-self-dual-and-commensurable.md), the complex period lattice obtained at $(L,L')$ by replacing all embeddings $\sigma_\tau$ by $\sigma_\tau\circ\sigma$ is the ordinary complex period lattice at $(L_1,L_1')$. This is the arithmetic reidentification needed before applying the normalized theta average at a conjugate place.

**The compensating ideal.** Let $C=\sigma(J_0)J_0^{-1}=\mathfrak b/\sigma(\mathfrak b)$. The relative different is fixed by $\sigma$: the $\mathcal O_K$-trace dual of $\mathcal O_E$ is preserved because $\sigma$ preserves $\mathcal O_E$ and $\operatorname{Tr}_{E/K}$. Since $\sigma$ commutes with conjugation,
$$
C\bar C
 =\frac{\mathfrak b\bar{\mathfrak b}}{\sigma(\mathfrak b\bar{\mathfrak b})}
 =\mathcal O_E.
$$
Set $L_1=\sigma L$ and $L_1'=C\,\sigma L'$. Entrywise application of $\sigma$ commutes with the Hermitian pairing, in the sense $h(\sigma v,\sigma w)=\sigma(h(v,w))$, so it carries a self-dual lattice to a self-dual lattice. For any invertible fractional ideal $C$ and any lattice $M$, the Hermitian dual of $CM$ is $\bar C^{-1}M^\#$. To see this, test a vector against all $c m$ with $c\in C,\ m\in M$. This is equivalent to requiring its pairing against every $m$ to lie in $\bar C^{-1}$. Multiplying by $\bar C$ yields the stated formula, since $1$ is a finite sum of products from $\bar C$ and $\bar C^{-1}$. With $C\bar C=\mathcal O_E$ and $M=\sigma L'$, we get $(L'_1)^\#=L'_1$. Both new lattices still span the full spaces.

**The Hom module.** For any two full lattices $M,M'$ and invertible fractional ideal $C$,
$$
\operatorname{Hom}_{\mathcal O_E}(M,CM')=
 C\,\operatorname{Hom}_{\mathcal O_E}(M,M').
$$
The inclusion from right to left follows from the defining lattice condition. For the reverse, if $A(M)\subseteq CM'$, then $uA(M)\subseteq M'$ for each $u\in C^{-1}$. Write $1=\sum_i c_i u_i$ with $c_i\in C,u_i\in C^{-1}$, and express $A=\sum_i c_i(u_iA)$ as required. Moreover, applying $\sigma$ to a lattice map carries it to a map of the conjugate lattices, with inverse obtained by $\sigma^{-1}$. Hence
$$
Y(L_1,L'_1)
 =J_0C\,\operatorname{Hom}_{\mathcal O_E}(\sigma L,\sigma L')
 =\sigma(J_0)\,\sigma\operatorname{Hom}_{\mathcal O_E}(L,L')
 =\sigma Y(L,L').
$$
For the complex assertion, the generating period $w\,(\sigma_\tau(\sigma(A_{ij})))_{\tau,ij}$ of the twisted embedding lattice, with $w\in\Lambda_c,\ A\in Y(L,L')$, equals the ordinary period of the matrix $\sigma(A)$. Identity (1) identifies the generating sets in both directions. The twist compensates for the change of the chosen half-different under $\sigma$.

**Lean correspondence.** The different and half-different comparison is [`exists_twisting_ideal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/ExistsSelfDualPairGaloisConjugateHomLattice.lean#L216). The dual of the twisted lattice is given by [`isSDLat_twist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/ExistsSelfDualPairGaloisConjugateHomLattice.lean#L96) and the Hom equality by [`exists_conjugate_pair`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/ExistsSelfDualPairGaloisConjugateHomLattice.lean#L287). The identification is used in [`norm_core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/VacuumNormConjCmPointsAllEmbeddings.lean#L31).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
