# The mass of a definite self-dual lattice is the standard mass

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM quadratic extension unramified at every finite place. Let $(V,h)$ be a nondegenerate Hermitian $E$-space of rank $r$ with positive signature $(r,0)$ at every complex embedding of $E$. Let $L$ be a full self-dual $\mathcal O_E$-lattice in $V$. Write $h_{\mathrm{st}}$ for $\bar x^t y$ on $E^r$ and $S=\mathcal O_E^r$ for its standard lattice. Then
$$
\operatorname{Mass}(h,L)=\operatorname{Mass}(h_{\mathrm{st}},S).
\tag{1}
$$
Here $\operatorname{Mass}(h,L)$ means the sum of inverse automorphism orders over the rational isometry classes in the genus of $L$, as in [the finite-adelic comparison](finite-adelic-classes-recover-the-hermitian-genus-mass.md). The right side for the host field and rank $r$ is `massI D r`. The column class-number formula uses (1) in rank $k$, with $L$ the self-dual overlattice in the first host space.

### The two forms are locally isometric

At every finite place of $F$, [a local integral frame](a-self-dual-lattice-has-an-integral-frame-at-each-finite-place.md) identifies $(V_v,h_v,L_v)$ with the standard form and lattice. In particular it gives an isometry of the local Hermitian spaces. At a real place of $F$, the extended scalar algebra is $\mathbb C$ with conjugation. A positive definite Hermitian form has an orthonormal basis by ordinary complex Gram–Schmidt, so the two spaces are also isometric there.

Apply Landherr's local–global theorem in the following form. Two nondegenerate Hermitian forms of the same dimension over a quadratic extension of number fields, with adjoint involution the nontrivial automorphism, are isometric over that extension if at every place of the fixed field they become isometric after scalar extension to its completion. At a split place this uses the quadratic product algebra with exchanged factors. All the local hypotheses have just been checked. Thus there is an $E$-linear isometry $\phi:V\to E^r$. In the Lean proof the local–global step is obtained from the quadratic Hasse norm theorem. [Landherr, “Äquivalenz Hermitescher Formen über einem beliebigen algebraischen Zahlkörper”, 1935, p. 247](https://webhomes.maths.ed.ac.uk/~v1ranick/papers/landherr.pdf#page=3)

### Transport the genus, then compare it with the standard genus

Any $E$-linear isometry sends lattices to lattices, commutes with their scalar extensions to the local orders, and conjugates their automorphism groups. It therefore gives a bijection on the isometry classes in the genera and preserves every mass term. Hence
$$
\operatorname{Mass}(h,L)=\operatorname{Mass}(h_{\mathrm{st}},\phi L).
$$
The lattice $\phi L$ is again self-dual. Indeed $h_{\mathrm{st}}(\phi y,\phi x)=h(y,x)$ for all $y,x$, so integrality against $L$ and against $\phi L$ are equivalent. The local integral frame theorem applied to $\phi L$ now gives a local isometry of the *lattices* $(\phi L)_v$ and $S_v$ at every finite $v$, within the standard Hermitian space. Thus they lie in the same genus. For any third lattice, composing its local isometries with these shows that it is in the genus of $\phi L$ exactly when it is in the genus of $S$. The inverse stabilizer weights in this common genus are the same, proving (1).

This identification makes the [word-prime rank comparison](a-short-prime-window-controls-the-column-dimension.md) use one fixed mass for the changing local overlattice. The local stabilizer index accounts for the changing level.

### Lean correspondence

- [`exists_isometry`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnramifiedOfIsCMUnram.lean#L45) applies the Landherr congruence theorem under the host unramified and positive-signature conditions.
- [`inGenus_of_selfDual`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/UnitaryExistence/FiniteNotIsUnitOneAddSmul.lean#L384) gives an isometry localized at each rational prime. [`sameGenus_stdLat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnramifiedOfIsCMUnram.lean#L103) transfers this to the Hermitian semilocal genus by denominators prime to the rational prime below the chosen place.
- [`mass_eq_std`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnramifiedOfIsCMUnram.lean#L126) transports mass along the global isometry and uses equality of genera. [`mass_eq_massI`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnramifiedOfIsCMUnram.lean#L147) specializes (1) to the host CM data. [`mass_selfDualLattice_firstSpace_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/MassSelfDualLatticeFirstSpaceEq.lean#L96) applies this to the self-dual lattices in the first space.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
