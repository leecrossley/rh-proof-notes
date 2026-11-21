# First localization kernels control second cohomology length

[Chinese proof](../zh/%E4%B8%80%E9%98%B6%E5%B1%80%E9%83%A8%E5%8C%96%E6%A0%B8%E6%80%8E%E6%A0%B7%E6%8E%A7%E5%88%B6%E4%BA%8C%E9%98%B6%E4%B8%8A%E5%90%8C%E8%B0%83%E7%9A%84%E6%80%BB%E9%95%BF%E5%BA%A6.md)

## Statement

Let $L$ be a number field, $\ell$ a prime, with no real places if $\ell=2$. Let $S$ be the places above $\ell$, and $G_{L,S}$ the Galois group allowing ramification there. For $e\ge1$ put $T=\mathbb Z_\ell(e+1)$ and $W=(\mathbb Q_\ell/\mathbb Z_\ell)(-e)$. Let $\Sha^i$ denote the kernel of localization at $S$ in degree $i$. Assume finite-coefficient Poitou–Tate duality, local cohomology finiteness and local Tate duality. Over $\mathbb Z_\ell$, allowing infinite lengths, one has
$$
\begin{aligned}
\operatorname{length}H^2(G_{L,S},T)+\operatorname{length}H^0(G_{L,S},W)
={}&\operatorname{length}\Sha^1(W)
+\sum_{v\mid\ell}\operatorname{length}H^0(G_{L_v},W).
\end{aligned}
$$
Also $\operatorname{length}\Sha^1(W)\le\operatorname{length}H^2(G_{L,S},T)$. This is used in [negative-weight finiteness](finiteness-of-the-negative-weight-torsion-localization-kernel.md), and the equality provides the converse bound for `LemmaK`.

## Finite-level duality

For $r\ge1$ put $T_r=T/\ell^rT$ and $W_r=W[\ell^r]$. They are Cartier dual, since inversion and one Tate twist take $e+1$ to $-e$. Finite-level Poitou–Tate gives $\#\Sha^2(T_r)=\#\Sha^1(W_r)$ and
$$
\#\operatorname{coker}\bigl(H^2(G_{L,S},T_r)\to\prod_{v\mid\ell}H^2(G_{L_v},T_r)\bigr)
=\#H^0(G_{L,S},W_r).
$$
Local Tate duality gives $\#H^2(G_{L_v},T_r)=\#H^0(G_{L_v},W_r)$. The hypothesis at $2$ removes real-place corrections.

Write $X=H^2(G_{L,S},T)$, $Y=\prod_{v\mid\ell}H^2(G_{L_v},T)$, and $f$ for restriction. Finite-level third cohomology vanishes. The inverse systems have finite terms, hence stabilize in image at each level, so the first derived inverse-limit terms vanish. Integral third cohomology also vanishes. The long exact sequence of $0\to T\xrightarrow{\ell^r}T\to T_r\to0$ thus identifies $X/\ell^rX$ and $Y/\ell^rY$ with the corresponding finite-level groups, compatibly with restriction. The integral modules are complete and finitely generated: lift generators of the first quotient, approximate at each subsequent quotient and use completeness. These properties are the comparisons `global_lim` and `local_lim`.

## The limiting kernels

The local invariants of $W$ are finite, since the open local cyclotomic image has an element whose $e$th power differs from one, and its difference from one annihilates them. The global invariants lie inside the local ones. Thus local invariants in $W_r$ stabilize. The corresponding local second cohomology groups have eventually constant cardinality, and their transition maps are surjective by the reduction comparison. Consequently $Y$ is finite with length equal to the sum of local invariant lengths. Take $r$ large enough that $\ell^rY=0$. The finite-level restriction then has kernel $\ker f/(\ker f\cap\ell^rX)$ and cokernel $\operatorname{coker} f$.

For large $r$ the map $\Sha^1(W_r)\to\Sha^1(W)$ is injective. If a finite-level cocycle is the global coboundary of $a\in W$, at any $v\mid\ell$ it is also the local coboundary of $b_v\in W_r$. Thus $a-b_v$ is a local invariant, which belongs to $W_r$ for large $r$. Hence $a\in W_r$ and the finite-level class was zero. The images exhaust $\Sha^1(W)$, because a continuous cocycle has finite image in the discrete module and one can adjoin the finitely many local coboundary parameters to one finite torsion layer. The lengths of $\ker f/(\ker f\cap\ell^rX)$ tend to the length of $\ker f$ by Artin–Rees and finite generation, allowing infinity. The two finite-level cardinality equalities now give
$$
\operatorname{length}\ker f=\operatorname{length}\Sha^1(W),\qquad
\operatorname{length}\operatorname{coker} f=\operatorname{length}H^0(G_{L,S},W).
$$

Finally add the two exact-sequence length identities for $f$. They give $\operatorname{length}X+\operatorname{length}\operatorname{coker}f=\operatorname{length}\ker f+\operatorname{length}Y$, avoiding any subtraction of infinite quantities. Substitute the equalities just proved. The inequality follows from $\ker f\subset X$.

## Lean correspondence

- [`finite_level`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/LengthEqLengthInvariantsOfTorsionLevels.lean#L517), [`ptShaAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/LengthEqLengthInvariantsOfTorsionLevels.lean#L462) and [`ptCokerAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/FoundationProofs/LengthEqLengthInvariantsOfTorsionLevels.lean#L393) perform the finite-level comparison, also treating $e=0$ in the source. [`Sha2Zl`, `PTCase` and `PTShaAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GaloisCohomology/Statement.lean#L82) specify the duality targets.
- [`vFormula_of_classicalTheorems`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/GaloisCohomologyLength/Formula.lean#L15), [`VLen_le_shaLen_add`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/GaloisCohomologyLength/Formula.lean#L29) and [`VFormula`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/GaloisLibrary/GaloisCohomologyLength/VFormula.lean) assemble the length identity. [`shaLeV`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/AdditiveValuationNorms/ShaLeV.lean#L7) and [`sFinal`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/SFinal.lean#L100) use it in the two directions.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
