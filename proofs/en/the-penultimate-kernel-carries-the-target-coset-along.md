# The penultimate kernel carries the target coset along

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the sharp-chain data and the field, prime, character, selection and twist-avoidance hypotheses of [the ordinary kernel proof](the-ordinary-point-kernel-transforms-with-the-level-characters.md). Keep the hypotheses `ChIdx.Ok` and `ChTh.Ok` for the class indexing and the theta distribution. At the penultimate step $i=m-2$, the source has one extra coordinate in its large matrix space and the target has zero. A source point $p$ consists of a decorated lattice with its frames. A target point is $(p',Y)$, where $p'$ consists of the target decorated lattice and frames and $Y$ is an admissible coset in the target space. Then for any source and target frame actions $g,g'$,
$$
k_i\bigl(gp,(g'p',\gamma'Y)\bigr)
=\rho_{i+1}(g')k_i\bigl(p,(p',Y)\bigr)\rho_i(g^{-1}),
$$
where $\gamma'$ is the rational unitary component of $g'$. The crucial local hypotheses in `ChIdx.Ok` are that the coefficient at this step is insensitive to the choice of representative of $Y$, that it has the specified period in the matrix argument, that the target conjugating matrix is the identity, and that the source and target frame groups carry the indicated level characters.

### The coset and the extra column

Use $\mathcal G$ for the type places, $\mathcal Q$ for the twist places and $q_P$ for the norm of $P\in\mathcal B=\mathcal G\sqcup\mathcal Q$. Write $\mathcal O_P=\mathcal O_{E,P}$. If $N'$ is the target lattice, an admissible coset has a representative $y$ that lies in $q_P^{-1}N'_P$ at a type place and in $q_P^{-M}N'_P$ at a twist place. The differences of representatives lie in $N'_P$ at a type place and in $q_P^M N'_P$ at a twist place. Here $M\ge1$ is the coset depth. More explicitly, $Y=y+L$ where $L$ is the intersection over $\mathcal B$ of the modules of these allowed differences. Each element of $Y$ meets the same denominator conditions. The map $\gamma'$ sends the local lattices to those of $\gamma'N'$ and commutes with scalar multiplication, so $\gamma'Y$ is an admissible coset for the moved lattice.

For a coefficient-map argument $x$ let $X=(F'_P)^{-1}xF_P$ and let $y_P=(F'_P)^{-1}y$. The local coefficient is $\Psi_P(X,y_P)$, the local large-matrix test function applied to
$$
J(X,y_P)(v,t)=Xv+t y_P.
$$
It includes the fixed source conjugating matrix and the corresponding scalar normalization. The target conjugating matrix is the identity. The hypothesis `psiInv` says that $\Psi_P(X,y_P+z)=\Psi_P(X,y_P)$ for $z\in\mathcal O_P^{N_{i+1}}$ at a type place and $z\in q_P^M\mathcal O_P^{N_{i+1}}$ at a twist place. Thus the local coefficient depends only on $Y$, as the difference between any two possible coordinate representatives belongs to the asserted period.

The scalar weight for the finite kernel sum is $\phi_T(x)\prod_P\Psi_P(X,y_P)$. If $x$ changes by $c_B$ times a map integral between the lattices at every selected or bad place, $\phi_T$ is unchanged by the word-prime residue argument in [the ordinary kernel proof](the-ordinary-point-kernel-transforms-with-the-level-characters.md). At every $P\in\mathcal B$ the coordinate matrix changes by a multiple of $q_P^B$ times an integral matrix. Hypothesis `psiInvX` makes this a period of $\Psi_P$ with $y_P$ fixed. The entire weight therefore has the required global congruence period.

### Two local moves

Use the frame comparisons of the ordinary proof, with source matrix $\kappa_P$ of level character $a_P$ and target matrix $\kappa'_P$ of character $a'_P$. The coordinate matrix of $\gamma'x\gamma^{-1}$ in the new frames is $\kappa'_P X\kappa_P^{-1}$. Choose a member of $Y$ whose image under $\gamma'$ is the chosen representative of $\gamma'Y$. If its old coordinate is $v_P$, its new coordinate is $\kappa'_Pv_P$. The equality $\Psi_P(X,v_P)=\Psi_P(X,y_P)$ follows from `psiInv`.

For any allowed integral source block $s$ of level character $a$, choose the first-parabolic lift $r$ into the large space. Since there is exactly one extra source coordinate and the first parabolic fixes its basis vector, $r=\operatorname{diag}(s,1)$. Then $J(Xs,v)=J(X,v)r$, and the additive argument in the level character is zero. After conjugating by the source chart matrix, the lift acts on the local test function by its prescribed large-matrix level law. Its determinant is $\det s$, a local unit. The fixed normalizing factors do not change. Thus
$$
\Psi_P(Xs,v)s_{S,P}(\det s)=a\,\Psi_P(X,v).
$$

For any allowed target block $s'$ of character $a'$, the lift is $s'$ itself, since there are no extra coordinates. The chart matrix at this layer is the identity. The identity $J(s'X,s'v)=s'J(X,v)$ makes this the target large-matrix level law. It gives
$$
\Psi_P(s'X,s'v)s_{S,P}(\det s')=a'\,\Psi_P(X,v).
$$
At this layer the adjacent superdiagonal argument is an empty sum, just as on the source with one extra coordinate. This accounts for the level characters in both equations without a summation over any remaining parameters.

Apply the source law with $s=\kappa_P^{-1}$ and the target law with $s'=\kappa'_P$. The determinant term at the target equals $s_{T,P}(\det(\kappa'_P)^{-1})$ since the two determinant characters are reciprocal on units. The resulting scalar is $a'_Pa_P^{-1}$. Also $\phi_T$ is invariant under the two global unitary moves. Multiply the local equalities and use [the finite kernel-sum covariance proof](changing-frames-in-the-finite-kernel-sum.md), with `ChTh.Ok` giving the theta distribution laws. The product of level characters supplies precisely the missing factors in the two value representations. The tied normalizations identify the resulting first coupled kernel with the actual $k_i$, proving the claim.

### Lean correspondence

- [`joinCol` and `PsiAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L981) define the added column and local coefficient. [`ChIdx.Ok`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L993) supplies both local periods and the target chart normalization.
- [`ybSet` and `XiCpl1`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1128) give admissible cosets and the product weight. [`ybSet_gmap`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L1190) transports the cosets and [`coset_sub`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SmulCompSmul.lean#L210) controls the difference of representatives.
- [`joinCol_target` and `joinCol_source`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FirstCoupledKernelEquivariantCosets.lean#L18) give the matrix identities. [`psiAt_source` and `psiAt_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FirstCoupledKernelEquivariantCosets.lean#L97) turn them into the local scalar laws.
- [`xiCpl1_invariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FirstCoupledKernelEquivariantCosets.lean#L147) and [`xiCpl1_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FirstCoupledKernelEquivariantCosets.lean#L189) assemble these laws, and [`firstCoupledKernel_equivariant_cosets` and `kAt_equiv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/FirstCoupledKernelEquivariantCosets.lean#L235) prove covariance of the actual kernel.

Status. Source-based reconstruction draft. The two local large-matrix test-function laws used here are the same inputs as for the ordinary kernel. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
