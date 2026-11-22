# Unfolding a unit-norm orbit leaves the complement volume

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E/F$ be the quadratic CM extension of a host, unramified at finite places. Let $W$ be a nondegenerate Hermitian $E$-space of signature $(P,Q)$ at every real place, with a self-dual $\mathcal O_E$-lattice $L$. Take $x\in L$ of norm $\beta\in\{1,-1\}$, and put $W'=x^\perp$ and $L'=L\cap W'$. Write $G=U(W)$ and $H=U(W')$, embedded by fixing $x$. The signatures of $W'$ are $(P-1,Q)$ if $\beta=1$, and $(P,Q-1)$ if $\beta=-1$. Normalize finite Haar measures by giving the stabilizers $K_f$ of $\widehat L$ and $K'_f$ of $\widehat{L'}$ measure one. At infinity use the given compact-dual Haar measures on $G_\infty$ and $H_\infty$. Let $\nu_\infty$ be the compatible quotient measure on $H_\infty\backslash G_\infty$, that is, the measure for which integrating along the left $H_\infty$-fibres and then over the quotient gives Haar integration on $G_\infty$. Suppose the two rational quotient volumes $V_G,V_H$ are finite and positive.

**Claim.** For any nonnegative continuous compactly supported function $\Phi_\infty$ on $W_\infty$, let $\Phi(y)=\mathbf 1_{\widehat L}(y_f)\Phi_\infty(y_\infty)$. Then
$$
\frac{1}{V_G}\int_{G(F)\backslash G(\mathbb A_F)}
\sum_{\substack{y\in W\\ h(y,y)=\beta}}\Phi(g^{-1}y)\,dg
=\frac{V_H}{V_G}\int_{H_\infty\backslash G_\infty}
\Phi_\infty(g_\infty^{-1}x)\,d\nu_\infty(g_\infty).
$$

The rational norm-$\beta$ vectors form a single $G(F)$-orbit. Indeed, the isometry $Ex\to Ey$ taking $x$ to $y$ extends to the two Hermitian spaces by Witt extension. The subgroup fixing $x$ is $H(F)$, since a map fixing $x$ preserves $x^\perp$, and any isometry of $x^\perp$ extends by the identity on $Ex$. Representatives $\gamma$ of $H(F)\backslash G(F)$ give each $y=\gamma^{-1}x$ exactly once. With a fundamental set for $G(F)$, the integrals indexed by $\gamma$ run over its translates $\gamma\mathcal F$, a fundamental set for $H(F)$. All summands are nonnegative. Tonelli therefore gives the integral over $H(F)\backslash G(\mathbb A_F)$ of $\Phi(g^{-1}x)$.

We need the support of this integrand at finite places. At each such place $v$, the unit length gives an integral projection $z\mapsto h(x,z)x/\beta$ onto the line (with the pairing taken linear in $z$). Consequently $L_v=\mathcal O_{E,v}x\perp L'_v$, and the complement is self-dual. The same holds for any $y_v\in L_v$ of length $\beta$. By the [local integral frame classification](a-self-dual-lattice-has-an-integral-frame-at-each-finite-place.md), the two complements are isometric as lattices, including in the split case. Combining that isometry with $x\mapsto y_v$ supplies an element of $K_v$. Thus $g_v^{-1}x\in L_v$ exactly when $g_v\in H(F_v)K_v$. The restricted product gives $g_f\in H(\mathbb A_{F,f})K_f$: at the almost all places with $g_v\in K_v$, use the trivial $H$-component. The stabilizer of $x$ in $K_f$ is just $K'_f$ under the orthogonal splitting.

The integrand is constant on left $H(\mathbb A_F)$-cosets. Applying the quotient Haar formula first integrates over $H(F)\backslash H(\mathbb A_F)$, producing the factor $V_H$. At finite places the remaining quotient support is the image of $K_f$. Its measure is $\mu_G(K_f)/\mu_H(K'_f)=1$: in the quotient integration formula the inner integral of $\mathbf 1_{K_f}$ is $\mu_H(K'_f)$ on this image and zero off it. The remaining archimedean integral is the one stated.

### Source and scope

The Lean proof uses rational points in a one-row coordinate tuple, and obtains the rational orbit by extending a line isometry. It constructs the complement embedding at finite and infinite places simultaneously. In signature coordinates the real stabilizer is a conjugate of $U(P-1,Q)$ or $U(P,Q-1)$. The choice of a measurable real orbit map and the finite level support are built into the unfolding-kernel lemma. The proof above uses the same two quotient integrations and the same finite normalization. [§rational_orbit§](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnitaryUnfoldingVolumeVectorStabilizer.lean#L113) · [§unfoldAt§](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnitaryUnfoldingVolumeVectorStabilizer.lean#L150) · [§exists_unfoldingKernel_levelSubgroup_bruhat§](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsUnfoldingKernelLevelSubgroupBruhat.lean#L8).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
