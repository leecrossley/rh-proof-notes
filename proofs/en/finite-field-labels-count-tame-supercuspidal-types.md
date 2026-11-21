# Finite-field labels count tame supercuspidal types

[Chinese proof](../zh/%E6%B8%A9%E5%92%8C%E8%B6%85%E5%B0%96%E7%B1%BB%E5%9E%8B%E6%80%8E%E6%A0%B7%E7%94%B1%E6%9C%89%E9%99%90%E5%9F%9F%E6%A0%87%E7%AD%BE%E8%AE%A1%E6%95%B0.md)

## Statement

Let $K=E_w$ be a local number field completion isomorphic topologically to $\mathbb Q_p$, with residue size $q$, and choose Weil Frobenius $\Phi_-$ of degree $-1$. Assume local Langlands with `IsRecT`. For $n\ge1$, if $\pi$ is irreducible smooth supercuspidal on $\mathrm{GL}_n(K)$ and $\operatorname{rec}(\pi)$ is trivial on wild inertia, then $\pi^{K_1}\ne0$ for $K_1=1+\mathfrak m_KM_n(\mathcal O_K)$. The conclusion is `dz_of_cusp`.

## An upper count of Weil parameters

Fix $c\in\mathbb C^\times$ and let $\mathcal T(n,c)$ be tame Weil–Deligne classes of rank $n$ with irreducible Weil part and determinant $c$ at $\Phi_-$. The nilpotent operator vanishes since its nonzero kernel is stable. Let $\mathcal L_n$ be monic irreducibles of degree $n$ over $\mathbb F_q$ excluding $X$. For a tame generator $\gamma$, put $M=r(\gamma)$, $G=r(\Phi_-)$. The convention is $MG=GM^q$. Since $M$ has finite order, it is diagonalizable, and $G$ carries $V_z$ to $V_{z^q}$. The orbit of $z$ has length $d$. Choose a $G^d$ eigenvector $v$ in $V_z$. The vectors $v,Gv,\ldots,G^{d-1}v$ are independent by distinct $M$ eigenvalues and span a subspace stable under $M,G$. Irreducibility gives $d=n$. In this basis $G$ shifts cyclically with final factor $(-1)^{n-1}c$. Thus the orbit and determinant determine the isomorphism class.

Now $z^{q^n}=z$ and $z\ne0$. Identify $(q^n-1)$st roots in $\mathbb C$ with $\mathbb F_{q^n}^\times$ by chosen generators. The map commutes with the $q$th power, so the image of $z$ has minimal polynomial of degree $n$. Its label in $\mathcal L_n$ determines the orbit and hence the parameter for fixed $c$. This gives the injection $\mathcal T(n,c)\hookrightarrow\mathcal L_n$.

## A lower count of depth-zero representations

The inputs `St7`, `St4`, `St6` and `St5` give: each label $P$ gives an irreducible finite-group supercuspidal $\tau_P$ on $\mathrm{GL}_n(\mathbb F_q)$, distinct labels give distinct types, and inflation to $\mathrm{GL}_n(\mathcal O_K)$ embeds in a smooth irreducible supercuspidal $Y_P$ with central character taking any prescribed nonzero value $c$ at the uniformizer $\varpi$. Its $K_1$-invariants are exactly this type. Hence $Y_P$ are depth zero and pairwise nonisomorphic by their invariants.

Take $\varpi$ corresponding to $\Phi_-$ under reciprocity and $c=\det\operatorname{rec}(\pi)(\Phi_-)$. Local Langlands gives each $Y_P$ an irreducible rank-$n$ Weil parameter, tame by depth zero, of the same determinant by the central character condition. Its injectivity for these representations gives $\mathcal L_n\hookrightarrow\mathcal T(n,c)$. Composing with the first injection gives a bijective self-map of the finite label set. The label of $\operatorname{rec}(\pi)$ is therefore reached by a $Y_P$. Uniqueness for a label gives equal parameters, and injectivity of the correspondence with this depth-zero member gives $\pi\simeq Y_P$. This proves the invariant statement used in the [tame repeated-root criterion](tame-inertia-repeated-roots-exclude-repeated-higher-rank-types.md).

## Lean correspondence

- [`St1a` through `St3`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/GaloisPermutationReps/SubquotientEquivalence/IsTypeMap.lean#L30) and [the matrix label comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/GaloisPermutationReps/SubquotientEquivalence/IsUnitRho.lean#L40) count the Weil parameters.
- [`TameSet` and `Lab`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/GaloisPermutationReps/SubquotientEquivalence/IsTypeMap.lean#L14) give the sets, and [`st8a`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/GaloisPermutationReps/SubquotientEquivalence/HasCentralCharOfEquiv.lean#L83) builds the depth-zero labels.
- [`depth_zero_intermediate_holds` and `depth_zero_count_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/WeilBound/RepresentationTheoryGL/GaloisPermutationReps/SubquotientEquivalence/DepthZeroIntermediateHolds.lean#L15) assemble the counts. [`dz_of_cusp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/IntegralStructures/InertCharpoly/CharPolOfInert.lean#L114) applies them.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
