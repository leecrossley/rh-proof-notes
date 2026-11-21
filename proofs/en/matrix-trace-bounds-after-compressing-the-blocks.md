# Matrix trace bounds after compressing the blocks

[Chinese proof](../zh/%E6%A0%BC%E7%9A%84%E6%96%9C%E7%8E%87%E4%BC%B0%E8%AE%A1%E6%80%8E%E6%A0%B7%E7%94%A8%E5%88%B0%E7%9F%A9%E9%98%B5%E8%BF%B9.md)

## Statement

Let $I$ be finite and $D,d_i,r_i$ nonnegative integers. Take complex matrices $B_i$ of size $D\times d_i$ and $V_i$ of size $d_i\times r_i$ with $V_i^*V_i=I_{r_i}$. For $g_i\ge0$ set $A_i=\sqrt{g_i}B_i$, $C_i=A_iV_i$,
$$
Q=\sum_iA_iA_i^*,\quad Q'=\sum_i C_iC_i^*,\quad R=\sum_i d_i,\quad R'=\sum_i r_i.
$$
The squared Frobenius norm of a matrix is the sum of squared absolute values of its entries. Let real parameters satisfy
$$
D_*>0,\quad 0<\sigma\le1/20,\quad D_*/\sigma\le R,\quad
-1\le\eta_0\le\sigma/2,\quad \eta_1\le\sigma/2,\quad
0\le e_0,\quad \sqrt{e_0}\le\sigma/2,\quad 0\le\delta\le1/4.
$$
Assume $R-R'\le\delta R$ and the `InputSG` hypotheses
$$
\|A_i^*A_j\|_F^2\le (1+\eta_0)d_id_j/D_* \quad(i\ne j),\qquad
\|A_i^*A_i-I_{d_i}\|_F^2\le e_0d_i,\qquad D\le(1+\eta_1)D_*.
$$
Then $D>0$, $R'>0$, $2e_0\le1/4$, and
$$
\operatorname{tr}(Q'^2)\le (1+5\sigma+3\sqrt\delta)\frac{(\operatorname{tr}Q')^2}{D},
\qquad
\sum_i\|C_i^*C_i-I_{r_i}\|_F^2\le 2e_0R'.
$$

## Upper bounds after compression

Put $a=\sqrt{e_0}$. Trace Cauchy–Schwarz gives $\operatorname{tr}(A_i^*A_i)\ge(1-a)d_i$. Therefore $\operatorname{tr}Q\ge(1-a)R>0$ and $D>0$. Also $R'\ge3R/4>0$ and $2e_0\le2(\sigma/2)^2\le1/4$.

By cyclicity, $\operatorname{tr}(Q^2)=\sum_{i,j}\|A_i^*A_j\|_F^2$. The diagonal term is at most $(1+a)^2d_i$ by the triangle inequality. Sum the cross bounds using $1+\eta_0\ge0$, and use $D_*\le\sigma R$ to deduce
$$
\operatorname{tr}(Q^2)\le[1+\eta_0+(1+a)^2\sigma]R^2/D_*.
$$
Unitary changes of basis complete the columns of each $V_i$ to an orthonormal basis. Thus $C_i^*C_j=V_i^*A_i^*A_jV_j$ is a block of a unitary transform and its Frobenius norm can only decrease. Hence $\operatorname{tr}(Q'^2)\le\operatorname{tr}(Q^2)$. The same argument for $V_i^*(A_i^*A_i-I_{d_i})V_i$ bounds the sum of the squared compressed defects by $e_0 R\le2e_0R'$.

## Lower bound for the retained trace

For $P_i=V_iV_i^*$ the trace lost from block $i$ is
$$
\operatorname{tr}\bigl((I-P_i)A_i^*A_i\bigr)
=(d_i-r_i)+\operatorname{tr}\bigl((I-P_i)(A_i^*A_i-I)\bigr).
$$
The last term is at most $\sqrt{d_i-r_i}\,a\sqrt{d_i}$. Summing via Cauchy–Schwarz gives $\operatorname{tr}Q-\operatorname{tr}Q'\le(R-R')+a\sqrt{(R-R')R}\le(\delta+a\sqrt\delta)R$. Therefore with $t=\sqrt\delta$,
$$
\operatorname{tr}Q'\ge(1-a-t^2-at)R>0
$$
since $t\le1/2$ and $a\le1/40$.

## The constants in the ratio

The bound on $D$ and the upper bound on the square trace give
$$
D\operatorname{tr}(Q'^2)\le(1+\eta_1)[1+\eta_0+(1+a)^2\sigma]R^2
\le(1+5\sigma)(1-a)^2R^2.
$$
For the last step, upper bound $\eta_0,\eta_1,a$ by $\sigma/2$. The difference between $(1+5\sigma)(1-\sigma/2)^2$ and $(1+\sigma/2)[1+\sigma/2+(1+\sigma/2)^2\sigma]$ is $2\sigma-\tfrac{13}{2}\sigma^2+\tfrac12\sigma^3-\tfrac18\sigma^4\ge0$ for $0<\sigma\le1/20$, and $1-\sigma/2\le1-a$.

Write $b=1-a$, $v=t(t+a)$ and $P=1+5\sigma+3t$. Then
$$
2P(t+a)\le 2\cdot(11/4)\cdot(21/40)=231/80\le3b.
$$
It follows that $2Pbv\le3tb^2$, so expansion gives $P(b-v)^2\ge(1+5\sigma)b^2$. By the trace lower bound and $b-v>0$,
$$
D\operatorname{tr}(Q'^2)\le(1+5\sigma)b^2R^2
\le P(b-v)^2R^2\le P(\operatorname{tr}Q')^2.
$$
Division by $D$ gives the required ratio.

## Source and application

The ratio bounds the spread of the eigenvalues of $Q'$, since $\operatorname{tr}(Q'^2)\ge(\operatorname{tr}Q')^2/D$. The other bound controls the total departure of the blocks from isometries. The slope estimate uses $\eta=5\sigma+3\sqrt\delta$ and $e=2e_0$ in its term $(\eta+4\sqrt e)H_*$. The local rank-weighted mean and the gap $r$ to the largest shifted maximal slope are formed in `frame_at_of`. [Global slope estimate](from-local-lattice-slopes-to-a-global-slope-bound.md) · [Application to the discrepancy](quotient-slopes-and-count-discrepancy.md)

- `InputSG`, `FrameTraceRatioLinear` and `FrameDeviationLinear` state the input and the two estimates. [Frame estimates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/FrameTraceRatioFinEquiv.lean)
- `compressDiagDefectBound` and `compressTraceSquareBound` prove the bounds, with the two numerical comparisons in `num_main` and `num_ram`. [Compression and constants](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/TraceConjTransposeMulSelf.lean)
- `ramification_linear_case_holds` expresses the compression for linear maps. `ramification_condition_holds` and `joint_a_ramified_holds` apply the lattice slope theorem. The actual window construction enters via `frame_at_of`. [Ramification and the lattice theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SizeWindowBrackets/ChainSlopeWindows/JointDModelAppliesUnitLattice.lean) · [Window frame](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/TopDensityNGeSixteen.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
