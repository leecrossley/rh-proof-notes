# Hecke periods cannot decay at rate three fifths

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88Hecke%E5%91%A8%E6%9C%9F%E4%B8%8D%E8%83%BD%E4%BB%A5%E4%BA%94%E5%88%86%E4%B9%8B%E4%B8%89%E8%A1%B0%E5%87%8F.md)

## Statement

Let $L$ be totally imaginary, $1\le j<r_2(L)$, and $\pi\in O_L$ a prime element. Put $\Gamma_N=\mathrm{GL}_N(O_L)$, $G_N=\mathrm{GL}_N(L)$, $q_N=\operatorname{diag}(\pi,1,\ldots,1)$, $J_N=\Gamma_N\cap q_N^{-1}\Gamma_Nq_N$ and $i_N=[\Gamma_N:J_N]$. On invariant homogeneous real $j$-cochains on $G_N$, $T_N$ averages left multiplication of all entries by $q_N\gamma$ over $J_N\backslash\Gamma_N$. Write $F[z]$ for the period on a real bar cycle in $\Gamma_N$. Above a fixed rank $N_0$, if $F$ is a cocycle and every $j$-cycle $z$ satisfies $|(T_N^rF)[z]|\le C_z(3/5)^r$ for all $r\ge0$, then all $F[z]$ vanish. This is `SHecke` in the [invariant-form argument](hecke-iteration-represents-cycle-integrals-by-invariant-forms.md).

## Proof

Fix $n=2j+4$. By homological stability, $H_j(\Gamma_n,\mathbb R)\to H_j(\Gamma_N,\mathbb R)$ is an isomorphism for $N\ge n$. This homology is finite dimensional and `SFin` gives generating cycles $z_1,\ldots,z_s$. On $\Gamma_n$-invariant cocycles $H$ on $G_n$, put $P(H)=(H[z_i])_i$ and $Q(H)=((T_nH)[z_i])_i$. If $P(H)=0$, the restricted cohomology class is zero. The restriction, conjugation, and transfer description of Hecke averaging preserves this zero class, as `PHeckeKer` shows for any finite-index double coset of the indicated form. Thus $\ker P\subseteq\ker Q$, giving a linear map $\operatorname{im}P\to\mathbb R^s$ with operator norm $K$ in the maximum norm. This $K$ depends on the fixed small rank.

For $N=n+d$ with $d\ge1$, the [double coset calculation `PKey`](two-contributions-to-the-hecke-period-average.md) says
$$
(T_NF)[\iota z]=(1-i_n/i_N)F[\iota z]+(i_n/i_N)(T_n(F|_n))[z]
$$
for stabilized cycles $\iota z$. The $i_n$ cosets from the small group give the second term. All remaining cosets transfer the original period, using the affine block comparison on their stabilizers. The finite index satisfies $i_N\ge N$, so for $N\ge n+1+\lceil5(1+K)i_n\rceil$ set $a=i_n/i_N$ with $a(1+K)\le1/5$.

Apply the formula to $F_r=T_N^rF$, which is still invariant and closed because the average commutes with the homogeneous differential. For $x_r=(F_r[\iota z_i])_i$ we have $x_{r+1}=(1-a)x_r+aQ(F_r|_n)$ with $\|Q(F_r|_n)\|\le K\|x_r\|$. The reverse triangle inequality gives $\|x_{r+1}\|\ge(4/5)\|x_r\|$. Induction gives $\|x_r\|\ge(4/5)^r\|x_0\|$, while the finitely many assumed period bounds give $\|x_r\|\le C(3/5)^r$. Letting $r\to\infty$ in $\|x_0\|\le C(3/4)^r$ gives $x_0=0$. Since the stabilized cycles generate homology, every original period vanishes.

## Lean correspondence

- [`SHecke`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/SBridgeAlt.lean#L73) states the criterion and [`ActLPos`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/ActLPos.lean#L42) defines the average and the diagonal element.
- [`PHeckeKer`, `PIndex` and `PKey`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PHeckeFormal.lean#L67) give transfer, index and the two contributions. [`pKey`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PKey.lean#L13) proves the comparison.
- [Norm estimate and decay](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Assemble.lean#L119) assemble [`sHecke_of`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/SHeckeOf.lean#L9). [Transfer of the zero class](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/Formal.lean#L108) and [the index](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/LiteratureResults/KTheoryStability/ReductionBoundsTorsion/HeckeDoubleCosets/PermMatrixMulApply.lean#L177) give its first inputs.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
