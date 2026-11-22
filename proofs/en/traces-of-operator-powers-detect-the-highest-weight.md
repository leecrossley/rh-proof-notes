# Traces of operator powers detect the highest weight

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $R$ be a commutative ring, $V$ an $R$-module, and $E=(E_{ab})_{1\le a,b\le N}$ a matrix of endomorphisms satisfying
$$
[E_{ab},E_{cd}]=\delta_{bc}E_{ad}-\delta_{da}E_{cb}.
$$
Let $M$ be stable under all these operators. Suppose $v\in V$ is highest modulo $M$, meaning $E_{ab}v\in M$ for $a<b$ and $E_{aa}v-\mu_av\in M$ for given $\mu_a\in R$. Let $H(\mu)$ be the upper triangular scalar matrix with diagonal $\mu_i+N-i$ and every entry strictly above the diagonal equal to $-1$. For every $n\ge0$,
$$
C_n v=c_n(\mu)v\pmod M,\qquad
C_n=\operatorname{tr}(E^n),\quad c_n(\mu)=\sum_{i,l}(H(\mu)^n)_{il}.
$$
In the polynomial row representation over any field $k$, $C_n$ acts on the entire dual Weyl space $\nabla_k(\nu)$ by $c_n(\nu)$ for every dominant nonnegative integral weight $\nu$.

### Commuting through a power

All matrix powers are taken in the endomorphism ring. The commutator product rule gives
$$
[E_{ab},(E^n)_{cd}]=\delta_{bc}(E^n)_{ad}-\delta_{da}(E^n)_{cb}.
$$
For the induction, expand $(E^{n+1})_{cd}=\sum_l E_{cl}(E^n)_{ld}$. The two product-rule terms with a Kronecker delta at $l=a$ or $l=b$ cancel because both are $E_{cb}(E^n)_{ad}$ with opposite signs. The remaining terms give the displayed formula at $n+1$. Its diagonal sum is zero, so $C_n$ commutes with every $E_{ab}$.

Work now in $V/M$. Write $r_{ni}=\sum_l(H^n)_{il}$. We prove by induction that $(E^n)_{ij}v=0$ for $i<j$ and $(E^n)_{ii}v=r_{ni}v$. At $n=0$ these are the identity-matrix statements. In an upper entry $(E^{n+1})_{ij}v=\sum_l E_{il}(E^n)_{lj}v$, the terms with $l<j$ vanish by induction and $l=j$ vanishes by highestness. For $l>j$ commute the raising operator $E_{il}$ past $(E^n)_{lj}$; the new term is $(E^n)_{ij}v=0$, since $j\ne i$. In the diagonal entry at $i$, the terms with $l<i$ again vanish. The $l=i$ term gives $\mu_i r_{ni}v$. For $l>i$ the same commutator now gives $(E^n)_{ii}v-(E^n)_{ll}v$, or $(r_{ni}-r_{nl})v$. Adding yields
$$
r_{n+1,i}=(\mu_i+N-i)r_{ni}-\sum_{l>i} r_{nl},\qquad r_{0i}=1.
$$
These are the row sums of powers of $H$, and summing the diagonal proves the trace formula.

### Extending the eigenvalue across the integral model

For matrix polynomials $E_{ab}=\sum_s x_{as}\partial_{bs}$. They have the required commutators by the product rule, and the [highest polynomial](maximal-row-height-gives-a-dominant-highest-vector.md) $h_\nu$ is annihilated by $E_{ab}$ for $a<b$, since adding row $a$ to row $b$ leaves each initial minor invariant. The case $M=0$ computes $C_n h_\nu$. Over $\mathbb Q$, the coefficient of $t^j$ in the row substitution $x_{bs}\mapsto x_{bs}+t x_{as}$ is $E_{ab}^{\,j}/j!$ when $a\ne b$. The coefficients for $a=b$ act by $\binom{E_{aa}}{j}$. Hence $C_n$ commutes with every divided row operator over $\mathbb Q$. The dual Weyl space over $\mathbb Q$ is the smallest subspace stable under those divided operators and containing $h_\nu$. Therefore the scalar on $h_\nu$ is the scalar throughout that space.

The operators $C_n$ and the scalar expression $c_n$ are defined integrally. Their equality on an integral dual Weyl polynomial follows by embedding its coefficients in $\mathbb Q$, where the equality has just been proved. Over an arbitrary field $k$, the flag-minor spanning theorem expresses any dual Weyl polynomial as a linear combination of reductions of integer flag-minor products. Each of those products is already in the integral dual Weyl module. Scalar extension carries $C_n$ and $c_n$ to the corresponding expressions over $k$, proving the assertion even when some factorials vanish in $k$.

### Lean correspondence

- [`glRel_pow_comm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/GlMatrixUnitPowCommutatorAndTraceCentral.lean#L9) is the commutator identity and trace centrality.
- [`trace_pow_hw`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TraceGlMatrixUnitPowHighestWeightMod.lean#L150) computes the trace modulo $M$.
- [`gel_dualWeyl_rat`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TraceRowOperatorPowerDualWeylHighestWeight.lean#L42) gives the scalar action over $\mathbb Q$.
- [`gel_dualWeyl_field`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/TraceRowOperatorPowerDualWeylFieldSmul.lean#L33) gives the base change by the integral minor products.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
