# Weighted incidence gives the word-prime Hecke commutation

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Fix a word prime $T$, a step $i$ of a column chain and a place $v$ of the host over $T$. The layer $i$ has a point set $\mathcal P$ with a group $G$ acting on it and a finite set of orbit representatives $r_c$. Their stabilizers $G_{r_c}$ are finite. Write $I(p,q)$ for the relation that $q$ is an outgoing neighbour of $p$ for the Hecke operator at $v$. This relation is invariant under the simultaneous action of $G$, and both fibres at each point are finite. Use an analogous point model $\mathcal P'$ for layer $i+1$.

A class form $\phi$ in the space of forms of layer $i$ extends to an equivariant function $\Phi$ on $\mathcal P$ with value $\phi(c)$ at $r_c$. Equivariance here is $\Phi(gq)=g\Phi(q)$, using the representation on values. The Hecke operator $U_{i,v}$ is induced by the outgoing-neighbour sum on such functions. The step $K_i$ is a kernel sum over $r_c$ with weight $1/|G_{r_c}|$. Its point kernel $k(p,p')$ is linear on the value space and satisfies
$$
k(gp,p')\,g=k(p,p'),\qquad
k(p,g'p')=g'k(p,p')
$$
for the source and target actions. Suppose the following relation holds for all $p,p'$ and input values $y$, where $t$ is the odd rank increment of the construction and $s=(t+1)/2$:
$$
\sum_{q': I'(p',q')} k(p,q')y
   =T^s\sum_{q:I(q,p)} k(q,p')y.
\tag{1}
$$
Then on the space of class forms one has $U_{i+1,v}K_i=T^s K_iU_{i,v}$. The hypotheses here describe the required orbit model and the point-kernel incidence identity `UKLaw`. The latter has a separate coefficient-kernel input for the true columns.

## Proof

For any invariant weight $f(p,q)$ on incident pairs, count pairs up to simultaneous $G$-action. An orbit of pairs with first representative $r_c$ meets the fibre at $r_c$ in one orbit of $G_{r_c}$. If $(r_c,q)$ represents this pair orbit, its fibre size is $|G_{r_c}|/|G_{r_c,q}|$. The sum over this fibre, weighted by $1/|G_{r_c}|$, contributes $f(r_c,q)/|G_{r_c,q}|$. If we choose a representative with fixed second endpoint, the identical argument gives the same contribution, since the two stabilizers of the pair are conjugate. The number of pair orbits is finite because the representative set and each incident fibre are finite. It follows that
$$
\sum_c\frac{1}{|G_{r_c}|}\sum_{q:I(r_c,q)} f(r_c,q)
=
\sum_c\frac{1}{|G_{r_c}|}\sum_{q:I(q,r_c)} f(q,r_c).
\tag{2}
$$

For fixed target representative $r'_{c'}$, set $f(p,q)=k(p,r'_{c'})\Phi(q)$. This weight is invariant since $k(gp,r'_{c'})\Phi(gq)=k(gp,r'_{c'})g\Phi(q)=k(p,r'_{c'})\Phi(q)$. By linearity, the left side of (2) is the $c'$-value of $K_i U_{i,v}\phi$. In $U_{i+1,v}K_i\phi$ outgoing target neighbours are summed after the kernel action. The $c'$-value is
$$
\sum_c\frac{1}{|G_{r_c}|}\sum_{q':I'(r'_{c'},q')} k(r_c,q')\Phi(r_c).
$$
Apply (1) to each inner sum. This gives $T^s$ times the right side of (2) with precisely the weight $f$ above. The two values agree after multiplying by $T^s$, and this holds for every target representative. Target equivariance ensures that the kernel sum continues to represent a form in the target point model. This proves the commutation used in the [iteration of the word-prime bound](commuting-the-hecke-product-through-the-column-chain.md).

## Lean correspondence

- [`KerPt.UKLaw`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/FormsStable.lean#L216) states (1).
- [`isExt_KT`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelChainTransitionIsExtKernelSum.lean#L8) gives the extension formula for the kernel sum on representatives.
- [`count_incidence`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelChainUOperatorCommutationOfPointPairLaw.lean#L15) gives (2).
- [`levelChainUOperatorCommutation_of_pointPairLaw`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelChainUOperatorCommutationOfPointPairLaw.lean#L52) applies it to the equivariant kernel.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
