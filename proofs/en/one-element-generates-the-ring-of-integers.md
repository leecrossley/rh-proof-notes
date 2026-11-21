# One element generates the ring of integers

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E4%B8%80%E4%B8%AA%E5%85%83%E7%B4%A0%E5%B0%B1%E8%83%BD%E7%94%9F%E6%88%90%E5%B1%80%E9%83%A8%E5%9F%9F%E7%9A%84%E6%95%B4%E4%B8%AA%E6%95%B4%E6%95%B0%E7%8E%AF.md)

## Statement

Let $A\subseteq B$ be DVRs with local inclusion, $B$ finite over $A$ and $A$ having finite residue field. Then $B=A[\alpha]$ for some $\alpha\in B$. This applies to $\mathbb Z_\ell\subseteq O_E$ for a finite extension $E/\mathbb Q_\ell$. It supplies the shared integral polynomial coordinates in the [trace argument](integral-trace-is-almost-surjective-in-the-cyclotomic-tower.md).

## Proof

The residue field $k_B$ is finite because it is a quotient of the finite-dimensional $k_A$ vector space $B/\mathfrak m_A B$. Choose $\bar\alpha$ generating $k_B^\times$, hence $k_B$ over $k_A$, and lift to $\alpha_0\in B$. Lift its minimal polynomial to $P\in A[X]$. Then $P(\alpha_0)\in\mathfrak m_B$ and $P'(\alpha_0)$ is a unit by separability. If $P(\alpha_0)\notin\mathfrak m_B^2$, take $\alpha=\alpha_0$. Otherwise add a uniformizer $\pi_B$ to $\alpha_0$. Modulo $\mathfrak m_B^2$ this changes the value by $\pi_B P'(\alpha_0)$, which is nonzero. Thus $A[\alpha]$ contains a lift generating the residue field and a uniformizer $\beta=P(\alpha)$.

Put $C=A[\alpha]$. For any $b\in B$, lift its residue as a polynomial in $\alpha$ to obtain $b=c+\beta b_1$ with $c\in C$. Repeating on $b_1$ gives $B=C+\beta^nB$ for every $n$. A uniformizer of $A$ generates $\beta^e B$ for some $e\ge1$ by the local inclusion. Taking $n=e$ gives $B/C=\pi_A(B/C)$. The quotient is a finite $A$-module, so Nakayama gives $B=C$.

## Lean correspondence

- [`mem_adjoin_mod`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/ProjectiveLattices/AvMono.lean#L14), [`adjoin_eq_top_of_gen`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/ProjectiveLattices/AvMono.lean#L56) and [`exists_adjoin_eq_top`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/ProjectiveLattices/AvMono.lean#L109) give approximation, Nakayama, and the choice of uniformizer polynomial.
- [`exists_generator`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/ExistsTraceNormGe.lean#L50) applies this over $\mathbb Z_\ell$.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
