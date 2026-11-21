# Frobenius minus one on the fixed period quotient

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%9B%BA%E5%AE%9A%E5%91%A8%E6%9C%9F%E5%95%86%E9%87%8C%E7%9A%84Frobenius%E5%87%8F%E4%B8%80%E5%8F%AF%E9%80%86.md)

Let $B$ be a commutative ring with subrings $B^+,E$, and let $\varphi:B\to B$ preserve both. Let $\ell$ be prime, $t\in B^+$, and $\mathcal F_j=t^j B^++\ell B$ for $j\ge0$. Take a $\varphi$-stable subring $S\supset E$ of $B$. Assume:

- $\varphi(t)\in\mathcal F_2$, and each $q\in E$ has $t^cq\in\mathcal F_0$ for some $c\ge0$.
- $S,E$ are $\ell$-saturated in $B$. For each $k\ge0$, sequences $f_i\in S\cap\mathcal F_{i+k}$ have a sum $s\in S$ with $s-\sum_{i<j}f_i\in\mathcal F_{j+k}$ for all $j$.
- $\bigcap_j(E+\mathcal F_j)\subset E+\ell B$. For every $y\in S$ and $k\ge0$, there are $y_0\in B$ and $r\ge0$ with $y-y_0\in\mathcal F_k$ and $\varphi^r(y_0)\in E+\ell B$.
- Every sum $\sum_i\ell^i s_i$ with $s_i\in S$ can be realized in $S$ modulo $\ell^jB$ at every finite stage $j$, and $\bigcap_j(E+\ell^jB)=E$.

For $d\ge0$ and $P\in M_d(E)$, let $\Phi(x)=P\varphi(x)$ with coordinatewise Frobenius. Then $\Phi-1$ is bijective on $S^d/E^d$.

**Proof.** Working modulo $\ell$ shows $\varphi(\mathcal F_j)\subset\mathcal F_{2j}$ and $q\mathcal F_{j+c}\subset\mathcal F_j$ when $t^cq\in\mathcal F_0$. Take a common $c$ for the entries of $P$. With $F_m=\mathcal F_{m+c+1}^d$, the inequality $2(m+c+1)-c\ge m+c+2$ gives $\Phi(F_m)\subset F_{m+1}$.

For $y\in S^d$, approximate each coordinate modulo $\mathcal F_{c+1}$ by one whose Frobenius iterate is in $E+\ell B$. Take $r$ the largest required iterate, since $\varphi$ preserves $E+\ell B$. Then
$$
\Phi^ry_0=P\varphi(P)\cdots\varphi^{r-1}(P)\varphi^r(y_0)\in E^d+\ell B^d .
$$
The error remains in $F_0$, so $\Phi^r y\in E^d+F_0$. All completeness, closure and saturation hypotheses of the [difference equation lemma](two-completenesses-solve-a-frobenius-difference-equation.md) hold coordinatewise. That lemma proves the result, also trivial for $d=0$.

For the project take $B=O\otimes W(\mathbb C_\ell^\flat)$, $B^+=O\otimes W(\mathcal O_{\mathbb C_\ell^\flat})$, $E$ the étale coefficient ring, $S=B^H$ where $H$ is the kernel of the action on the cyclotomic tower, and $t$ the image of $U$. An $E$-basis of $D(T)$ maps to an $H$-fixed $B$-basis under the period comparison $J$. Thus $(B\otimes T)^H$ has coordinates $S^d$ and $J(D(T))$ has coordinates $E^d$. The basis identifies Frobenius with $P\varphi$ where $P$ is its matrix in $D(T)$. This proves the asserted bijectivity on the fixed-period quotient in `DecW`.

`near_frob` and `near_mul_of_bound` give the filtration estimates, `semi_iterate` expands the matrix product and `matrix_frob_sub_one_bijective` applies the lemma. `decompletion_matrix` and `decW_of_matrix` check and transport the hypotheses using [closure in both topologies](fixed-period-completeness-and-etale-closure.md) and [approximation in the tilt](approximating-fixed-tilt-elements-by-cyclotomic-polynomials.md). [Frobenius](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L24) · [Multiplication](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L31) · [Iteration](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L67) · [Bijection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/MatrixFrobeniusSubOneBijectiveModSubring.lean#L97) · [Period model](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DecompletionPhiSubOneBijective.lean#L25) · [Coordinate comparison](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/InertiaEigenvalues/DecWOfMatrix.lean#L40)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
