# Choosing the embedding that sees each split word prime

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the field and word-prime data of the true column chain. In particular $E/\mathbb Q$ is Galois, $E/F$ is the quadratic CM extension, and the list of embeddings $\sigma_\tau:E\hookrightarrow K$ for $\tau\in\mathcal E$ accounts for all embeddings into $K$ together with their conjugates $\sigma_\tau\circ\mathrm{conj}$. Fix a word prime $T$ and a generator $\pi_T\in\mathcal O_E$ with $\pi_T\bar\pi_T=T$ and the two factors coprime. Assume all $\sigma_\tau$ take the same value on $\pi_T$. Write $\mathcal T$ for the primes dividing $(\pi_T)$. By the prime data $|\mathcal T|=|\mathcal E|$. For any prime $w$ of $K$ over $T$, there is a bijection
$$
\tau_w:\mathcal T\longrightarrow\mathcal E
$$
such that for every $P\in\mathcal T$ one of the following holds:

- The contraction of $w$ along $\sigma_{\tau_w(P)}$ is $P$, for every $P\in\mathcal T$.
- The contraction of $w$ along $\sigma_{\tau_w(P)}$ is $\bar P$, for every $P\in\mathcal T$.

The first case holds exactly when the common value $\sigma_\tau(\pi_T)$ belongs to $w$. In the first case, $\sigma_{\tau_w(P)}(x)$ is integral at $w$ if and only if $x$ is integral at $P$. In the second case the same equivalence holds with $\sigma_{\tau_w(P)}(\bar x)$ in place of $\sigma_{\tau_w(P)}(x)$, for every $x\in E$. These are the two possibilities of the integrality test `Sees`.

### Matching each prime with an embedding

The Galois group of $E/\mathbb Q$ acts transitively on the primes above $T$. For a direct argument, if two such primes were in different orbits, use the Chinese remainder theorem to choose an algebraic integer $a$ congruent to zero on one whole orbit and to one on the other. Then its field norm $\prod_g g(a)$ would be an ordinary integer congruent to zero at a prime in the first orbit and to one at a prime in the second. The contractions of both primes to $\mathbb Z$ are $(T)$, which is impossible.

Choose one embedding into $K$ and contract $w$ along it to get a prime above $T$ of $E$. Precomposing by Galois automorphisms gives all other contractions above $T$, by transitivity. Thus for each selected $P$ one of the embeddings into $K$ contracts $w$ to $P$. Write this embedding as $\sigma_\tau$ or its conjugate. Then $\sigma_\tau$ itself contracts $w$ to $P$ or $\bar P$ respectively. Choose one such $\tau$ for every $P$. A single $\tau$ cannot be chosen for two distinct selected primes, since its contraction is unique and no two selected primes are conjugates of one another. Equal cardinalities now give a bijection.

### The same split side at all embeddings

If the contraction for some $\sigma_\tau$ is a selected prime $P$, then the image $\sigma_\tau(\pi_T)$ belongs to $w$. Since this image is independent of $\tau$, every matched contraction contains $\pi_T$. Thus all matched contractions are on the selected side. If the common image is outside $w$, every matched contraction is on the conjugate side. This is the criterion for the flag in the true chain, denoted `seenP`. In particular it is a single flag for $w$ and the fixed word, shared by all selected primes.

### Integrality under contraction

For any embedding $\sigma:E\hookrightarrow K$, with contraction $Q$ of $w$, the preimage of $\mathcal O_{K,w}$ is $\mathcal O_{E,Q}$. A fraction in $\mathcal O_{E,Q}$ has denominator outside $Q$, whose image is a unit at $w$. Conversely, if $x\notin\mathcal O_{E,Q}$, then $x^{-1}$ belongs to the maximal ideal of that discrete valuation ring. Its image lies in the maximal ideal at $w$, since a localized fraction's numerator and denominator are tested by the contraction. This precludes integrality of $\sigma(x)$. Finally conjugation carries $\mathcal O_{E,P}$ to $\mathcal O_{E,\bar P}$. Using the contraction for $\sigma_{\tau_w(P)}$ therefore gives the asserted test on the appropriate argument, $x$ or $\bar x$.

### Lean correspondence

- [`Fields.Ok` and `AbelianUnramifiedExtensionConditions`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/AbelianHostFieldConditions.lean#L80) give the field and embedding data. [`Primes.Ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/AbelianHostFieldConditions.lean#L206) gives the prime factorization, count and agreement of the embeddings on $\pi_T$.
- [`tauAt`, `eq_of_sees` and `tauAt_sees`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/HermitianCodeWordWeilElementMemQuadraticField.lean#L110) choose the bijection. [`seesP_tauAt` and `seesPbar_tauAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/AutomorphicMembership/HermitianCodeWordWeilElementMemQuadraticField.lean#L155) give its common orientation.
- [`val_tauAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/ExistsRecordDat.lean#L20) proves the integrality test and [`sees_ofOk`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/ExistsRecordDat.lean#L59) identifies it with the test in the assembled chain.

Status. Source-based reconstruction draft. The transitivity argument above uses the Chinese remainder theorem. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
