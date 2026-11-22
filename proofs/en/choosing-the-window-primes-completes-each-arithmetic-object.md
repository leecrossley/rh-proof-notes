# Choosing the window primes completes each arithmetic object

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix a sufficiently small $\varepsilon>0$. Use a standard parameter record $C$ and the eventual order of choices $c_D,c_h,x$ from [the family design](point-kits-on-the-host-windows-give-a-family-design.md), with $c_D\ge0$, $c_h\ge402$, and the error parameter $g_{\rm err}\ge10$. Fix a scale $s=(x,\varepsilon,J)$, admissible ranks and a host with $C_{T2}$ as prescribed, and its canonical auxiliary prime $q_0$. Fix the two arrays of weights satisfying the preliminary weight windows. Let $M$ be the integer word count $\lceil 3\exp(C_\Gamma m^5f x^\varepsilon)^2 x^{C_F}\rceil$, take an injective code of these words by $(k-2)$-bit strings, and fix a weight label $u_0<n$. Assume the recursion `RecExP` for a point property $Q$ and the level-prime existence theorem `LevelPrime`.

Then for all sufficiently large allowed $x$, there is a point at exactly $s$ with the specified ranks, host, weights, code and label. It carries the required size, arithmetic and canonical-instance data, and satisfies $Q$. The point also has the tame, auxiliary-divisibility and twist conditions `withObj`. This is the point supply `ObjCP` used to form one kit at each allowed scale.

### Choose the level only after fixing its numerical factors

The good-chain construction [`chGood_of_host`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/SetUnipotentTranslate.lean#L477) builds a preliminary chain $P$ over the host and chosen ranks, with the given weights, code and distinguished label. Its conclusion `ChGood` includes the numerical inequalities for the recursion. All the hypotheses used to construct it hold after increasing the parameter and scale thresholds once. Apply the recursion (as in [the two-pass construction](two-passes-give-layered-objects-over-the-same-numerical-context.md)) to obtain positive integers $d_u$ and a positive real $D_*$ before selecting any word prime. Write
$$
X_u^*=(D_*/d_u)^{1/(fk)}\Gamma^{-2/(fk)}
$$
for the adjusted height, where $\Gamma>0$ is the common adjustment prescribed by $C,s,P$. For some $c_s>0$ uniform in the words, the recursion provides $\log X_u^*\ge c_s m s.L$.

The level-prime input supplies a prime $T_u$ in
$$
[X_u^*,\, X_u^*(1+1/(fk))]
$$
for every word, with the splitting, congruence and distinctness conditions of the level extension. The quantitative input here is the theorem `exists_levCh_of_levelPrime`: for every sufficiently large $x$ and good chain data with this positive logarithmic lower bound for all $u$, there is a level extension of that very chain with these $d_u,D_*,\Gamma$. It simultaneously selects the primes and records their window conditions. Use it to choose $L_v$. The recursion applies to this choice because its output on level extensions is universal for the given factors and adjustment. It returns the actual arithmetic record $D$ and its layered object $Y$ over $P,L_v$, with the prescribed weight and size conditions.

### Extract the point and verify its tests

The size theorem [`exists_sizeData_over`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsParametersOver.lean#L21) constructs an initial size record $L_0$ from the good context and the layered data. It carries $s$, the given weights and the required bounds, and identifies the field, ranks, word labels and level data with those of the original chain. In particular any word of $D$ corresponds to one of $P$ and has its selected prime.

Write $s.X'=\exp(x^{\varepsilon/3})$ for the lower cutoff in the point extraction. The relevant source scale estimate says that for sufficiently large $x$ the logarithmic lower bound $c_s m s.L\le\log X_u^*$ gives $s.X'\le X_u^*$. In the rank windows $m\ge x^{(1-\varepsilon/8)/2}$ and $s.L=x^\varepsilon$, so $c_s m s.L$ eventually dominates $x^{\varepsilon/3}$. The lower endpoint of the window therefore gives $s.X'\le T_u$ for every word. The size theorem for the other cutoff $s.w''(n)$ gives $1\le s.w''(n)$ on the same sufficiently late range.

Apply `exists_ledPart` to $D,Y,L_0$, with these two cutoff inequalities and $g_{\rm err}\ge10$. It yields a point extracted from the layers whose record has scale $s$, the two prescribed arrays of weights, the required valuation bounds and the canonical instance. These are exactly the four tests in the conclusion of the recursion, so $Q$ holds there. The transport from $P,L_v$ supplies the stated ranks, host primes, coefficient field, code and selected label. The tame and auxiliary-divisibility clauses of the good context and the local twist tests of $Y$ give the point conditions at the corresponding coefficient primes.

### Check the auxiliary prime on that point

The actual auxiliary prime of the resulting host is $q_0$, since the construction preserves the host data and its canonical congruence definition. It belongs to the prescribed level primes. The least-prime bound gives $q_0<s.X'\le b$, where $b=e^{s.L}$, so $\log q_0\le s.L$. The numerical window estimate in `and_q0Pt` also puts it below the generator cutoff used in the proof. It is different from the two progression primes by its defining exclusions. It is below each generator prime, which is at least $(kb)^8$, and is below every word prime by $q_0<s.X'\le T_u$. Thus it gives the required global twisting facts on the selected point. The proof uses the stated level-prime and numerical input theorems; their distribution and size arguments are upstream of this object construction.

### Lean correspondence

- [`objCP_and_of_recExP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsObjectsOfAdmissibleTwistDatum.lean#L70) fixes the bounds $g_{\rm err}\ge10,c_D\ge0,c_h\ge402$, chooses the preliminary and level extensions in order, and supplies the prescribed weight point.
- [`exists_levCh_of_levelPrime`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLevChOfLevelPrime.lean#L20) chooses the word primes with the existing factors. [`exists_ledPart`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsLedPart.lean#L195) extracts a point satisfying the four tests of the recursion.
- [`ObjCP.and_q0Pt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsObjectsOfAdmissibleTwistDatum.lean#L19) verifies the global twisting facts for the auxiliary prime. [`objCP_of_recExP`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsObjectsOfAdmissibleTwistDatum.lean#L121) combines them with $Q$ and the other point clauses.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
