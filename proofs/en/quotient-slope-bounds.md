# Two quotient-slope bounds from local lengths

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E9%95%BF%E5%BA%A6%E5%A6%82%E4%BD%95%E7%BB%99%E5%87%BA%E5%95%86%E6%A0%BC%E7%9A%84%E4%B8%A4%E6%9D%A1%E6%96%9C%E7%8E%87%E7%95%8C.md) · [Reading and review status](../../STATUS.md)

The [count-discrepancy argument](quotient-slopes-and-count-discrepancy.md) needs a lower bound on the mean slope and an upper bound on the maximum slope. This note deduces both from the local formulas, retaining their common contribution and explicitly bounding the additional losses on exceptional places.

## Numerical data and the two claims

Let $W,J$ be finite sets of places and lift indices, respectively, with $\lambda_w\ge0$ for $w\in W$. The application obtains $\lambda_w$ by multiplying a logarithmic weight by the ramification index. For real $g_{jw},F_{jw},E_{jw}$ and $\tau_w$, put

$$
\begin{aligned}
s_w&=\sum_{j\in J}(g_{jw}+F_{jw}-E_{jw}),&
G_a&=2\sum_w\lambda_w\Big(\sum_{j\in J}g_{jw}-\tau_w\Big),\\
F_o&=2\sum_w\lambda_w\sum_{j\in J}F_{jw},&
E_e&=2\sum_w\lambda_w\sum_{j\in J}E_{jw}.
\end{aligned}
$$

It follows that $G_a+F_o-E_e=2\sum_w\lambda_w(s_w-\tau_w)$. Write $s'_w$ for the local exponent in the actual slope formula, $\Delta_w\ge0$ for the additional local loss bound, $L_w$ for the recorded length in the formula, and $W_T\subseteq W$ for the places treated separately. In the application these are the places with residue characteristic equal to the specified $T$.

Write $\mu_M,\mu_{M,1},\mu_N$ for the mean slopes of the base, intermediate and quotient lattices, and $\nu_M,\nu_{M,1},\nu_N$ for their maximum slopes. Under the hypotheses below the mean-slope claim is

$$
\mu_N\ge\mu_M+G_a+F_o-E_e-(4Q+L_T+R_X+1). \tag{1}
$$

For the maximum-slope claim, assume separately that each $s'_w\le s_w$, that $\nu_{M,1}\le\nu_M$, and that $\nu_N\le\nu_{M,1}+2\sum_w\lambda_w(s'_w-\tau_w)$. Then

$$
\nu_N\le\nu_M+G_a+F_o-E_e. \tag{2}
$$

## Mean-slope hypotheses

Take real $d_M,d_u,\delta,f,T,b,Q,P_T,R_d,L_T,R_X$. Assume $d_M>0$, $0\le\delta<1$ and $d_u=(1-\delta)d_M$. At $w\in W_T$ assume $\tau_w=0$. At $w\notin W_T$ assume $L_w\le d_M(\tau_w+\Delta_w)$. Also assume

$$
2\sum_{w\in W_T}\lambda_w L_w/d_u\le P_T,\qquad
2\sum_{w\in W}\lambda_w(s_w-s'_w)\le R_d .
$$

The [local mean-slope formula](local-lengths-and-lattice-slopes.md) is applied in the form

$$
\mu_N=\mu_{M,1}
+2\sum_w\lambda_w(s'_w-\tau_w)
-2\sum_w\lambda_w(L_w/d_u-\tau_w). \tag{3}
$$

Write $T_a=2\sum_w\lambda_w\tau_w$. Assume all $\tau_w\ge0$, and

$$
\begin{gathered}
\delta\le 2f/T\le 1/2,\quad T_a\le b^2,\quad
Q=\sum_w\lambda_w\Delta_w,\quad P_T\le L_T,\quad R_d\le R_X,\\
\mu_{M,1}=\mu_M-f\frac{\log(T-1)}{T-2},\qquad
4fb^2/T+f\frac{\log(T-1)}{T-2}\le1 .
\end{gathered}
$$

In the application $T>2$. The source statement uses Lean's total real operations in general, including zero as the quotient with denominator zero and $\log 0=0$, with $\log u=\log|u|$ for $u\ne0$. The proof uses only the stated equalities and inequalities.

## Absorbing the change of rank

Since $d_u=(1-\delta)d_M>0$, for $w\notin W_T$ we have

$$
L_w/d_u-\tau_w\le
\frac{\Delta_w}{1-\delta}+\frac{\delta}{1-\delta}\tau_w .
$$

At $w\in W_T$ the $\tau_w$ vanish and the weighted contribution is at most $P_T$. Since $\lambda_w,\Delta_w,\tau_w$ are nonnegative, extending the sums bounding the other contributions to all of $W$ yields

$$
2\sum_w\lambda_w(L_w/d_u-\tau_w)
\le P_T+\frac{2Q}{1-\delta}+\frac{\delta}{1-\delta}T_a
\le P_T+4Q+4fb^2/T .
$$

Here $\delta\le1/2$ gives $1/(1-\delta)\le2$, and $\delta/(1-\delta)\le2\delta\le4f/T$. In (3), using $s_w$ instead of $s'_w$ in the common term costs at most $R_d$ in the lower bound. Use the expression for $\mu_{M,1}$. The resulting error is at most $4Q+P_T+R_d+4fb^2/T+f\log(T-1)/(T-2)$. By the hypotheses this is at most $4Q+L_T+R_X+1$, giving (1). To obtain (2), replace $s'_w$ by the greater $s_w$ in the maximum-slope hypothesis, using $\lambda_w\ge0$, and then use $\nu_{M,1}\le\nu_M$.

## Use in the count-discrepancy proof

In `slopesN_at_of`, $Q$ is the sum `IOsum`. Since $Q\ge0$, $4Q\le CQ$ for a uniform $C\ge4$. The remaining local bounds give $L_T\le C|T_{\rm top}|m(a_E/k+b')\log T$ and $R_X\le CX''$. They turn the error in (1) into the required bound by $L_5$. The maximum-slope bound can be relaxed by the nonnegative term $CmB_0$ to match the numerical conditions. The set $T_{\rm top}$ consists of vertices in the finite group and $T$ denotes the selected residue characteristic.

- The inputs and conclusions are in [`HypLow`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ClaimGaFree.lean#L65), [`HypLow2`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ClaimGaFree.lean#L80), and [`HypHigh`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ClaimGaFree.lean#L94).
- The common term is [`weightedSlopeExcess_decomposition`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/WeightedSlopeExcessDecomposition.lean#L9); the bounds are [`lower_bound_simplified`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/WeightedSlopeExcessDecomposition.lean#L180) and [`claimHigh_valid`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/WeightedSlopeExcessDecomposition.lean#L191).
- The actual comparison data appear in [`Places_at`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TopDensityNGeSixteen.lean#L1516), [`slopesN_at_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TopDensityNGeSixteen.lean#L1529), and [`model_slopes_five`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/QuadraticLogDerivCongr.lean#L678). The local results used by `linkGLOBAL_items` are linked through [`LinkMin.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/LinkMin.lean) and [`PlacesMin.lean`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/PlacesMin.lean).

English translation draft. The local length formulas and comparisons are assumed at this step.
