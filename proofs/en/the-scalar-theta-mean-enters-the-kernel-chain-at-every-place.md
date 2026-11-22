# The scalar theta mean enters the kernel chain at every infinite place

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Statement

Let $K_c$ be a totally imaginary coefficient number field, and $M\subset\mathbb C$ a number field containing its fixed image, the host torus data, the period-generator coefficients, and the Taylor coefficients of the standard theta vacua used below. Let $\mathcal R=\operatorname{Hom}_{\mathbb Q}(M,\mathbb C)$ and let $V$ be the set of infinite places of $K_c$. Write $v(\rho)\in V$ for the place represented by the restriction of $\rho$. The coefficient field $K_c$ is distinct in the notation from the imaginary quadratic field of the CM lattice.

Take a kernel chain with $m\ge2$ lift labels $i=0,\ldots,m-1$. The first $m-2$ labels carry individual maps, and the last two carry one coupled map. Write $r_i>0$ for the even ranks at levels $i=0,\ldots,m$, $g_i=r_i r_{i+1}$, and $R=r_m$. Use the host identification of ranks $r_i=k+i(t+1)$, where $t\ge0$ and $k\ge m+3$, and $f\ge1$ is the number of host complex variables for each matrix entry. Let $\mathcal T$ be the set of the $f$ period and weight labels. The row data have degree weights $\nu_{i\tau j}\ge0$ for $0\le j<r_i$, and we abbreviate $D_{i\tau}=\sum_j\nu_{i\tau j}$, $H_{i\tau}=\sum_j\operatorname{ph}(\nu_{i\tau j})$, where $\operatorname{ph}(x)=x\log x-x$ with the continuous value $0$ at $x=0$. Take positive volume $v_0=rd/2$, generator primes $p_0,p_1$, a word prime $T\ge2$, and scale parameters $L\ge1$, $L_a\ge L$. In the application $rd$ is the host root discriminant. Put
$$
 U=fm^2R^2\log(p_0p_1T).
$$

Use the following inputs of the kernel-chain deduction.

1. The torus, theta base, and row data are compatible with the host. The host theta is normalized by a discriminant twelfth root, and its determinant character and normalized family satisfy the transformation and coefficient algebraicity laws. The standard vacuum is the natural theta at each standard lattice pair. If $\kappa_i(\rho)$ denotes its log squared norm in the conjugate torus at $\rho$, then $\kappa_i(\rho)=g_i a(\rho)$ for one real scalar $a(\rho)$ for all the rectangles. For every scale $S$ with $\log v_0+|L'_K(1)/L_K(1)|\le S$, the mean of $\kappa_0$ is at most $C_t f g_0 S$. Here $C_t$ is the universal constant of the signed theta mean theorem, and $L_K$ is the quadratic Dirichlet $L$-function of the CM field.
2. The period logarithms $o_\tau(\rho)$, defined by the negative logarithmic metric of the integral eigenline generator at $\tau$, have full embedding mean $\log\Omega$ independent of $\tau$. The [generator-period proof](the-relative-different-corrects-the-mean-period-metric.md) gives $o_\tau(\rho)=\log(A_\rho/\pi)-2\log|\rho(c_\tau)|$ for the integral eigenline generator $c_\tau$ and CM area $A_\rho>0$ at $\rho$.
3. At each $\rho$, the ordinary kernel at $i<m-2$ has squared-norm bound $e^{B_i(\rho)}$ and the coupled kernel has squared-norm bound $e^{B_{m-2}(\rho)+B_{m-1}(\rho)}$, all for the metrics at $v(\rho)$. The input squared norms are nonnegative. For some $C_K,E\ge0$, and class counts $h_j$ and index counts $n_j$ in $\mathbb Z_{\ge0}$ satisfying $h_j,n_j\le e^{EU}$ for $0\le j\le m$, the exponent is
$$
 \begin{split}
 B_i(\rho)={}&\sum_{\tau\in\mathcal T}(H_{i\tau}-D_{i\tau}o_\tau(\rho))
       +\kappa_i(\rho)+f g_i\log(8+32f g_i v_0)\\
 &+2C_K U+\sum_{\tau\in\mathcal T}(1+2g_i\log(2D_{i\tau}+2))
       +\log(h_i h_{i+1})+\log(n_i n_{i+1}).
 \end{split}
$$
Here and in the count bounds below use the Lean convention $\log 0=0$ for a possibly empty finite index set. Positive real quantities use the ordinary logarithm.
4. The numerical rows satisfy $\log rd\le L$, $|L'_K(1)/L_K(1)|\le L$, and $\log p_j\le C_Y L+1$ for $j=0,1$, with $C_Y\in\mathbb R$. For the auxiliary scale parameters $b,x,A$ assume $b\ge2$, $\log b\le L$, $rd\le b$, $fR\le b$, $4x\le b$, $A=xb$, and $\nu_{i\tau j}\le3A$.

There exist period logarithms $o_\tau(v)$ and a theta logarithm $\theta(v)$ with
$$
 \frac1{|V|}\sum_{v\in V}o_\tau(v)=\log\Omega,\qquad
 \frac1{|V|}\sum_{v\in V}\theta(v)\le 2\max(C_t,0)L.
$$
At each infinite place these logarithms can replace $o_\tau(\rho)$ and $\kappa_i(\rho)$ in the ordinary and coupled kernel bounds, with $\kappa_i$ replaced by $f g_i\theta(v)$. The counts can be absorbed into a single error $K_i\le(C_K+2E)U$. With $C=C_K+2E+2\max(C_t,0)+20+2\max(C_Y,0)$, the resulting data furnish the archimedean part of the chain estimate `KerSide`. The following proof isolates its averaging and numerical steps from the hypotheses giving the pointwise kernels and the count bounds. [Numerical deduction `kerSide_of_meansS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L104) · [Geometric application `kerSide_chainS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L219) · [Pointwise exponent `kernelBound_sq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/DivisorBase/TopPlaceLogTheta.lean#L17)

## Proof

For the standard pair the relative determinant ideals are the unit ideal. The character is therefore $1$. The refining average over an unchanged lattice has a single coset, and the intertwiners at a standard pair are the identities. Thus the natural vector is exactly the standard vacuum. Because the normalized family has algebraic Taylor coefficients at every admitted pair, the finitely many vacua can all be included in $M$. In fact the algebraicity statement here supplies a number field for each complete Taylor series. Taking the compositum of those finitely many fields, the coefficient field and fields containing the algebraic torus data and period generators gives the indicated common field. [Standard pairs and vacuum `eNat_std`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/NormalisedFamilyStandardLatticesEqBaseVector.lean#L114) · [Field data `ThetaFieldData`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/DivisorBase/TopPlaceLogTheta.lean#L56)

For clarity, let $F_\rho$ be the scalar vacuum on the conjugate elliptic lattice, and $N_\rho>0$ its Gaussian-weighted mean square on the corresponding torus. A rational orthonormal frame for the rectangle, transported along the conjugation, gives $f g_i$ copies of $F_\rho$. The torus measure is a product measure in these coordinates. Hence the squared norm is $N_\rho^{f g_i}$ and we can take $a(\rho)=f\log N_\rho$. This is the power identity established in [The genus-one mean square controls every conjugate theta](the-genus-one-mean-square-controls-every-conjugate-theta.md). The signed mean bound of [The norm of an algebraic integer bounds the mean theta logarithm](the-norm-of-an-algebraic-integer-bounds-the-mean-theta-logarithm.md) can be applied with scale $2L$, since $v_0=rd/2$ and
$$
 \log v_0+|L'_K(1)/L_K(1)|\le\log rd+|L'_K(1)/L_K(1)|\le2L.
$$
The mean of $\kappa_0$ equals $g_0$ times the mean of $a$. Since $g_0>0$, division by $g_0$ gives
$$
   \frac1{[M:\mathbb Q]}\sum_\rho a(\rho)\le 2\max(C_t,0)fL.
$$
[Rank-product identity `logThAt_eq_mul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/LogNormConjVacuumEqRankProductMul.lean#L20) · [Dividing the first rank product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L282)

Since $K_c$ is totally imaginary, each $v\in V$ represents exactly two embeddings of $K_c$. Each has exactly $[M:K_c]$ extensions to $M$ in characteristic zero. Accordingly each fiber $v(\rho)=v$ has $D=2[M:K_c]$ elements, and its uniform weights are
$$
 w(v,\rho)=D^{-1}\mathbf1_{\{v(\rho)=v\}},\qquad
 \sum_\rho w(v,\rho)=1,\qquad
 \frac1{|V|}\sum_v w(v,\rho)=\frac1{[M:\mathbb Q]}.
$$
Define $o_\tau(v)=\sum_\rho w(v,\rho)o_\tau(\rho)$ and $\theta(v)=f^{-1}\sum_\rho w(v,\rho)a(\rho)$. Then the two mean statements follow from the last weight identity and the two full embedding averages. In particular the individual $\theta(v)$ are signed real numbers. The exact identity used in the kernel transfer is $\sum_\rho w(v,\rho)\kappa_i(\rho)=f g_i\theta(v)$. [Place weights `exists_weights`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/FinrankEqTwoMul.lean#L43) · [Generator period mean](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/MeanLogMetricGeneratorEqMeanPeriodStatement.lean#L7)

For any $i<m-2$ and any $v$, choose a member of its fiber minimizing $B_i(\rho)$. This minimum is at most $\overline B_i(v)=\sum_\rho w(v,\rho)B_i(\rho)$. The pointwise kernel inequality uses the same metrics at every embedding in this fiber. Multiplying $e^{B_i(\rho)}\le e^{\overline B_i(v)}$ by the nonnegative input squared norm gives the bound with exponent $\overline B_i(v)$. For the coupled kernel minimize the sum $B_{m-2}(\rho)+B_{m-1}(\rho)$ over the one fiber. Its minimum is at most $\overline B_{m-2}(v)+\overline B_{m-1}(v)$, which gives the coupled bound by the same argument. This also applies when $m=2$, in which case there are no ordinary maps. For any bijective relabeling of the $m$ lift labels, summing over the labels of an individual map selects its unique label and summing over those of the coupled map selects precisely the last two labels. This is the form of `FactorBounds`. [Transfer `factorBounds_of_weights`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/PrimeWordLocalConstants.lean#L107) · [Definition `FactorBounds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Divisors/FactorBounds.lean#L40)

Taking the fiber average of $B_i$ is an affine calculation. The terms independent of $\rho$ survive because the weights sum to one. The two variable terms become the linear form in $o_\tau(v)$ and the term $f g_i\theta(v)$ identified above. Set
$$
 K_i=C_K U+\tfrac12\log(h_i h_{i+1})+\tfrac12\log(n_i n_{i+1}).
$$
Each of the two products is at most $e^{2EU}$. If a product is positive its logarithm is at most $2EU$, and if it is zero the same bound follows from $EU\ge0$ and the convention for the logarithm. Therefore $K_i\le(C_K+2E)U$. The averaged exponent is exactly
$$
  \sum_\tau (H_{i\tau}-D_{i\tau}o_\tau(v))
  +f g_i\theta(v)+f g_i\log(8+32f g_i v_0)+2K_i
  +\sum_\tau\bigl(1+2g_i\log(2D_{i\tau}+2)\bigr).
$$
In `liftedMapLogSize` the two additional count slots are set to zero, since the counts already occur in $K_i$. The reading condition `Reads` identifies the two sums over the recorded weight rows with $H_{i\tau},D_{i\tau}$. [Affine identity `kernelBound_wt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/PrimeWordLocalConstants.lean#L55) · [Numerical exponent `liftedMapLogSize`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/ThetaSupremumBounds/DivIneqExplicit6.lean#L15)

For the remaining numerical bounds, $0\le g_i\le R^2$ by monotonicity of the ranks. Since $f R\le b$, $R\le b$, and $v_0\le b/2$,
$$
 8+32f g_i v_0\le 8+16b^3\le 32b^3\le b^8
$$
using $b\ge2$. Likewise $3x\le b$ and $R\le b$ give $D_{i\tau}\le R\cdot3xb\le b^3$. Thus $2D_{i\tau}+2\le4b^3\le b^5$. After taking logarithms the bounds are $8L$ and $5L$, both at most $CL_a$. The prime sizes give $\log(p_0p_1)\le (2\max(C_Y,0)+2)L\le CL$. The chosen $C$ also bounds $C_K+2E$ and $2\max(C_t,0)$. Hence the stage error meets the `KerSide` bound $K_i\le C U+C f R^2\log(p_0p_1)$, and the two zero count slots satisfy their bounds by positivity. These are its exact numerical conditions. The squared-norm bounds previously transferred to the place $v$ verify its map predicate. [Volume term `log_eight_leS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L28) · [Degree term `log_nu_leS`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L63) · [Archimedean chain data `KerSide`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/Divisors/FactorBounds.lean#L50)

The geometric theorem uses $E=C_c+C_i+C_y$, the sum of constants for the class, index and terminal-level counts. Its period-generator and squared-norm inputs remain necessary. The scalar theta estimate contributes precisely the signed mean $2\max(C_t,0)L$ in the chain’s archimedean part. This step supplies the squared-norm factors in the divisor argument, which are subsequently combined with its finite-place and period factors. [Named inputs of the geometric application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L221)

## Source and verification

The averaging, coupling and numerical estimates were checked against the pinned source. The pointwise analytic kernel bounds, count estimates and generator-period identity enter as the hypotheses above. No Lean replay or additional axiom check was performed for this note.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
