# Changing frames in the finite kernel sum

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $E$ be a number field with the involution used for the standard Hermitian forms, and let $K$ be the coefficient field. Fix ranks $a,b$, finite sets $\mathcal S,\mathcal B$ of primes of $E$, and positive integers $c_A,c_B$. Take self-dual lattices $N\subset E^a$, $N'\subset E^b$ and frames $F_P,F'_P$ at the places $P\in\mathcal B$. A frame is an invertible matrix on the corresponding ambient vector space. Write
$$
H=H(N,N')=\{x:E^a\longrightarrow E^b \text{ linear}\mid xN_P\subseteq N'_P \text{ for every }P\in\mathcal S\},
$$
where $N_P$ and $N'_P$ denote localization. Suppose a scalar weight $\Xi$ on the space of linear maps is invariant under translation by $c_B H$.

For a fixed adjacent theta step, let $\Theta(N,F;N',F';x)$ be its normalized jet operator with the congruence parameter $c_B$, acting from a $K$-space $V$ to another $K$-space $V'$. Assume the following three properties of the theta distribution, at all self-dual lattices and all frames to which they apply.

1. The value at $x$ depends only on its class modulo $c_B H$.
2. For unitary $\gamma,\gamma'$ sending the lattices and frames to their images and $x$ to $\gamma'x\gamma^{-1}$, the operator transforms by $\rho'(\gamma')\Theta(x)\rho(\gamma^{-1})$. Here $\rho,\rho'$ are the source and target unitary representations.
3. Right multiplication of $F_P,F'_P$ by locally integral automorphisms $B_P,B'_P$ multiplies the operator by
   $$
   \Delta=\prod_{P\in\mathcal B}s_{S,P}(\det B_P)s_{T,P}(\det B'_P),
   $$
   where $s_{S,P},s_{T,P}$ are the source and target determinant characters on local units.

Define the coefficient kernel by
$$
\mathcal K_\Xi(N,F;N',F')=
\sum_{[x]\in (c_A^{-1}H)/(c_B H)}\Xi(x)\Theta(N,F;N',F';x).
$$
For the transformed lattices $\widetilde N=\gamma N$, $\widetilde N'=\gamma'N'$ and frames $\widetilde F_P=\gamma F_P B_P$, $\widetilde F'_P=\gamma'F'_P B'_P$, take a new scalar weight $\widetilde\Xi$. If, for every $x$,
$$
\widetilde\Xi(\gamma'x\gamma^{-1})\Delta=d\,\Xi(x)
$$
for a fixed $d\in K$, then the new kernel is
$$
\mathcal K_{\widetilde\Xi}(\widetilde N,\widetilde F;\widetilde N',\widetilde F')
=d\,\rho'(\gamma')\mathcal K_\Xi(N,F;N',F')\rho(\gamma^{-1}).
$$

### Proof

To check finiteness, multiply a representative $x\in c_A^{-1}H$ by $c_A$ and reduce the resulting local homomorphism $N_P\to N'_P$ modulo $c_Ac_B$ at every $P\in\mathcal S$. The kernel of this map is $c_B H$. Indeed each module $\operatorname{Hom}_{\mathcal O_{E,P}}(N_P,N'_P)$ is free of rank $ab$, so vanishing of the reduction means that $x/c_B$ is a local homomorphism there. The residue rings $\mathcal O_{E,P}/(c_Ac_B)$ are finite. The resulting map on the quotient is injective into a finite product. Periodicity of $\Xi$ and of $\Theta$ gives independence of the representative in each summand.

Set $e(x)=\gamma'x\gamma^{-1}$. A localized vector of $\gamma N$ is exactly $\gamma v$ with $v\in N_P$, since localization commutes with the $E$-linear automorphism. The relation $e(x)\gamma v=\gamma' x v$ shows that $e(x)$ belongs to the new local Hom module exactly when $x$ belongs to the old one. This applies at every $P$. The inverse map is $y\mapsto\gamma'^{-1}y\gamma$. Both maps commute with scalar multiplication by $c_A$ and $c_B$. Thus $e$ induces a bijection on the indicated quotient.

Use $e(x)$ as the representative of the corresponding class in the new sum. The unitary and determinant laws, applied in that order to the evaluation of the new summand, give
$$
\begin{aligned}
\widetilde\Xi(e(x))\,\Theta(\widetilde N,\widetilde F;\widetilde N',\widetilde F';e(x))
&=\widetilde\Xi(e(x))\Delta\,\rho'(\gamma')\Theta(N,F;N',F';x)\rho(\gamma^{-1})\\
&=d\,\rho'(\gamma')\bigl(\Xi(x)\Theta(N,F;N',F';x)\bigr)\rho(\gamma^{-1}).
\end{aligned}
$$
Every class of the new sum is obtained exactly once. Linearity of left and right composition gives the formula on summing.

In the application, a full frame action $g$ consists of a global unitary component $\gamma$ together with a residue-frame action at the type primes and an integral-frame action at the twist primes. Let $a_P$ be the level character of the frame move at $P$ and let $a'_P$ be the corresponding target character. The local coefficient calculation supplies $d=(\prod_P a'_P)(\prod_P a_P)^{-1}$. The representation of $g$ on values is $\rho_\mathrm{fr}(g)=(\prod_P a_P)\rho(\gamma)$. The preceding identity is therefore precisely covariance at the target and contravariance at the source for the full frame representations.

### Lean correspondence

- [`homAt`, `divLat`, `mulLat` and `latSum`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L594) define the quotient of localized Hom lattices. [`ThDist.Ok` and `kerOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L619) give the distribution laws and the weighted sum. The additive subdivision property in `ThDist.Ok` is used elsewhere in the proof.
- [`homConjEquiv_mem_homAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HomConjEquivMemHomAt.lean#L52) and [`latSum_transport_equiv`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HomConjEquivMemHomAt.lean#L13) construct the quotient change of variables. [`kerOf_gmap_frames`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/HomConjEquivMemHomAt.lean#L90) deduces the kernel identity.
- [`finite_divLat_quot_mulLat_homAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/FiniteDivLatticeQuotient.lean#L42) proves the finiteness assertion by a global-module argument. The proof above uses local reduction to establish the same finiteness.
- [`frmRho`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L425) inserts the level characters into the two value representations.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
