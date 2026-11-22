# The excluded odd shifts and the unserved orbit gain

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be an ordinary inert prime with nonzero projected Frobenius element $h_p$ of even order $d$, with $p$ in the prescribed size range $p\le X''\le a$. Fix a word and layer $i<m$ and an orbit in the component with first coordinate zero. A place is $(0,t)$, and its $e$-th partner is $(0,t+eh_p)$. Write $s\in\mathbb Z/d\mathbb Z$ for the orbit index and $T$ for its set of top indices. Each index has a Young diagram $\nu_s$ of size $D_s\le a^2$. At a top index let $\alpha_s=\nu_s(0)-\nu_s(1)$, the number of height-one columns, and put $\alpha_s=0$ elsewhere. Assume $\alpha_s\le2a$. Write $C_s$ for the capacity, the second row length at a top index and the first row length elsewhere. Put $N_0=N_i$, $N_1=N_{i+1}$, and $N_m\ge\max(1,N_0,N_1)$. Use the shape comparisons
$$
A_s\le\alpha_s\ (s\in T),\qquad U_{s,e}\ge C_{s+e}\quad(e\ge1).
$$
Here $A_s$ is the numerical top size diminished by the geometry error, and $U_{s,e}$ is the corresponding numerical upper capacity at the partner.

For $s\in T$, let the numerical exclusion rule omit an odd $e$ if $e$ is the first positive shift to a different top place. The numerical gain $g_0$ for this orbit is the sum of $(A_s/p^e-U_{s,e})_+$ over the remaining positive odd shifts and all top indices, minus
$$
\mathrm{dl}=K_1 d N_m^2\log_p(2a)+K_2|T|\log_p^2(2a),
\qquad K_1\ge5,\ K_2\ge4 .
\tag{1}
$$
The height-one determinant estimate on the standard orbit expansion gives the local gain
$$
G_A=\sum_{s\in T}
 \sum_{\substack{e\ge1\ {\rm odd}\\\text{unless }e<d\text{ and }s+e\in T}}
  (\alpha_s/p^e-C_{s+e})_+-\mathcal D ,
\tag{2}
$$
where $\mathcal D$ is the exact factorial and digit loss
$$
\sum_s\bigl(N_1\ell_p(\alpha_s)+N_0N_1\ell_p(D_s-\alpha_s)\bigr)+
\sum_{s\in T}\ell_p(\alpha_s)^2,\qquad
\ell_p(0)=0,\quad \ell_p(n)=1+\lfloor\log_p n\rfloor\ (n>0).
$$
This is `gainA`. We show $g_0\le G_A$ and explain its use in the orbit bound. The coefficient estimate giving (2) is the [height-one calculation](hasse-derivatives-explain-the-height-one-orbit-gain.md) applied to the actual orbit by the [trace frame and Gauss comparison](recovering-the-standard-phase-from-the-actual-orbit-series.md).

If $1\le e<d$ and $s+e\in T$, the target is different from $s$, since no positive shift smaller than $d$ fixes an orbit point. It is reached for the first time at step $e$, since the map from $0,\dots,d-1$ to the orbit is injective. Hence every shift excluded in (2) is also excluded in the numerical gain. This implication is sufficient: the sum defining $g_0$ uses a subset of the shifts in (2). For each such term, $p^e>0$ and the size and capacity comparisons give $A_s/p^e-U_{s,e}\le\alpha_s/p^e-C_{s+e}$. Taking positive parts preserves the inequality. The nonnegative terms in (2) are bounded by $\alpha_s/p^e$, so the series converges and the termwise inequality can be summed. The top labels in the arithmetic sum correspond bijectively to the $s$ in $T$, since the orbit index parametrizes all places in this orbit once.

For the losses, put $\Lambda=\log_p(2a)\ge1$. The bounds $\alpha_s\le2a$ and $D_s-\alpha_s\le a^2$ imply $\ell_p(\alpha_s)\le2\Lambda$ and $\ell_p(D_s-\alpha_s)\le3\Lambda$, also for zero arguments. Thus the first sum in $\mathcal D$ is at most $d(2N_1+3N_0N_1)\Lambda\le5dN_m^2\Lambda$. The second is at most $4|T|\Lambda^2$. This proves $\mathcal D\le\mathrm{dl}$ by (1), and consequently $g_0\le G_A$.

For an orbit with the standard theta expansion, the kernel theorem gives determinant coefficient valuation at least $G_A$. Also the standard expansion itself has [integral jets in additive coordinates](two-coboundaries-and-frobenius-give-integral-additive-jets.md) and hence determinant coefficient valuation at least zero. If $g_0>0$ use (2) and $g_0\le G_A$; if $g_0\le0$ use integrality. The result is the bound $\max(0,g_0)$ for this type of orbit, as used in [the lift composition](adding-the-layer-valuations-of-the-theta-lift.md). It uses the standard biextension data and the expansion with sign $-1$.

**Lean correspondence.** The first-return rule and loss comparison are [`excl_of_top`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/WordFreeNumberLeOrbitBound.lean#L74) and [`loss_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/WordFreeNumberLeOrbitBound.lean#L111), with the termwise inequality assembled in [`wordFreeNumber_le_orbitBound`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/WordFreeNumberLeOrbitBound.lean#L168). The two coefficient inputs and the maximum are [`kvalGe_gainA`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/KvalGeOrbitGainWithoutOperator.lean#L106), [`kvalGe_zero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/StandardOrbitSeriesValuationBoundZero.lean#L363), and [`orbit_bound_rec`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/OrbitBoundStandardSeriesInertPlaces.lean#L22).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
