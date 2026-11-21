# Cancelling denominators proves uniqueness of Wach lattices

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%A4%E4%B8%AAWach%E6%A0%BC%E5%9C%A8%E6%B6%88%E5%8E%BB%E5%88%86%E6%AF%8D%E5%90%8E%E5%BF%85%E9%A1%BB%E7%9B%B8%E7%AD%89.md)

Use $A,U,X,Q,\gamma,\varphi$ from the [matrix divisibility lemma](matrix-divisibility-through-the-cyclotomic-levels.md), so that $\varphi(X)=XQ$. Let $\mathcal D$ be an $A$-module with corresponding semilinear operators, on which multiplication by $X$ is injective. Suppose $M,M_1\subset\mathcal D$ are free of the same finite rank $r$. For each $N\in\{M,M_1\}$, assume $(\gamma-1)N\subset UN$ and, for each $v\in N$, there are exponents $k,j\ge0$ with $Q^k\varphi(v)\in N$ and $Q^jv\in A\varphi(N)$. If $X^aM_1\subset M$ and $X^a M\subset M_1$ for some $a\ge0$, then $M=M_1$.

**Proof.** Take row bases $b,b_1$ and a matrix $B$ with $X^a b_1=bB$. Write $\gamma(b)=bG$ and $\gamma(b_1)=b_1G_1$, where $G,G_1\equiv I\bmod U$. Apply $\gamma$ to $X^a b_1=bB$, multiply by $X^a$ and compare coordinates in $b$. This gives
$$
X^aG\gamma(B)=\gamma(X)^a B G_1.
$$
Choose common exponents on the two finite bases so that $Q^h\varphi(b)=bF$, $Q^{h_1}\varphi(b_1)=b_1F_1$. The reverse Frobenius condition gives $\varphi(b_1)F'_1=Q^e b_1$ for a common $e$, since the Frobenius images of a basis generate the span. Hence $F_1F'_1=Q^{h_1+e}I$. Applying $\varphi$ to $X^ab_1=bB$, multiplying by $Q^{h+h_1} X^a$, and cancelling $X^a$ in $\mathcal D$, yields
$$
(Q^{h_1}F)\varphi(B)=Q^{a+h} B F_1 .
$$
All hypotheses of matrix divisibility now hold, so $B=X^aB_0$ over $A$. Cancel $X^a$ in the original basis relation to get $b_1=bB_0$, hence $M_1\subset M$. Exchange the roles to obtain equality.

Equal finite rank follows in the application from both bases becoming bases of the same module over a nonzero scalar extension. One lattice there is the target Wach lattice and the other is the double saturation of the image. The two initial inclusions after powers of $X$ are supplied by a separate comparison. [One inclusion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachModuleUniquenessCharacterisation.lean#L162) · [Equality](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachModuleUniquenessCharacterisation.lean#L247) · [Comparison after inverting $X$](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/WachFreeLatticeEqWachLatticeInvertX.lean#L235)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
