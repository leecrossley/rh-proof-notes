# The point tests recover the localized class form lattice

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Fix a layer $0\le i\le m$ of the true column chain for the word prime $T$. Use the [split point realization](constructing-the-point-model-by-a-torsion-quotient.md), the [word-prime embedding test](choosing-the-embedding-that-sees-each-split-word-prime.md) and the [local value lattice](a-local-frame-identifies-the-weyl-value-lattice.md). The host field is $E$, the coefficient field is $K$, and $C$ is the finite set of arithmetic classes at this layer. Write $d_c$ for the chosen arithmetic representative of $c$ and $p_c=\operatorname{pt}(d_c)$ for its point. Let $\phi$ be a complex class form: its values are in the polynomial value space and are fixed by the indicated character-twisted actions of the stabilizers of the representatives. Let $\mathscr F_K$ be the coefficient-field form space, defined by the same fixed-value conditions over $K$.

An arithmetic point $d$ has self-dual lattice $N(d)$ and local residue functionals at the selected primes. Write $L^\sharp(d)$ for the Hermitian dual of the simultaneous kernel sublattice in $N(d)$. For a full host lattice $M\subset E^n$ write $W_w(M)=\operatorname{ev}(\mathcal O_{K,w}\Delta(M))$, where $\operatorname{ev}$ is coefficient evaluation and $\Delta(M)$ is the global Weyl value lattice.

For $w\nmid T$ the point-coordinate lattice `Woff` is an additive subgroup attached to the off-prime component $z$ of a point. Write it as $W^{\rm off}_w(z)$. It is equivariant under the point group, and at an arithmetic point it satisfies
$$
W^{\rm off}_w(\operatorname{pt}(d)_{\rm off})=W_w(L^\sharp(d)).
$$
Consequently the existence of a preimage of $\phi$ in the localized coefficient-field class form lattice with value lattices $\Delta(L^\sharp(d_c))$ is equivalent to testing each $\phi(c)$ in the following point value sets. At $w\mid T$ use the ordinary test $V_{w,\varnothing}(p_c)$, and at $w\nmid T$ use $W^{\rm off}_w((p_c)_{\rm off})$. At a selected-side $w\mid T$ the same equivalence holds with the single-kernel point test $V_{w,\{P_0\}}(p_c)$ and the coefficient value lattices $\Delta(L^\sharp_{P_0,\ker}(d_c))$ for a fixed selected $P_0$.

### The test away from the word prime

The definition uses every way of presenting the off-prime component. A value $y$ belongs to $W^{\rm off}_w(z)$ if for every point group element $g$ and arithmetic point $d$ with $(g\operatorname{pt}(d))_{\rm off}=z$ we have
$$
g^{-1}y\in W_w(L^\sharp(d)).
$$
Thus it is an intersection of additive subgroups transported into the same value space. If $y$ satisfies the tests at $z$, then $hy$ satisfies them at $hz$: for a presentation $g\operatorname{pt}(d)$ of $hz$, apply the original test with $h^{-1}g$, obtaining $(h^{-1}g)^{-1}y=g^{-1}hy$. The inverse of $h$ gives equivalence in the opposite direction. Here the group action on the off-prime coordinate depends only on that coordinate, as checked in the point quotient.

For an arithmetic point $d_0$, using the presentation $1\operatorname{pt}(d_0)$ gives the inclusion in $W_w(L^\sharp(d_0))$. For the converse let $y$ belong to this latter lattice and consider an arbitrary presentation $g\operatorname{pt}(d)$ with the same off-prime component. Decompose $g=\zeta h$ into a central torsion element $\zeta$ and the image $h$ of an arithmetic frame transformation at the label of $d$. The equality of off-prime components puts $d_0$ at the same label and gives a frame transformation $k$ of rational matrix $1$ with $khd$ and $d_0$ having equal off-prime data. This is the quotient relation proved in the point realization.

The sharp lattice agrees with $N$ away from the conjugates of the selected primes. In fact the primal kernel lattice equals $N$ away from the selected primes, by localization of the residue functionals. Taking Hermitian duals moves these possible changes to their conjugates, since $N^\#=N$. Every contraction of $w$ into $E$ along an embedding $\iota_\tau:E\to K$ is away from $T$, since $T\notin w$. At these contractions the sharp lattices of $khd$ and $d_0$ agree by equality of their off-prime data. A frame matrix equal to $1$ fixes the host lattice, so the sharp lattice of $khd$ is the same as that of $hd$. Extending the localized lattices to $\mathcal O_{K,w}$, taking ordinary dot-product duals and applying the local frame rule thus gives
$$
W_w(L^\sharp(d_0))=W_w(L^\sharp(hd)).
$$

Multiplication by $\zeta^{-1}$ preserves the last value lattice. The underlying scalar in $K$ satisfies a monic equation $X^r-1=0$, and its inverse satisfies the same equation, so both are in $\mathcal O_K^\times$. The arithmetic coordinate action for $h^{-1}$ takes $W_w(L^\sharp(hd))$ to $W_w(L^\sharp(d))$. To see the lattice part directly, if a frame matrix $\gamma$ sends a host lattice $M$ to $\gamma M$, the local dot-product dual bases are multiplied on the left by the inverse transposes of the embedded matrices $\iota_\tau(\gamma)$. The transported coefficient lattice is therefore obtained by the same action $\rho_\lambda$ of the inverse transposes. The character factor is another torsion unit. On evaluation this is the complex frame action, since coefficient embedding commutes with substitution and scalar multiplication. Applying $\zeta^{-1}$ and then $h^{-1}$ proves $g^{-1}y\in W_w(L^\sharp(d))$. This verifies all presentations.

### One denominator for all class values

For any choice of full host lattices $M_c$ at the representatives, the global coefficient form lattice consists of the rows $F\in\mathscr F_K$ with $F(c)\in\Delta(M_c)$ for every $c\in C$. A row in its localization at $w$ has all components locally in $\mathcal O_{K,w}\Delta(M_c)$, since a single scalar outside $w$ brings the whole row into the global lattice.

For the converse suppose that each $\phi(c)$ equals $\operatorname{ev}(F_c)$ for some $F_c\in\mathcal O_{K,w}\Delta(M_c)$. Each $F_c$ is unique by injectivity of coefficient evaluation. The complex stabilizer at $c$ fixes $\phi(c)$. The character-twisted action on the coefficient space intertwines with its complex action under evaluation. Therefore the coefficient stabilizer fixes $F_c$, again by injectivity. Thus the tuple $(F_c)_c$ belongs to $\mathscr F_K$. Choose a denominator $s_c\in\mathcal O_K\setminus w$ with $s_cF_c\in\Delta(M_c)$ for every class. The product $s=\prod_{c\in C}s_c$ is outside $w$ since $w$ is prime. It clears every component's denominator, so the tuple is in the desired localized form lattice. The same argument shows the preimage is unique.

Now use the tested lattices in the statement. At a word place, the [selected and conjugate coordinate comparison](reading-the-word-prime-value-lattice-in-point-coordinates.md) identifies the point tests at each arithmetic representative with the indicated $W_w(M_c)$. Away from the word prime use the equality just proved. Applying the classwise argument proves all three form tests.

### Compatibility of polynomial coordinates with the action

The point group acts by a rational unitary matrix $\gamma$ and a torsion scalar. At a word place $w$, take the coordinate move for the tuple of matrices induced by $\gamma$ at the selected primes. The matrix in its block $\tau$ is $(\iota_\tau(\gamma)^{-1})^{\mathsf t}$ in the selected case and $\iota_\tau(\bar\gamma)$ in the conjugate case. These are equal by $\gamma^*\gamma=1$. The polynomial coordinate of the action is therefore the point coordinate move times the embedded torsion scalar. This checks the action compatibility in `Coord.Ok`. The off-prime equivariance and form tests give its other conditions. Along with the value comparisons at all selected kernels, this yields the coordinate witness `exists_coord`.

### Lean correspondence

- [`woff` and `mem_woff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L103) use every presentation of the off-prime component. [`Real.fst` and `Real.gen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/KerIsTerm.lean#L125) give the required identifications and factorization.
- [`locP_Lsh_off` and `delAtr_off`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemClosureIff.lean#L266) transport off-prime lattice equality to the coefficient lattice. [`wl_hom`, `wl_zeta`, `woff_pt` and `woff_act`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L326) use the two actions and give off-prime equivariance.
- [`forms_iff` and `valIn_iff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L281) give the finite denominator argument and compare the tests. [`gm_unit`, `coord_ok` and `exists_coord`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsCoordinatesValueLatticesEqWeylLattices.lean#L381) give the action and package the coordinate witness.

Status. Source-based reconstruction draft. The statement uses finite arithmetic classes and the split point realization with its character-twisted actions. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
