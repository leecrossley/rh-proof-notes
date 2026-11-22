# The type-local test transforms by its flag character

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be a number field, $P$ a nonzero prime of $\mathcal O_E$, $A=\mathcal O_{E,P}$ with residue field $\kappa$, and $q=|\kappa|$. Let the coefficient field be $K$. The reduction of an integral matrix is denoted with a bar. For the characters, flag parameters $k,s,r,t$ and phases $\Lambda_j$ in the [residue-field calculation](the-type-level-phase-is-multiplicative-on-flag-matrices.md), fix $i\ge0$ and put $a=r+it$ and $b=a+t$. Write $X_{[a]}$ for the leading $a$ by $a$ square of a matrix $X$ with at least $a$ rows and columns. Define a function of $b$ by $a$ matrices over $E$ by
$$
\Phi(X)
=\Lambda_i(\overline{X_{[a]}})\,
\chi_{i,0}(\det\overline{X_{[a]}})^{-1}
$$
when $X$ has integral entries, the rows with indices at least $a$ have entries in $qA$, and $\overline{X_{[a]}}$ obeys the flag conditions `Pat`. Set $\Phi(X)=0$ when any of the three conditions fails. In the displayed formula the inverse of zero is taken to be zero, as in the source field convention.

For a dimension $d\in\{a,b\}$ let the level consist of matrices $G\in\mathrm{GL}_d(A)$ with these conditions. In each of the first $r$ columns, the reduction has diagonal entry $1$ and the zero positions from `Pat`, now with all $d$ rows tested. At every boundary $r+jt$ with $j\ge0$, the entries in rows at or below the boundary and columns before it belong to $qA$. In the application, $G$ is the matrix of a source or target level automorphism in the adapted bases, and its inverse has the same conditions. For such a source matrix $G$ of size $a$ and target matrix $H$ of size $b$,
$$
\begin{aligned}
\Phi(XG)\chi_i(\overline{\det G})&=\Lambda_i(\bar G)\Phi(X),\\
\Phi(HX)\chi_i(\overline{\det H})&=\Lambda_{i+1}(\bar H)\Phi(X).
\end{aligned}
$$
The source formula also allows $b\ge a$ arbitrary. These laws are the type cases of `phiAt_source` and `phiAt_target` on the ordinary steps $i+2\le m$.

### Adapting the basis to the level

The original vector space at a layer has $n$ ordinary coordinates followed by $c$ extra coordinates. Fix the position $k_0\le n$ at which to insert the extra coordinates into the ordered basis. Move them, in order, immediately after the first $k_0$ ordinary coordinates, and scale extra vector number $l$ by $q^{l+1}$ for $l=0,\ldots,c-1$. The resulting vectors form a basis of the reference lattice over $A$, called `lamY`. The matrix `entB` is exactly the matrix between these bases at the source and target. Each entry is the corresponding permuted original matrix entry times the source scaling divided by the target scaling. It therefore respects composition, by cancellation of the intermediate basis changes, and preserves determinants on endomorphisms.

The local group `JG` preserves the reference lattice and certain sublattices obtained by multiplying a suffix of this basis by $q$. If the input index is before the suffix and the output index in it, preservation of this sublattice forces the matrix entry to belong to $qA$. At each of the first $r$ positions the additional condition on the difference of the basis vector and its image forces that column to reduce to the basis column in all rows at or after its position. In fact the difference lies in the lattice with that suffix scaled by $q$. This gives the flag pattern with the ordinary order and the diagonal ones.

The sharp type group `JGsym` uses the order with $k=k_0$ and $s=r_S$ described in the residue-field calculation. It scales suffixes in this order. At position $k+s$ the suffix starts instead at the order index $s$, the beginning of $[0,k)$ in that order. The condition on the basis vector there forces the extra zeros of its column in all rows $p<k$. At a boundary $r+jt$, the suffix is the set of ordinary indices at least $r+jt$, since the strict chain inequality $k_0+r_S<r$ places the exceptional boundary before these cuts. Thus the level matrices meet exactly the divisibility and reduction conditions needed in the stated laws. Since they preserve the reference lattice in both directions, their matrices and inverses are integral and their determinants are units. The scalar determinant factor `muAt` on such a unit is just $\chi_i$ of its reduction, since the local valuation is zero.

### Source multiplication

Suppose $X$ passes the three support tests. The integral product $XG$ still has its lower rows in $qA$, by right multiplication. Its leading square reduces to $\overline{X_{[a]}}\,\bar G$. The cut conditions on $G$ imply the side-block flag conditions in the reduction because $q\in P$, and the first $r$ columns have the required pattern by assumption. Thus the residue-field calculation shows that the product still has the flag pattern and its phase is $\Lambda_i(\overline{X_{[a]}})\Lambda_i(\bar G)$.

The leading determinant of this product is $\det(\overline{X_{[a]}})\det(\bar G)$. The extended character is multiplicative and its value at $\det(\bar G)$ is nonzero. Taking inverses, with the zero convention as above, gives the source identity. In particular the argument works when the leading determinant of $X$ vanishes.

### Target multiplication

In the lower rows of $HX$, split the sum over intermediate indices at $a$. For an index below $a$, the contribution belongs to $qA$ by the boundary condition for $H$ at $a=r+it$. For an index at or above $a$, the entry of $X$ belongs to $qA$. Hence the lower rows stay in $qA$. In the leading square, the intermediate indices at or above $a$ vanish after reduction, again by the lower-row condition on $X$. It follows that
$$
\overline{(HX)_{[a]}}=\overline{H_{[a]}}\,\overline{X_{[a]}}.
$$
This product has the flag pattern, and its phase is the product with $\Lambda_i(\overline{H_{[a]}})$.

Let $D$ be the final $t$ by $t$ diagonal block of $\bar H$. The same boundary condition makes $\bar H$ upper block triangular for the cut at $a$. Therefore
$$
\det\bar H=\det\overline{H_{[a]}}\cdot\det D
$$
and both factors are nonzero. Multiplying by the full determinant character cancels the inverse character of $\det\overline{H_{[a]}}$ in $\Phi(HX)$ and leaves $\chi_i(\det D)$. The remaining factor $\Lambda_i(\overline{H_{[a]}})\chi_i(\det D)$ is precisely $\Lambda_{i+1}(\bar H)$, which supplies the target identity.

Finally, if $X$ fails the support tests, neither transformed matrix passes: stability for the inverse level matrix would bring it back to $X$. Both identities then have zero on each side. In the chain, the adapted dimensions at successive ordinary layers are $r+it$ and $r+(i+1)t$, so the formulas apply directly to `PhiG` and `PhiGS` with the nonsymmetric and sharp characters respectively.

### Lean correspondence

- [`entB`, `JG`, `JGsym`, `PhiG` and `PhiGS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L692) define the adapted matrix, levels and local tests. [`entB_comp` and `entB_det`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L416) justify composition and determinants.
- [`ent_div`, `ent_col`, `levG_of_JG` and `levG_of_JGsym`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L540) extract the congruences from the preserved lattices. [`locChar_unit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/MemZmuOfPowPred.lean#L111) identifies the determinant character on units.
- [`SuppG.source` and `SuppG.target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L348) give the matrix calculations with support. [`ite_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L635) extends them to all arguments. [`phiM_source` and `phiM_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L692) transport them back to the linear maps. [`phiAt_source` and `phiAt_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L819) make the ordinary-step application.

Status. Source-based reconstruction draft. These laws are inputs to the [ordinary point covariance](the-ordinary-point-kernel-transforms-with-the-level-characters.md) before unfolding. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
