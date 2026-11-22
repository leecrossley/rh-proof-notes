# Hecke character normalizations are units away from their prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be the chain's CM field with involution $z\mapsto\bar z$, let $K$ be its coefficient number field, and let $\sigma:K\to\mathbb C$ and $\iota_\tau:E\to K$ be the chosen embeddings. Assume each composite embedding carries the involution to complex conjugation. Take a Hecke character $\mu$ as in `IsMu0` at a layer. Thus it is unitary, trivial on the base field's ideles, unramified away from the places over the two type primes, and tame at every finite place. Here unramified means trivial on local units, and tame means trivial on units congruent to $1$ modulo the maximal ideal. Its infinite component on $z\in E^\times$ is
$$
\mu_\infty(z)=\prod_\tau \left(\frac{\sigma\iota_\tau(z)}{|\sigma\iota_\tau(z)|}\right)^{n_\tau},
\qquad n_\tau=-2e_\tau\in\mathbb Z,
$$
where the $e_\tau$ are the rational weights of this character. The global character is trivial on diagonally embedded $E^\times$, so its local components satisfy the product rule.

Let $P$ be a finite place of $E$, let $p$ be a rational prime outside $P$, and let $w$ be a prime of $K$ above $p$. For any $x\in E^\times$ and any $c\in K$ with $\sigma(c)=\mu_P(x)$, one has
$$
c\in\mathcal O_{K,w}^{\times}.
$$
In particular, in the built chain let $T$ be the word prime and $w\mid T$. Take an auxiliary twist place $P$ outside the type places, with its rational norm prime $q\ne T$ and distinct from both type primes. The twist $\xi$ has finite order. Then the chain's scalar
$$
\operatorname{muq}(j+1,P)
=\operatorname{muVal}(j,P)^{-1}\operatorname{qValC}(\xi,P)^{-1}
$$
is a unit at $w$, for every $0\le j<m$. Here `muVal` corresponds under $\sigma$ to the value of the layer character on a uniformizer at $P$, and `qValC` is the finite-order twist value specified at the local norm prime.

### A pure finite-place power

Let $S$ be the finite set where the character may be ramified. Write $\operatorname{ord}_Q$ for the additive order at $Q$. For every finite $Q$ and local unit $u$, the order of the residue unit group, $m_Q=|\mathcal O_E/Q|-1$, satisfies $u^{m_Q}\equiv1\bmod Q$. Tameness then gives $\mu_Q(u)^{m_Q}=1$. Let $M'=\prod_{Q\in S\cup\{P\}}m_Q$, a positive integer.

The class group of $E$ is finite. Consequently there is an $h\ge1$ for which $P^h=(a)$ with $a\in E^\times$. Take
$$
z_0=a^{\operatorname{ord}_P(x)},\qquad
z=z_0^{M'},\qquad M=hM'.
$$
Then $\operatorname{ord}_P(z)=M\operatorname{ord}_P(x)$, and $z$ is a unit at every other finite place. At a place of $S\setminus\{P\}$ its character value is $1$ by the choice of $M'$. At every place outside $S\cup\{P\}$ the same is true by unramifiedness. At $P$, the quotient $z_0/x^h$ is a local unit, so
$$
\mu_P(z)=\mu_P(x)^M
$$
by the choice of $M'$. The product rule applied to $z$ gives $\mu_P(x)^M\mu_\infty(z)=1$.

### The infinite component and the other valuation

For each nonzero complex number $v$ one has $(v/|v|)^2=v/\bar v$. Squaring the product rule and using the displayed infinite component gives
$$
\sigma(c^{2M})=\prod_\tau\left(\frac{\sigma\iota_\tau(z)}
  {\overline{\sigma\iota_\tau(z)}}\right)^{-n_\tau}.
$$
The composite embeddings preserve conjugation, so injectivity of $\sigma$ gives the identity over $K$
$$
c^{2M}=\prod_\tau\iota_\tau(z/\bar z)^{-n_\tau}.
$$
The contraction of $w$ along each $\iota_\tau$ contains $p$. It is therefore neither $P$ nor $\bar P$, since $p$ is rational and $p\notin P$. At this contraction, $z$ and $\bar z$ are both local units. A local unit stays a unit under extension to $w$. Thus every factor of the product is a unit at $w$, which gives $\operatorname{ord}_w(c^{2M})=0$. The equality $2M\operatorname{ord}_w(c)=0$ gives the desired assertion.

### The finite-order twist factor

If a character $\xi$ has finite order $N$, then each of its values satisfies $b^N=1$. Both $b$ and $b^{-1}$ are algebraic integers, so $b$ has order zero at every finite place of the coefficient field. The definition of `qValC` says to take the common value, when it exists, on integral supported ideles that are congruent to $q$ at $P$ modulo $P^2$ and congruent to $1$ at all other primes. Otherwise it takes $1$.

There is an idele on which to evaluate any such common value. If $v$ is the place of the base field under $P$, write $v\mathcal O_E=P^hJ$ with $J$ coprime to $P$. The Chinese remainder theorem gives a nonzero algebraic integer $b$ with $b\equiv q\bmod P^2$ and $b\equiv1\bmod J$. If a chosen representative is zero, add a nonzero member of the product ideal. Set the idele equal to $b$ at all places above $v$ and to $1$ elsewhere. It is a unit of the finite adele algebra because each coordinate is nonzero and only finitely many differ from $1$. At any other place over $v$ the ideal $J$ forces the required congruence. In the integral tensor model the idele is $1+(b-1)e_v$, with $e_v$ the integral idempotent supported at $v$, which gives the same local congruences. Thus `qValC` is a finite-order value or $1$, both units at $w$. The same argument applies to the analogue `unifVal` by specifying an element of $P\setminus P^2$ in place of $q$.

In the chain both type primes and the word prime belong to the twist avoidance set. The prime description of the auxiliary twist places says their norms are outside that set. Thus the layer character is unramified at $P$, its uniformizer value is the specified `muVal`, and $T\notin P$. The proved Hecke unit claim and the finite-order claim apply to the two scalar factors separately. Their inverses and product are units at $w$, which proves the condition `MuqUnit`.

### Lean correspondence

- [`IsMu0` and `Chars.Tied`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/AbelianHostFieldConditions.lean#L314) specify these layer characters and identify their values. [`HasInfQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/UnitaryNorms/IsUnitaryNormOf.lean#L93) gives the exponents.
- [`exists_pow_locK`, `exists_gen` and `exists_pow_locK_mul_inf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsPowLocKMulInf.lean#L36) construct the finite-place power and apply the product rule. [`mu_core` and `mu_unit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/CharacterValueAtT.lean#L553) give the conjugation quotient and take its valuations.
- [`exists_supported_idele`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsSupportedIdele.lean#L120) constructs the supported finite idele in the integral tensor model. [`valuation_finOrder_apply` and `twistUnit`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ValuationFinOrderApply.lean#L11) use roots of unity.
- [`muqQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1001) gives the scalar product. [`MuqUnit` and `muqUnit_of_tied`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/BadPrimeNormPrimeNeLevelPrime.lean#L153) give the condition used at the twist places.

Status. Source-based reconstruction draft. The layer Hecke character is assumed to have the stated ramification and infinite-type properties. The unit argument uses the finite class group of a number field. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
