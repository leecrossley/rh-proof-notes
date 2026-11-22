# The fourfold frame Gram matrix modulo the CM root

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $d\equiv3\bmod4$ be positive and let $\Lambda_0\subset\mathbb C$ be a lattice of CM multiplier ring $\mathbb Z[\omega]$, where $\omega=(1+\sqrt{-d})/2$. Write $\mathscr A_0$ for its area. Let $H$ be a Hermitian form, linear in its first argument, on $\mathbb C^n$ with periodic subgroup $\Lambda$. Form four independent copies of both. Assume $g$ is a complex-linear isometry from the four copies of $H$ to the form on $\mathbb C^{4n}$ with matrix $\mathscr A_0^{-1}I$. Assume the finite quotient of $g(\Lambda^{\oplus4})$ by its intersection with $\Lambda_0^{\oplus4n}$ has order $N$ prime to $p$. Let $\iota:\mathbb C\cong\mathbb C_p$ be a coefficient field isomorphism carrying the specified embedding of the algebraic numbers. Let $\delta_0=\iota(\sqrt{-d})$. Take directions $v_j\in\mathbb C^n$ with $\Lambda_0 v_j\subset\Lambda$. These are the assumptions of the source's Gram transfer applied to a fourfold theta isometry.

For $x=(b,j)$ with copy $b\in\{1,2,3,4\}$, let $Y_x=g(\operatorname{in}_b v_j)$ and define the column $D_x=\iota(Y_x)$ entrywise. Then $D$ has integral entries, and with $\gamma=\iota(g^{-1})$ one has
$$
\gamma D_{b,j}=\operatorname{in}_b\iota(v_j),\qquad
D_{b,j}^{t}D_{b',k}
=\mathbf 1_{b=b'}\,\iota(\mathscr A_0 H(v_j,v_k))+\delta_0 q_{(b,j),(b',k)}
$$
for integral $q_{x,y}$.

**Proof.** For $\omega_0\in\Lambda_0$ the vector $\omega_0Y_x$ lies in $g(\Lambda^{\oplus4})$, so $N\omega_0Y_x\in\Lambda_0^{\oplus4n}$. Each coordinate of $NY_x$ is therefore a multiplier of $\Lambda_0$, and belongs to $\mathbb Z[\omega]$. Its algebraic image under $\iota$ has norm at most one. The denominator $N$ is a unit, proving integrality of $D$. The same reasoning with differences gives
$D_{w,x}-\iota(\overline{Y_{w,x}})\in\delta_0 R$, where $R$ is the valuation ring, because $\omega-\bar\omega=\sqrt{-d}$. Thus in the bilinear product $D_x^tD_y$, replacing the second vector by the image of its complex conjugate gives an error in $\delta_0 R$. The Hermitian product of $Y_x,Y_y$ is the original block Hermitian product by isometry, giving the asserted formula. The identity with $\gamma$ follows by applying $g^{-1}$.

Now take any finite list of new variables $z_k$ and integral matrix $A=(A_{jk})$. Let $M_{ik}=\sum_j\iota(v_{j,i})A_{jk}$. The target coordinates $M$ need not themselves be integral. Define $C=D\,\operatorname{diag}_4(A)$, applying $A$ in each block. It is integral, $\gamma C=\operatorname{diag}_4(M)$, and
$$
C^tC=\operatorname{diag}_4(B)+\delta_0 Q,\qquad
B_{kl}=\sum_{j,j'}A_{jk}\,\iota(\mathscr A_0 H(v_j,v_{j'}))\, A_{j'l}.
$$
Each entry of $Q$ is a finite sum of integral products, so $Q$ is integral. This formula separates the required target Gram computation $B$ from the comparison error $\delta_0 Q$.

**Lean correspondence.** The multiplier-ring and signed root assertions are recorded by [`MulRing` and `IotaOK`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussianEigenFrames/StatementB.lean#L10). The isometry calculation is [`GramTransfer_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussianEigenFrames/GramFrameComposition/MatrixFormDiagBlocksBlockEmbed.lean#L146). The composition with the coefficient matrix is [`FrameCompose_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/GaussianEigenFrames/GramFrameComposition/JetsLin.lean#L96). The curve and one-place theta applications use both in [`shape_paired_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/FourthPowerTheta.lean#L63).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
