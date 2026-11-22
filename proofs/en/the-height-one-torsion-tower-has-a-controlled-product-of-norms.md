# The height-one torsion tower has a controlled product of norms

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $K,\mathcal O,p,F$ have the hypotheses of [the height-one isomorphism](interpolating-torsion-characters-builds-the-height-one-isomorphism.md). Put $P(X)=[p]_F(X)$, an integral series with constant zero and linear coefficient $p$. There exist $t_n$ in the open unit disc with $t_0=0$, $t_1\ne0$ and $P(t_{n+1})=t_n$ for all $n$. Let $G_n$ be the nonzero multiples $[j]_F(t_n)$, $1\le j<p^n$. Then $G_n\subseteq G_{n+1}$, and for $r=|t_1|$,
$$
r^{p-1}=|p|<1,\qquad r\le|x|<1\ (x\in G_n),
\qquad \prod_{x\in G_n}|x|=|p|^n.
$$

### Constructing the points

Use the open-disc root theorem for integral power series. It states that if the least degree with unit coefficient is $l>0$, an integral series over the complete algebraically closed $K$ has a root in the open unit disc. For $P(X)-c$, with $|c|<1$, this least degree is $p$. Thus $P$ maps the disc onto itself. For $P(X)/X$ the least degree is $p-1>0$. Its constant is $p\ne0$, so its small root is nonzero. Take this root for $t_1$ and then choose one preimage at each subsequent level. Since $[p^{n-1}]_F(t_n)=t_1\ne0$ and $[p^n]_F(t_n)=0$, $t_n$ has exact order $p^n$ for the formal group on the disc. Its multiples are distinct modulo this integer. Also $[j]_F(t_n)=[pj]_F(t_{n+1})$, proving the inclusions.

### Products on fibres

For $|c|<1$ the series $P(X)-c$ has integral coefficients and unit degree-$p$ coefficient. Suppose $x_1,\ldots,x_p$ are distinct small roots. Divide successively by their linear factors as in the interpolation proof. The remaining series is integral and has unit constant term, since modulo the maximal ideal the product of the factors is $X^p$ and the degree-$p$ coefficient of $P(X)-c$ is a unit. If $c\ne0$, taking constant terms now gives $\prod_i|x_i|=|c|$. If $c=0$, one factor is $X$; taking linear coefficients gives the same formula on the nonzero factors with $|p|$ in place of $|c|$.

For $c=0$ the roots can be the $p$ points $[j]_F(t_1)$. When $1\le j<p$, the linear coefficient of $[j]$ is the unit $j$, so on the small disc its linear term dominates its integral higher terms. All $p-1$ nonzero roots have norm $r$. This proves $r^{p-1}=|p|$. For a lower-level point $[a]_F(t_n)$, the $p$ points $[a+p^n b]_F(t_{n+1})$, $0\le b<p$, lie in its fibre. They are distinct by exact order. The product of their norms equals the norm of the lower-level point when it is nonzero. The zero fibre contributes $|p|$ after omitting zero. Multiplying over the fibres gives $\prod_{x\in G_{n+1}}|x|=|p|\prod_{x\in G_n}|x|$, starting from the empty product $1$ at $n=0$.

For $x\in G_n$, if $x$ has order $p$ its norm is $r$. Otherwise repeatedly apply $P$ until reaching a nonzero point of order $p$. At every step $P(0)=0$ and integrality imply $|P(x)|\le|x|$, so again $|x|\ge r$. This proves the needed lower bound without requiring the norms of all primitive points to be computed exactly.

### Lean correspondence

- [`exists_torsion_tower`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsFormalGroupHeightOneTorsionTower.lean#L33) applies the open-disc root theorem to $P-c$ and to $P/X$.
- [`prod_fibre`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NormFormalGroupHeightOneTorsionTower.lean#L54) and [`prod_zero_fibre`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NormFormalGroupHeightOneTorsionTower.lean#L84) give the two products. [`tower_norm`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/NormFormalGroupHeightOneTorsionTower.lean#L118) passes to all torsion levels.
- [the exact-order theorem](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/FormalGroupTorsionTowerExactOrderStatement.lean#L7) identifies the distinct multiples. The open-disc root theorem used for existence is [`exists_root_openDisc_of_weierstrassDegree`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsRootOpenDiscOfWeierstrassDegreeStatement.lean#L6).

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
