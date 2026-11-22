# The twist-local test transforms by the quotient determinant

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

### Statement

Let $E$ be a number field, $P$ a nonzero prime of $\mathcal O_E$, $A=\mathcal O_{E,P}$ and $\kappa=A/PA$. Put $q=|\kappa|$, so $q\in PA$. Let $\xi:\kappa^\times\to K^\times$ be a character with values in a coefficient field $K$. Extend it by $\xi_0(0)=0$, and use a bar for reduction of integral entries. Fix source and target dimensions $a,b$ and a cut $0\le r\le\min(a,b)$. On a $b$ by $a$ matrix $X$ over $E$ define the local twist function
$$
\Phi_Q(X)=\xi_0(\det\overline{X_{[r]}})
$$
if every entry of $X$ is integral and every entry below the first $r$ rows in the first $r$ columns belongs to $qA$. Here $X_{[r]}$ is the leading $r$ by $r$ square. If either condition fails, put $\Phi_Q(X)=0$.

In dimension $d=a$ or $d=b$, let the level subgroup consist of $G\in \mathrm{GL}_d(A)$ preserving the sublattice $A^r\oplus q A^{d-r}$. In the corresponding block decomposition let $\bar G_{22}$ be its last diagonal block after reduction. Then $\det\bar G_{22}\ne0$ and, for any source level matrix $G$ and any target level matrix $H$,
$$
\begin{aligned}
\Phi_Q(XG)\,\xi(\overline{\det G})^{-1}&=\xi(\det\bar G_{22})^{-1}\Phi_Q(X),\\
\Phi_Q(HX)\,\xi(\overline{\det H})^{-1}&=\xi(\det\bar H_{22})^{-1}\Phi_Q(X).
\end{aligned}
$$
The right-hand character is the inverse character of the determinant on the quotient by the preserved initial $r$-dimensional subspace. In the project this is `lamQB` and the left-hand factor is `muAt` on local determinant units.

### Proof

The lower-left entries of a level matrix lie in $qA$. To see this, apply it to each basis vector among the first $r$ and use preservation of $A^r\oplus qA^{d-r}$. Thus $\bar G$ is block upper triangular, and its determinant is
$$
\det\bar G=\det\bar G_{11}\det\bar G_{22}.
$$
The full determinant is nonzero because $G$ and its inverse are integral. Both diagonal determinant factors are therefore nonzero. These observations also apply to $H$.

Suppose $X$ passes the support conditions. The lower-left block of $XG$ is $X_{21}G_{11}+X_{22}G_{21}$, an integral matrix with every entry in $qA$ because $X_{21}$ and $G_{21}$ have that property. At the target the corresponding calculation is $H_{21}X_{11}+H_{22}X_{21}$. In particular both products still pass the support conditions. In the leading block, the contribution through the other side of the cut has a factor $G_{21}$ for the source multiplication or $X_{21}$ for the target multiplication. It disappears upon reduction. Thus the leading blocks after reduction are $\bar X_{11}\bar G_{11}$ and $\bar H_{11}\bar X_{11}$. Multiplicativity of determinants and of $\xi_0$ yields
$$
\Phi_Q(XG)=\Phi_Q(X)\xi(\det\bar G_{11}),
\qquad
\Phi_Q(HX)=\xi(\det\bar H_{11})\Phi_Q(X).
$$
This also holds when $\det\bar X_{11}=0$. Dividing by the corresponding full determinant character gives the claimed quotient factors.

The level groups contain the inverses of all their elements. Hence passing the support conditions is equivalent before and after either multiplication, by applying the argument to the inverse. On arguments outside the support both sides vanish.

### Identifying the twist function in the chain

In the chain, in layer $j$, write $n=N_j$ for the ordinary dimension, $c=c(j)$ for the number of extra coordinates and $k_0$ for the insertion index of the extra coordinates. Put $k_j=k_0+j$ at an ordinary step. The twist lattice `parL` in the original coordinates is the standard local lattice with the ordinary coordinates numbered $k_j,\ldots,n-1$ multiplied by $q$. The extra coordinates are left as they are. In the adapted basis `entB` for a twist prime, there are no scaling factors and the extra coordinates are inserted immediately after the first $k_0$ ordinary coordinates. Since $k_0\le k_j\le n$ and $k_j+c=r$ on the ordinary layers, the last $n-k_j$ adapted indices are precisely the scaled coordinates of `parL`. The group `JQ` preserves both the standard lattice and `parL`, so its adapted matrices give the subgroup used in the proof. The last diagonal block is the same minor over the original coordinates $k_j,\ldots,n-1$ that defines `lamQB`.

For the twist function, `PhiAt` chooses `PhiQ` with this leading cut $r$. The determinant factor `muAt` is built with the residue character $\xi^{-1}$ at a twist prime. On the determinant of a level automorphism its valuation is zero, so the factor reduces to $\xi(\overline{\det G})^{-1}$ or its target counterpart. As `entB` respects composition and determinants, these formulas give the twist cases of the full adjacent-step laws.

### Lean correspondence

- [`parL`, `JQ`, `lamQB` and `PhiQ`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L699) give the twist lattice, level, residue character and local test. [`SuppQ.mul` and `SuppQ.det`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L285) prove the support and determinant formulas.
- [`suppQ_of_JQ` and `lamQB_eq`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L607) identify the adapted matrix conditions and its last block. [`detQ`, `phiQ_source` and `phiQ_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L740) give the determinant ratio and the two laws.
- [`PhiAt` and `muAt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/FiniteSumNonzeroLargeDepth.lean#L927) select the local function and determinant character. [`phiAt_source` and `phiAt_target`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/PhiMapsAndOmegaLaw.lean#L819) use the formulas when $i+2\le m$.

Status. Source-based reconstruction draft. Together with the [type-local character law](the-type-local-test-transforms-by-its-flag-character.md), these are the local determinant calculations before unfolding the ordinary point kernel. See the [Lean verification record](../../STATUS.md#lean-verification--lean-核验).
