# Three theta averages differ by an eighth root

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $V$ be a finite-dimensional complex Hermitian space with positive definite form $H$, and let $E=\operatorname{Im}H$. Let $\Lambda_1,\Lambda_2,\Lambda_3$ be full commensurable lattices, each self-dual for $E$. On their union fix the same sign function $\alpha$, taking values in $\{\pm1\}$ on each lattice and satisfying
$$
\alpha(x+y)=\alpha(x)\alpha(y)\exp(\pi i E(x,y))
\quad (x,y\text{ in the same lattice}).
$$
Use $V_x=\alpha(x)U_x$ for $x$ in their union, with $U_xf(z)=f(z+x)\exp(-\pi H(z,x)-\pi H(x,x)/2)$. Let $F\ne0$ be entire and fixed by $V_x$ for all $x\in\Lambda_1$. For $n_{ij}=[\Lambda_j:\Lambda_j\cap\Lambda_i]$, define the normalized average $I_{ij}f=n_{ij}^{-1/2}\sum_x V_xf$, with $x$ representing the cosets in that index, for $f$ fixed by $\Lambda_i$. Then
$$
I_{23}I_{12}F=\mu\, I_{13}F,\qquad \mu^8=1 .
$$
The scalar is the positive normalization $\sqrt{n_{13}/(n_{12}n_{23})}$ times the finite sum in the proof below.

**Averages and inverses.** The cocycle $U_xU_y=\exp(-\pi iE(x,y))U_{x+y}$ makes $x\mapsto V_x$ a representation on each lattice. Put $\Delta=\Lambda_1\cap\Lambda_2\cap\Lambda_3$. Each $V_x$ for $x\in\Lambda_j$ preserves the space of $\Delta$-fixed functions and acts there through the finite group $\Lambda_j/\Delta$. Use the inner product given by integrating $f(z)\overline{g(z)}\exp(-\pi H(z,z))$ on a bounded fundamental region for $\Delta$. The integrand is periodic under $\Delta$ for two such functions. Translating $z$ by $x$ in the integral and cancelling the two exponential factors shows $V_x$ is unitary there. Thus the average $P_j$ over the finite group is a self-adjoint projection onto the functions fixed by $\Lambda_j$. For an input fixed by $\Lambda_i$, its repeated terms reduce to the indicated cosets, so $I_{ij}=\sqrt{n_{ij}}P_j$ on this input space.

For $f$ fixed by $\Lambda_i$, averaging a translate $U_y f$ over $\Lambda_i/\Delta$ kills it if $y\notin\Lambda_i$, whenever $U_y f$ is $\Delta$-fixed: the commutator is $\exp(-2\pi i E(x,y))$, nontrivial by self-duality of $\Lambda_i$. If $y\in\Lambda_i$, $V_y f=f$. This gives $P_iP_j f=f/n_{ij}$, since exactly a fraction $1/n_{ij}$ of the terms in $P_j$ belong to the intersection. Also $n_{ij}=n_{ji}$: the $E$-pairing modulo $\mathbb Z$ gives a nondegenerate pairing between the two finite quotients by the intersection, using self-duality on both sides. Hence $I_{ji}I_{ij}f=f$, and $I_{ij}$ preserves the norm, since $\|P_j f\|^2=\langle f,P_j f\rangle=\|f\|^2/n_{ij}$.

**Compute the scalar.** For representatives $y$ of $\Lambda_2/(\Lambda_1\cap\Lambda_2)$ and $z$ of $\Lambda_3/(\Lambda_2\cap\Lambda_3)$, expand $I_{23}I_{12}$ as the sum of $V_zV_y$. Apply $I_{31}=\sqrt{n_{13}}P_1$ on this $\Lambda_3$-fixed result. The individual summands are $\Delta$-fixed. By the commutator, $P_1$ kills all pairs except $z+y\in\Lambda_1$, for which $U_{z+y}F=\alpha(z+y)F$. Consequently $I_{31}I_{23}I_{12}F=\mu F$, where
$$
\mu=\sqrt{\frac{n_{13}}{n_{12}n_{23}}}\sum_{\substack{z,y\text{ as above}\\z+y\in\Lambda_1}}
\psi(z,y),\qquad
\psi(z,y)=\alpha(z)\alpha(y)\alpha(z+y)e^{-\pi i E(z,y)} .
$$
Inverting $I_{31}$ proves the composition formula. The norm preservation and $F\ne0$ show $|\mu|=1$.

**The finite quadratic phase.** The summation pairs are representatives for
$$
A=\{(z,y)\in\Lambda_3\times\Lambda_2:z+y\in\Lambda_1\}\big/\{(t,u-t):t\in\Lambda_2\cap\Lambda_3,\ u\in\Lambda_1\cap\Lambda_2\}.
$$
Indeed one first changes $z$ by a vector in $\Lambda_2\cap\Lambda_3$ while changing $y$ by the opposite vector, then reduces $y$ modulo $\Lambda_1\cap\Lambda_2$. The phase is invariant under these operations: $V_{z+t}V_{y-t}=V_z V_t V_{-t} V_y=V_zV_y$, and replacing $y$ by $y+u$ inserts $V_u$ at the right, where it fixes $F$. Since the product acts by the scalar $\psi(z,y)$ on the nonzero $F$, that scalar is unchanged. The lattice semicharacter law gives $\psi(kz,ky)=\psi(z,y)^{k^2}$, since $\alpha(kz)=\alpha(z)^k$ and the sign powers $k$ and $k^2$ agree. For two pairs $(z,y),(z',y')$, the phase ratio on addition is
$$
\frac{\psi(z+z',y+y')}{\psi(z,y)\psi(z',y')}=e^{2\pi i E(y,z')}.
$$
To check it, expand the three sign products using the lattice law. In the exponent the terms $2E(z,z')$ and $2E(y,y')$ contribute integer multiples of $2\pi i$, and the remaining mixed term is $2E(y,z')$. Thus the phase has bilinear polarization on $A$. Since $|\mu|=1$, the sum is nonzero. The [finite quadratic Gauss sum theorem](the-eighth-power-of-a-finite-quadratic-gauss-sum.md) makes its eighth power positive real. The normalization in $\mu$ is positive, so $\mu^8$ is positive real with norm $1$, hence equals $1$.

**Lean correspondence.** The normalized composition and phase are defined in [`psiT`, `tripleSum` and `tripleMu`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/GaussDegenerate.lean#L12). The finite quotient is constructed in [`pairs` and `triv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/TripleSumEighthOf.lean#L13), and [`TripleSumEighth_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/TripleSumEighthOf.lean#L160) passes to its Gauss sum. The pairwise inverse and triple formula are assembled in [`interInv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/QuadraticSemicharacterIdentityReformulated2.lean#L33) and [`tripleFormula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/SelfDualCovolume.lean#L29). Lean obtains the norm-one comparison by reversing the last two lattices and conjugating the phase; the finite projections above give the same norm-one comparison. The conclusion is [`TripleEighth_proof`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/QuadraticSemicharacters/CayleyGaussianIntegrals/TripleEighthProof.lean#L241).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
