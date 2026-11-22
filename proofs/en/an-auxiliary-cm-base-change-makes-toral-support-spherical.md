# An auxiliary CM base change makes toral support spherical

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let \(E\) be a CM number field with algebraic closure \(\Omega\), \(\ell\) a prime, and \(\iota\colon\overline{\mathbb Q}_\ell\simeq\mathbb C\) an isomorphism. Let \(n\ge1\) and let \((\pi,\chi)\) be a regular algebraic polarized cuspidal datum of rank \(n\) over \(E\), with a weakly attached Galois representation \(r\). Fix a finite place \(w\), its prolongation to \(\Omega\), and the local component \(\sigma=\pi_w\). Let \(a_w\colon W_w\to E_w^\times\) be local reciprocity in the convention \(v_w(a_w(g))=-\deg g\). Assume that the algebraically normalized component
\[
\sigma^{\mathrm{alg}}=\sigma\otimes|\det|_w^{(1-n)/2}
\]
has supercuspidal support consisting of the smooth characters \(\xi_1,\ldots,\xi_n\) of \(E_w^\times\). Suppose the support is unlinked, meaning no member is another multiplied by \(|\cdot|_w\). For each \(g\in W_w\) of nonzero degree, there is a finite CM extension \(M/E\) fixed by \(g\), a place \(u\) over \(w\) from the same prolongation, and a cuspidal base change \(P\) in the same regular algebraic polarized scope. The component \(P_u\) is spherical, with Satake multiset \(B\). For any \(g_0\in W_w\) and \(g'\in W_u\) inducing the same automorphism of \(\Omega\), the characteristic polynomial of the normalized spherical Weil action at \(g'\) is
\[
\det(X-\operatorname{satWD}_{B}(g'))=\prod_{j=1}^{n}(X-\xi_j(a_w(g_0))).
\]
The base change input includes the prime-degree local character-support law and the cuspidality criterion explained in the [solvable ascent proof](a-nonvanishing-trace-keeps-a-solvable-base-change-cuspidal.md). [Lean statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/ToralDeRham/FrobeniusCharpolyOfUnlinkedUnramifiedSupport.lean#L32)

## Killing inertia while retaining the test element

First choose an open subgroup \(N\subseteq G_E\) on which \(\operatorname{tr}r\ne0\). The [first CM globalization](a-prescribed-local-abelian-extension-can-be-globalized-with-cm-disjointness.md) gives a finite solvable Galois extension \(M_0/E\) satisfying \(G_E=G_{M_0}N\), split at the chosen place over \(w\), with that place also split over \(M_0^+\). Hence every former element of the local decomposition group, including \(g\), still acts as a local element over \(M_0\). Its degree stays nonzero. The solvable ascent proof gives a cuspidal lift \(\pi_0\) over \(M_0\) with \(r|_{G_{M_0}}\) weakly attached.

Put \(s=(1-n)/2\) and \(\xi_j^0=\xi_j|\cdot|_w^{-s}\), so that these are the characters of the unnormalized support. Pull them back by the local norm at the chosen place of \(M_0\). The [open subgroup construction](a-profinite-quotient-kills-the-toral-inertia-and-keeps-one-weil-element.md), applied to these pulled-back characters following local reciprocity, gives an open abelian quotient of the decomposition group whose kernel \(V\) contains \(g\) and whose intersection with inertia is in all the character kernels. Choose an open subgroup \(N_1\subseteq G_{M_0}\) on which the trace of \(r|_{G_{M_0}}\) is nonzero. Apply the second CM globalization with \(V\) and \(N_1\). This is possible because the chosen place of \(M_0\) is split over \(M_0^+\). It gives \(M/M_0\) with \(G_{M_0}=G_MN_1\) and local decomposition group \(V\). Solvable ascent gives a cuspidal lift \(P\) of \(\pi_0\). The two support laws compose by transitivity of the norm. [The two field extensions in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/ToralDeRham/WeaklyAttachedToralOfCmLift.lean#L29)

In particular \(g\) fixes \(M\). Every element of the inertia group of \(M_u\), viewed in \(W_w\), belongs to the subgroup on which each \(\xi_j^0\circ a_w\) is trivial. Local reciprocity maps this inertia group onto \(\mathcal O_{M_u}^\times\), and the Artin maps are compatible with the norm. Thus the support characters \(\xi_j^0\circ N_{M_u/E_w}\) are unramified. [From killed inertia to unramified norm pullback](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/UnramifiedCompNormOfKilledInertiaFixing.lean#L13)

## Why the norm pullback is still unlinked

For a regular algebraic polarization the weight \(b\) is defined by the relation of infinitesimal characters at conjugate complex embeddings. The twist \(\sigma^{\mathrm{alg}}\otimes|\det|_w^{b/2}\) is generic and unitarizable. For a generic unitary irreducible representation of \(\mathrm{GL}_n\) over a nonarchimedean local field of characteristic zero, the unitary dual classification writes it as a normalized induction of unitary square-integrable segment constituents, each twisted by a real exponent in \((-1/2,1/2)\). The generic restriction leaves unitary square-integrable factors and their complementary pairs: a longer Speh factor is the nongeneric irreducible quotient of a reducible standard module, and genericity of an irreducible product forces all its factors to be generic. The project uses that generic form of the classification. [Tadić, Theorem D](https://www.numdam.org/item/10.24033/asens.1510.pdf) · [Generic input used in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/PublishedTheorems/GaloisCohomology₂/IsComplementaryProductOfIsCuspidal.lean#L25)

The cuspidal support of a segment of length at least two contains two successive absolute-value twists. The unlinked hypothesis therefore forces every segment in this decomposition to have length one. Each factor is then a unitary character, of absolute value \(1\) on \(E_w^\times\), times an allowed twist. Consequently for each \(j\) there is \(e_j\in(-1/2,1/2)\) with
\[
|\xi_j(x)|=|x|_w^{e_j-b/2}\qquad(x\in E_w^\times).
\]
Norm pullback preserves this formula with the absolute value of the extension field, because \(|N_{M_u/E_w}x|_w=|x|_u\). The exponent differences \(e_i-e_j\) all lie strictly between \(-1\) and \(1\). If two pulled-back characters differed by \(|\cdot|_u\), evaluation on a uniformizer and taking complex absolute values would force their exponents to differ by \(1\). Thus the pulled-back support remains unlinked. Multiplying every character by the common twist \(|\cdot|_u^{-s}\) preserves this condition. [Derivation of the strict range](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/ToralDeRham/NormEqOneOfIsUnitarisable.lean#L100) · [Norm pullback](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/UnlinkedCharsCompNormU.lean#L14)

## Computing the polynomial upstairs

The unnormalized local support of \(P_u\) is now the multiset of unramified, unlinked characters \(\beta_j=\xi_j^0\circ N_{M_u/E_w}\). The normalized principal series induced from these characters is irreducible, since no pair differs by an absolute-value twist. It contains the spherical vector whose Satake multiset is \(B=\{\beta_j(\varpi_u)\}_{j=1}^n\), where \(\varpi_u\) is a uniformizer. It is the local component with the given support. [Zelevinsky, §1.10–1.11 and Theorem 4.2](https://archive.numdam.org/item/10.24033/asens.1379.pdf) · [Finding the Satake multiset in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/ToralDeRham/LocalComponentsOfSmoothCharacters.lean#L176)

Since the characters are unramified, \(\beta_j(a_u(g'))=\beta_j(\varpi_u)^{-\deg g'}\). The normalized spherical Weil action therefore has eigenvalues
\[
q_u^{s\deg g'}\beta_j(\varpi_u)^{-\deg g'}
=(\beta_j|\cdot|_u^s)(a_u(g'))
=\xi_j(a_w(g_0)).
\]
The last equality uses both norm compatibility of normalized absolute values and \(N_{M_u/E_w}(a_u(g'))=a_w(g_0)\). Taking the product of the corresponding linear factors proves the polynomial comparison. [Spherical polynomial in this Frobenius convention](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SatWDCharPolChars.lean#L68) · [Application to the lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/ToralDeRham/FrobeniusCharpolyEqSatakeOfPlaceAbove.lean#L28)


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
