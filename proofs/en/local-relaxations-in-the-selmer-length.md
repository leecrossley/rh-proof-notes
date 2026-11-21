# Adding local relaxations to a Selmer length

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E6%8A%8A%E5%90%84%E5%A4%84%E6%94%BE%E5%AE%BD%E7%9A%84%E6%9D%A1%E4%BB%B6%E5%8A%A0%E5%88%B0Selmer%E9%95%BF%E5%BA%A6%E4%B8%8A.md)

**Proposition.** Let $\mathcal O$ be commutative, $M$ an $\mathcal O$-module with linear action of a group $G$, and $\Psi:H\to Z^1(G,M)$ an $\mathcal O$-linear map. The argument applies to continuous cohomology when the indicated restriction maps are defined. In $H^1=Z^1/B^1$, choose a submodule $Q$. For each $w$ in a finite index set $I$, let $D_w\subseteq G$ be a subgroup with $\mathcal O$-linear restriction, and $F_w\subseteq A_w\subseteq H^1(D_w,M)$ two local conditions. Suppose all classes $[\Psi h]$ belong to $Q$ and have restrictions in $A_w$. Assume the strict Selmer submodule $S_F=\{\xi\in Q:\xi|_{D_w}\in F_w\ \forall w\}$ has length at most $s$, with $\operatorname{length}(A_w/F_w)\le b_w$. Suppose $\operatorname{length}\ker\Psi\le L$ and $\operatorname{length}(\operatorname{im}\Psi\cap B^1)\le B$. Then
$$
\operatorname{length}_{\mathcal O}H\le L+B+s+\sum_w b_w
$$
with extended lengths allowed.

Let $S_A=\{\xi\in Q:\xi|_{D_w}\in A_w\ \forall w\}$. The map $S_A\to\bigoplus_w A_w/F_w$ that records the local classes has kernel $S_F$, so $S_A/S_F$ embeds in the direct sum. Length additivity gives $\operatorname{length}S_A\le s+\sum_w b_w$. Now factor $H\to Z^1\to H^1$. At the first step remove the kernel of $\Psi$, and at the second remove the submodule $\operatorname{im}\Psi\cap B^1$ in its image. The final image lies in $S_A$. Length additivity at both steps proves the bound.

In the application $H=\operatorname{Hom}_A(N,M_c)$ for the column relation module and the $c$th block quotient lattice, and $\Psi(\phi)(g)=\phi(y(g))$. The [column kernel calculation](column-relations-bound-the-kernel-in-three-blocks.md) supplies $L$. The [two-denominator calculation](coboundary-cost-of-two-denominators.md) supplies $B$ for block zero and the higher blocks. Block one has trivial action and $B=0$. The strict global bound $s$ is respectively the Selmer length of the original representation, the class-number valuation from unramified additive characters, or the localization-kernel length for a negative cyclotomic twist. Each requires its own strict local conditions. Columns satisfying the strict condition contribute zero relaxation, and row and specified ramification places supply the remaining $b_w$.

## Lean correspondence

- `selRelax` and `blockRhoAbs` give the local quotient argument and length decomposition. [Length decomposition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthEqKerAddRange.lean) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthKerSmulLe.lean#L147)
- `blockTrivAbs` handles the trivial action with zero coboundaries. [Trivial action](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/BlockChiOneTriv.lean#L35)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
