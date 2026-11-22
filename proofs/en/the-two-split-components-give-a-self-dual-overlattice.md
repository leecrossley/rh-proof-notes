# The two split components give a self-dual overlattice

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setting and conclusion

Let $E/F$ be the host CM extension, and $V$ the first Hermitian space over $E$. Fix a word with rational prime $T$, and let $\Lambda$ be its full integral base lattice. Write $\Lambda^\#=\{y:h(x,y)\in\mathcal O_E\text{ for all }x\in\Lambda\}$ for its Hermitian dual. The level record assumes
$$
T\Lambda^\#\subseteq\Lambda\subseteq\Lambda^\#,\qquad
[\Lambda^\#:\Lambda]=T^{2f},\qquad f=[F:\mathbb Q].
\tag{1}
$$
Assume $T$ has $f$ places $v$ in $F$, each with residue field of size $T$. Write $\Lambda_v,\Lambda_v^\#$ for the completed lattices at $v$. At $v\mid T$ there is a module $M_v$ of cardinality $T$ over the integer ring of $E\otimes_F F_v$, and an integral-linear map $f_v:\Lambda_v^\#\to M_v$ that is nonzero and vanishes on $\Lambda_v$. The local level at $v\mid T$ preserves $\Lambda_v$ and fixes $f_v$. Elsewhere it preserves $\Lambda_v$. The host extension is unramified at the finite places. These are the base, dual and functional conditions in the column level data.

**Conclusion.** There is a full self-dual $N$ with $\Lambda\subseteq N\subseteq\Lambda^\#$, equal to $\Lambda$ locally away from $T$, which is preserved by the prescribed local and adelic levels. At each $v\mid T$, $E\otimes_F F_v\simeq F_v\times F_v$, with an ordering such that $N_v$ consists of the first component of $\Lambda_v^\#$ and the second component of $\Lambda_v$. In a frame for the first component the level inside the stabilizer of $N_v$ is the inverse image of the stabilizer of a nonzero row over $\mathbb F_T$. This is the reference case used by the [level-index formula](the-column-level-index-factors-into-finite-field-indices.md).

## Choosing the two residue functionals

The additive group of $M_v$ has prime order $T$, so its endomorphism ring is $\mathbb F_T$. The scalar action gives a unital homomorphism from the integer ring of $E\otimes_F F_v$ to $\mathbb F_T$. The inert alternative for this unramified degree-two algebra would give a local ring with residue field $\mathbb F_{T^2}$. Any unital map to $\mathbb F_T$ would have maximal-ideal kernel and hence require an embedding of that residue field, which is impossible. Thus the algebra splits. The integer ring is $\mathcal O_{F_v}\times\mathcal O_{F_v}$, and precisely one of its two idempotents maps to $1$. Order the factors so that this is the first. The involution exchanges the factors, so the Hermitian form pairs the two components nondegenerately. The map $f_v$ uses just the first component and identifies its image with the first residue module. It is onto since its nonzero image has prime order.

Choose $x\in\Lambda_v^\#$ supported on the first component with $f_v(x)\ne0$. Then $x\notin\Lambda_v$. Double duality for local lattices gives $y\in\Lambda_v^\#$ with $h(x,y)$ nonintegral. To see the double-dual identity, use dual bases on the two factors and test coordinates against the basis vectors of the original lattice. The value $h(x,y)$ is supported on the second coefficient component. Write $\ell(y)$ for that component. There is an element $y_0$ for which $\ell(y_0)$ has least valuation: $T\ell(y)$ is integral on $\Lambda_v^\#$ by (1), and some value is nonintegral. Thus the least valuation is a finite negative integer. The second functional
$$
f_{2,v}(y)=\ell(y)/\ell(y_0)\pmod{\mathfrak m_v}
$$
is well-defined. It is onto because it takes value $1$ at $y_0$. It vanishes on $\Lambda_v$ because the pairings there were integral before dividing, and it vanishes on all vectors supported on the first component. The two maps act on disjoint components, so $(f_v,f_{2,v})$ is onto a group of order $T^2$.

## The global index forces the kernels

The reductions of $\Lambda^\#$ modulo $T\Lambda^\#$ realize arbitrary specified local reductions at all $v\mid T$, by the Chinese remainder theorem on the module over $\mathcal O_F/(T)$. Equivalently, one may approximate all these local vectors by one global vector with errors in $T\Lambda_v^\#$. This description applies to completions because the quotient at each $v\mid T$ is a finite module supported at $v$, hence passage to the completion preserves it.

Both local functionals vanish on $T\Lambda_v^\#$. The simultaneous map from $\Lambda^\#$ to $\prod_{v\mid T}(M_v\times\mathbb F_T)$ is consequently onto, with kernel containing $\Lambda$. Its index is $T^{2f}$. Equality of the two finite indices in (1) shows that its kernel is exactly $\Lambda$. It follows also that at each $v$ the kernel of the local pair is $\Lambda_v$. In detail, approximate a local kernel element at $v$, and zero at the other places over $T$, by one global element. Its residues put it in the global kernel, and its error at $v$ is already in $\Lambda_v$.

## Gluing and identifying the stabilizer

At $v\mid T$ define $N_v$ by taking the full first component of $\Lambda_v^\#$ and the second component of $\Lambda_v$. The first is exactly the lattice dual to the second under the split Hermitian pairing. Taking the dual in this paired form exchanges the two components and dualizes them, so $N_v$ is self-dual. Away from $T$ use $\Lambda_v$, which is self-dual there because $T$ is a unit and (1) gives $\Lambda_v^\#=\Lambda_v$.

Define $N\subseteq\Lambda^\#$ by requiring its local component at each $v\mid T$ to lie in $N_v$. It is a full finitely generated integral lattice since it lies between $\Lambda$ and the full lattice $\Lambda^\#$. Its completions are exactly those specified. Indeed a prescribed $N_v$-vector can again be approximated modulo $T\Lambda_v^\#$ at $v$ and by zero at the other places over $T$. The resulting vector is in $N$, and the error lies in $\Lambda_v$. Global duality follows from integrality at every place, or by comparing completions of $N$ and $N^\#$. This is the lattice `overLat`, expressed using the two projections at each split place.

At $v\mid T$, a unitary matrix is determined by its first component. Its second component is the dual inverse with respect to the pairing. Therefore the stabilizer of $N_v$ identifies, in a basis of its first component, with $\mathrm{GL}_k(\mathcal O_{F_v})$. The kernel of $f_v$ in the first component of $\Lambda_v^\#$ is the first component of $\Lambda_v$, by the two-functionals calculation. The second component of $\Lambda_v$ is already part of $N_v$. Hence in this stabilizer, fixing the functional $f_v$ already ensures preservation of $\Lambda_v$. The level condition is exactly fixing the row modulo the maximal ideal in the lattice frame. The row is nonzero since $f_v\ne0$, and it factors through reduction because the scalar action on $M_v$ is through the residue field. Thus the local level preserves $N_v$ and has the asserted form. Away from $T$, the original level preserves $\Lambda_v=N_v$. The adelic level preserves $N$ by testing at all places.

## Lean correspondence

- [`exists_local`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemLocLatOverLat.lean#L442) uses the prime-order action to choose the first residue factor. [`exists_second_functional`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsSecondFunctional.lean#L59) provides the second functional by normalizing a pairing of least valuation.
- [`mem_of_count`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemLocLatOverLat.lean#L105) matches the global index with the product of the two-residue quotients. [`overLat` and `mem_locLat_overLat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemLocLatOverLat.lean#L535) glue the full lattice and check its completions.
- [`exists_overLattice`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemLocLatOverLat.lean#L582) supplies self-duality and stability. [`localAtT_of_overAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/OverLatticeIffSelfDualOverBase.lean#L19) transports the local frame and nonzero row data. [`selfDualOverBase`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SelfDualLatticeOverColumnBaseLattice.lean#L8) is the theorem used in the [class-number argument](the-column-class-number-is-the-genus-mass-times-the-level-index.md).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
