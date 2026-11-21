# Descending a crystalline lift costs the degree valuation

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E6%8F%90%E5%8D%87%E6%8C%87%E6%95%B0%E5%9C%A8%E6%8D%A2%E5%9B%9E%E5%8E%9F%E5%B1%80%E9%83%A8%E5%9F%9F%E6%97%B6%E5%8F%AA%E5%8A%A0%E6%AC%A1%E6%95%B0%E8%B5%8B%E5%80%BC.md)

Let $K'/K$ be a finite Galois extension of $\ell$-adic local fields, $O$ a coefficient integer ring, and $F:T_1\to T_2$ an equivariant surjection of full stable $O$-lattices in crystalline representations. Write $H_f^1(K,T)$ for integral classes becoming coboundaries after adding crystalline periods. Use naturality of restriction and corestriction for the lattice-to-period maps. If $a\ge0$ and $\ell^aH_f^1(K',T_2)\subset F_*H_f^1(K',T_1)$, then
$$
\ell^{a+v_\ell([K':K])}H_f^1(K,T_2)\subset F_*H_f^1(K,T_1).
$$

**Proof.** For $c\in H_f^1(K,T_2)$, choose $c'\in H_f^1(K',T_1)$ with $F_*c'=\ell^a\operatorname{res}c$. Corestriction preserves finite membership by period naturality, and commutes with $F_*$. To see the degree, set $G=G_K,H=G_{K'}$, take left coset representatives $S$, and write $gt=t_gh(g,t)$ for $t,t_g\in S$, $h(g,t)\in H$. On a cocycle $f$ of $H$, corestriction is $\sum_{t\in S}t_g f(h(g,t))$. For $f=z|_H$, the cocycle equality gives $t_g z(h(g,t))=z(g)+gz(t)-z(t_g)$. Summing and using the permutation $t\mapsto t_g$ gives $[K':K]z(g)$ plus the coboundary of $\sum_t z(t)$. Therefore $F_*\operatorname{cor}c'=\ell^a[K':K]c$. Divide the lift by the prime-to-$\ell$ unit in the degree.

For the project's split cases at $2,3$, the conductor parameter $N$ and common filtration half-width $h$ give $s=\max(1,v_\ell(N))$ and the declared allowance
$$
e_L=32(2hs+1)+s+\lfloor\log_\ell(2h)\rfloor+\lfloor\log_\ell N\rfloor+1,
$$
with integer logarithms at zero taken as zero. `LocNum.exists_up` gives a cyclotomic extension under `Cyc` on which Case B applies, with $v_\ell([K':K])\le\lfloor\log_\ell N\rfloor+1$. The source stays crystalline with jumps in $[-h,h]$, and the Case B cost is at most $32(Hs+1)$, $H\le2h$. The sum of these costs is bounded by $e_L$. Apply the descent both to the original and the dual twist for the column and row bounds.

`coreDesc` gives the general exponent. `UpperTheory.N.liftK_of` uses the extension and Case B, and `lift_exponent_admissible_cols_rows_of_crystalline` applies it twice. The bound in Case B and the extension-degree bound are upstream results here. [Restriction and corestriction](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LiftingTheory.lean#L462) · [Descent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/LiftingTheory.lean#L500) · [Extension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/LocNum.lean#L121) · [Case B](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/SharpRestriction/LevelLetterCocycles/BaseChangePreservesUnitaryOf.lean#L4357) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/LiftKOf.lean#L12) · [Columns and rows](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/LiftExponentAdmissibleColsRowsOfCrystalline.lean#L33) · [Declared exponent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/ResidueCharacters/InvariantsKilledOverCyclotomicAlt.lean#L11)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
