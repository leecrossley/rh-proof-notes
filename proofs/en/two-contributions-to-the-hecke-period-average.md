# Two contributions to the Hecke period average

[Chinese proof](../zh/Hecke%E9%99%AA%E9%9B%86%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E6%88%90%E4%B8%A4%E4%B8%AA%E5%91%A8%E6%9C%9F%E8%B4%A1%E7%8C%AE.md)

## Statement

Use the Hecke notation in the [period criterion](hecke-periods-cannot-decay-at-three-fifths.md) with totally imaginary $L$, prime element $\pi$, $1\le j<r_2(L)$, $n,d\ge1$ and $N=n+d$. Write $\iota$ for stabilization by $I_d$. For a $\Gamma_N$-invariant homogeneous real $j$-cocycle $F$ on $G_N$ and a cycle $z$ of $\Gamma_n$,
$$
(T_NF)[\iota_*z]=(1-i_n/i_N)F[\iota_*z]+(i_n/i_N)(T_n(F|_n))[z].
$$
This is `PKey`.

## The small-group cosets

Let $K=O_L/(\pi)$ and $e_0$ be the first coordinate. In $q_m c q_m^{-1}$, the first column below the first entry is divided by $\pi$. Integrality of these entries suffices, as the determinant remains a unit. Thus $J_m$ is the stabilizer of $Ke_0$ after reduction, and $J_mc$ is determined by $K\overline{c^{-1}e_0}$. The index is finite and at least $m$ by coordinate permutations. The small $\Gamma_n$ cosets inject since their intersection with $J_N$ is $\iota J_n$. They are exactly the cosets with the last $d$ coordinates of $\overline{c^{-1}e_0}$ zero. Indeed integral permutations and elementary matrices within the first $n$ coordinates can move the reduced line to $Ke_0$. Since $q_N=\iota q_n$, the sum over these cosets is $i_n(T_n(F|_n))[z]$.

## Stabilizers in the other cosets

Let $X$ be the remaining cosets with right $\Gamma_n$ action. At $x=J_Nc$, the stabilizer $H_x$ consists of $h$ with $c\iota(h)c^{-1}\in J_N$. Choose a coordinate $p$ in the lower block with $v_p$ nonzero modulo $\pi$ for $v=c^{-1}e_0$. Choose $u,s\in O_L$ with $uv_p+\pi s=1$. Put $y=(u/\pi)v+s e_p$ and $A=I+(y-e_p)e_p^{\mathsf T}$. This replaces only the $p$th column and has determinant $y_p=1/\pi$. Then $\delta=q_NcA$ is integral since its altered column is $ue_0+s q_Nc e_p$, and has determinant $\det c$, so $\delta\in\Gamma_N$.

For $h\in H_x$, the conjugate $\alpha(h)=A^{-1}\iota(h)A$ is integral by conjugating $q_Nc\iota(h)c^{-1}q_N^{-1}\in\Gamma_N$ by $\delta^{-1}$. Since the $p$th row and column of $S=\iota(h)$ are those of the identity, direct multiplication gives $\alpha(h)=S+(S-I)y e_p^{\mathsf T}$. This adds only an upper-right column. The affine block theorem `SAff` says that for totally imaginary $L$ and $j<r_2(L)$, the representations $\begin{pmatrix}\alpha_0(h)&B(h)\\0&I_d\end{pmatrix}$ and $\iota\alpha_0(h)$ over $O_L$ give the same images of real $j$-cycles in homology. Apply it on $H_x$. In $q_Nc\iota(h)=\delta\alpha(h)A^{-1}$, left multiplication by $\delta$ disappears by invariance. Right multiplication by $A^{-1}$ just changes the base point for the homogeneous cochain, preserving cycle values by the prism homotopy. Thus the period from this coset agrees with the original on $H_x$.

## Summing over the cosets

For $x=J_Nc$ define $\Phi_x(h_0,\ldots,h_j)$ to be the value of $F$ on $(q_Nc\iota(h_i))_i$ minus its value on $(\iota(h_i))_i$. The left factor $q_NJ_Nq_N^{-1}\subseteq\Gamma_N$ gives independence of the representative. The cochains satisfy $\Phi_{xh}(y)=\Phi_x(hy)$ and the preceding reasoning gives zero on cycles in the stabilizer of $x$.

For such a finite right $\Gamma_n$-set, `PTransfer` says the sum over $x$ vanishes on cycles. For each orbit, a left $H_x$-equivariant retraction $\Gamma_n\to H_x$ is obtained by choosing representatives of $H_x\backslash\Gamma_n$. Its pullback of the restriction is cochain-homotopic to the original via the prism. On the stabilizer, vanishing on cycles makes the cochain a coboundary by linear extension from boundaries. Therefore the original is a coboundary of an $H_x$-invariant cochain. Averaging that primitive over the orbit is $\Gamma_n$-invariant and gives the orbit sum as a coboundary. Summing the orbits proves the assertion. Hence the remaining cosets contribute $(i_N-i_n)F[\iota_*z]$. Add the small-group sum and divide by $i_N$.

## Lean correspondence

- [`PKey` and `PStabVan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PHeckeFormal.lean#L96), [`keyGen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/KeyGenAlt.lean) and [`pKey`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PKey.lean#L13) give the formula.
- [Coset index and column criterion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PermMatrixMulApply.lean#L138) and [`aff_conj`, `aff_gamma` and `pStabVan`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Affine.lean#L61) handle the split and stabilizer calculation.
- [`PTransfer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Transfer.lean#L14) and [`pCobSub`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/TkFcPzTop.lean) give the sum. [`SAff`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean) supplies the affine homology input.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
