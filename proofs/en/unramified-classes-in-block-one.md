# Block one's global classes are ideal class group characters

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%80%E5%8F%B7%E5%9D%97%E7%9A%84%E5%85%A8%E5%B1%80%E6%9D%A1%E4%BB%B6%E5%8F%AA%E7%95%99%E4%B8%8B%E7%B1%BB%E7%BE%A4%E7%89%B9%E5%BE%81.md)

**Proposition.** Let $E$ be a number field, $\ell$ prime and $\mathcal O$ a DVR finite over $\mathbb Z_\ell$, with $\ell$ nonzero and noninvertible. Set $K=\operatorname{Frac}\mathcal O$, $e=\operatorname{ord}_{\mathcal O}(\ell)$. Let $G_E$ act trivially on the discrete module $M=K/\mathcal O$. Assume either $\ell\ne2$ or $E$ has no real embeddings. If $S\subseteq H^1(G_E,M)$ is a submodule represented by continuous cocycles unramified at every finite place, then
$$
\operatorname{length}_{\mathcal O}S\le e\,v_\ell(h_E),\qquad h_E=|\operatorname{Cl}(\mathcal O_E)|.
$$
Equality holds for the full submodule of such classes.

With trivial action a cocycle is an additive homomorphism and all coboundaries vanish. Thus an unramified class is represented by a homomorphism vanishing on inertia. In the project each finite inertia group is covered by one of two families of subgroups on which the global condition requires vanishing, or by a locally prescribed unramified condition. Compactness of $G_E$ and discreteness of $M$ make the image finite. At any real place, complex conjugation has order at most two, and the hypothesis gives $\ell$ odd, so $M$ has no nonzero $2$-torsion. The homomorphism therefore vanishes there too.

The Hilbert class field theorem identifies the maximal everywhere unramified abelian quotient, with real places remaining real, with the ordinary ideal class group via the Artin map. The full module is therefore $\operatorname{Hom}(\operatorname{Cl}(\mathcal O_E),M)$. If the class group decomposes into cyclic groups of orders $n_j$, the corresponding Hom summands are $M[n_j]\simeq\mathcal O/(n_j)$ of lengths $e v_\ell(n_j)$. Summing gives $e v_\ell(h_E)$, and the submodule $S$ has no larger length. [Milne, Class Field Theory, Chapter V, Theorem 3.6 and Example 3.9](https://www.jmilne.org/math/CourseNotes/CFT.pdf#page=168)

## Lean correspondence

- `vhEInChi` checks the inertia coverage for block one in `realDisplayAllK_of`. [Coverage](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/CupProductVanishing/CupProductProofs/CoboundaryTrivialActionZero.lean#L49) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/RealDisplayAllKOf.lean#L146)
- `GlobalTheory.UnramifiedClassBound.vhE_of_globalArtinReciprocity` applies global Artin reciprocity, and `length_unrHom_le` gives the normalized form. [Class number](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/UnramifiedGaloisHomsBoundedClassNumberOfArtinRec.lean#L16) · [Normalization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/UnramifiedHomsBoundedByClassNumberOfArtin.lean#L48)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
