# A self-dual lattice has an integral frame at each finite place

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be a CM quadratic extension unramified at every finite place of $F$, with conjugation $x\mapsto\bar x$. Let $V=E^r$ and $h(x,y)=\bar x^tJ y$, where $J\in\mathrm{GL}_r(E)$ satisfies $J^*=J$. Let $N\subset V$ be a full finitely generated $\mathcal O_E$-lattice satisfying
$$
N=N^\#=\{x\in V:h(N,x)\subseteq\mathcal O_E\}.
$$
For a finite place $v$ of $F$, write $E_v=E\otimes_F F_v$, $R_v=\mathcal O_E\otimes_{\mathcal O_F}\mathcal O_{F_v}$, and $N_v=R_vN$. There is a matrix $B\in\mathrm{GL}_r(E_v)$ such that
$$
B^*J B=I_r,\qquad N_v=B R_v^r.
$$
In particular, the stabilizer of $N_v$ in the local unitary group becomes the group of unitary integral matrices in the coordinates $B^{-1}x$. This is the coordinate comparison used by the [column level index](the-column-level-index-factors-into-finite-field-indices.md) and the genus mass comparison. The argument includes residue characteristic two and rank zero.

### Carry the dual to the completion

The map $x\mapsto(y\mapsto h(y,x))$ identifies $V$ with its conjugate-linear $E$-dual. Under this map the dual lattice is the space of integral conjugate-linear functionals on $N$. The lattice $N$ is projective over the Dedekind ring $\mathcal O_E$, since it is finitely generated and torsion free. The dual therefore commutes with base change to $R_v$. Concretely, one can take bases over each local discrete valuation ring, in which testing a finite set of generators gives all the integrality conditions. At a split place one tests the opposite component in the pairing, since conjugation exchanges the components. Thus $N_v$ is self-dual. In a basis of this free local module the Gram matrix is integral and invertible over $R_v$: it identifies the lattice and its module dual by the same functional description.

### The two local forms

If $E_v=F_v\times F_v$, conjugation exchanges the factors and the Hermitian pairing is specified by a perfect bilinear pairing between the two factors of $N_v$. Choose a basis of the plus factor. In the minus factor choose its dual basis for the pairing, which is integral because the pairing is perfect. Pair the corresponding basis vectors of the two factors to obtain $r$ vectors over $R_v$. Their Hermitian Gram matrix is $I_r$.

If $E_v/F_v$ is an unramified quadratic field, apply the orthonormal-basis argument in [the local involution proof](the-local-involution-splits-or-gives-an-unramified-quadratic-ring.md#a-hyperbolic-basis-in-even-rank), stopping before the conversion of pairs to hyperbolic planes. A nonsingular residue Hermitian form in positive rank has a vector of nonzero norm by the nondegenerate trace pairing. The lifted vector has unit norm and can be rescaled to length one since the norm on units is onto, including at two. The restriction to its orthogonal complement is again unimodular. Induction gives an orthonormal basis in every rank.

In either case put the basis vectors in the columns of $B$. This gives both required equations. For a unitary $g$, the lattice condition $gN_v=N_v$ now reads $B^{-1}gB\,R_v^r=R_v^r$. Equivalently that matrix and its inverse are integral. The first displayed equation makes the adjoint of $B^{-1}gB$ its inverse, so integrality of its entries already implies integrality of its inverse.

### Lean correspondence

- [`unramified`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsFrameCm.lean#L99) applies the host separation of conjugation modulo primes. At a fixed ramified prime the residue involution would be trivial, which is excluded by that separation.
- [`exists_orthonormal_frame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/AdelicLatticeProofs/FiniteResidueFieldAdicCompletionIntegers.lean#L831) establishes both the Gram identity in the completed algebra and the integral basis assertion.
- [`exists_frame_cm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsFrameCm.lean#L110) transports these identities to the order in $E\otimes_F F_v$ and its lattice scalar extension. [`exists_frame`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsFrameCm.lean#L169) specializes to the first space of the column data.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
