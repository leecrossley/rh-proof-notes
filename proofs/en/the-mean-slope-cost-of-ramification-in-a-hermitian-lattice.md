# The mean slope cost of ramification in a Hermitian lattice

[Chinese proof](../zh/%E5%88%86%E6%AD%A7%E6%9D%A1%E4%BB%B6%E6%80%8E%E6%A0%B7%E6%94%B9%E5%8F%98%E8%B5%AB%E7%B1%B3%E7%89%B9%E6%A0%BC%E7%9A%84%E5%B9%B3%E5%9D%87%E6%96%9C%E7%8E%87.md)

## Statement

Let $K$ be a totally imaginary number field and $W$ a full Hermitian $\mathcal O_K$-lattice of rank $r>0$ in the $K$-space $V$. Thus $W$ is finitely generated and spans $V$, with a positive definite Hermitian metric at each infinite place. Let $I$ be finite, $T\ge3$ an integer, and $G=\prod_{v\in I}G_v$ with each $G_v$ a group of order $T-1$. Suppose a Hermitian lattice $B$ has coordinates $\Psi:V^G\hookrightarrow V_B$ taking $W^G$ onto $B$ and giving the orthogonal sum metric at every infinite place. Let $U\subset V^G$ consist of functions summing to zero on every coordinate line and set $B_{\mathrm{ram}}=B\cap\Psi(U)$ with the induced metric. In the project's slope normalization,
$$
\mu(B_{\mathrm{ram}})=\mu(B)-|I|\frac{\log(T-1)}{T-2}.
$$
This is the lattice statement of `slope_ramified_induced_prime_field`, with `InducedLattice` supplying the coordinates. [Use in the quotient slope](quotient-slope-bounds.md)

## The integral coordinates and their Gram matrix

Put $s=T-2$ and $J=\prod_{v\in I}(G_v\setminus\{1\})$. For $b\in J$ put $P_b(g)=\prod_v(e_{b_v}-e_1)(g_v)$, using point indicators in each factor. Every $F\in U$ has a unique expansion $\sum_b P_b F(b)$. On $J$ these functions are point indicators, and at a point with an identity coordinate, the zero-sum relation in that coordinate determines the value by points with fewer identity coordinates. The coefficients of $P_b$ are integers, so $F(b)\in W$ for every $b\in J$ suffices for integrality at every $g$. Thus $B_{\mathrm{ram}}$ is the image of the whole $W^J$ under these coordinates, with no extra index. [The coordinate-line argument](rank-of-the-ramified-subspace-under-a-free-action.md)

In the coordinate metric, the matrix of inner products of the $P_b$ is $M=\bigotimes_{v\in I}(I_s+J_s)$, where $J_s$ has all entries one. Indeed $\langle e_a-e_1,e_b-e_1\rangle=\mathbf 1_{a=b}+1$ in each factor. The all-ones direction has eigenvalue $s+1=T-1$ and its perpendicular complement has eigenvalue one. For $m=|J|=s^{|I|}$, each factor contributes the all-ones direction to exactly $m/s$ tensor basis vectors. Thus $\log\det M=|I|(m/s)\log(T-1)$. For $I=\varnothing$ the tensor matrix is $(1)$ and the log determinant vanishes.

## Compute the slope

Choose a $K$-basis from $W$ spanning a free sublattice of index $j$, with Gram matrices $D_w$ at the $n_\infty$ infinite places. The project's height is $\operatorname{ht}(W)=\prod_w\det D_w/j$ and its slope is $-\log\operatorname{ht}(W)/(n_\infty r)$. The basis given by the $P_b$ times the basis vectors of $W$ has index $j^m$ in the ramified lattice. At $w$ it has Gram matrix $M\otimes D_w$, with determinant $(\det M)^r(\det D_w)^m$. Consequently
$$
\log\operatorname{ht}(B_{\mathrm{ram}})=m\log\operatorname{ht}(W)+n_\infty r\log\det M,
\qquad
\mu(B_{\mathrm{ram}})=\mu(W)-\frac{\log\det M}{m}.
$$
The corresponding calculation for the full orthogonal sum gives $\mu(B)=\mu(W)$. Substituting the determinant proves the claim.

## Arithmetic realization and source

Take the level-zero forms lattice $B=(D.\mathrm{fm}(u)).\mathrm{lat}(0)$ and the auxiliary prime $T$ totally split in the chosen base field. The index $v$ runs over its places, and $G_v$ is the residue-field unit group. Choose a representative of each orbit of the class set and take $V$ to be the forms supported on those representatives. Translation by $\rho(g)$ puts this space on the corresponding translated classes. The free action makes the supports disjoint. Forms split into summands by class, integrality is tested class by class and preserved in both directions by the unit operators, and disjoint supports are orthogonal with each translation an isometry. This gives the required $\Psi$ by summing $\rho(g)F(g)$ over $g$. Applying the sum of the $G_v$-operators to these coordinates sums along the $v$-lines, so the common kernel is the ramified subspace.

- `induced_lattice_map_sz` and `majorant_kronecker_map` identify the integral lattice and the metric in `slope_ramified_induced_prime_field`. `mu_eq_log_ht`, `kron_mu` and `log_det_szGram_div` perform the height and determinant calculation. [Induced lattice and slope](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL6/DiagonalSlopes/SlopeRamifiedInducedPrimeField.lean) · [Height and tensor determinants](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/Columns/SliceIntegralDeltaNeBot.lean)
- `slice_map_bijective`, `slice_mem_lattice_iff` and `slice_summands_orthogonal` give the zero-level coordinates. `slope_formula_of_diamonds` specializes the formula using the splitting, stabilizer, integrality and unit action inputs. [Arithmetic specialization](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Formalism/LocalToGlobal/GlobalTheory/GL6/DiagonalSlopes/SlopeFormulaOfCharacterFinite.lean)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
