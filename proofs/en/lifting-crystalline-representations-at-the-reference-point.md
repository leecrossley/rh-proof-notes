# Lifting crystalline representations at the reference point

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E9%80%90%E9%98%B6%E6%8F%90%E5%8D%87%E5%8F%82%E8%80%83%E7%82%B9%E9%99%84%E8%BF%91%E7%9A%84%E6%99%B6%E4%BD%93%E8%A1%A8%E7%A4%BA.md)

## Statement

Use $O,\ell,G=G_{\mathbb Q_\ell},G_0,\eta,\Psi,e$ of the [local chart](the-weight-distribution-in-the-local-smooth-chart.md), $E=\operatorname{Frac}O$, and `LocalPublishedTheorems`. Let $B$ be a finite-dimensional commutative $E$-algebra augmented by $\pi:B\to E$ with nilpotent kernel. Consider continuous rank-three lifts with sign $\eta$, reference augmentation $r_0=\operatorname{diag}(\Psi,1,\Psi^{-1})$, and crystalline restriction to $G_0$. Every such lift can be conjugated to upper triangular by a lower unitriangular matrix with identity augmentation. Conjugating back preserves the conditions. Across any surjective augmented map $B\to B'$, each such lift over $B'$ lifts to $B$, with an upper triangular lift if it was upper triangular. These are `ordEq`, `crLift` and `triLift`.

## Upper triangular parameters

Write $t_i(g)$ for the diagonal entries. The diagonal group law multiplies normally on $\eta=1$ and acts on the second diagonal by reversed inverses on $\eta=-1$. Write
$$
\beta_1=M_{01}/t_1,\qquad\beta_2=M_{12}/t_2,\qquad
\gamma=M_{02}/t_2-\tfrac12\beta_1\beta_2 .
$$
For $\beta=(\beta_1,\beta_2)$ use the two-dimensional action $M_1$ given by ratios $t_0/t_1,t_1/t_2$, preceded by interchange and negation on the negative coset. Put $\chi_2=\eta t_0/t_2$ and $\omega(v,w)=v_1w_2-v_2w_1$. Upper triangular multiplication with the signed involution becomes
$$
\begin{aligned}
\beta(gh)&=\beta(g)+M_1(g)\beta(h),\\
\gamma(gh)&=\gamma(g)+\chi_2(g)\gamma(h)+
            \tfrac12\omega(\beta(g),M_1(g)\beta(h)).
\end{aligned}
$$
Choose the diagonal, then $\beta$, then solve for $\gamma$. Solutions in the last step differ by a $\chi_2$-cocycle.

## Lifting a triangular representation

For the diagonal, restriction to $G_0$ gives crystalline subquotients that differ from the reference by nilpotent-unit characters. The crystalline nilpotent-character theorem makes these characters trivial on inertia on $G_0$. This extends to inertia on $G$ because the subgroup has finite index and logarithms of nilpotent units have no additive torsion. Thus the ratios to the reference are unramified. Lift the three logarithms at Frobenius to the upper augmentation ideal. In log coordinates the negative sign acts by reversed negation. Split into symmetric and antisymmetric vectors for reversal, on which that action is sign and trivial, respectively. Continuous cocycles on $\widehat{\mathbb Z}$ with these actions are determined by any assigned value at Frobenius, by projection to order two for the sign or to $\mathbb Z_\ell$ for the trivial action. Exponentiate the lifted logarithms and multiply by the reference.

For the adjacent entries, the two components of $\beta'$ on $G_0$ are finite cocycles by crystallinity of the rank-two subquotients. The condition descends to the full group because finite quotient cohomology vanishes in characteristic zero. The two-dimensional module $M_1$ is de Rham and of positive weights, so [positive-weight exactness](crystalline-obstructions-in-positive-weight.md) gives a finite cocycle $\beta$ reducing to $\beta'$.

For the corner, the negative of the last term in the multiplication law is a two-cocycle. This follows by expanding $\beta(gh)$ and using $\omega(M_1(g)v,M_1(g)w)=\chi_2(g)\omega(v,w)$. Local Tate duality identifies the dimension of $H^2$ with the dimension of $\operatorname{Hom}_G(B(\chi_2),E(1))$. On inertia in $G_0$, $\chi_2$ is $\chi_\ell^{2e}$. An infinite-order cyclotomic value gives an invertible difference from the cyclotomic character since $2e\ge2$. Thus $H^2=0$ and the corner equation is solvable. This upper triangular lift is crystalline on $G_0$ since the adjacent classes are finite. The corner's reduction differs from $\gamma'$ by a cocycle, finite on $G_0$ by weight $2e$ and hence finite globally by the finite-index argument. Lift this difference by positive-weight exactness and adjust $\gamma$ to match $\gamma'$. This proves triangular lifting.

## Triangularizing at every nilpotent thickness

Over dual numbers write $r=(1+\epsilon c)r_0$. The adjoint cocycle is finite by the crystalline extension criterion. The [local cocycle calculation](twelve-local-crystalline-cocycle-directions-in-rank-three.md) makes its strictly lower part a coboundary $g\cdot X-X$ for strictly lower $X$. Conjugation by $1+\epsilon X$ cancels it.

For the general case with nonzero augmentation ideal $J$, choose nonzero $\epsilon_0\in J$ killed by $J$, from its last nonzero power. By induction on $\dim_E B$, triangularize over $B/E\epsilon_0$. Lift the lower conjugation and apply it to $r$, so it is triangular modulo $\epsilon_0$. Lift the triangular reduction by the preceding argument to a triangular crystalline $r_1$ over $B$. Compare $r_1$ and $r$ over
$$
F=B\times_E E[\epsilon]/(\epsilon^2).
$$
Its two maps to $B$ send $(b,\pi(b)+a\epsilon)$ to $b$ and $b+a\epsilon_0$, respectively. Together they identify $F$ with pairs agreeing modulo $E\epsilon_0$. The two lifts therefore assemble into an $F$-representation. It is crystalline on $G_0$ as a subrepresentation of their direct sum. Its projection to the dual numbers is crystalline and can be triangularized. Combine that conjugation with the identity on the triangular $B$-component $r_1$, using their common augmentation to glue them over $F$. The second map to $B$ now gives a lower unitriangular conjugation of $r$ to upper triangular. This completes the induction.

To lift a general $B'$ point, triangularize it, lift the triangular representation, and lift the entries of the lower unitriangular conjugation within the augmentation ideal. Undo the conjugation at the upper level to recover the given point over $B'$.

## Lean correspondence

- [`OrdDual.dual_ord`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/OrdDual.lean#L140), [`ordEq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ExistsEps.lean#L59) and [`crLift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/CrLift.lean#L45) give the dual-number argument, induction and lifting.
- [`triM`, `Tor`, `Tor.M1`, `Tor.χ2` and `Tor.IsGam`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/TriDefs.lean) give triangular parameters.
- [`triDiag`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/TriDiag.lean#L105) and [the nilpotent torus lift](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ExistsTorusLiftToNilpotentThickening.lean#L168) give the diagonal construction.
- [Finite-cocycle base change](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/TorsionDatumFiniteCocyclesBaseChange.lean#L81), [existence of a corner solution](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/ExistsContinuousIsGamOfTorusCocycle.lean#L17) and [`triLift`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/TriLift.lean#L262) give the rest of triangular lifting.
- [`dcr_pair`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/PadicHodgeTheory/OrdinaryDeformation.lean#L226) and [crystalline amalgamation over a fiber product](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/CrystallineOrdinaryIdeals/CrystallineDeformationAmalgamateOverFibreProductStatement.lean) justify the induction step.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
