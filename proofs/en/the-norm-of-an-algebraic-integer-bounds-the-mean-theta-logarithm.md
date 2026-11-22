# The norm of an algebraic integer bounds the mean theta logarithm

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $\Lambda=\delta I$ be the normalized host curve-ideal lattice, with $d>0$ prime, $d\equiv7\bmod8$, $[\mathcal O_K:I]$ prime to $2d$, and $\delta^{12}=\Delta(I)$. Use any number field $M\subset\mathbb C$ containing the curve invariants and host embedding data. For each embedding $\rho:M\hookrightarrow\mathbb C$, let $\Lambda_\rho$ have the conjugate invariants and let $f_\rho$ be the normalized scalar theta at the unique half-period class with both CM projections nonzero. Set $N_\rho=\mathcal N_{\Lambda_\rho}(f_\rho)>0$, using the probability-normalized Gaussian torus metric. Write
$$
D_K=\frac{L'(1,\chi_K)}{L(1,\chi_K)},\qquad
B_K=\tfrac12(\log\sqrt d-\gamma_{\!E}+D_K).
$$
Then, with $\operatorname{mean}_\rho=[M:\mathbb Q]^{-1}\sum_\rho$,
$$
\operatorname{mean}_\rho\log N_\rho\le B_K,\qquad
\operatorname{mean}_\rho\max(0,\log N_\rho)
 \le\operatorname{mean}_\rho\log N_\rho+\tfrac14\log d+2\log C_0.
\tag{1}
$$
Here $C_0\ge1$ is the absolute constant of the [Jacobi expansion](a-jacobi-expansion-evaluates-the-scalar-theta-mean-square.md). The signed mean yields the archimedean norm upper bound for the natural theta family in every pair of even ranks.

**Use the integral product.** Choose bases $\Lambda_\rho=\omega_\rho(\mathbb Z+\tau_\rho\mathbb Z)$ as in the Jacobi calculation, with $1/2\le y_\rho=\operatorname{Im}\tau_\rho\le\sqrt d/2$. Let $\Theta_\rho$ be the even nonzero theta constant for the chosen half-period and $\eta_\rho=\eta(\tau_\rho)$. The [integral theta-to-eta ratio](the-twelfth-theta-to-eta-ratio-has-integral-conjugates.md) gives one nonzero algebraic integer $X\in M$ satisfying $|\rho X|=(|\Theta_\rho|/|\eta_\rho|)^{12}$ for all $\rho$. The absolute field norm $\prod_\rho|\rho X|$ is at least one because it is the absolute value of a nonzero rational integer. Taking logarithms gives
$$
\operatorname{mean}_\rho(\log|\Theta_\rho|-\log|\eta_\rho|)\ge0.
$$
The scalar mean square and the area formula are $N_\rho=(\sqrt{2y_\rho}|\Theta_\rho|^2)^{-1}$ and $A_\rho=4\pi^2y_\rho|\eta_\rho|^4$. Taking logs and eliminating $y_\rho$ gives the exact relation
$$
\log N_\rho
 =-\tfrac12\log A_\rho+\tfrac12\log(2\pi^2)
   -2(\log|\Theta_\rho|-\log|\eta_\rho|).
$$
Now use the [class mean of the area](the-cm-class-mean-of-the-normalized-period-area.md), which is $\gamma_{\!E}+\log(2\pi^2/\sqrt d)-D_K$. The inequality for the theta-to-eta ratio gives the first assertion in (1).

For the positive part, the formula for $N_\rho$, the upper bound $2y_\rho\le\sqrt d$ and $|\Theta_\rho|\le C_0$ give $\log N_\rho\ge-\tfrac14\log d-2\log C_0$. For a real number $u\ge-A$ with $A\ge0$, $\max(0,u)\le u+A$. Apply this separately to each logarithm and average. This proves the second assertion.

**The scale used for the host family.** In the host $v=\operatorname{rd}(E)/2$, with $\operatorname{rd}(E)=|\operatorname{disc}(E)|^{1/[E:\mathbb Q]}$, and $v\ge\sqrt d$. The numerical inequality follows from the host root-discriminant estimate $\operatorname{rd}(E)\ge 2^{e+1-2^{-e}}\sqrt d$ for its ramification parameter $e\ge2$: $e+1-2^{-e}\ge1$. Consequently, if $L_{\rm sc}\ge\log v+|D_K|$, then $L_{\rm sc}\ge1/2$ since $d\ge7$, and $B_K\le L_{\rm sc}/2$ since $\gamma_{\!E}>0$. Also $\tfrac14\log d\le L_{\rm sc}/2$. The positive-part bound is therefore at most $(1+4\log C_0)L_{\rm sc}$. If one instead has $2L_{\rm sc}\ge\log\operatorname{rd}(E)+|D_K|$, the signed bound is at most $L_{\rm sc}$.

For even ranks $a,b$, let the pair $L,L'$ be admitted, and assume the number field $M$ also contains the Taylor coefficients of $e_{\mathrm{nat},\chi}(L,L')$. The [conjugate norm formula](the-genus-one-mean-square-controls-every-conjugate-theta.md) computes its squared norm at each embedding as $N_\rho^{[E:K]ab}$. Thus the signed average of the family norm logarithms is at most $\tfrac12[E:K]ab\,L_{\rm sc}$ for the first scale condition. The ordinary norms and translation invariance have already been proved in [the torus mean-square argument](the-natural-theta-has-the-same-mean-square-on-every-admitted-pair.md), and the conjugate norm formula proves independence of the admitted pair separately at each embedding. This gives the four parts of the archimedean family package once the single-average representation has been constructed for the natural family.

**Lean correspondence.** The scalar inequalities and their hypotheses are in [`HidaSetting` and the mean statements](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/BlockTheory/GlobalSignature/SignedLogMeans.lean#L23). The analytic and algebraic inputs combine in [`core`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DecoratedLatticeProofs/ThetaZeroMeanLogNormConjugatesOfWeber.lean#L26) and [`theta0Mean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DecoratedLatticeProofs/ThetaZeroMeanLogNormConjugatesOfWeber.lean#L132). The numerical root-discriminant input is [`factRd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/RankBoundMonotoneInDimension.lean#L556), used in [`two_sqrt_le_rd`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExplicitPosMeanOfPositivePart.lean#L32) and [`bound_le_half`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsPeriodLatticeIff.lean#L279). The signed theorem used in the family is [`exists_thetaZeroMeanLogLeConstMul`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/ExistsThetaZeroMeanLogLeConstMulStatement.lean#L7), and the complete family package is [`familyNorms`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/NormalisedFamilyNormBoundAbsoluteConstant.lean#L64). It is used in [the kernel half-chain bounds](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/DivisorProofs/KernelHalfChainNumbersAnyLevelPrime.lean#L226).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
