# Restoring the word-prime value lattice after one lift

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Fix a column chain of length $m$ with word prime $T$, and a finite place $w$ of the coefficient field $K$ over $T$. Work over the valuation ring $\mathcal O_w$, with embedding of $K$ into the complex coefficients of the forms. Let $S_i(w)$ be the localized lattice of forms at layer $i$. Use the equivariant point coordinates of the [Hecke commutation proof](weighted-incidence-gives-the-word-prime-hecke-commutation.md). Assume that these coordinates identify $S_i(w)$ with the forms whose extended values belong to the pointwise Weyl lattices defined below with $V=\varnothing$. Assume the point-kernel laws `IntP` and `IntBar` described below, and that $T$ is prime to all class stabilizer orders.

Let $f$ be the number of coefficient embeddings $\tau$ used in the Weyl modules, $N_i$ the layer ranks with $N_i\le N_m$, and $W_\tau\ge0$ the maximum weight used at embedding $\tau$ through the chain. Suppose each determinant-shift parameter $s_{i,\tau}$ satisfies $0\le s_{i,\tau}\le W_\tau$, and that the first weight at each non-top embedding of the next layer after the determinant shift is at most $W_\tau$. The local comparison either uses the selected split side at $w$ or its conjugate side. Let $H_j$ be the product of $U_{j,v}$ over the places $v$ corresponding to the top embeddings on the selected side, and $H_j=1$ on the conjugate side. Set
$$
e=\begin{cases}2\sum_\tau W_\tau+fN_m,&\text{selected side},\\0,&\text{conjugate side}.\end{cases}
$$
Then $T^e H_{i+1}K_i$ takes $S_i(w)$ into $S_{i+1}(w)$ for every $i<m$, where the assertion means that the resulting complex form is the image of a vector of the indicated coefficient-field lattice. This is `UKSharp`.

## Pointwise lattices and their change under incidence

At a point $P$ the model has, for each place $v$ over $T$, a local lattice $\Lambda_v(P)$ of rank $N_j$ in a split coordinate space and a nonzero residue-linear functional $f_v$ on it. The functional factors through the quotient by $T\Lambda_v(P)$. Put $\Lambda_v^0(P)=\ker f_v$. At the selected side and for a subset $V$ of places, take a basis of $\Lambda_v^0(P)$ at $v\in V$ and of $\Lambda_v(P)$ elsewhere. On the conjugate side the model uses the kernel lattices throughout. Transport the standard tensor Weyl lattice over $\mathcal O_w$ by these bases to obtain a lattice $B_j(w,V,P)$ of values. It is independent of the bases because integral invertible changes of basis preserve the Weyl lattice. In the source this lattice is `Co.valB`. It is closed under addition and $\mathcal O_w$-scalar multiplication and transported by the equivariance action, as required by the point-coordinate comparison.

On the selected side, for $v\in V$, a neighbour $Q$ of $P$ under the incidence for $v$ has $\Lambda_v^0(Q)=\Lambda_v(P)$, with the data at all other places unchanged. Consequently $B_j(w,V,Q)=B_j(w,V\setminus\{v\},P)$. The outgoing-neighbour sum for $U_{j,v}$ sends forms whose extended values are in the former lattices into forms whose extended values are in the latter. Thus each $U_{j,v}$ in $H_j$ removes one kernel condition.

A remaining kernel condition can also be removed by a scalar power of $T$. At its place $v$, choose a basis $h_1$ of $\Lambda_v(P)$ in which $f_v$ modulo $T$ is a nonzero multiple of the first coordinate. Such a basis exists by lifting a change of basis in the residue field to an invertible integral matrix. In this basis the kernel is spanned by $T$ times the first basis vector and the other basis vectors. Any basis $h$ of the kernel therefore has the form $h=h_1\operatorname{diag}(T,1,\ldots,1)k$ with $k$ an integral invertible matrix. Write $\lambda=\lambda_{j,\tau}^\mathrm{sh}$ for the shifted weight at $\tau=\tau(w,v)$, $\delta$ for its determinant shift, and $\nu=\lambda-\delta(1,\ldots,1)$ for its natural weight. The coordinate action in the source is inverse row substitution times the determinant to power $-\delta$. On each monomial of first row degree $a_1$ the diagonal factor gives $T^{-\delta-a_1}$. Every first row degree in a polynomial of the Weyl lattice is at most $\nu_1$, its largest natural weight. Indeed its highest weight generator is a product of $\nu_1$ initial minors, counted with multiplicity. Under formal row operations each minor becomes a linear combination of minors and remains of degree at most one in any row. Taking coefficients in the row-operation parameters gives the same bound for every divided-power word generating the lattice. Multiplication by $T^{\lambda_1}$ leaves the nonnegative exponent $\nu_1-a_1$ and stays inside the Weyl lattice. More explicitly each divided-power word is row-weight homogeneous because a divided row operator transfers a fixed number of degrees between the two rows. The diagonal clearing therefore multiplies a generator by a single nonnegative integral power of $T$. Any coefficients in the local model ring map into $\mathcal O_w$, so this operation in the one tensor factor gives
$$
T^{\lambda_{j,\tau,1}^\mathrm{sh}} B_j(w,V,P)
\ \subseteq\ B_j(w,V\setminus\{v\},P).
\tag{1}
$$
This also makes sense when the shift gives a negative scalar exponent.

## The single-step accounting

The law `IntP` says that, on the selected side, multiplication by $T^{fN_i+\sum_\tau s_{i,\tau}}$ takes the image of every kernel entry on $B_i(w,\varnothing,P)$ into $B_{i+1}(w,V_{\rm all},P')$. The law `IntBar` says that on the conjugate side each entry maps such values into $T^{f(t+1)/2} B_{i+1}(w,\varnothing,P')$, with adjacent ranks differing by $t+1$ for the odd chain parameter $t$. [The passage to all point pairs](coefficient-kernel-bounds-pass-to-all-word-prime-points.md) derives these laws from the arithmetic coefficient kernels and the point-coordinate identifications. On either side a scaled entry estimate is inherited by the sum over source classes: the weight $1/|\mathrm{Stab}(c)|$ has valuation zero at $w$ and the pointwise lattices are $\mathcal O_w$-modules. Kernel equivariance ensures the sum is again a form.

On the selected side apply $H_{i+1}$ to remove all conditions at the top embeddings. For each remaining condition use (1) at layer $i+1$. The full exponent used is at most
$$
 fN_i+\sum_\tau s_{i,\tau}+
       \sum_{\tau\ {\rm non\text{-}top}}\lambda_{i+1,\tau,1}^\mathrm{sh}
 \ \le\ fN_m+2\sum_\tau W_\tau.
$$
The difference from $e$ is a nonnegative integer, and the ordinary value lattice is stable under its corresponding power of $T$. On the conjugate side $f(t+1)/2\ge0$ and the ordinary lattice already contains its multiple, so no extra power is needed. Returning through the point-coordinate comparison gives the asserted map.

## Lean correspondence

- [`KerPt.IntBar` and `KerPt.IntP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/FormsStable.lean#L220) state the precise kernel-law hypotheses. [`UKSharp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/FormsStable.lean#L313) is the conclusion.
- [`valB_of_inc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ValBOfInc.lean#L9) is the equality of point lattices for incident points.
- [`frame_ker_decomp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelPrimePowSmulMemValueLatticeErase.lean#L399) gives the basis comparison. [`diag_step`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelPrimePowSmulMemValueLatticeErase.lean#L207) and [`pow_smul_mem_valB_erase`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelPrimePowSmulMemValueLatticeErase.lean#L534) give (1).
- [`extIn_K`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExtInOfValIn.lean#L139) transfers an entry estimate to the class sum. [`ukSharp`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExtInOfValIn.lean#L155) accounts for all the powers of $T$.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
