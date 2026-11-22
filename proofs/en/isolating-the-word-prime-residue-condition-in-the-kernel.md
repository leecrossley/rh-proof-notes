# Isolating the word-prime residue condition in the kernel

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix an adjacent step $0\le i<m$ of a true chain with classes fixed at both layers. Write $T=T(u)$ for its word prime, $\mathcal T$ for the selected primes above $T$, and $\mathcal B$ for the type and twist places. Keep the field, prime, selection, twist-avoidance and indexed class hypotheses of [the ordinary kernel proof](the-ordinary-point-kernel-transforms-with-the-level-characters.md). Let $p,p'$ be points at the two layers, with lattices $N,N'$ and frames at $\mathcal B$. A replacement of either point is allowed to change the lattices at primes in $\mathcal T$ and their conjugates and to change the selected residue functionals. It must preserve the other localizations, the residue frames at the type places, the actual frames at the twist places, and the coset data.

Under the local coefficient hypotheses below, there is a fixed weight $\Xi_0$ such that the kernel at any two such replacements is the finite kernel sum for their lattices and frames with scalar weight
$$
x\longmapsto \phi_T(x)\Xi_0(x).
$$
Here $\phi_T$ uses the residue functionals of the **replacement** lattices. The same $\Xi_0$ works for every replacement. It is supported on $c_A^{-1}H_{\mathcal B}$ and is periodic by $c_B H_{\mathcal B}$, where $H_{\mathcal B}$ is the module of maps integral between the two lattices at all bad places and $c_A,c_B$ are [the box scales](the-ordinary-point-kernel-transforms-with-the-level-characters.md#periodicity-of-the-arithmetic-weight). Moreover $\Xi_0(x)\in\mathcal O_{K,w}$ for every place $w$ of the coefficient field $K$ above $T$ and all $x$. Lean packages these conclusions as `KerIsTerm`.

The local hypotheses are that each bad-place weight in its local frames is invariant under addition by $q_P^B$ times an integral matrix, and that its values are integral at each $w\mid T$. These are the two conditions of `AwayAt`. The local weight uses the ordinary unfolded coefficient at $i<m-2$, the target coset coefficient at $i=m-2$, and the source coset coefficient at $i=m-1$. The [type-place calculation](type-place-unfolding-stays-in-a-ring-generated-by-roots-of-unity.md) and the [twist-place calculation](twist-place-entries-are-integral-at-the-word-prime.md) obtain the two local properties from the class and character data. The latter uses [the unit bound for the multiplicative normalization](hecke-character-normalizations-are-units-away-from-their-prime.md) at $w$ in the ordinary and penultimate cases.

### The fixed weight

No prime in $\mathcal B$ is above $T$, by avoidance of $T$ in the twist support and distinctness of the two type primes from $T$. Thus the bad-place localizations do not change under a permitted replacement. The chosen frame at a type place depends only on its localized lattice and the residue frame, since it is chosen from the lifts of precisely that residue frame. Both data stay the same. The actual twist frames are fixed by hypothesis. The coordinate coset representatives can also be held fixed. It follows that the factors of the original scalar datum at $\mathcal B$ have the same value on every given $x$ for all replacements. Denote their product by $\Phi(x)$.

Define $\Xi_0(x)=\Phi(x)$ on $c_A^{-1}H_{\mathcal B}$ and $\Xi_0(x)=0$ outside it. The value is integral at $w$ as a product of local integral values or zero. The cutoff is unchanged on adding any $c_B y$ with $y\in H_{\mathcal B}$ because $c_BH_{\mathcal B}\subseteq c_A^{-1}H_{\mathcal B}$. At every $P\in\mathcal B$ the corresponding framed matrix addition is a multiple of $q_P^B$ times an integral matrix, since $q_P^B\mid c_B$. The defining period of the local factor therefore gives $\Phi(x+c_By)=\Phi(x)$. This proves the asserted period of $\Xi_0$.

In the kernel of the replacement pair every representative is chosen in $c_A^{-1}H_{\mathcal T\cup\mathcal B}$ for its full Hom module. Each such representative is also in the bad-place module with the $c_A$ scale. On it the cutoff defining $\Xi_0$ stays equal to one. The scalar expression is therefore $\phi_T(x)\Xi_0(x)$ with exactly the residue indicator, the same local weight at $\mathcal B$, and the correct theta distribution for the replacement pair. Equality term by term gives the factorization.

### Simultaneous diamond action

Fix $P\in\mathcal T$ and $a\in k_P^\times$. The diamond move multiplies the designated residue functional at $P$ by $a$ and preserves all other decoration data, including the underlying lattice. Apply it at the same time on the source and the target. The finite-sum quotient, frames and $\Xi_0$ all stay the same by the factorization. In $\phi_T$, the condition $f'_P(xv)=f_P(v)$ becomes $a f'_P(xv)=a f_P(v)$, which is equivalent because $a$ is a unit. Every summand is unchanged. This proves
$$
k_i(\langle a\rangle_P p,\langle a\rangle_P p')=k_i(p,p'),
$$
the coefficient diamond law `KerDil`.

### Lean correspondence

- [`AwayAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/JetOpIntegral.lean#L25) defines the local valuation and periodicity input. [`badPrimeNorm_prime_ne_levelPrime` and `frsF_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BadPrimeNormPrimeNeLevelPrime.lean#L56) identify the unchanged bad-place localizations and frames.
- [`muqUnit_of_tied`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BadPrimeNormPrimeNeLevelPrime.lean#L157) supplies the unit input. [`exists_local` and `kerIsTerm_of_muqUnit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BadPrimeNormPrimeNeLevelPrime.lean#L174) select the three coefficient shapes and factor the scalar datum for all permitted replacements. [`KerIsTerm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/KerIsTerm.lean#L178) states the common weight and its integral bound.
- [`levelPrimeDatum_diamond_invariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DecoratedLatticePointMoveDiamond.lean#L11) cancels the two residue-unit factors. [`kAt_dia`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DecoratedLatticePointMoveDiamond.lean#L31) transports the equality to the actual adjacent point entries. [`kerDil`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/MoveStep.lean#L53) uses it for the true chain.

Status. Source-based reconstruction draft. The local coefficient integrality and periodicity inputs are stated above. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
