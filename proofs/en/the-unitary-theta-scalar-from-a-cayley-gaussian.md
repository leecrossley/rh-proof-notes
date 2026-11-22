# The unitary theta scalar from a Cayley Gaussian

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $V$ be a finite-dimensional complex vector space with positive definite Hermitian form $H$, linear in the first variable, and $E=\operatorname{Im}H$. Let $\Lambda$ be a full self-dual lattice for $E$. Let $\delta$ be unitary with no nonzero fixed vector, and suppose $\delta\Lambda$ and $\Lambda$ are commensurable. Let $\alpha$ be a common $\{\pm1\}$-valued semicharacter as in [the three-lattice comparison](three-theta-averages-differ-by-an-eighth-root.md), now on $\Lambda,\delta\Lambda$, with $\alpha(\delta x)=\alpha(x)$ for $x\in\Lambda$. Assume the theta space for $\Lambda,\alpha$ is one-dimensional. For each theta function $f$ in it,
$$
f(\delta^{-1}z)=c\,I_{\Lambda,\delta\Lambda} f(z),\qquad c^8=(\det_{\mathbb C}\delta)^4
$$
for a common scalar $c$. This is `UnitaryConstant` and its eighth-power consequence.

**The scalar and a test kernel.** Pullback by $\delta^{-1}$ intertwines the theta translations, by unitarity and sign compatibility, so it takes the theta space for $\Lambda$ to that for $\delta\Lambda$. The normalized lattice average $I_{\Lambda,\delta\Lambda}$ is invertible between these spaces, with inverse the reverse average, by the pairwise argument in the three-lattice comparison. Hence a common nonzero scalar $c$ exists by the line hypothesis. To determine it, let
$$
P(z,w)=\sum_{x\in\Lambda}\alpha(x)U_x\!\left(v\mapsto e^{\pi H(v,w)}\right)(z),\qquad W(z)=e^{-\pi H(z,z)} .
$$
The sum converges uniformly on compact subsets in $z,w$: the magnitude of the $x$-term is bounded there by a constant times $e^{-C\|x\|^2+D\|x\|}$ with $C>0$, using positive definiteness. The series of these bounds converges, for example by comparison in integer coordinates of a lattice basis. The sum is entire in $z$. Reindexing by a lattice translation using the cocycle shows $P(\cdot,w)$ is a theta function. Thus the common scalar equality applies to it at every $w$.

Put $\Lambda'=\Lambda\cap\delta\Lambda$, $n=[\delta\Lambda:\Lambda']$, and take a bounded fundamental region $D'$ for $\Lambda'$. Choose Lebesgue measure from an $H$-orthonormal complex basis. For this measure $\operatorname{vol}(V/\Lambda)=1$: the alternating Gram matrix in a lattice basis has determinant $1$ by self-duality, and in real coordinates of the orthonormal complex basis the determinant of $E$ is $1$. The change of basis therefore has absolute determinant $1$. The same holds for $\delta\Lambda$, and $\operatorname{vol}D'=n$ since both indices are equal.

Compute the integral of $P(\delta^{-1}z,z)W(z)$ over $D'$ by first using the common scalar identity. In the average, for a representative $y\in\delta\Lambda$, the summand is $\alpha(y)U_y(P(\cdot,z))(z)W(z)$. By the translation product formula its $x$-term for $x\in\Lambda$ is
$$
\alpha(y)\alpha(x)e^{-\pi i E(y,x)}e^{-\pi H(y+x,y+x)/2}\,
e^{2\pi i E(y+x,z)}.
$$
The last factor is a character on $V/\Lambda'$ since $x+y$ pairs integrally with $\Lambda'$. Its integral is zero unless $x+y=0$, by translation invariance and nondegeneracy of $E$. The Gaussian bounds allow termwise integration. Thus only the representative $y\in\Lambda'$ of the zero class contributes. Its $x=-y$ term has constant $1$, so the integral is $c\,\operatorname{vol}(D')/\sqrt n=c\sqrt n$.

**Unfold the same integral.** Write $A=1-\delta^{-1}$, which is invertible, and $C=A^{-1}-1/2$. Unitarity gives $A^*=1-\delta=-\delta A$ and $A+A^*=A^*A$; hence $A^{-1}+(A^*)^{-1}=1$ and $C^*=-C$. For $x\in\Lambda$, put
$$
\phi(x)=\alpha(x)e^{-\pi H(Cx,x)},\qquad G(v)=e^{-\pi H(Av,v)} .
$$
Expanding the exponent of $\alpha(x)U_x(v\mapsto e^{\pi H(v,z)})(\delta^{-1}z)W(z)$ gives $\phi(x)G(z-A^{-1}x)$. Indeed with $u=A^{-1}x$, the linear terms after shifting $z$ use $A^*u=-\delta x$, and the constant terms use $H(x,u)+H(u,x)=H(x,x)$.

The phase descends to the finite quotient $\Lambda/A\Lambda'$. In fact
$$
\phi(x+y)=\phi(x)\phi(y)e^{-2\pi i E(A^{-1}x,y)}
$$
on $\Lambda$, by the semicharacter law, $C^*=-C$, and $E(x,y)\in\mathbb Z$. Its polarization has radical $A\Lambda'$: pairing $A^{-1}x$ integrally with $\Lambda$ means $u=A^{-1}x\in\Lambda$ by self-duality, and then $u-x=\delta^{-1}u\in\Lambda$, so $u\in\Lambda'$. Conversely this condition suffices. For $u\in\Lambda'$, $\alpha(u)=\alpha(\delta^{-1}u)$; the semicharacter law at $x=u-\delta^{-1}u$ gives $\alpha(x)=e^{-\pi i E(u,\delta^{-1}u)}$. The imaginary part of $H(Cx,x)$ is $E(u,x)=-E(u,\delta^{-1}u)$. Its real part vanishes by the skew adjoint, so $\phi(Au)=1$. This proves descent and nondegeneracy on the quotient. Also $\phi(kx)=\phi(x)^{k^2}$, since the sign raised to $k$ or to $k^2$ is the same.

Choose representatives $S$ of $\Lambda/A\Lambda'$. For $x=s+Au$, $s\in S,u\in\Lambda'$, the corresponding summand is $\phi(s)G(z-A^{-1}s-u)$. Absolute integrability of $G$ follows from $\operatorname{Re}H(Av,v)=H(Av,Av)/2$. The translates $D'-u$ tile $V$ up to null sets; summing integrals of the absolute values for each $s$ gives the integral of $|G|$, so unfolding is justified. The integral in question becomes $(\sum_{s\in S}\phi(s))\int_V G$. A unitary diagonalization of $\delta$ diagonalizes $A$, and each eigenvalue $a$ of $A$ has positive real part. In polar coordinates on one complex coordinate $\int_{\mathbb C}e^{-\pi a |z|^2}\,dz=1/a$, using $\operatorname{Re}a>0$ in the radial integral. Hence $\int_V G=1/\det_{\mathbb C} A$.

**Compare and take the eighth power.** The index $m=[\Lambda:A\Lambda']$ equals $n|\det_{\mathbb C}A|^2$, since $A\Lambda'\subset\Lambda$ and a complex-linear change multiplies real volume by the squared modulus of its determinant. The two integral formulas give
$$
c=\frac{|\det A|}{\det A}\,\frac{1}{\sqrt m}\sum_{s\in S}\phi(s).
$$
The sum normalized by $\sqrt m$ has eighth power $1$ by the [finite quadratic Gauss sum proof](the-eighth-power-of-a-finite-quadratic-gauss-sum.md). As $A^*=-\delta A$, $\overline{\det A}=(-1)^{\dim_\mathbb C V}\det\delta\,\det A$. Therefore $(|\det A|/\det A)^8=(\overline{\det A}/\det A)^4=(\det\delta)^4$, as wanted.

**Lean correspondence.** The statements are [`UnitaryConstant` and `UnitaryEighth`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/UnitaryConstant.lean#L89). The term shift, diagonal evaluation and unfolding are [`kernelTermShift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/ExtensionActionPermutesPlaces.lean#L35), [`diagonalIntegral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/DiagonalIntegral.lean#L76), and [`unfoldingIntegral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/UnfoldingIntegral.lean#L67). The Gaussian integral is [`cayleyGaussianIntegral`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/CayleyGaussianIntegral.lean#L61); the comparison is [`const_value`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/DiagIntegrable.lean#L140) and [`UnitaryConstant_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/SelfDualCovolumeProof.lean#L109). The determinant argument is [`UnitaryEighth_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/UnitaryEighthOf.lean#L117). The choice of measure above gives the covolume directly from the alternating Gram matrix.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
