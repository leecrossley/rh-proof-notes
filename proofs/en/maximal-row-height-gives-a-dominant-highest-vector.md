# Maximal row height gives a dominant highest vector

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $k$ be any field, $N\ge0$, and $R=k[x_{as}:1\le a,s\le N]$. Write $E_{ab}=\sum_s x_{as}\partial/\partial x_{bs}$. The row weight of a monomial is the list of its total degrees in the $N$ rows. Let $M\subsetneq M'$ be linear subspaces of $R$, each preserved by all $E_{ab}$, by taking any row-weight component, and by every permutation of the rows. Suppose that the monomials in all elements of $M'$ have total degree bounded by a common $c$. Then there exist $\mu_1\ge\cdots\ge\mu_N\ge0$ and a nonzero row-homogeneous $v\in M'\setminus M$ of weight $\mu$ such that $E_{ab}v\in M$ whenever $a<b$. In particular the class of $v$ in $M'/M$ is a highest vector for the operators $E_{ab}$, with diagonal eigenvalues $\mu_a$ read in $k$.

Start with an element of $M'\setminus M$. At least one of its row-weight components lies in $M'\setminus M$, since all the components lie in $M'$ and their sum would lie in $M$ if each did. Among the available weights choose one maximizing
$$
H(\mu)=\sum_{a=1}^N(N+1-a)\mu_a.
$$
The bound $H(\mu)\le Nc$ ensures a maximum. If $a<b$ but $\mu_a<\mu_b$, interchange the two rows of $v$. The resulting vector is in $M'$ and is outside $M$, since the transposition acts invertibly on $M$. Its height increases by $(b-a)(\mu_b-\mu_a)>0$. Thus $\mu$ is decreasing. If $E_{ab}v$ is nonzero for $a<b$, every monomial surviving differentiation has row weight $\mu+e_a-e_b$. Membership in $M'\setminus M$ would increase the height by $b-a$, so the result belongs to $M$. Finally $E_{aa}$ acts on each monomial by its degree in row $a$, hence $E_{aa}v=\mu_a v$.

### Applying the height argument to the dual Weyl space

For a decreasing list $\nu_1,\ldots,\nu_N$ of nonnegative integers, let $\nabla_k(\nu)$ be the polynomials of column weight $\nu$ invariant under adding a formal multiple of column $l$ to column $j$, for $l<j$. The invariance is a polynomial identity in the multiple. The standard monomial span theorem used here says that this space is spanned by products of minors in the first $s$ columns and $s$ chosen rows, with $\nu_s-\nu_{s+1}$ factors of size $s$ and $\nu_{N+1}=0$. Indeed the theorem specifies that the number of factors of size at least $s$ is $\nu_s$. In every nonzero product each minor has distinct chosen rows. It is homogeneous in row weights, and at most $\min(j,s)$ entries of a size-$s$ minor belong to the first $j$ rows. Consequently a monomial of row weight $\mu$ in $\nabla_k(\nu)$ satisfies
$$
\sum_{a\le j}\mu_a\le\sum_{a\le j}\nu_a,\qquad
\sum_a\mu_a=\sum_a\nu_a .
$$
In particular one may take $c=\sum_a\nu_a$ whenever $M'\subseteq\nabla_k(\nu)$.

This span also explains the highest-weight line. With row weight exactly $\nu$, all the prefix inequalities are equalities. Each factor of size $s$ must reach the bound at $j=s$, so it uses precisely the first $s$ rows. Its determinant is the top-left size-$s$ minor $\Delta_s$, up to sign. Thus the row-weight-$\nu$ subspace is the line on
$$
h_\nu=\prod_{s=1}^N\Delta_s^{\nu_s-\nu_{s+1}} .
$$
This polynomial is in $\nabla_k(\nu)$ by the column operations, and its value at the identity is one. These statements include $N=0$ with empty products and sums.

### Lean correspondence

- [`exists_dominant_highest_vector_of_lt`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/ExistsDominantHighestVectorOfLtStable.lean#L77) makes the maximal-height choice.
- [`rowE` and `Good`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Definitions/GlobalTwisting/GoodTopBot.lean#L22) give the operators and the three stability assumptions.
- [`standardMonomialSpanDomain`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/GradedWeylDivisibility/FinalC.lean#L37) is the spanning theorem used here. The row-degree conclusion is [`rowDeg_dominated_of_mem_dualWeyl`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/RowDegDominatedOfMemDualWeylModule.lean#L12).
- [`hw_line_field`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/GlobalInterpolation/DualWeylHighestWeightSpaceLineField.lean#L62) proves the same line in Lean by passing to the algebraic closure and descending its scalar.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
