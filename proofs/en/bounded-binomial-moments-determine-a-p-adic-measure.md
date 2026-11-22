# Bounded binomial moments determine a p-adic measure

[Proof catalogue](../../PROOFS.en.md) · [Reading and review status](../../STATUS.md)

Let $q$ be prime, $g\ge0$, and $c_\nu\in\mathbb C_q$ for $\nu\in\mathbb N^g$, with $\sup_\nu|c_\nu|_q<\infty$. On $C(\mathbb Z_q^g,\mathbb C_q)$ with the supremum norm there is a bounded $\mathbb C_q$-linear functional $\mu$ with $\mu\bigl(\prod_i\binom{x_i}{\nu_i}\bigr)=c_\nu$ and
$$
\|\mu\|=\sup_\nu |c_\nu|_q.
$$
For any product $F(x)=\prod_i f_i(x_i)$ of continuous functions, it is given by
$$
\mu(F)=\sum_{\nu\in\mathbb N^g} c_\nu\prod_i(\Delta^{\nu_i} f_i)(0),
\qquad \Delta f(x)=f(x+1)-f(x).
$$

### The forward differences

Let $D_\nu F$ be the successive forward differences in the $g$ coordinates, of orders $\nu_i$, evaluated at the origin. Each difference operator is a contraction for the nonarchimedean supremum norm. Thus $|D_\nu F|_q\le\|F\|_\infty$. For a product one gets $D_\nu F=\prod_i(\Delta^{\nu_i}f_i)(0)$ by taking the differences one coordinate at a time.

Here is a direct explanation for $D_\nu F\to0$ outside finite sets of multi-indices. First take a function constant on residue boxes modulo $q^r$. The shift $U_i$ in coordinate $i$ has $U_i^{q^r}=1$ on this space. The intermediate binomial coefficients of $(U_i-1)^{q^r}$ are divisible by $q$; equivalently that power is $U_i^{q^r}-1=0$ modulo $q$ in the integral group ring. Consequently $\|(U_i-1)^{q^r}\|\le q^{-1}$ on this space. It follows that $|D_\nu F|_q$ tends to zero whenever one order $\nu_i$ tends to infinity. For an arbitrary continuous $F$, use a uniform residue-box approximation by compactness and uniform continuity. All differences are contractions, so the bound on the approximation error is uniform in every $\nu$. This proves convergence outside finite boxes in $\mathbb N^g$. The case $g=0$ uses the single empty multi-index.

### Construction and norm

Define $\mu(F)=\sum_\nu c_\nu D_\nu F$. Because the summands tend to zero outside finite sets and $\mathbb C_q$ is complete and nonarchimedean, finite subsums converge to this value regardless of order. It is linear and each finite subsum has norm at most $\sup_\nu |c_\nu|_q\,\|F\|_\infty$. The same bound holds for the limit.

The polynomial $x\mapsto\binom{x}{j}$ has norm at most one on $\mathbb Z_q$ by the density of the natural numbers and the integrality of their binomial coefficients. Its forward difference equals $\binom{x}{j-1}$, with the difference of $1$ equal to zero. At zero the $m$-th forward difference is therefore $1$ for $m=j$ and $0$ otherwise. The products of these polynomials give $D_\nu\bigl(\prod_i\binom{x_i}{\rho_i}\bigr)=1$ for $\nu=\rho$ and zero otherwise. Evaluating the functional on them gives the reverse norm bound. These tests also give uniqueness. For a continuous function $F$, the series $\sum_\nu D_\nu F\prod_i\binom{x_i}{\nu_i}$ converges uniformly by the difference bound. It agrees with $F$ on the natural grid, since there the series is finite and ordinary binomial inversion in each coordinate gives $F$ back. By continuity it agrees everywhere. In particular the multivariable table of power series coefficients in the multiplicative chart can be used directly as the binomial moments, with no change of norm.

### Lean correspondence

- [`fwdDiff_tendsto_zero'`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsMeasureOfBoundedMoments.lean#L11) uses the forward-difference limit over a normed space. The same file constructs the iterated coordinate differences as `exists_multiDiff`, using the one-coordinate limit on coordinate slices.
- [`GlobalTheory.MultiMahler.exists_measure_of_bounded_moments`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/ExistsMeasureOfBoundedMoments.lean#L113) defines the functional and proves its exact norm bound by binomial tests.
- [`measure_of_products`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/JetHarmonics/MeasureOfProducts.lean#L69) applies the result to products of normalized theta series.

Status. Source-based reconstruction draft. The [Lean verification record](../../STATUS.md#lean-verification--lean-核验) describes the published formal proof.
