# The weight distribution in the local smooth chart

[Chinese proof](../zh/%E5%B1%80%E9%83%A8%E5%85%89%E6%BB%91%E5%9B%BE%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%8D%81%E4%BA%8C%E4%B8%AA%E6%96%B9%E5%90%91%E5%88%86%E9%85%8D%E7%BB%99%E5%90%84%E4%B8%AA%E6%9D%83.md)

## Statement and local conditions

Use $O,\ell,e,\eta,\Psi,\tau$ and the local theorems of the [crystalline cocycle calculation](twelve-local-crystalline-cocycle-directions-in-rank-three.md). Write $E=\operatorname{Frac}O$, and let $U$ be the universal lift ring at $G_{\mathbb Q_\ell}$ with reference point $x:U\to O$. Put $G_0=\ker\eta\cap\ker\tau$. For the saturated ordinary ideal $I_Y$, there is a unique branch $P=I_t$ through $x$, with a map
$$
\phi:U\to E[[T_1,\ldots,T_{12}]]
$$
of kernel $P$ and constant term $x$, inducing the completed local chart at the reference point after inverting nonzero elements of $O$. Matrix entries are homogeneous by row weight minus column weight. The variable counts in weights $(-2,-1,0,1,2)$ are $(1,2,3,4,2)$. The condition of killing $P$ is invariant under conjugation congruent to the identity. These are the properties in `LocGood`.

For $s\in G_0\cap I_\ell$, the ordinary equations give the inertia characteristic polynomial with eigencharacters $\kappa_a(s)=\Psi(s)^{1-a}$ for $a=0,1,2$. They also impose $\prod_{a=0}^2(M_{s_a}-\kappa_a(s_a)1)=0$ in increasing order for any three such $s_a$. The saturated ideal is $I_Y=(I_{\rm ord}:\Delta^\infty)$, with $\Delta$ built from $\ell$ and two adjacent Frobenius trace comparisons. See the [ordinary equations and crystalline criterion](ordinary-equations-detect-crystalline-lifts.md).

Two inputs are used. A point of $U$ over a finite-dimensional $\mathbb Q_\ell$-algebra killing $I_Y$ is crystalline on $G_0$. Conversely a continuous crystalline point there over a finite-dimensional $E$-algebra with nilpotent augmentation ideal and reference augmentation kills $I_Y$. Also a crystalline lift of this kind lifts across each surjection of augmented algebras. These are `saturatedOrdinaryIdeal_cuts_out_crystalline_locus` and `crLift`.

## The unweighted chart

Starting with a point that kills $I_Y$, lift its crystalline representation and use the converse criterion. Continuous lifts over these nilpotent thickenings correspond to substitutions in $U$ at the reference augmentation. Thus the lifting hypothesis of [formal smoothness at a reference branch](formal-smoothness-selects-the-reference-branch.md) applies. Invert nonzero elements of $O$ and complete there. The completed algebra is $E[[T_1,\ldots,T_n]]$, by lifting a cotangent basis to all truncations and inverting the resulting substitution to first order. The local ring embeds in the completion and is a domain, giving the unique minimal prime $P$ above $I_Y$ through $x$. There is $y$ with $x(y)\ne0$ and $yP\subset I_Y$. A derivation at $x$ killing $I_Y$ then kills $P$, since $0=\delta(ya)=x(y)\delta(a)$ for $a\in P$.

A dual-number lift $(1+\epsilon c)r_0$ is the extension of the reference representation by itself attached to the adjoint cocycle $c$. On $G_0$ the reference representation is crystalline. The extension is crystalline exactly when it splits after tensoring with $B_{\mathrm{cris}}$. The resulting coboundary condition is equivalent over $G$ and $G_0$ by vanishing of first cohomology of a finite group in characteristic zero. Thus the tangent dimension is the dimension $12$ of the finite cocycles computed above.

## Choosing homogeneous coordinates

For every $g,a,b$, subtract the reference value from the matrix entry to obtain $z_{g,a,b}$. The linear terms of their chart images span the cotangent space. A functional vanishing on all these terms gives a derivation on $U$ killing the universal entries. Multiplying by a common nonzero scalar on finitely many formal generators makes the derivation integral. The corresponding integral dual-number point leaves every matrix entry unchanged, hence is the reference point by universality. It follows that the functional vanishes on the entire chart cotangent space. Choose twelve deviations whose linear terms form a basis. Their chart images give an invertible formal change of variables, so assume $\phi(z_i)=T_i$.

Take an infinite-order $t\in1+\mathfrak m_O$ and the conjugation automorphism $\theta$ from $\operatorname{diag}(t,1,t^{-1})$. It fixes $x$, preserves the ordinary relations and saturation, and hence preserves the unique branch $P$. Deviations have the same weights as their entries since off-diagonal reference entries vanish. On the chart the conjugation is $T_i\mapsto t^{w_i}T_i$, by its values on the new coordinates. For an entry of weight $j$, comparing coefficients yields
$$
\left(t^{\sum_i w_i\nu_i}-t^j\right)[T^\nu]\phi(a)=0 .
$$
The powers of $t$ are distinct, proving homogeneity. Each coordinate jet gives a finite cocycle of its weight by dividing the coefficient of the entry by the appropriate reference diagonal value. The jets are independent on the selected deviations. Thus each weight's count is bounded by the corresponding cocycle dimension. Both totals are twelve, giving equality in every weight.

Finally, conjugate the universal branch over the domain $(U/P)[[X_{ab}]]$ by $1+X$. The ordinary equations and the nonzero saturating factor are preserved, so the resulting point kills $I_Y$. Its kernel is prime and is contained in $P$ by setting $X=0$, hence equals $P$ by minimality. Substitution of $h-1$ for $X$ proves stability under any conjugation congruent to the identity.

## Lean correspondence

- [`Dat3`, `ordIdeal`, `IY`, `It` and `IsCompl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/IsInertiaInfiniteCyclotomic.lean) give the definitions.
- [`saturatedOrdinaryIdeal_smooth_at_residualRep`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/CrystallineOrdinaryIdeals/OrdinaryLocusIdealLeKerOfIsBasePoint.lean#L102), [`rtCompl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/CrystallineOrdinaryIdeals/RtCompl.lean#L8) and [`tangent_finrank_eq_twelve`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/CrystallineOrdinaryIdeals/SaturatedOrdinaryIdealTangentFinrankEqTwelve.lean#L298) give the smooth chart and its dimension.
- [`rtChart`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/RtChart.lean), [`chartSpan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ChartSpan.lean#L94), [`chartChange`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ChartChange.lean#L105), [`chartGraded`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ChartGraded.lean#L100), and [`chartCount`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ChartCount.lean#L80) supply the weighted coordinates and counts.
- [`locGood`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/LocGood.lean) packages the calculations. [`rtConj`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/CrystallineOrdinaryIdeals/ExistsConjLift.lean#L100) handles conjugation.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
