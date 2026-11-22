# Local congruences glue the common target projection

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be a CM number field with conjugation, write $\mathcal O=\mathcal O_E$, and use the standard Hermitian form on $E^b$. Let $M_0,M_1$ be full self-dual $\mathcal O$-lattices of even rank $b$, and fix a nonzero $n\in\mathcal O$. Let
$$
R=\{g\in\operatorname{Mat}_b(E):gM_0\subseteq M_0,\quad gM_1\subseteq M_1\},\qquad
J=n(M_0\cap M_1).
$$
For $g\in R$ define three matrices
$$
p_0(g)=g^2-g,\quad p_1(g)=g^*g,\quad p_2(g)=(1-g)^*(1-g),
$$
where $g^*$ is the Hermitian adjoint. Assume that for every rational prime $p$ there is $g_p\in R$ for which each $p_j(g_p)y$, $0\le j\le2$, $y\in M_0\cup M_1$, belongs to $J\otimes_{\mathbb Z}\mathbb Z_{(p)}$. Here membership means that some integer not divisible by $p$ multiplies that vector into $J$. This is the local projection property `PLocal`. Then there is $e\in R$ such that all three $p_j(e)$ carry both lattices into $J$ itself. This is the [approximate projection required for the theta square](an-approximate-target-projection-splits-the-four-period-lattices.md).

### An integer clears all target errors

The ring $R$ is closed under adjoints. For either $M_i$, self-duality allows membership in $M_i$ to be tested by pairing with each of its elements. If $x,y\in M_i$ and $gM_i\subseteq M_i$, then $\langle y,g^*x\rangle=\langle gy,x\rangle$ is integral. Thus $g^*x\in M_i$, as required. It follows that all the $p_j(g)$ belong to $R$.

There is an integer $D>0$ with $DM_i\subseteq J$ for $i=0,1$. The intersection of two full lattices is full, since a common denominator puts each vector in both. Scaling by $n\ne0$ preserves the span, so $J$ is also full. Clear a denominator for each generator of either $M_i$ and multiply the finitely many resulting positive integers. Consequently, at a rational prime outside $D$, every element of $R$ sends both lattices into the localization of $J$.

### The congruences in the ring of simultaneous endomorphisms

For each rational prime $p\mid D$, prescribe $e\equiv g_p\pmod{p^D R}$. These conditions can be imposed together by ordinary integer Bézout coefficients. In detail, put $Q_p=\prod_{q\mid D,\ q\ne p}q^D$ and choose an integer $b_p$ for which $b_pQ_p\equiv1\pmod{p^D}$. Then $e=\sum_{p\mid D}b_p Q_p g_p$ is in $R$ and has the stated congruences. The other coefficients vanish modulo $p^D$. If $D=1$, the empty sum gives $e=0$ and no local congruence is required.

Since $R$ is closed under adjoints, $p^D R$ is a two-sided ideal stable under adjoints. Therefore $p_j(e)-p_j(g_p)\in p^D R$. For $y\in M_i$, write the difference on $y$ as $p^D r y$ with $r\in R$. As $p^{v_p(D)}\mid D$ and $v_p(D)\le D$, $p^D/D\in\mathbb Z_{(p)}$. We have $D r y\in J$, so $p^D r y$ lies in its localization at $p$. The prescribed local membership for $p_j(g_p)y$ then proves local membership for $p_j(e)y$. At $p\nmid D$ this membership was automatic. A vector belonging to the localizations of $J$ at every rational prime belongs to $J$: the ideal of integers sending the vector into $J$ contains a number prime to each rational prime, and hence is all of $\mathbb Z$. This proves the global assertion.

### Lean correspondence

- [`PLocal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/SqPair.lean#L11) gives the local hypothesis. [Simultaneous endomorphisms and adjoints](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/SquarePairGluing/ConjTransposeMemLam.lean#L1) proves the ring closure. [Clearing the simultaneous denominator](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/SquarePairGluing/ExistsDenLe.lean#L1) gives $D$ and the congruence identities of the three polynomials.
- [`crt_exists`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/SquarePairGluing/SqPairGlueMain.lean#L14) constructs the integer Bézout combination and [`sqPairGlue_main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/UnitaryGroupMassFormula/SquarePairGluing/SqPairGlueMain.lean#L56) gives the global result.
- In the project the local hypothesis is supplied for these lattices over the host CM field by [`square_pair_local`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OrbitalBoundsConclusion/SqPairLocal.lean#L6). Their combination is [`split_pair_generation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/PeriodIntegrals/OrbitalBoundsConclusion/SplitPairGen.lean#L5).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
