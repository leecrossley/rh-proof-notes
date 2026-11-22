# A single unit aligns the split torsion characters

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $q$ be split in the maximal order $\mathcal O=\mathbb Z+\mathbb Zw$ of discriminant $-d$, where $d$ is prime and $d\equiv7\pmod{16}$. Let $\iota:\mathbb C\to\mathbb C_q$ fix the choice of split embedding. Start from a multiplicative chart of scale $\omega$ for the good CM curve. Use the small-point coordinate law: the chart identifies small formal points with multiplicative coordinates $\eta$ with $|\eta-1|_q<1$, respects multiplication by integers, and two corresponding complex parameters differ by a lattice period exactly when their coordinates agree. Use also its CM scalar law for the two split projections. Then there is one $a\in\mathbb Z_q^\times$ such that the rescaled chart $\omega a$ sends the good torsion lift $y$ of every level $n\ge0$ to $\iota(\kappa_1(y))$, the prescribed value of the theta bracket. The good lifts in this assertion have the form
$$
y=(s+tw)/q^n,\quad s,t\in\mathbb Z,\qquad
|\iota(\overline{s+tw})|_q\le q^{-2n}.
$$
With the prescribed bracket convention $\kappa_1(y)=\zeta_n^t$, where $\zeta_n$ is the compatible complex primitive $q^n$-th root of unity.

### Reading the chart's choice of generators

Choose $P_n$ of multiplicative coordinate $\iota(\zeta_n)$. Its $q^n$ multiple has coordinate one, so $q^nP_n$ is a lattice period and $P_n=(u_n+b_nw)/q^n$ for integers $u_n,b_n$. The CM scalar law gives $|\iota(\overline{u_n+b_nw})|_q\le q^{-n}$. More explicitly, choose an order element $e$ which is a unit close to one on the chosen split embedding and satisfies $|\iota(\bar e)|_q\le q^{-n}$, using the two congruences at the split primes. Multiplication by $\bar e$ kills the multiplicative $q^n$-torsion of $P_n$, so $\bar e P_n$ is a period. Taking the conjugate of this integrality and using that $\iota(e)$ is a unit gives the asserted bound on the numerator.

If $q\mid b_n$ for $n>0$, the bound on the conjugate numerator implies both split embeddings of $u_n+b_nw$ are divisible by $q$: their difference is $b_n(w-\bar w)$. Hence $(u_n+b_nw)/q\in\mathcal O$, contradicting exact order $q^n$ for the chart point. Also $qP_{n+1}$ and $P_n$ have the same coordinate by compatibility of the roots of unity. The equality of their classes modulo $\mathcal O$ gives $b_{n+1}\equiv b_n\pmod{q^n}$. The residues $b_n\bmod q^n$ therefore give a unit $\beta\in\mathbb Z_q^\times$, and take $a=\beta^{-1}$.

### Matching every good lift

Rescaling the logarithmic chart by $a$ replaces its map on multiplicative parameters by $\eta\mapsto\eta^a$ before applying the old chart; at $q^n$-torsion the exponent is $a_n=a\bmod q^n$. To send $\iota(\zeta_n^t)$ to $y$, use the old chart with coordinate $\iota(\zeta_n)^{t a_n}$, corresponding to $t a_n P_n$. The numerator of $t a_n P_n-y$, with denominator $q^n$, has coefficient of $w$ congruent to $t a_n b_n-t=0\bmod q^n$. Its conjugate embedding has norm at most $q^{-n}$, by the bounds for $P_n$ and $y$. Since the difference between the two split embeddings is a multiple of that coefficient of $w$, the chosen embedding also has norm at most $q^{-n}$. Dividing by $q^n$ gives an integral element at both places over $q$, and all other places were already integral. Thus the difference is a period. This proves the required matching in the rescaled chart at every level, while $a$ remains a unit and leaves the chart integral.

### Lean correspondence

- [`gen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsNormalisedMultiplicativeChart.lean#L143) constructs the compatible generators with the split bound. The same file uses `div_ok` for simultaneous integrality at the two split places.
- [`exists_normalised_chart`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsNormalisedMultiplicativeChart.lean#L200) takes the compatible limit and applies its inverse to all good lifts.
- [`main`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/WeilOperatorThetaTranslateShiftPrimeToQ.lean#L61) subsequently uses this matching to identify torsion operators with the multiplicative shift of a theta series.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
