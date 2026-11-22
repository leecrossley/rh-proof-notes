# The terminal kernel carries the source coset along

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix the sharp-chain field, prime, character, selection and twist-avoidance hypotheses of [the ordinary kernel proof](the-ordinary-point-kernel-transforms-with-the-level-characters.md), together with `ChIdx.Ok` and `ChTh.Ok`. Take the terminal step $i=m-1$. Write $n=N_{m-1}$ and $b=N_m$ for the adjacent ranks. The source point is $(p,Y)$, formed by a framed decorated lattice $p$ with an admissible coset $Y$ as in [the penultimate calculation](the-penultimate-kernel-carries-the-target-coset-along.md). The target point $p'$ is a terminal framed decorated lattice. Its type-place level groups are obtained from the sharp row level by extension by the identity on the last coordinate. At each twist place the target level group is the product of this block extension of the twist row level and the principal congruence subgroup at a depth $C\ge\max(4m+1,2m+2M)$, where $M$ is the coset depth. The resulting level characters are induced by reduction of the upper block.

For all source and target frame moves $g,g'$ with rational unitary components $\gamma,\gamma'$ respectively, the actual terminal coefficient kernel satisfies
$$
k_{m-1}\bigl((gp,\gamma Y),g'p'\bigr)
=\rho_m(g')\,k_{m-1}\bigl((p,Y),p'\bigr)\,\rho_{m-1}(g^{-1}).
$$

### The two factors of the weight

In a bad-place frame, split a matrix of the Hom argument into its first $b-1$ rows $U$ and its last row $\ell$. The weight at $P$ is
$$
\operatorname{locTop}_P((U,\ell),y_P)
=\Phi_{{\rm top},P}(U)\mathcal F_P(\ell,y_P),
$$
where $y_P$ is the coordinate of a representative of $Y$ in the **source** frame. There are no extra directions adjoining the source of this step. The head weight $\Phi_{{\rm top},P}$ tests integrality of the entries of $U$ and of specified lower-block entries divided by $q_P$. It then uses reductions of the original entries in the flag tests, the additive character of adjacent entries, and the determinant characters of the designated blocks. At a twist place it uses the determinant character of the leading block and the integrality tests. In particular the head weight is supported on integral $U$ and is unchanged by addition of $q_P$ times an integral matrix. This follows directly from its definition, since such a perturbation preserves both integrality tests and leaves all the reductions unchanged. The source rank is $r+(m-1)t$ in the type-place definition, exactly the number of columns tested for integrality.

The last row has the independent factor $\mathcal F_P$ of [the terminal Fourier calculation](why-the-terminal-fourier-factor-descends-to-a-coset.md). At a type place the support requires $\ell$ to be integral and $q_Py_P$ is integral. At a twist place the support requires $q_P^M\ell$ to be integral and $q_P^M y_P$ is integral. The local depth condition $D_P\ge 2M$ holds there. The global scalar is the product over bad places of these local weights, times the word-prime residue indicator $\phi_T$.

For periodicity, add $c_B$ times a map integral between the local lattices. The argument of every local weight changes by a matrix in $q_P^B\mathcal O_P$, entry by entry. As $B\ge M\ge1$, the head weight stays fixed and the last-row perturbation law fixes $\mathcal F_P$. The word-prime indicator is unchanged by the residue argument of the ordinary step. This proves the complete scalar period required for the finite kernel sum.

### The source action

The passage between frames gives $\kappa_P,\kappa'_P$ and their two level characters $a_P,a'_P$ as in the ordinary step. The moved coordinate matrix is $\kappa'_P X_P\kappa_P^{-1}$. The coset is now moved by $\gamma$, so choose a representative of $Y$ that maps to the chosen representative of $\gamma Y$. If its old coordinate is $v_P$, its new coordinate is $\kappa_Pv_P$. The difference $v_P-y_P$ is in the integral source coordinate lattice at a type place or in its $q_P^M$ multiple at a twist place. Consequently [the terminal Fourier calculation](why-the-terminal-fourier-factor-descends-to-a-coset.md) gives
$$
\mathcal F_P(\ell\kappa_P^{-1},\kappa_Pv_P)=\mathcal F_P(\ell,y_P).
$$

The top head source law says that for any allowed source-level matrix $s$ of character $a_s$,
$$
\Phi_{{\rm top},P}(Us)\,s_{S,P}(\det s)=a_s\,\Phi_{{\rm top},P}(U).
$$
To apply it, lift $s$ by the same level projection as in the ordinary proof. The last source chart has $h=1$ and no extra direction, so the lift is $s$ and there is no character shift from the extra flag. Thus the local large-matrix source law for the head has exactly $a_s$ as its row character. With $s=\kappa_P^{-1}$ the source correction contributes $a_P^{-1}$.

### The terminal target action

The level groups allow us to reduce the target move to $\operatorname{diag}(J,1)$ for an integral $(b-1)$-dimensional matrix $J$ of the row level. At a type place choose a lift $J$ of the upper block of $\kappa'_P$ modulo $q_P$. The remaining factor $\epsilon=\kappa'_P\operatorname{diag}(J,1)^{-1}$ reduces to the identity. If a matrix argument is integral, multiplying on the left by $\epsilon$ changes each entry by an element of $q_P\mathcal O_P$, preserving the head weight and the last-row Fourier factor. If the argument is outside the integral support, both it and its image under $\epsilon$ are outside it because $\epsilon$ and $\epsilon^{-1}$ are integral. In this case both weights are zero.

At a twist place write $\kappa'_P=\operatorname{diag}(J,1)\epsilon$ with $\epsilon\equiv1\bmod q_P^C$. The support of the local weight requires all entries to lie in $q_P^{-M}\mathcal O_P$ and the head to be integral. Define the support test module to consist of all matrices obeying these two integrality bounds. On this module the change introduced by $\epsilon$ has entries in $q_P^{C-M}\mathcal O_P$. Because $C-M\ge M+1$, the image remains in the module and the same argument applies to $\epsilon^{-1}$. This proves equivalence of the support test in both directions. Within it the head weight is unchanged modulo $q_P$ and the last-row factor is unchanged by the Fourier perturbation law. The target level character and determinant character both reduce to those of $J$, since $\epsilon$ reduces to the identity. At a type place this holds by the reduction construction of $J$.

The action of $\operatorname{diag}(J,1)$ on a matrix replaces $U$ by $JU$ and fixes $\ell$. The sharp type row level and the twist row level obey
$$
\Phi_{{\rm top},P}(JU)s_{S,P}(\det J)=a'_P\Phi_{{\rm top},P}(U).
$$
It follows that target multiplication by $\kappa'_P$ gives the same identity for $\operatorname{locTop}_P$ with determinant $\det\kappa'_P$. Apply it after the source action, with the representative in the moved source coset. Reciprocation of the determinant characters on units identifies the complete determinant correction with $s_{S,P}(\det\kappa_P^{-1})s_{T,P}(\det(\kappa'_P)^{-1})$. The product of the right hand side characters is $a'_Pa_P^{-1}$.

The word-prime indicator stays fixed under the rational unitary moves, just as for the ordinary step. Taking the product restores the scalar identity of [the finite kernel-sum proof](changing-frames-in-the-finite-kernel-sum.md). Its other inputs are the scalar period proved above and the terminal distribution laws from `ChTh.Ok`. Finally the actual terminal kernel uses this top weight with the same theta distribution by the tied normalizations. This identifies both representations in the formula with the frame groups of the actual two layers and proves covariance.

### Lean correspondence

- [`locTop` and `XiTop`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/IntegralGLSuccEmbeddingMemParahoricTimesPrincipa.lean#L391) give the two factors. [`xiTop_invariant`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/XiTopInvariant.lean#L17) proves the period.
- [`phiTop_level`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopSource.lean#L64) and [`locTop_source`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SmulCompSmul.lean#L239) give the source action.
- [`TopDepth`, `topLevG` and `topLevQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/IntegralGLSuccEmbeddingMemParahoricTimesPrincipa.lean#L155) specify the target levels. [`locTop_inv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/IntegralGLSuccEmbeddingMemParahoricTimesPrincipa.lean#L511) and [`locTop_invQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/LevelGroupNeTopNeBot.lean#L155) remove the two principal-congruence corrections. [`phiTop_target_sym`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopTargetSym.lean#L192) and [`phiTop_target_twist`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiTopTargetTwist.lean#L78) give the two block actions.
- [`locTop_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SmulCompSmul.lean#L160) and [`xiTop_law`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/SmulCompSmul.lean#L254) assemble the local transformations. [`kerOf_xiTop`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/KAtTopEquiv.lean#L18) gives the resulting covariance, and [`kAt_top_equiv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/KAtTopEquiv.lean#L65) identifies it with the actual terminal law.

Status. Source-based reconstruction draft. The head-weight laws under multiplication by the level groups are specified inputs to this argument. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
