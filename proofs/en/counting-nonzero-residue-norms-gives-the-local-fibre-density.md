# Counting nonzero residue norms gives the local fibre density

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K$ be a nonarchimedean local field of characteristic zero, $A$ its integer ring, $\varpi$ a uniformizer and $q=|A/\varpi A|$. Let $B$ be a quadratic algebra over $K$, either $K\times K$ with the exchange involution or an unramified quadratic field with its conjugation. Write $R$ for its maximal order, and $\eta=1$ in the split case and $\eta=-1$ in the inert case. Let $V=B^n$, $n\ge1$, with a nondegenerate Hermitian form $h$ and a full self-dual $R$-lattice $L$. Let $Q(x)=h(x,x)$ in $K$.

Take a nontrivial continuous unitary additive character $\psi$ of $K$ and write $\varpi^{-c}A$ for the annihilator of $A$ under $(s,t)\mapsto\psi(st)$. Let $\nu$ be the self-dual Haar measure for this pairing and $\mu$ the self-dual Haar measure for $\psi(\mathrm{Tr}_{B/K}h(x,y))$. Assume a family of measures $\mu_t$ on the fibres $Q^{-1}(t)$, $t\ne0$, which disintegrates $\mu$ relative to $\nu$ on the nonzero fibres. Its integrals of continuous functions of compact support contained in $Q^{-1}(K^\times)$ are continuous in $t\ne0$. These are the fibre assumptions used in `SelfDualLatticeDensity`.

Then
$$
\mu(L)=q^{-cn},\qquad
\nu(A)=q^{-c/2},\qquad
\mu_t(L)=q^{c(1/2-n)}(1-\eta^n q^{-n})
\quad(t\in A^\times).
\tag{1}
$$
The last factor is the finite-place representation density for a unit norm. Both $+1$ and $-1$ are units at every finite place.

### Compute the two Haar volumes

For a compact open additive subgroup $M$, the Fourier transform of its indicator for a self-dual pairing is $\mu(M)\mathbf1_{M^\perp}$. Indeed, integration of the character on $M$ gives $\mu(M)$ for a trivial character and zero otherwise, by translation by an element on which the character is nontrivial. Fourier inversion at zero gives $\mu(M)\mu(M^\perp)=1$. Apply it first in $K$, with $A^\perp=\varpi^{-c}A$, to get $\nu(A)=q^{-c/2}$.

The trace pairing on $R/A$ is perfect, including at residue characteristic two. In the split case it pairs the two coordinates separately. In the unramified field case it is perfect since its reduction is the trace pairing of a separable quadratic residue extension. Consequently the annihilator of $R$ for $\psi\circ \mathrm{Tr}_{B/K}$ is $\varpi^{-c}R$. Testing $h(x,y)$ against all $R$-multiples of $x\in L$, Hermitian self-duality now shows $L^\perp=\varpi^{-c}L$. The $K$-dimension of $V$ is $2n$, so the two volumes differ by the factor $q^{2cn}$. This gives $\mu(L)=q^{-cn}$.

### Count the residue vectors with unit value

Use the [integral frame argument](a-self-dual-lattice-has-an-integral-frame-at-each-finite-place.md) for $L$ over the split or unramified algebra. In split coordinates, $Q$ reduces to $\bar x\cdot\bar y$ on two vectors in $(A/\varpi A)^n$, where bars in this calculation denote reduction. For any nonzero prescribed value, the first vector must be nonzero and the second lies in an affine hyperplane. There are $(q^n-1)q^{n-1}$ choices. In the inert case $Q$ reduces to the sum of $n$ norms from the field with $q^2$ elements to that with $q$ elements. The single-variable norm has one preimage of zero and $q+1$ of each nonzero value, by cyclicity of the multiplicative groups. For a fixed nonzero $t$ the number $N_j(t)$ of vectors of length $j$ with sum of norms $t$ therefore obeys
$$
N_j(t)=(q+1)q^{2(j-1)}-q N_{j-1}(t),\qquad N_0(t)=0.
$$
For each vector in the first $j-1$ coordinates the last norm needs the remaining value. It has $q+1$ choices except when the remaining value is zero, when it has one. Substituting the recurrence gives $N_j(t)=q^{2j-1}-(-1)^j q^{j-1}$ for $j\ge1$. The split and inert answers are thus both $q^{2n-1}(1-\eta^n q^{-n})$ for each nonzero value.

Each residue vector in $L/\varpi L$ has the same measure, namely $\mu(L)q^{-2n}$. Summing over the $q-1$ nonzero values gives
$$
\mu\{x\in L:Q(x)\in A^\times\}
=\mu(L)(1-q^{-1})(1-\eta^n q^{-n}).
\tag{2}
$$

### Identify the common fibre value at every unit

The norm $R^\times\to A^\times$ is onto. In the split case take $(u,1)$ for a desired norm $u$, and in the unramified field case use the [unit norm lifting](the-local-involution-splits-or-gives-an-unramified-quadratic-ring.md#trace-and-norm-in-the-local-domain-case). Multiplication on $V$ by a unit of norm $u$ maps $L$ to itself, preserves $\mu$, and multiplies $Q$ by $u$. The base change $t\mapsto ut$ preserves $\nu$. It follows from disintegration that $t\mapsto\mu_t(L)$ on the units is invariant almost everywhere under $t\mapsto ut$, for each fixed unit $u$. One can see this by measuring the pullback of any measurable subset of the units in (2) and using the two measure-preserving changes of variables.

In fact the fibre mass on the units is continuous. It is the integral of the indicator of the compact open set $L\cap Q^{-1}(A^\times)$, whose support lies over nonzero $t$. Every nonempty open subset of the units has positive Haar measure. Thus the almost-everywhere equality for each $u$ is an equality everywhere. Any two units differ by a unit multiplier, so the fibre mass has a single value. Disintegrating (2) gives that value as the ratio of (2) to
$\nu(A^\times)=(1-q^{-1})\nu(A)$. Substitution of the two Haar volumes proves (1).

### Lean correspondence

- [`densityValue` and `SelfDualLatticeDensity`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/DualExponentDensity.lean#L57) state (1) and the fibre hypotheses. [`IsFibreFamily`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/GenusMassVolumes.lean#L183) specifies support, disintegration and continuity.
- [`localDensity_of_selfDualLatticeLemmas`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LocalDensityOfSelfDualLatticeLemmas.lean#L208) uses dual boxes to compute the volumes, counts residue norms by a binary norm form, and uses scalar norm lifting in `fibre_mass_mul_units_eq` to identify the common unit fibre.
- [`selfDualLatticeDensity`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/SelfDualLatticeDensity.lean#L9) applies the proved local lattice lemmas. [`local_value`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/VolumeRatioOfUnfolding.lean#L223) brings the density into the adelic comparison with the local character of the given adelic character.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
