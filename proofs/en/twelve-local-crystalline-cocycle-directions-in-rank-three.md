# Twelve local crystalline cocycle directions in rank three

[Chinese proof](../zh/%E7%A7%A9%E4%B8%89%E5%B1%80%E9%83%A8%E6%99%B6%E4%BD%93%E4%BD%99%E9%97%AD%E9%93%BE%E4%B8%BA%E4%BB%80%E4%B9%88%E6%9C%89%E5%8D%81%E4%BA%8C%E4%B8%AA%E6%96%B9%E5%90%91.md)

## Statement

Let $\ell\ne2$ be prime, $O$ a complete DVR finite over $\mathbb Z_\ell$, and $E/\mathbb Q_\ell$ a finite extension with the compatible $O$-map. Put $G=G_{\mathbb Q_\ell}$ with inertia $I_\ell$. Let $\Psi:G\to O^\times$ be continuous, $\eta:G\to\{\pm1\}$ unramified with kernel given by the fixed subgroup of a finite local extension, and $\tau$ a unit character with open kernel. Assume $\Psi|_{I_\ell}=\chi_\ell^e\tau|_{I_\ell}$ with $e\ge1$, as in `Dat3`. The reference matrix part is $\operatorname{diag}(\Psi,1,\Psi^{-1})$ and the sign is $\eta$. The adjoint module $V=M_3(E)$ uses diagonal conjugation and, when $\eta=-1$, first uses $X\mapsto-JX^{\mathsf T}J$ for the reversing matrix $J$. Weight is the difference of the corresponding entries of $(1,0,-1)$. Assume `LocalPublishedTheorems`, including local finiteness, Tate duality, Euler characteristic and the Bloch–Kato dimension theorem.

Let $Z_f^1(G,V)$ consist of continuous cocycles becoming coboundaries in $V\otimes_{\mathbb Q_\ell}B_{\mathrm{cris}}$. Its weights $(-2,-1,0,1,2)$ have dimensions $(1,2,3,4,2)$, and all other weights vanish. Projection to a weight preserves this condition. In negative weights $Z_f^1$ consists of coboundaries, and in weight zero it consists of cocycles vanishing on inertia.

## Decomposition into characters

Reflection across the antidiagonal interchanges $(a,b)$ and $(2-b,2-a)$, preserving their weights. For each distinct reflected pair use the sum and difference of its matrix units, on which $X\mapsto-JX^{\mathsf T}J$ acts by $-1,+1$. The three antidiagonal units have sign $-1$. Consequently the lines of weight $j$ have characters $\kappa=\Psi^j$ or $\Psi^j\eta$. On the open subgroup $I_\ell\cap\ker\tau$ they equal $\chi_\ell^{ej}$, and for $j=0$ they are unramified. Cocycles, coboundaries, and the period-ring condition all decompose along these lines.

## Dimension on a line

For $W=E(\kappa)$, coboundaries have dimension $1-\dim_E W^G$. For $ej\ne0$, the cyclotomic character admits infinite-order values on every open inertia subgroup, so $W^G=0$. The one-character filtration theorem gives a one-dimensional $D_{\mathrm{dR}}(W)$, with $\operatorname{Fil}^0$ equal to all of it for $j<0$ and zero for $j>0$ in the weight convention here. The local dimension formula is
$$
\dim_E H_f^1(G,W)=\dim_E(D_{\mathrm{dR}}(W)/\operatorname{Fil}^0)+\dim_E W^G.
$$
Adding back coboundaries gives dimension one for $j<0$, with every finite cocycle a coboundary, and dimension two for $j>0$.

For $j=0$, `z1fUnr` identifies finite cocycles with cocycles zero on inertia. Such a cocycle is determined by its value $u\in E$ at arithmetic Frobenius, whose powers are dense in the unramified quotient. Any $u$ occurs. If the character value $\alpha$ at Frobenius is different from $1$, take $(\kappa(g)-1)u/(\alpha-1)$. If $\alpha=1$, take the projection $\widehat{\mathbb Z}\to\mathbb Z_\ell$ multiplied by $u$. Thus each weight-zero line contributes one.

The counts of positions of the five weights are $(1,2,3,2,1)$. Multiplying by the relevant dimensions gives $(1,2,3,4,2)$, totaling twelve. These bound the number of coordinate jets of each weight in the [local smooth chart](../zh/%E5%B1%80%E9%83%A8%E5%85%89%E6%BB%91%E5%9B%BE%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%8D%81%E4%BA%8C%E4%B8%AA%E6%96%B9%E5%90%91%E5%88%86%E9%85%8D%E7%BB%99%E5%90%84%E4%B8%AA%E6%9D%83.md). The negative-weight coboundary and weight-zero inertia statements enter the [local condition for rigidity](deformation-tangent-vectors-satisfy-the-bloch-kato-local-conditions.md).

## Lean correspondence

- [`Dat3`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/IsInertiaInfiniteCyclotomic.lean#L11) and [`finiteCocycles`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/FiniteCohomology.lean#L112) specify data and cocycles.
- [`dim_Z1f_crystalline_deformation`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/DimZ1fCrystallineDeformation.lean#L194) uses `dzE` and `dz_eq` for the reflection basis, `dz_unr` for Frobenius evaluation, and `dz_sum` for the weight dimensions.
- [`z1fChar`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ExistsNeOne.lean#L63), [`bkDim`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/CocycleTransportH1fSurjective.lean#L133) and [`z1fUnr`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ExistsIntBasis.lean#L370) supply the line calculations. [Unramified cocycles from a Frobenius value](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ExistsUniqueUnramifiedCocycleFrobeniusValue.lean#L112) gives the weight-zero parametrization.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
