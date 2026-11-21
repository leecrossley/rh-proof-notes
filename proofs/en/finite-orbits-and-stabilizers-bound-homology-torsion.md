# Finite orbits and stabilizers bound homology torsion

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E6%9C%89%E9%99%90%E8%BD%A8%E9%81%93%E5%92%8C%E7%A8%B3%E5%AE%9A%E5%AD%90%E6%95%B0%E5%87%BA%E7%BE%A4%E5%90%8C%E8%B0%83%E6%89%AD%E7%BB%93.md)

## Statement

Let $G$ be a group and $P_i=\mathbb Z[X_i]$ permutation modules with equivariant differentials $d_i:P_{i+1}\to P_i$ and surjective augmentation $P_0\to M$, exact at $P_0,\ldots,P_m$. Let $m,A\ge0$ and $s,b\ge1$ be integers. For each $i\le m$ assume $X_i$ has at most $A$ orbits, each with finite stabilizer of order at most $s$. For any generator $[x]$ of $P_{m+1}$ assume the sum of absolute coefficients of $d_m[x]$ is at most $b$. Then
$$
|\operatorname{Tor}H_m(G,M)|\le b^A s^{mAs^m}
$$
and the torsion is finite. With trivial $\mathbb Z$ coefficients and alternating face deletions one may use $b=m+2$.

## Proof

On one orbit with stabilizer $S$, the permutation module is induced from the trivial $S$-module. By Shapiro its positive-degree homology is $H_j(S,\mathbb Z)$. Transfer through the trivial group kills this by $t=|S|$, since restriction to the trivial subgroup followed by the map back multiplies by $t$ and the intermediate positive-degree homology is zero. The bar group in degree $j$ has rank $t^j$, so its cycle subgroup and the homology require at most $t^j$ generators. This gives order at most $t^{t^j}\le s^{s^j}$. Summing over the orbits bounds $|H_j(G,P_i)|$ by $s^{As^j}$ for $i\le m$ and $j>0$.

For $m=0$, coinvariants are right exact, so $H_0(G,M)$ has the $a\le A$ orbits of $X_0$ as generators and images of the $d_0[x]$ as relations. Taking orbit sums does not increase their $\ell^1$ lengths. From the relations choose a maximal rationally independent subset giving a lattice $\Lambda_0$ of rational span $V$, and add standard basis vectors to obtain a full-rank lattice $\Gamma$ in $\mathbb Z^a$. With $\Lambda$ the lattice of all relations, the torsion is $(V\cap\mathbb Z^a)/\Lambda$. Independence of the added vectors modulo $V$ gives $\Gamma\cap V=\Lambda_0$, so $(V\cap\mathbb Z^a)/\Lambda_0$ injects into $\mathbb Z^a/\Gamma$. Hadamard bounds the index of $\Gamma$ by $b^a$: each column's Euclidean norm is bounded by its $\ell^1$ norm, and added columns have length one. Passing to the quotient by $\Lambda$ can only decrease the order. This proves the base case.

For $m\ge1$ put $K=\ker(P_0\to M)$. The shifted resolution of $K$ starting at $P_1$ meets the hypotheses in degree $m-1$ with the same $b$. The sequence
$$
H_m(G,P_0)\longrightarrow H_m(G,M)\longrightarrow H_{m-1}(G,K)
$$
from the short exact sequence bounds the torsion in the middle by the size of the left group times the torsion size on the right. Insert $s^{As^m}$ and the induction bound $b^A s^{(m-1)As^{m-1}}$. Since $s^{m-1}\le s^m$, this is at most the claimed bound.

## Lean correspondence

- [`shift` and `mainFace`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/TorsionBoundsChains/LogLeExp.lean#L12), [orbit homology](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/TorsionBoundsChains/PermTrans.lean#L9), [permutation counts](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/TorsionBoundsChains/PermCard.lean#L12), and [finite group homology](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/TorsionBoundsChains/FinGroup.lean) give the induction.
- [Coinvariants](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/TorsionBoundsChains/Imports.lean#L9) and [lattice torsion](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/TorsionBoundsChains/CokerTors.lean#L11) handle the base case.
- [`tors_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/HermiteNormalForms/Assembly.lean#L25) applies this to [arithmetic group orbits and stabilizers](hermitian-forms-bound-matrix-group-torsion.md).

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
