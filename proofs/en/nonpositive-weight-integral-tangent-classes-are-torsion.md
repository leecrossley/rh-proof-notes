# Nonpositive-weight integral tangent classes are torsion

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E9%9D%9E%E6%AD%A3%E6%9D%83%E7%9A%84%E6%95%B4%E7%B3%BB%E6%95%B0%E5%88%87%E5%90%91%E7%B1%BB%E5%8F%98%E6%88%90%E6%89%AD%E7%BB%93.md)

## Statement

Use the [Gaussian deformation frame](the-large-conductor-v-case-over-the-gaussian-field.md) at general weight $e\ge1$. For $j\le0$ let $W_j\subset M_3(O)$ be the coordinate weight-$j$ submodule with the adjoint action of $r_0$. Suppose $z:\Gamma\to W_j$ is a continuous cocycle vanishing on $N_v=I_v\cap\ker\eta\cap\ker\bar\Psi$ at each $v\in S\setminus T$. For $j=0$ also require vanishing on $I_v$ for $v\in T$. For $j<0$ require it to be a coboundary on $D_\ell\cap\ker\eta$. Assume `LemmaK`, global Poitou–Tate duality, local finiteness, local Tate duality, and the local Euler characteristic formula. Then there are $a\in O\setminus\{0\}$ and $X\in M_3(O)$ with $az(g)=g\cdot X-X$ for all $g$. The sign of $X$ can be reversed for the coboundary convention in `Frame.VanE`.

## One-dimensional summands

Let $J$ reverse the coordinates and $b(X)=-JX^{\mathsf T}J$. This involution preserves position weights, since the map on indices $(i,k)\mapsto(2-k,2-i)$ preserves their difference. On $W_j$ the adjoint action multiplies by $\Psi^j$, with the additional action of $b$ on the coset $\eta=-1$. Since $2\in O^\times$, the two eigenspaces split, and their scalar actions are $\Psi^j$ and $\Psi^j\eta$. Treat each scalar coordinate with character $\lambda=\Psi^j\eta^s$, $s=0,1$, and take the product of the finitely many nonzero annihilators at the end.

## Weight zero

On $\ker\eta$, the cocycle becomes an additive homomorphism. Its pullback to the Gaussian field is unramified. Indeed for $v\in T$ this follows from the inertia condition, and outside $T$, a power of each element in $I_v\cap\ker\eta$ lies in $N_v$ by finiteness of $k^\times$. The power's value is that positive integer times the original value, and $O$ has characteristic zero. Conjugating inertia multiplies the values on $\ker\eta$ by a unit. The reductions modulo $\mathfrak m^r$ of the pulled-back homomorphism factor through the class group, which is trivial since the Gaussian integers are norm-Euclidean. Thus the original homomorphism is zero. The cocycle descends to the order-two quotient. For a cocycle $u$ on a finite group $G$, if $S_u=\sum_hu(h)$ then $S_u=|G|u(g)+gS_u$. Thus $|G|u$ is a coboundary, settling weight zero.

## Negative weights

For $j=-h<0$ the pullback character is $\widetilde\psi^{-1}\varepsilon_\ell^{-eh}$ for the finite-order $\widetilde\psi=\psi_G^h\eta^{-s}$. At $\ell$, subtract the given coboundary on $D_\ell\cap\ker\eta$. The remaining cocycle factors through a quotient of order at most two with values in invariants of that subgroup. The same averaging shows it is a coboundary over the fraction field. Conjugate for the other absolute places.

For $v\ne\ell$, we use $H^1(D_v,\operatorname{Frac}(O)(\lambda))=0$ whenever $\lambda=\zeta\varepsilon_\ell^w$ with $\zeta$ finite order and $w\ne0,1$. Choose an arithmetic Frobenius of residue norm $q>1$. The values of $\lambda$ and $\varepsilon_\ell\lambda^{-1}$ there differ from one, since $q^w$ and $q^{1-w}$ are not roots of unity. Call the two nonzero differences $d_1,d_2$. For the finite module $M_r=O/\ell^rO$ with action $\lambda$, $H^0$ has cardinality at most $|O/d_1O|$. The invariant submodule of the Cartier dual has cardinality at most $|O/d_2O|$, by duality with $M_r/d_2M_r$. Local Tate duality gives the same bound for $|H^2|$. At $v\ne\ell$ the Euler characteristic gives $|H^1|=|H^0||H^2|$. Thus some fixed integer $B!$ kills all these first cohomology groups.

For an integral cocycle $u$, this gives $B!u(g)\equiv(\lambda(g)-1)m_r\bmod\ell^r$ for each $r$. Cross-multiply with the equality at a fixed $\lambda(g_0)\ne1$ to cancel $m_r$. The error lies in all $\ell^rO$, hence vanishes. In the fraction field, $u(g)=(\lambda(g)-1)u(g_0)/(\lambda(g_0)-1)$. A fraction-field cocycle can be scaled to an integral one by compactness. This proves local vanishing and applies here since $w=-eh<0$.

We now have the required local coboundaries in the fraction field at every place. Apply [field-coefficient vanishing](divisible-coefficient-finiteness-kills-field-valued-cocycles.md) and clear denominators. Reassembling the weight summands gives the nonzero annihilator.

## Lean correspondence

- [`adRep_baseLift_apply`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/UnitaryThreeGroups/AdRepBaseLiftApply.lean#L16) and [`vanEOf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoVanEOf.lean#L27) split and reassemble the weight.
- [`lineZero`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoLineZero.lean#L9) and [`cobIndex`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoCobIndex.lean#L6) give weight zero and averaging.
- [`locKill`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoLocKill.lean#L24) and [`cobLim`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoCobLim.lean#L50) pass from local finite layers to field coefficients.
- [`soCocL`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoCocL.lean#L10), [`lineNeg`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoLineNeg.lean#L27) and [`hostVanE`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LevelCohomology/SoHostVanE.lean#L11) complete the global argument.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
