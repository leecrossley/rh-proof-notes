# One determinant bounds the congruence ideal by the block lengths

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E4%B8%80%E4%B8%AA%E8%A1%8C%E5%88%97%E5%BC%8F%E6%8A%8A%E5%90%8C%E4%BD%99%E7%90%86%E6%83%B3%E7%9A%84%E9%95%BF%E5%BA%A6%E5%88%86%E7%BB%99%E5%90%84%E5%9D%97.md)

Let $\mathcal O$ be a DVR with fraction field $K$ and residue field $k$. Let $p:X'\to X$ be a map, $Z\subseteq X$, $\pi'\in X'$ and $\pi=p(\pi')$. Let $\mathbb T\subseteq\mathcal O^X$ and $\mathbb T'\subseteq\mathcal O^{X'}$ be $\mathcal O$-algebras. Suppose $b_1,\dots,b_q\in\mathcal O^{X'}$ satisfy:

1. Every $f'\in\mathbb T'$ can be written $\sum_j(a_j\circ p)b_j$ with $a_j\in\mathbb T$.
2. For $x\notin Z$, the functions $b_j$ restricted to $p^{-1}(x)$ are $\mathcal O$-linearly independent.

Take an $\mathcal O$-subalgebra $A\subseteq\prod_{x'\in X'}M_d(K)$. The evaluation action on $K^d$ gives the left $A$-module $V_{x'}$. Let $N$ be a finitely presented left $A$-module with $g$ generators and $m$ relations, recorded by the $m\times g$ matrix $P$. Assume:

1. For every $g\times g$ matrix over $A$, the function of the expanded $gd\times gd$ determinants at $x'$ belongs to $\mathbb T'$.
2. For each $p(x')\notin Z$, there is a nonzero $A$-linear map $N\to V_{x'}$.
3. Evaluation at $\pi'$ takes values in $M_d(\mathcal O)$ and has a common ordered block-triangular form. Each diagonal block map $\rho_c:A\to M_{d_c}(\mathcal O)$ is surjective, and $|k|>g\sum_cd_c$.

**Proposition.** Let $M_c=(K/\mathcal O)^{d_c}$ with action via $\rho_c$, and let $\mathfrak c_\pi$ be the values at $\pi$ of members of $\mathbb T$ vanishing off $Z$. Then
$$
\operatorname{length}_{\mathcal O}(\mathcal O/\mathfrak c_\pi)
\le\sum_c\operatorname{length}_{\mathcal O}\operatorname{Hom}_A(N,M_c)
\tag{1}
$$
with extended lengths.

A map from $N$ to any left $A$-module is given by a tuple of generator images $v$ with $Pv=0$. This identifies the Hom in (1) with the kernel of $P_c$ on the quotient lattice. The [simultaneous kernel lemma](one-integral-matrix-keeps-all-block-kernels.md) gives $C\in M_{g,m}(A)$ such that $(CP)_c$ has the same kernel as $P_c$ on every block quotient. Let $f'\in\mathbb T'$ be the determinant function of $CP$. At any $x'$ above a point outside $Z$, (2) of the matrix hypotheses supplies a nonzero tuple $v$ killed by $P$, hence $CP$ is singular and $f'(x')=0$.

Write $f'=\sum_j(a_j\circ p)b_j$. Above $x\notin Z$ the independence on the fiber forces each $a_j(x)=0$. Consequently $a_j(\pi)\in\mathfrak c_\pi$ and $f'(\pi')\in\mathfrak c_\pi$. For any $a\in\mathfrak c_\pi$, the surjection $\mathcal O/(a)\to\mathcal O/\mathfrak c_\pi$ bounds the latter length by $\operatorname{ord}(a)$, with $\operatorname{ord}(0)=\infty$.

At $\pi'$ the block order reindexes the matrix into block-triangular form with diagonal blocks $(CP)_c$. The valuation of the determinant is the sum of their determinant valuations. For any square integral matrix $B$, its determinant valuation equals the length of its kernel on $(K/\mathcal O)^n$: use Smith normal form, where each nonzero diagonal entry $b$ contributes $b^{-1}\mathcal O/\mathcal O$ of length $\operatorname{ord}(b)$ and a zero entry gives infinite length. Thus $\operatorname{ord}(f'(\pi'))$ is the sum of the quotient-kernel lengths for $(CP)_c$, hence for $P_c$. This proves (1).

The [column relations](column-dimension-detects-outside-representations.md) supply the maps off $Z$. If $N$ is given only as finitely generated and $A$ is left Noetherian, choose generators of the relation submodule for the presentation. The [coefficient-extension argument](congruence-length-after-residue-extension.md) handles a small residue field by descending the length inequality from a larger one.

## Lean correspondence

- `finPres`, `homEquiv` and `kerHomRect` identify the maps with relations. `descent`, `vccSpan` and `lenKer` give the determinant and length comparison. [Kernel](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/GenFin.lean#L172) · [Descent](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/VccSpan.lean#L7) · [Length](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/LengthKerOfDetEqZero.lean#L214)
- `globalConcrete_of` proves (1), and `globalModule` gives the finite-generation formulation used by `lemma_five_three_holds`. [Comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/GlobalConcreteOf.lean#L75) · [Module form](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/CharacterColumnKernels/IdempotentNormalForms/GlobalModuleOf.lean#L43) · [Application](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WachLatticeTwists/RamifiedBlockRings/RamifiedBlockProofs/IdempotentImageSurjective.lean#L133)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
