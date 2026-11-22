# An unramified toral lift compares all inertial polynomials

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let \(E\) be CM with algebraic closure \(\Omega\), \(\ell\) a prime, \(\iota\colon\overline{\mathbb Q}_\ell\simeq\mathbb C\), and \(n\ge1\). Let \((\pi,\chi)\) be regular algebraic polarized and cuspidal on \(\mathrm{GL}_n/E\), and let \(r\) be weakly attached. Fix a finite place \(w\), a local component \(\sigma=\pi_w\) with nonzero \(K_1\)-fixed vectors, a prolongation to \(\Omega\) and an extended local Langlands correspondence \(\operatorname{rec}\) at that place. Here \(K_1\) is the kernel of reduction of the maximal compact subgroup. Write \(\sigma^{\mathrm{alg}}=\sigma\otimes|\det|_w^{(1-n)/2}\). Suppose the monodromy of \(\operatorname{rec}(\sigma^{\mathrm{alg}})\) is zero and either
- \(\sigma^{\mathrm{alg}}\) has unlinked support consisting of rank-one characters, or
- \(E_w\) is continuously isomorphic to \(\mathbb Q_p\) for a prime \(p\), and the members of rank at least two in any supercuspidal support of \(\sigma^{\mathrm{alg}}\) are pairwise inequivalent up to unramified determinant twist, counting repeated entries.

Then the local Weil–Deligne parameter of \(r\) has zero monodromy and the same inertial characteristic polynomials as \(\operatorname{rec}(\sigma^{\mathrm{alg}})\). At \(w\mid\ell\) the local representation is also potentially semistable and de Rham, with jumps \((n-1)/2-z\) for \(z\) running through the infinitesimal character at every induced embedding, with multiplicity. This statement quantifies over the same prolongations, tied period data, local bridges and induced coefficient-field embeddings as the [toral comparison](spherical-comparison-gives-the-local-parameter-for-unlinked-toral-support.md). [Precise principal-congruence statement](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/PAdicSplitting/LocalGlobalCompatAtIwahoriFixedPlaces.lean#L18)

## The auxiliary lift and the equality on inertia

In the first case the toral theorem already gives the conclusions. In the second case the [depth-zero support proof](zero-monodromy-makes-the-depth-zero-support-unlinked.md) gives a support of \(\sigma\) satisfying the mixed conditions. The needed lifting input, called `ToTor`, has this statement. For a weak attachment in all ranks as above, at a place with completion \(\mathbb Q_p\) and mixed support, and for any prolongation and extended local correspondence, there exists a finite CM extension \(M/E\) in \(\Omega\), an ensuing place \(u\mid w\) from the same prolongation, and a regular algebraic polarized cuspidal form \(P\) over \(M\) such that:

- \(r|_{G_M}\) is weakly attached to \(P\), and the infinitesimal character of \(P\) at any complex embedding of \(M\) equals that of \(\pi\) at its restriction to \(E\).
- The normalized local component \(T^{\mathrm{alg}}\) of \(T=P_u\) has unlinked rank-one support and admits an extended local Langlands correspondence \(\operatorname{rec}'\).
- For every inertia element \(t\) downstairs, there is an inertia element \(t'\) upstairs that is the same automorphism of \(\Omega\), with
  \[
  \det(X-\operatorname{rec}'(T^{\mathrm{alg}})(t'))
  =\det(X-\operatorname{rec}(\sigma^{\mathrm{alg}})(t)).
  \]

This lift uses an extension unramified at the selected place, so all of the downstairs inertia acts upstairs. The proof uses a [depth-zero support comparison and a tower of cyclic prime-degree base changes](residue-degree-divisibility-turns-mixed-depth-zero-support-toral.md). [Lifting input](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/PAdicSplitting/InfLifts.lean#L40) · [Construction in Lean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/PAdicSplitting/PToTor.lean#L61)

Apply the toral theorem to \(P\) and \(r|_{G_M}\) at \(u\). Away from \(\ell\), it identifies the Weil–Deligne parameter upstairs with \(\operatorname{rec}'(T^{\mathrm{alg}})\), which has zero monodromy. Compatibility of the Weil–Deligne construction with restriction to \(M_u/E_w\) implies zero monodromy downstairs and gives the same characteristic polynomial at \(t\) as upstairs at \(t'\). The displayed equality then identifies this polynomial with that of \(\operatorname{rec}(\sigma^{\mathrm{alg}})\).

At \(w\mid\ell\) the toral theorem makes the restriction potentially semistable, which implies potential semistability downstairs. In compatible local bridges, restriction of its Weil–Deligne parameter again preserves characteristic polynomials at elements inducing the same automorphism. Monodromy vanishes upstairs and hence downstairs. For each \(t\) use the corresponding \(t'\) in the lift and the equality displayed above. This proves the comparison on the entire inertia group. [Restriction argument in both cases](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/PAdicSplitting/R2g.lean#L14)

## Returning the de Rham jumps

For the de Rham condition and jumps one needs an auxiliary lift at each chosen prolongation. The existence of extended local correspondences lets the proof apply `ToTor` anew to give that lift. On the lift the toral theorem supplies the jumps \((n-1)/2-z\) at each embedding of \(M\). For any induced embedding of the downstairs completion into the coefficient field, extend it to the upstairs completion, enlarging the finite coefficient field as needed. The infinitesimal-character law ensures that the expression upstairs uses the same \(z\) as downstairs. Descent of the filtered de Rham module along the finite extension gives de Rham comparison and preserves each graded multiplicity at these paired embeddings. The resulting jump multiset is the one in the statement. [Descent of the filtration](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/PAdicSplitting/PDrDesc.lean#L10) · [Combining the two branches](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SphericalGaloisCompatibility/PAdicSplitting/LocalGlobalCompatAtIwahoriFixedOfUnlinked.lean#L18)

The restriction comparison here is indexed by inertia elements. The auxiliary statement supplies polynomial equality on that group, which is the conclusion needed for the principal-congruence clause.


Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
