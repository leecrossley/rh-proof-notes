# The word-prime character factor is independent of the selected side

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be the quadratic CM extension of the column data, with conjugation $x\mapsto\bar x$, and let $K$ be the coefficient field. Fix a word $u$, its rational prime $T$, a twist $\mu$, and a step $i<m$. The set $S_T$ consists of the primes of $E$ dividing the principal ideal $(\pi_T)$, where $\pi_T\bar\pi_T=T$ and $(\pi_T)$ is coprime to $(\bar\pi_T)$. Above each prime $v$ of $F$ over $T$ there are two distinct primes $P,\bar P$ of $E$, with $P\in S_T$ and $\bar P\notin S_T$. The row set $S_{\rm row}$ consists of the served and twist primes used for the explicit frames. It meets no place over $T$. Let $\operatorname{sel}(v)$ be any selection of an $E$-prime over each $v$ of $F$; the selection above $T$ can be either $P$ or $\bar P$.

For a full self-dual Hermitian $\mathcal O_E$-lattice $M\subset E^n$, let $o_P(M)=v_P(\det B_P)$, where $B_P$ is any basis matrix of $M_P$ over the local discrete valuation ring at $P$ and $v_P$ is normalized by $v_P(P)=1$. Set $\Delta_P=o_P(M_2)-o_P(M_1)$ for two such lattices. Assume they have equal localizations at every prime not dividing $T$. Let $w_P\in K^\times$ denote `mUof` at the chosen step. Define
$$
M_{\rm off}(M)=
\prod_{\substack{v\text{ a finite prime of }F\\v\notin\{Q\cap\mathcal O_F:Q\in S_{\rm row}\}}}
w_{\operatorname{sel}(v)}^{\,o_{\operatorname{sel}(v)}(M)} .
$$
There are only finitely many factors different from one. With the character assumptions below,
$$
M_{\rm off}(M_1)=\left(\prod_{P\in S_T} w_P^{-\Delta_P}\right) M_{\rm off}(M_2).
\tag{1}
$$

### Conjugation of determinant orders

A change of local basis has unit determinant, so $o_P$ is well defined. The local Hermitian dual of $M_P$ lies at the conjugate place. If $B_P$ is a basis at $P$, the dual there is computed by a transpose inverse and conjugation, using the standard Hermitian pairing. The basis at $\bar P$ can therefore be taken to be $(\overline{B_P}^{\,t})^{-1}$. Conjugation identifies the normalized valuations since it is an isomorphism of the two local discrete valuation rings. Self-duality gives
$$
o_{\bar P}(M)=-o_P(M).
$$
For finiteness, choose a positive integer $d$ with $d\,\mathcal O_E^n\subset M\subset d^{-1}\mathcal O_E^n$. The first inclusion follows by clearing denominators for the standard basis in the rational span of $M$, and the second by clearing denominators of finitely many integral-module generators. Thus $o_P(M)=0$ if $P\nmid d$.

### Conjugation of character values

At $P\in S_T$, $w_P$ is the product of the inverses of the coefficient-field uniformizer values of the base Hecke character and of $\mu$. The `FromHecke` hypothesis identifies the base values at $P,\bar P$, under the coefficient-field embedding, with the complex values of a Hecke character trivial on the ideles of $F$ and unramified at both primes. The base character is unramified away from the served rational primes, which are distinct from $T$. For $\mu$ the tuple condition gives triviality on the ideles of $F$ and on all local units above $v$, since the residue characteristic $T$ belongs to the set of rational primes excluded from its tame support. This is the use of `Pr.T u ∈ S` in Lean. Both characters may therefore be evaluated on uniformizers without dependence on a unit factor.

Take a finite idele of $F$ supported at $v$ with a uniformizer there. Its image in $E$ has order one at both $P,\bar P$ since $v$ splits, and it has order zero elsewhere. At the two places it differs from the product of two separately supported uniformizer ideles only by local units. Each character is trivial on these units and on the original idele of $F$, so the two uniformizer values are inverses. For the base character the equality descends by injectivity of the chosen coefficient-field embedding. It follows that $w_{\bar P}=w_P^{-1}$.

In the tuple definition the uniformizer value at $P$ is specified by a test idele with an integral representative congruent to an element of $P\setminus P^2$ modulo $P^2$, and to $1$ at other primes. The supported test ideles have exactly the orders just used. Conversely such a test can be built at $P$ with any unit coordinates outside $v$ set to $1$. A character trivial on all units above $v$ has the same value on any supported ideles with equal orders, since their ratio is a unit at both places. This identifies the uniformizer value used in the argument with `unifVal`.

### The off-row product

The norm relation $T=\pi_T\bar\pi_T$ says that every prime over $T$ contains one of the two factors, and the coprimality rules out containing both. Conjugation is nontrivial on the primes above each $v\mid T$, so the quadratic extension splits there and exactly one of them is in $S_T$. The row set has no prime above $T$ because its served primes are disjoint from $T$ and its twist primes are supported at the permitted residue characteristics.

At a place $v\nmid T$ the two determinant orders coincide by the agreement of localizations, so its factor in the quotient of the products is one. If $v\mid T$ and $\operatorname{sel}(v)=P\in S_T$, the quotient is $w_P^{-\Delta_P}$. If $\operatorname{sel}(v)=\bar P$, it is
$$
w_{\bar P}^{-\Delta_{\bar P}}
=(w_P^{-1})^{\Delta_P}
=w_P^{-\Delta_P}.
$$
Multiply over $v\mid T$ and use the one-to-one correspondence between these $v$ and $S_T$ to obtain (1).

The framed determinant factor `muInvDet` is $M_{\rm off}(M)$ times the product of the prescribed local characters of the frame determinants at $S_{\rm row}$. When comparing two lattices with fixed row frames, this latter product is the same on both sides. Multiplying (1) by this common product gives the comparison of framed factors. The theta kernel uses the source framed factor and the inverse of the target framed factor.

### Lean correspondence

- [`ordDet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L117), [`muOff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L122), [`muInvDet`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L127) and [`mUof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/KernelLattices/ThDistC.lean#L188) fix the signs and frame factors.
- [`ordDet_conjP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/OrdDetConjFinite.lean#L66) and [`ordDet_conj_finite`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/OrdDetConjFinite.lean#L97) treat the dual determinant order and finite support. [`val_eq_inv_of_split`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnderEqIffMapLe.lean#L40) and [`unifVal_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLocalIdele.lean#L171) prove the two split character relations. [`mUof_conj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MemMulLatIff.lean#L398) combines them.
- [`level_notMem_rowSG`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelNotMemRowSG.lean#L64) excludes the word prime from the row. [`term_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelNotMemRowSG.lean#L100) compares a single factor and [`muOff_move`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/LevelNotMemRowSG.lean#L148) gives (1).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
