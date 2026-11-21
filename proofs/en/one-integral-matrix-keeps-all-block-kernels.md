# One integral matrix preserves the relation kernels in every block

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E5%90%8C%E4%B8%80%E7%BB%84%E6%95%B4%E7%B3%BB%E6%95%B0%E4%BF%9D%E4%BD%8F%E6%AF%8F%E4%B8%AA%E5%9D%97%E7%9A%84%E5%85%B3%E7%B3%BB%E6%A0%B8.md)

**Proposition.** Let $\mathcal O$ be a DVR with fraction field $K$ and residue field $k$, and let $A$ be a ring with central coefficients $\mathcal O$. For an $m\times g$ matrix $P$ over $A$, let $P_c$ be its $md_c\times gd_c$ scalar matrix after applying a surjective map of $\mathcal O$-algebras $\rho_c:A\to M_{d_c}(\mathcal O)$. The index $c$ ranges over a finite set $J$. If $|k|>g\sum_c d_c$, there exists a $g\times m$ matrix $C$ over $A$ such that for every $c$,
$$
\ker((CP)_c:(K/\mathcal O)^{gd_c}\to(K/\mathcal O)^{gd_c})
=\ker(P_c:(K/\mathcal O)^{gd_c}\to(K/\mathcal O)^{md_c}).
\tag{1}
$$

For a fixed block, Smith normal form gives $U_c\in\mathrm{GL}_{md_c}(\mathcal O)$ such that $Y_c=U_c^{-1}P_c$ is supported on a set $F_c$ of $n_c\le gd_c$ rows. Choose $n_c$ output rows $E_c$. If an integral $gd_c\times md_c$ matrix $B$ has
$$
\det((BU_c)_{E_c,F_c})\in\mathcal O^\times,
\tag{2}
$$
then $BP_cv=0$ implies $BU_cY_cv=0$. On the rows $E_c$ the selected minor can be inverted over $\mathcal O$, so $(Y_cv)_{F_c}=0$, yielding $P_cv=0$. The reverse inclusion is immediate. Condition (2) is achievable in one block by taking the $E_c$ rows of $B$ equal to the $F_c$ rows of $U_c^{-1}$ and the other rows zero. For $n_c=0$ the empty minor is $1$.

For simultaneous choice, take original elements of $A$ mapping to the matrix units in each block, and put each in turn in each one of the $g\times m$ positions with other entries zero. Denote the resulting finite list by $C_j$. For $C(\mathbf x)=\sum_j x_jC_j$ and any fixed $c$, its evaluation can realize any $B$ by using coefficients in $\mathcal O$ on the part of the list for $c$. Let $Q_c(\mathbf x)$ be the reduction modulo the maximal ideal of the minor in (2) for $C(\mathbf x)_c$. Its degree is at most $n_c$ and it is a nonzero polynomial since a unit value is achievable. Their product is nonzero and has degree at most $g\sum_cd_c$. Over $k$, a polynomial of total degree at most $D$ cannot vanish on the full Cartesian power of a set of more than $D$ elements unless it is zero. Induct on the number of variables using the one-variable root bound on each fiber. Thus there is a point of $k$ at which all $Q_c$ are nonzero. Lifting its coordinates to $\mathcal O$ yields a single $C$ with (2) in each block. This proves (1).

## Lean correspondence

- `gen_key` gives the minor criterion using Smith normal form. `genericFin` constructs the simultaneous matrix. [Criterion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/GenRelMapApply.lean#L29) · [Simultaneous choice](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/GenFin.lean#L29)
- `globalConcrete_of` uses (1) for the congruence ideal. The [residue extension](congruence-length-after-residue-extension.md) handles smaller residue fields. [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/GlobalConcreteOf.lean#L75)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
