# First-order deformations enter the dual cotangent module

[Chinese proof](../zh/%E4%B8%80%E9%98%B6%E5%8F%98%E5%BD%A2%E6%80%8E%E6%A0%B7%E6%8A%8A%E4%B8%8A%E5%90%8C%E8%B0%83%E7%B1%BB%E9%80%81%E8%BF%9B%E4%BD%99%E5%88%87%E6%A8%A1%E7%9A%84%E5%AF%B9%E5%81%B6.md)

Let $O$ be a DVR with finite residue field $k$, and $A=\bigoplus_{i\in X}A_i$ a commutative $O$-algebra graded by an abelian group $X$. Let $x:A\to O$ be an $O$-point, $J=\ker x$, and $J^2_{\rm sat}=\{f\in A:cf\in J^2\text{ for some }0\ne c\in O\}$. Fix $j\in X$ with $x(A_j)=0$. Let $C_j$ be the image of $A_j\cap J$ in $A/J^2_{\rm sat}$, and $Q_j$ its quotient by the images of a family $F_i\in A_j$. Set $\lambda=\operatorname{length}_O Q_j$, possibly infinite. These are `satSq`, `cotLat` and `cotLen`. [Definitions](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/ResMapBijective.lean#L245)

Let $a\ne0$ in $O$, $M$ an $O$-module, and $\mu\mapsto D_\mu$ an injective additive map to $O$-linear maps $A\to O/(a)$ killing each $F_i$. Suppose each $D_\mu$ lifts to an $O$-valued $O$-linear derivation $\widetilde D_\mu$ at $x$, i.e.
$$
\widetilde D_\mu(fg)=x(f)\widetilde D_\mu(g)+x(g)\widetilde D_\mu(f),
$$
vanishing on $A_i$ for $i\ne j$. Then $\operatorname{length}_O M\le\lambda$. [`LemmaM'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/OrbitVanishingLocal.lean#L120)

**Proof.** The product rule kills $J^2$. If $cf\in J^2$ with $c\ne0$, then $c\widetilde D_\mu(f)=0$ and cancellation in $O$ gives $\widetilde D_\mu(f)=0$. Thus both the lift and its reduction kill $J^2_{\rm sat}$. Restriction in degree $j$ descends to $C_j$, and killing $F_i$ makes it a map on $Q_j$. The map $M\to\operatorname{Hom}_O(Q_j,O/(a))$ is injective since the reductions vanish on all other degrees and every element of $A$ is a finite sum of homogeneous elements.

If $\lambda$ is finite, decompose $Q_j=\bigoplus_i O/(\pi^{b_i})$ for a uniformizer $\pi$, and write $a$ as a unit times $\pi^b$. The image of $1$ under a map from a cyclic summand to $O/(\pi^b)$ can be any element killed by $\pi^{b_i}$, of length $\min(b,b_i)$. Thus the Hom module has length at most $\sum_i b_i=\lambda$. A finite length $m$ module has cardinality $|k|^m$. By injection $M$ is finite and has finite length at most $\lambda$ by cardinality, even if the injection is only additive. For infinite $\lambda$ the length inequality is automatic.

The lift to $O$ allows cancellation when passing from $J^2$ to its saturation. The source `mprime_holds` computes the Hom bound by length induction, and `model_lower` and `vlen_le` apply it in degree $-1$ to [the normalized rank-three deformation](normalized-cocycles-give-derivations-on-the-deformation-ring.md). [Algebraic proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/CommutativeAlgebra/GradedModulesLength/Mprime.lean#L38) · [Model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/ModelLower.lean#L373) · [Cohomology](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/VlenLe.lean#L52)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
