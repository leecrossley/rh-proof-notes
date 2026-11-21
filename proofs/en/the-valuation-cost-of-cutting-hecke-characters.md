# The valuation cost of cutting Hecke characters

[Chinese proof](../zh/%E6%88%AA%E5%8E%BB%E4%B8%80%E9%83%A8%E5%88%86%E7%89%B9%E5%BE%81%E4%B8%BA%E4%BD%95%E5%8F%AA%E6%8D%9F%E5%A4%B1%E4%B8%80%E4%B8%AA%E8%B5%8B%E5%80%BC.md)

## Statement

Let $O$ be a discrete valuation ring with fraction field $K$ and normalized valuation $v$. Let $V=\bigoplus_{z\in X}V_z$ for a finite $X$, and let $L$ be a finitely generated spanning $O$-lattice. Write $V_J=\bigoplus_{z\in J}V_z$. Suppose some nonzero $d\in O$ makes all coordinate projections integral on $L$ after multiplying by $d$. For $Z,S\subseteq X$ let $q:V\to V_S$ be the projection, $L'=q(L)$ and $Z'=Z\cap S$. Suppose an operator $\alpha$ preserving $L$ acts as $A\,\mathrm{id}$ on $V_Z$ for nonzero $A\in O$, and is zero on $V_{X\setminus S}$. Put $L^\uparrow=V_Z\cap(L+V_{X\setminus Z})$, $L^\downarrow=V_Z\cap L$. Define the primed lattices similarly in $V_S$ with $Z'$ and $L'$. Then
$$
\operatorname{length}_O(L^\uparrow/L^\downarrow)
\le\operatorname{length}_O(L'^\uparrow/L'^\downarrow)+v(A)\sum_{z\in Z}\dim_K V_z .
$$
The quotient measures the difference between the projected integral lattice on the selected components and its intersection with those components. This is the discrete valuation ring form of `Alg.length_le`.

## A scalar annihilates the kernel

The upper lattice is the projection of $L$, so $dL^\uparrow\subseteq L^\downarrow$ by the common denominator. The same holds for the primed lattices. Both quotients are therefore finite-length. The map $q$ induces $\Phi:L^\uparrow/L^\downarrow\to L'^\uparrow/L'^\downarrow$. If $u$ represents a class in the kernel, then $q(u)\in L'^\downarrow\subseteq q(L)$. Choose $l\in L$ with $q(l)=q(u)$. We have $u-l\in V_{X\setminus S}$ and hence $Au=\alpha u=\alpha l\in L$. Since $Au\in V_Z$, it belongs to $L^\downarrow$.

The preimage $P$ of $\ker\Phi$ in $L^\uparrow$ is finitely generated and torsion-free over $O$, hence free of rank $r\le\dim V_Z$. The images of its basis generate the kernel, and $A$ kills them. Thus the kernel is a quotient of $(O/(A))^r$, of length $rv(A)$. Add the length of the image, bounded by the target's length, to obtain the claim.

## Hecke components and the common denominator

The project has a finite set $X$ of Hecke characters and an algebra $\mathcal T\subset O^X$ separating them pairwise. It acts on a finite $O$-module whose image after tensoring with $K$ is $L$. For fixed $z$, choose a separator from each $y\ne z$, subtract its value at $y$, and multiply the resulting factors. This gives $f_z\in\mathcal T$ supported only at $z$ and nonzero there. Dividing by $f_z(z)$ gives the rational coordinate idempotent, and $d=\prod_z f_z(z)$ clears every denominator.

Keeping $S$ means replacing $\mathcal T$ by its restriction image in $O^S$ and changing scalars accordingly. The restriction map is surjective, so this quotients the module by the product of its kernel ideal with the module. Over $K$ it removes exactly $V_{X\setminus S}$ and the image of the integral lattice is $q(L)$. In the application $Z$ is the locally good character set, $S$ the retained set, and the required $\alpha$ acts by a certain finite group order $A$ on $Z$ and kills the dropped components. Existence of this compatible operator is an arithmetic input. Dividing the length bound by the coefficient ramification index $e$ above $p$ uses $v(A)=ev_p(A)$ and gives the normalized cost in `eta_le`. [Summing the local costs](summing-the-local-cost-of-cutting-hecke-characters.md)

- `decomp` constructs integral multiples of the idempotents, `qK_eq_zero_iff` identifies the rational kernel, and `length_le_of_span` bounds the annihilated kernel. `length_le`, `length_ne_top` and `lenUnit_le_add` give the comparison, finiteness and normalization. [Lattice length comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/LengthLeOfSpan.lean)
- `eta_le` applies the comparison at each block and `etaJ_le` sums the blocks at one place and layer. [Local arithmetic application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/HeckeGaloisCriteria/IsHeckeGaloisIff.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
