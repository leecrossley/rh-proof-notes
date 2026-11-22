# Extending the coefficient kernel to all complex points

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Fix an adjacent step of a column chain with arithmetic points in sets $D_b$ at the source and $D'_{b'}$ at the target, indexed by the layer labels $b,b'$. A source arithmetic point has a map $\operatorname{pt}_b:D_b\to\mathcal P$ to its complex point model. Use a primed version at the target. The source arithmetic frame group $H_b$ acts on $D_b$ and maps by a homomorphism $h_b$ to the point group $G$. The map $\operatorname{pt}_b$ intertwines these actions. Assume the following realization properties on each side, with the corresponding point value representation $R:G\to\mathrm{GL}_{\mathbb C}(W)$.

1. A torsion group maps to the center of $G$ by $\zeta$. Every point is $\zeta(s)\operatorname{pt}_b(d)$ for some $s,b,d$. For every fixed $b$ and every $g\in G$ one can write $g=\zeta(s_0)h_b(a)$ with $a\in H_b$.
2. If $\zeta(s)\operatorname{pt}_b(d)=\operatorname{pt}_{\tilde b}(\tilde d)$, then $\tilde b=b$ and there is an $a\in H_b$ taking $d$ to $\tilde d$ such that $R(h_b(a))=R(\zeta(s))$.
3. The complex representative of every class is the image under $\operatorname{pt}_b$ of the chosen arithmetic representative.

In the actual realization `Dat.Real`, an element $a$ in property 2 can be chosen with rational matrix component $1$ and scalar character $s$. Both elements then act on values by the same scalar, which gives the needed equality of represented operators.

Let $k(d,d'):V\to V'$ be the $K$-linear arithmetic kernel on the true weight spaces, with dependence on the two labels understood. Assume arithmetic-frame covariance, and assume [agreement at the chosen representatives](evaluating-the-arithmetic-kernel-gives-the-point-kernel-at-representatives.md) with the prescribed complex operator $K_{\rm rep}$. Then there is a complex linear point kernel $\mathcal K:\mathcal P\times\mathcal P'\to\operatorname{Hom}_{\mathbb C}(W,W')$ satisfying full covariance on the two point models and agreeing with $K_{\rm rep}$ at the chosen representatives. At every arithmetic point pair, it sends the evaluation of $F\in V$ to the evaluation of $k(d,d')F$.

### Complexifying each arithmetic entry

Use the field embedding $\sigma:K\hookrightarrow\mathbb C$ in both value spaces and write $\operatorname{ev}:V\to W$, $\operatorname{ev}':V'\to W'$ for the coefficient evaluations. These are $\sigma$-linear. The image of a $K$-basis of $V$ is a complex basis of $W$. Here $V$ is the polynomial weight space, and evaluation maps coefficients to $\mathbb C$ and multiplies the polynomial on a tuple of invertible matrices by the prescribed determinant weights. It is injective on complex polynomials, since the determinant factors are nonzero on these matrices. Indeed, multiplying such a polynomial by the product of the determinants gives a polynomial vanishing on all matrix tuples. It is zero over the infinite field, and the polynomial ring is a domain.

Linear independence over $K$ of polynomials also persists over $\mathbb C$. A finite linear relation over $\mathbb C$ can be expressed in coordinates in a $K$-basis of the space spanned by its complex coefficients, giving separate $K$-linear relations on their images. Each gives zero coefficients by independence. For spanning, the complex polynomial value space is spanned by products, one for each embedding, of highest-weight minors with algebraic lowering operations applied. Each product has a preimage in the coefficient-field value space. Indeed the minor formulas and lowering operations commute with coefficient extension, and the lowered generators of the Weyl module belong to the indicated dual Weyl space. Taking complex spans and applying evaluation gives every value. These are the basis and spanning assertions used for $W$ and $W'$.

There is thus a unique complex linear map $\widetilde k(d,d')$ taking every evaluated basis vector $\operatorname{ev}(F_j)$ to $\operatorname{ev}'(k(d,d')F_j)$. By $\sigma$-linearity it has the corresponding formula for every $F\in V$. The arithmetic and complex actions on evaluated values agree. In coordinates this is the action by substitution of the inverse frame matrix and multiplication by the embedded character, which commutes with coefficient embedding and determinant factors. Arithmetic covariance therefore gives
$$
\widetilde k(a d,a'd')
=R'(h'_{b'}(a'))\,\widetilde k(d,d')\,R(h_b(a)^{-1}).
$$
It suffices to check this equality on evaluated basis vectors, since both sides are complex linear.

### Descending across torsion identifications

For points $p=\zeta(s)\operatorname{pt}_b(d)$ and $p'=\zeta'(s')\operatorname{pt}'_{b'}(d')$, set
$$
\mathcal K(p,p')
=R'(\zeta'(s'))\,\widetilde k(d,d')\,R(\zeta(s)^{-1}).
$$
If a second expression $\zeta(t)\operatorname{pt}_{\tilde b}(\tilde d)$ gives $p$, then $\zeta(t^{-1}s)\operatorname{pt}_b(d)=\operatorname{pt}_{\tilde b}(\tilde d)$. Property 2 identifies the labels and gives $a d=\tilde d$ and $R(h_b(a))=R(\zeta(t^{-1}s))$. Inserting this in the arithmetic covariance formula gives the same $\mathcal K$. Changing the target expression is checked in the same way, with left composition in place of right composition. Thus the formula is well-defined for every pair.

For $g=\zeta(s_0)h_b(a)$, centrality gives $gp=\zeta(s_0s)\operatorname{pt}_b(ad)$. Substitution in the formula and the covariance of $\widetilde k$ give
$$
\mathcal K(gp,p')=\mathcal K(p,p')R(g^{-1}).
$$
Applying the primed version at the target gives $\mathcal K(p,g'p')=R'(g')\mathcal K(p,p')$. Setting $s=s'=1$ recovers the arithmetic evaluations on every point pair. At the chosen class representatives the hypothesized equality with $K_{\rm rep}$ holds on the evaluated source values. These span $W$, so the equality holds on the full complex value space. This proves the two point covariance laws and the representative comparison required by the next steps of the word-prime argument.

### Lean correspondence

- [`Dat.Real`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/KerIsTerm.lean#L117) gives the groups, point realization and scalar identification. [`KerEq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/KerIsTerm.lean#L91) specifies the arithmetic assumptions on the kernel.
- [`fnOf_injective`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/PolyFn.lean#L265) proves injectivity of polynomial evaluation with determinant weights. [`span_evV` and `evV_linearIndependent`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/PolyFnLemmas.lean#L552) prove the complex basis assertions. [`evV_rho_eq_tr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/IwasawaDecomposition/HermitianLatticeChartFamilyLawBasis.lean#L71) checks the two value actions.
- [`exists_ext` and `exists_cplx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsPointKernelRealisedModels.lean#L13) give the descent and complexification arguments. [`exists_kerPt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsPointKernelRealisedModels.lean#L114) applies descent first in the target and then in the source, giving the point kernel with the indicated laws.

Status. Source-based reconstruction draft. The arithmetic and complex point realizations are hypotheses to the extension. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
