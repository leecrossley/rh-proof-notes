# Block projections construct the integral unitary frame

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $p\ge5$ be inert in $K=\mathbb Q(\sqrt{-d})$, where $d$ is the prime discriminant parameter of the host and $d\equiv7\bmod8$. Work with a CM period lattice
$$
\Lambda=\lambda\left(a\mathbb Z+\frac{b+\sqrt{-d}}2\,\mathbb Z\right),
\qquad a>0,\quad \lambda\ne0,\quad 4ac=b^2+d.
$$
Let $\Gamma\subset\mathbb C^n$ be self-dual for the alternating part of a Hermitian form. Suppose the complex-linear map $g$ is an isometry from four copies of this Hermitian space to the standard space with form $\operatorname{area}(\Lambda)^{-1}I$, and $g(\Gamma^4)$ is commensurable with $\Lambda^{4n}$. Assume that $I=[g(\Gamma^4):g(\Gamma^4)\cap\Lambda^{4n}]$ is prime to $p$. Fix an abstract field isomorphism $\iota:\mathbb C\cong\mathbb C_p$. Then the inverse isometry has the decomposition
$$
\iota(g^{-1})=\operatorname{diag}(B',B',B',B')\gamma,
$$
where $B'$ is invertible over $\mathbb C_p$, and the entries of $\gamma$ lie in the ring of integers of the unramified quadratic extension of $\mathbb Q_p$ and satisfy $\gamma^*\gamma=I_{4n}$. Here star on that ring means transpose and the nontrivial automorphism. This is the frame equation `IsFrameH`.

**Integral block moves.** Call the standard lattice $\Gamma_s=\Lambda^{4n}$ and the image lattice $\Gamma_b=g(\Gamma^4)$. The index gives $I\Gamma_b\subset\Gamma_s$. Self-duality of both lattices for the same alternating form gives $I\Gamma_s\subset\Gamma_b$: pairing $Ix$ for $x\in\Gamma_s$ with $y\in\Gamma_b$ is the pairing of $x$ with $Iy\in\Gamma_s$, so is integral. If $X$ is any complex-linear endomorphism preserving $\Gamma^4$, we therefore have
$$
I^2 gXg^{-1}(\Gamma_s)\subset\Gamma_s.
$$
Apply this to the standard vector with $\lambda a$ in one coordinate. Every entry of $gXg^{-1}$ is a ratio $(m a+k(b+\sqrt{-d})/2)/(I^2 a)$ with $m,k\in\mathbb Z$. If $p\mid a$, the equation for $a,b,c$ would give $b^2=-d\bmod p$, impossible by inertness. Hence these entries belong to $\mathcal O_{K,(p)}$. In particular the conclusion holds for all projections onto a single block and the maps transferring a coordinate block into another block and zeroing the rest.

**A rational matrix and one common Gram form.** Write $G=g^{-1}$ and $D(P)=\operatorname{diag}(P,P,P,P)$ for a square matrix $P$ of size $n$. In block $0$ of the rows of $G$, choose $n$ columns $w_1,\ldots,w_n$ giving an invertible matrix $P$, possible since all rows of $G$ are independent. For each block $a$, let $X_{a0}$ move block $0$ to block $a$. Form a square matrix $S$ by putting the columns $g X_{a0}G e_{w_j}$ in positions $(a,j)$. Then $GS=D(P)$, since $X_{a0}$ moves the chosen columns of the first row block into block $a$. Thus $S$ and its inverse $M$ have entries in $K$, by the preceding calculation, and $G=D(P)M$.

Rescale the source Gram matrix by the area of $\Lambda$ so that $G$ is an isometry from the identity Gram matrix to the direct sum of four copies of a matrix $H$. Use the convention that the first variable of the form is conjugate linear. The identity $G^*D(H)G=I_{4n}$ then gives
$$
M^* D(H_0)M=I_{4n},\qquad D(H_0)=S^*S,\quad H_0=P^*HP.
$$
Therefore $H_0$ itself has entries in $K$. The entries of $M,H_0$ transport to the unramified quadratic field through $\iota|_K$: $\iota(\sqrt{-d})$ is a root of an irreducible quadratic with distinct roots in residue characteristic $p$. Its Frobenius conjugate is the other root, so the transported Gram identity uses the quadratic adjoint. In what follows all the matrices with entries in that field are taken after this transport.

**An integral Hermitian projection.** Let $Z$ be the first block of rows of $M$, and $Z_a$ its block $a$. For the map $X_{0a}$, the integral matrix $U_a=g X_{0a}g^{-1}$ satisfies $X_{0a}M=MU_a$, since the block move commutes with $D(P)$. In particular $Z_a=ZU_a$. The inverse form of the Gram identity gives $ZZ^* H_0=I_n$. Thus $\Pi=Z^* H_0 Z$ is a Hermitian idempotent. Taking $a=0$ also gives $\Pi=U_0^*U_0$: the Gram of $MU_0$ in $D(H_0)$ is the Gram of its single nonzero row block $Z$. This proves $\Pi$ is integral even though we have used the entries of $M$ in the field.

In the standard integral module of rank $4n$, the image of a Hermitian integral idempotent is an orthogonal direct summand with perfect pairing: the complement is the kernel, and perfection follows by extending a linear functional by zero on that complement. Its rank is $n$, because $Z$ has rank $n$ and $ZZ^*H_0=I_n$. By the unit-length argument for the [unramified local Hermitian lattice](simultaneous-unitary-approximation-of-hermitian-lattices.md), it has an integral orthonormal basis. Let $A$ have those basis columns and put $T=ZA$. Then $T^*H_0 T=A^*\Pi A=I_n$. In particular $T$ is invertible, $T^{-1}Z=A^*\Pi$, and
$$
T^{-1} Z_a=A^*\Pi U_a
$$
is integral on every row block. Hence $\gamma=D(T^{-1})M$ is integral. It is unitary because $(T^{-1})^*T^{-1}=H_0$ and $M^*D(H_0)M=I_{4n}$. Taking $B'=\iota(P)T$ now proves the claimed frame equation.

**Lean correspondence.** The prime-to-$p$ bound on conjugated block moves is [`conj_entry_int`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/HermitianBlockFrames/ConjMatrixApply.lean#L9). The choice of columns and rational factorization is [`ratStep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/HermitianBlockFrames/AreaCmLNe.lean#L50). The integral projection and local frame are [`local_core'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/HermitianBlockFrames/LocMain.lean#L12); the field transport and assembly are [`hermFrame_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/TorsionIntegrality/UniformGaussModels/OrthogonalGaussModels/HermitianBlockFrames/Assembly.lean#L62). The isometry with the required relative index is an upstream input to this construction.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
