# The compact dual normalizes the real unitary quotient

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $P,Q\ge0$, $n=P+Q\ge1$, and $J=\operatorname{diag}(I_P,-I_Q)$. On $V=\mathbb C^n$ take the Hermitian norm $Q_J(z)=z^*Jz$, with real trace pairing $2\operatorname{Re}(z^*Jw)$. Use the additive character $e^{-2\pi i t}$, self-dual Haar measure $dX$ on $V$, and Lebesgue measure $dt$ on the norm line. Let $\omega_t$ be the fibre measures obtained from $dX$ by disintegration along $Q_J$ at nonzero $t$, with continuity for compactly supported tests there.

Fix $\beta\in\{1,-1\}$ represented by $J$ and $x_0\in V$ with $Q_J(x_0)=\beta$. Write $G=U(P,Q)$, $H=\operatorname{Stab}_G(x_0)$, and identify $H$ with the unitary group of $x_0^\perp$, of rank $n-1$. The source's `CDHaar` normalization has the following two clauses. The compact group $U(j,0)$ has Haar probability measure in every rank $j$. The density at the identity for $U(P,Q)$, measured in exponential coordinates against the Lie algebra measure $\lambda_J$ described below, equals the density of its compact dual $U(n,0)$. Use the same rule for $H$.

Then the quotient measure of $G$ by $H$, with these Haar measures, corresponds under $Hg\mapsto g^{-1}x_0$ to
$$
\frac{\omega_\beta}{c_n},
\qquad c_n=\frac{(2\pi)^n}{(n-1)!}.
\tag{1}
$$
This is the real factor used in the [local density comparison](counting-nonzero-residue-norms-gives-the-local-fibre-density.md) at the infinite places.

### The additive measures and the quadric

In the standard real coordinates of $V$, the trace pairing matrix has all diagonal entries of absolute value $2$. Fourier inversion for the usual dot product shows that a pairing with matrix $B$ has self-dual measure $|\det B|^{1/2}$ times ordinary Lebesgue measure. Indeed substituting $By$ in the second Fourier transform gives the Jacobian $|\det B|^{-1}$ and two factors of the chosen measure scalar. Here this scalar is $2^n$. On the real norm line the scalar is $1$. Thus $dX=2^n d_{\mathbb R^{2n}}X$.

A unitary matrix preserves both $Q_J$ and $dX$. It therefore preserves the fibre measures, first almost everywhere by disintegration and then at every nonzero level by continuity. Near every nonzero level the norm map is a smooth submersion, and the measures are given by the Jacobian change of variables in local coordinates. For example, choose a Hermitian frame with $x_0=e_0$, write $J=\operatorname{diag}(\beta,J')$, and let the first coordinate be $s+it$ and the others $z$. Near $e_0$, $s>0$ and
$$
Q_J(s+it,z)=\beta(s^2+t^2)+z^*J'z.
$$
Changing from $s$ to the norm value gives fibre density $2^{n-1}s^{-1}\,dt\,dz$. In particular the density at $e_0$ in the $(t,z)$ coordinates is $2^{n-1}$, independent of the signs. A global unitary frame for any two vectors of norm $\beta$ is obtained by choosing matching orthonormal bases on the complements. Thus $G$ acts transitively on this quadric. The map $Hg\mapsto g^{-1}x_0$ is its homogeneous-space parametrization.

### The tangent densities in the two signatures

For the Lie algebra of $G$, $\lambda_J$ is the additive Lebesgue measure characterized by
$$
(X,Y)\longmapsto X+iY,\qquad
(\lambda_J\otimes\lambda_J)\longmapsto
\text{ordinary Lebesgue measure on }\operatorname{Mat}_n(\mathbb C).
\tag{2}
$$
The real span of the Lie algebra and its $i$-multiple is a direct sum giving all complex matrices, since a matrix splits uniquely into a skew-adjoint and a self-adjoint part for the Hermitian form. Hence (2) specifies a positive scalar on the Lie algebra.

In the coordinates with $x_0=e_0$, every element of the Lie algebra is uniquely
$$
X=\begin{pmatrix}it&-\beta z^*J'\\ z&X'\end{pmatrix},
\qquad X'\in\mathfrak u(J'),\quad t\in\mathbb R,\ z\in\mathbb C^{n-1}.
$$
The lower-right Lie algebra is that of $H$. The measure in these coordinates is
$$
\lambda_J=2^{n-1}\,dt\,dz\,\lambda_{J'} .
\tag{3}
$$
To verify it, compute the real Jacobian of (2). The two real diagonal parameters give one complex entry with absolute Jacobian $1$. In each off-diagonal pair the two complex input variables $z_j,w_j$ give $z_j+iw_j$ and, up to conjugation and a sign, $z_j-iw_j$. The complex determinant of this last linear change has absolute value $2$, so its absolute real Jacobian is $4$. The lower-right block already has the normalization (2) by $\lambda_{J'}$. The full off-diagonal factor $4^{n-1}$ is precisely the square of the scalar in (3).

Let $a_G,a_H$ be the two Haar densities measured in these exponential coordinates at the identities. In a local product of a section of the quadric with $H$, the product of $\omega_\beta$ and $\lambda_{J'}$ has density $\lambda_J$ at the identity, by (3) and the preceding quadric calculation. The differential of the orbit map there is $X\mapsto -Xx_0$, so the coordinate sign has absolute Jacobian one. Both the quotient measure and $\omega_\beta$ are invariant measures for this transitive action. By uniqueness of the invariant quotient measure up to a scalar, the identity density determines the quotient measure to be $(a_G/a_H)\omega_\beta$. This reasoning is the infinitesimal version of comparing the measures of small exponential neighborhoods in the source.

### Evaluate the scalar on the compact dual

The rule for `CDHaar` makes $a_G/a_H$ the same as the ratio for $U(n,0)$ and $U(n-1,0)$. Both compact groups have total mass one. Their quotient consequently has total mass one by integration along the subgroup. The positive norm fibre is the sphere $Q_J(z)=1$. Its mass in the fibre measure can be read from the ball: for $u>0$,
$$
2^n\operatorname{vol}_{\mathbb R^{2n}}\{|z|^2\le u\}
=2^n\frac{\pi^n}{n!}u^n .
$$
The usual unit-ball factor follows by evaluating the Gaussian integral in Cartesian and polar coordinates. Differentiating the displayed mass at $u=1$, or applying polar coordinates to the disintegration, gives $c_n=(2\pi)^n/(n-1)!$. The compact scalar $a_G/a_H$ must therefore be $c_n^{-1}$, proving (1) for both signs. For several real places, the product Haar quotient formula gives $c_n^{-1}$ from each place.

### Lean correspondence

- [`IsOmegaLeb`, `OmegaDensity` and `CDHaar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalRingCardinality/DataCD.lean#L42) specify (2) and the compact-dual density condition. [`selfDual_dx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RealPlaceMeasures.lean#L88) computes the additive scalar.
- [`formula_base`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsCompactMatrixEntryAbsSumSublevel.lean#L257) computes the real quotient constant by matching the small-neighborhood densities. [`sphereMass`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/PositiveDefiniteUnitSphereMassProof.lean#L93) evaluates the sphere mass. [`compactDualQuotient`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/IsCompactMatrixEntryAbsSumSublevel.lean#L330) treats either norm sign and general frames.
- [`quot_integral_prod`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/UnitaryQuotientIntegralProdOverPlaces.lean#L69) uses the product of the quotients, and [`arch`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/VolumeRatioOfUnfolding.lean#L58) applies it to a product of positive compactly supported tests. In this exposition the tangent-density comparison is expressed by the Jacobians in (2) and (3).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
