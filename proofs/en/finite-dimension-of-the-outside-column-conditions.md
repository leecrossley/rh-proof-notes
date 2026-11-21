# The finite dimension of column conditions at an outside point

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%A4%96%E7%82%B9%E7%9A%84%E5%88%97%E6%9D%A1%E4%BB%B6%E5%8F%AA%E5%8D%A0%E6%9C%89%E9%99%90%E4%B8%AA%E7%BB%B4%E6%95%B0.md)

Fix a prime $\ell$, a finite extension $K_w/\mathbb Q_\ell$ and a coefficient field $L/\mathbb Q_\ell$ containing the images of all embeddings of $K_w$, with integers $\mathcal O$ and $G=G_{K_w}$. Let $A$ be an $\mathcal O$-algebra with action elements $u(g)\in A^\times$, in the project $u(g)=\chi_1(g)^{-1}r(g)$. Let $V_x$ be the $L$-representation at an evaluation point and $W$ the local restriction of the good-point large block twisted by $\chi_1^{-1}$. Assume both are continuous crystalline, with $\operatorname{Fil}^bD_{\rm dR}$ the whole period space for sufficiently small $b$, and with the Bloch–Kato dimension formula and finiteness of $H^1_f$. For every embedding $\tau:K_w\hookrightarrow L$ and $a<0$, assume their $\operatorname{gr}^a$ dimensions agree. Assume $W^G=0$.

**Proposition.** Let $L_x\subseteq \operatorname{Map}(G,V_x)$ consist of continuous cocycles $z$ such that there is $\xi\in V_x\otimes_{\mathbb Q_\ell}B_{\rm cris}$ with $z(g)\otimes1=g\xi-\xi$ for all $g$. Let $B_x$ be the subspace of coboundaries from $V_x$ and $j=\dim_LH^1_f(G,W)$. Then $B_x\subseteq L_x$ and $\dim_L(L_x/B_x)=j+\dim_L V_x^G$. Furthermore, if $P$ is an $A$-module with action via $u(g)$ and $f:P\to V_x$ is $A$-linear, the pointwise image of each integral cocycle with finite class in $L\otimes_{\mathcal O}P$ lies in $L_x$. This applies to $P=Ae_1$ and $P=AE$ with the stipulated continuous local actions.

For a coboundary of $v$, choose the period vector $v\otimes1$. The quotient $L_x/B_x$ is $H^1_f(G,V_x)$ by its crystalline definition. The group identification of $G$ with the global decomposition group and the coefficient identifications preserve these spaces, because precomposition carries both cocycles and coboundaries to the corresponding functions. The project map `colD` sends vectors to coboundaries, with kernel $V_x^G$.

For functoriality, extend $f$ to an equivariant $L$-linear $f_L$ on $P_L=L\otimes_{\mathcal O}P$. A period vector witnessing finiteness for a representative is sent by $f_L\otimes1$ to the witnessing vector for its image. Replacing the representative by a cohomologous cocycle changes the evaluated cocycle by a coboundary, already in $L_x$. The evaluated function is continuous by the linear maps in the finite-dimensional local comparison. Thus the original representative itself evaluates to a member of $L_x$.

For a crystalline $U$, the Bloch–Kato formula is
$$
\dim_L H^1_f(G,U)=\dim_L U^G+
\sum_\tau\dim_L(D_{{\rm dR},\tau}(U)/\operatorname{Fil}^0).
$$
For a common sufficiently small $b\le0$, the quotient dimension at $\tau$ is $\sum_{a=b}^{-1}\dim_L\operatorname{gr}^a D_{{\rm dR},\tau}(U)$ by telescoping adjacent filtration dimensions. These sums match for $V_x,W$, and $W^G=0$. This gives the dimension formula in the proposition. It is the bound used by the [column relation construction](column-dimension-detects-outside-representations.md): if the coboundary map has no kernel, the column has $j+1$ coefficients for a $j$-dimensional quotient, and a nonzero kernel vector of the coboundary map itself suffices in the other case.

At the good point the twisted representation splits as $W$ and the lines $\chi_c/\chi_1$. Crystalline periods commute with finite direct sums, and their dimensions are bounded by the representation dimensions. Since equality holds for the full crystalline representation, it holds on each summand. The project `admG2` gives jumps $c-1\ge0$ on the character lines, so the negative grades of the full twist match those of $W$. The same hypothesis fixes the graded dimensions across points and gives $W^G=0$. Normalized evaluations are isomorphic to the originals, so the agreement persists.

## Lean correspondence

- `finiteCocycles` uses the period-vector condition, and `colD_le_Lx` and `comp_mem_Lx` treat coboundaries and evaluated cocycles. [Definition](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/WeaklyAdmissibleFiltrations/Statement.lean#L190) · [Evaluation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/FiniteClassesContinuousLattice.lean#L599)
- `rank_finQuot`, `finrank_invariants_eq` and `count_eq` give the dimension; `rank_le_count` gives the cardinal rank bound. [Dimension](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/CohomZeroEquivContinuous.lean#L211)
- `wp_font`, `negX_of` and `colLx` turn the filtration data into the prescribed column space. [Weights](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/IsDROfWpIso.lean#L245) · [Column space](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/AdmissibleDesigns/ColLx.lean#L32)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
