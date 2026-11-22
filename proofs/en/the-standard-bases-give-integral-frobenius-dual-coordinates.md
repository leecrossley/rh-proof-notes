# The standard bases give integral Frobenius-dual coordinates

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

## Setting

We spell out the linear algebra in `hyp_of_stdBases`. Use the host fields $K\subset E$ of the Lean datum $D$, with $K$ imaginary quadratic, $E$ a CM field Galois over $\mathbb Q$, and conjugation $u\mapsto \overline u$ on $E$. The coordinate embeddings of $E$ into $\mathbb C$ are all those over the fixed embedding of $K$, indexed by $\mathcal P=\{0,1\}\times\mathrm{HH}(D)$ via the bijection `tauPl`. Fix a prime $p\ge5$ in `IsResidueClassZero` or `IsSg` and an embedding $\overline{\mathbb Q}\to\mathbb C_p$. The local setting here has uniform even, positive orbit length $d=d(D,p)$, with the extra condition $h_P(D,p)\ne0$ in the `IsResidueClassZero` case. Let $z^+$ be the next place on an orbit, and $\rho_z:E\to K_0\subset\mathbb C_p$ be the local coordinate embedding. The restriction to $K_0$ and the equation
$$
\sigma(\rho_z(x))=\rho_{z^+}(\overline x)
\tag{1}
$$
are verified below. [Hypotheses for the change to a hyperbolic frame](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/StandardBasesHyperbolicPairOrthonormal.lean#L28)

For nonnegative even $N,N'$, let $L\subset E^N,\ L'\subset E^{N'}$ be finitely generated full $\mathcal O_E$-lattices self-dual for the form $\sum_a\overline{x_a}y_a$. This is the condition `admitted`. Let $P_z,P'_z$ be the respective standard basis matrices. Their columns give bases after localization at the prime of $E$ induced by $\rho_z$. Precisely, the columns belong to the localized lattice, the matrices have nonzero determinant, and every element of the lattice has coordinates integral in that localization. In the inert classes under consideration they also satisfy
$$
\overline{P_{z^+}}^{\,t}P_z=1,\qquad
\overline{P'_{z^+}}^{\,t}P'_z=1.
\tag{2}
$$
These are the relevant clauses of `StdBases`. Its other clause at the discriminant prime does not apply here. [Local basis in terms of unit denominators](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/IsDiscriminantTwelfthRootOfIdealLattice.lean#L421) · [Standard bases and their compatibility along Frobenius](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GaloisGeometry/StdBases.lean#L11)

Write $Y$ for `YYl`, the $\mathcal O_E$-span of $aB$ where $a$ is in the inverse half-different $\mathfrak b^{-1}$ of the host and $B\in\operatorname{Hom}_E(E^N,E^{N'})$ takes $L$ into $L'$. Let $b_i\in\operatorname{Mat}_{N'\times N}(E)$ be the matrices of a `LocBasis` of $Y$ at $p$, with
$$
\operatorname{Tr}_{E/K}\sum_{b,a}(b_i)_{ba}\,\overline{(b_j)_{ba}}=\delta_{ij}.
\tag{3}
$$
The basis condition means that the $b_i$ are linearly independent over $K$, that each belongs to $Y$ after multiplication by some integer prime to $p$, and that each element of $Y$, after multiplication by such an integer, can be expressed with $\mathcal O_K$-coefficients in the $b_i$. Equation (3) is `Orthonormal`. [The Hom lattice and trace pairing](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/IsDiscriminantTwelfthRootOfIdealLattice.lean#L32) · [Precise local basis and orthonormality hypotheses](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/GlobalSchurBounds/GeneralLinearActions/IsDiscriminantTwelfthRootOfIdealLattice.lean#L215)

## The arithmetic meaning of the place step

For these two prime classes $p$ is outside the exceptional small primes and the two host primes $q_D,d_D$. In particular it misses the host conductor, hence is unramified in $E$, and the half-different has valuation zero at every prime over $p$. Thus the image of $E$ under each embedding is contained in the corresponding finite unramified extension inside $K_0$. The Frobenius $\sigma$ of $K_0$ acts there as the arithmetic Frobenius $\mathrm{Fr}_{\mathfrak p_z}$ at the prime $\mathfrak p_z$ determined by $\rho_z$: it gives the $p$-power congruence on the residue field, and in an unramified extension this characterizes the automorphism. The next-place rule in the Lean labeling is arithmetic Frobenius **followed by conjugation** on the argument of $\rho_z$:
$$
\rho_{z^+}(x)=\rho_z(\mathrm{Fr}_{\mathfrak p_z}(\overline x)).
$$
It uses the host group label of $\mathrm{Fr}_{\mathfrak p_z}$ and the conjugation element. Applying this to $\overline x$ gives (1). The second conjugation is essential to the switch between the primal and dual coordinates. [The Frobenius label and next-place rule](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PrimeOfLiesOver.lean#L72) · [Unramified embeddings and their Frobenius action](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsKurFrobTauEmbPosPl.lean#L76)

## Trace-dual matrices and their changed coordinates

Let $B_z(i)=\rho_z(b_i)$ and $B_z^c(i)=\rho_z(\bar b_i)$, entry by entry. For formulas below use $P_z,P'_z$ under $\rho_z$. The raw matrix-to-standard change and its inverse are
$$
C_z(M)=P'_z M P_z^{-1},\qquad C_z^{-1}(M)=(P'_z)^{-1}M P_z.
$$
Define
$$
h_z(i)=(P'_z)^{-1}B_z(i) P_z,\qquad
g_z(i)=(P'_z)^t B_z^c(i)(P_z^{-1})^t .
\tag{4}
$$
The latter is $C_z^t(B_z^c(i))$, where transpose on the operator means transpose for the entrywise bilinear dot product of matrices. The entries in position $(b,a)$ are `hK` and `gK` (with the argument order $a,b$). [Formulas for gK and hK](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsRingHomRhoK.lean#L30)

The $b_i$ form a $K$-basis of the full matrix space. In fact $L,L'$ are full finitely generated lattices, so multiplying the standard matrix units by a common nonzero integer takes $L$ into $L'$. This follows by clearing the finitely many denominators of the coordinates of their images on generators of $L$ in a full sublattice of $L'$. Since $1\in\mathfrak b^{-1}$ for an integral ideal $\mathfrak b$, the lattice $Y$ spans the matrix space over $E$, hence also over $K$, as it is an $\mathcal O_E$-module. The local basis property makes every member of $Y$ lie in the $K$-span of the $b_i$, proving the assertion. Thus the arrays $B,B^c$, with rows indexed by the place and matrix entry and columns indexed by $i$, are square, of size $[E:K]NN'$. Summing over the embeddings of $E$ over $K$ is the $E/K$ trace. Applying this to (3) gives $(B^c)^tB=1$, so also $B(B^c)^t=1$. [Dimension of the full lattice basis](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/RepTrace.lean#L70) · [Inverting the trace Gram matrix](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/InertKernelTheory/InertCoprimeLemmas/RepFrame.lean#L389)

Write $C=\bigoplus_z C_z$ as an operator on all raw entries. By (4) the arrays with columns $h(i),g(i)$ are $C^{-1}B,C^t B^c$. Their product $h g^t=C^{-1}B(B^c)^t C=1$ gives
$$
\sum_i h_{w,j,i} g_{z,k,i}=\delta_{wz}\delta_{jk}
$$
for matrix-entry indices $j,k$. The product $B g^t=C$ also follows and expresses the raw coefficient $C_z$ as the combination of columns of $B$ with coordinate coefficients $g_{z,k,i}$. This will identify the substituted power series. [Duality after the coordinate change](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/OrthonormalLocalBasisCoordinatesDual.lean#L26) · [The standard change of basis recovered from gK](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/LambdaTauOrthonormalBasisSumCoordinates.lean#L21)

## Integrality and the Frobenius switch

Each $b_i$, after multiplication by an integer prime to $p$, lies in $Y$. That scalar is a unit under $\rho_z$. Also $\mathfrak b^{-1}$ has integral image at this prime: choose $u\in\mathfrak b$ outside the prime, then $ua\in\mathcal O_E$ for $a\in\mathfrak b^{-1}$, and $\rho_z(u)$ is a unit. Thus each $b_i$ acts on the localized $L$ with image in the localized $L'$, by expressing its multiple as a sum of generators of $Y$ and then dividing by the unit. This means exactly that $h_z(i)$ is an integral matrix in the two local bases. [Local integrality of the inverse half-different](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormPadicEmbeddingLeOneOfMemInverseHalfDifferent.lean#L64) · [Integral h coordinates](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/NormLocalBasisStandardCoordLeOneInert.lean#L16)

Apply $\sigma$ to (4). Equation (1) sends $B_z^c(i)$ to $B_{z^+}(i)$. By (2), conjugating the equation and applying $\rho_{z^+}$ gives $\sigma(P_z)=P_{z^+}^{-t}$ and $\sigma(P'_z)=(P'_{z^+})^{-t}$. Consequently
$$
\sigma(g_z(i))=(P'_{z^+})^{-1}B_{z^+}(i)P_{z^+}=h_{z^+}(i),
\qquad \sigma(h_z(i))=g_{z^+}(i).
$$
Because $\sigma$ is an isometry, the already established integrality of $h$ gives the integrality of $g$. These are exactly the hypotheses of the [hyperbolic frame calculation](trace-dual-coordinates-give-the-hyperbolic-frame.md). [Frobenius changes an inverse transpose into the next primal basis](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/FrobeniusLiftMovesLetterCoordinates.lean#L23)

For any scalar $c$ and any raw series $G$, its orthonormal-series substitution is $G(c B W)$ in orthonormal coordinates $W_i$. Its standard-series substitution is $G(CZ)$ in the standard variables $Z_{z,a,b}$. When the hyperbolic linear map is substituted for $W$ it equals $g^t Z$ by the hyperbolic frame calculation. Then $G(c B g^t Z)=G(c C Z)$ by the array identity, which is the standard series evaluated at $cZ$. Thus the substitutions agree for every $c,G$, which is the desired conclusion `standardSeries_scaled_eq_orthonormalSeries_hyperbolicSubst`. [Equality of the two substituted series](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/StandardBasesHyperbolicPairOrthonormalStatement.lean#L12)

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
