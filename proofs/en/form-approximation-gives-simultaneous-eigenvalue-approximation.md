# Form approximation gives simultaneous eigenvalue approximation

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%BD%A2%E5%BC%8F%E7%9A%84%E8%BF%91%E4%BC%BC%E7%BB%99%E4%B8%80%E6%95%B4%E5%A5%97%E6%9C%AC%E5%BE%81%E5%80%BC%E5%90%8C%E4%BD%99.md)

## Statement

Fix prime $\ell$ and $\iota:\overline{\mathbb Q}_\ell\simeq\mathbb C$, using its transported norm on $\mathbb C$. Let $V$ be a complex vector space with linear operators $T_j$ and linear evaluations $e_x$ for arbitrary index sets $J,X$. Assume whenever all $|e_x(v)|_\ell\le R$ then all $|e_x(T_j v)|_\ell\le R$. Let $v_0$ and finitely many $v_i$ be joint eigenvectors with eigenvalues $\theta_j,\eta_{i,j}$, respectively. Suppose $|e_{x_0}(v_0)|_\ell=1$ and $|e_x(v_0+\sum_i v_i)|_\ell\le\varepsilon$ for all $x$. There are $c_i\in\overline{\mathbb Q}_\ell$ working for every integral polynomial $P$ in the $J$ coordinates:
$$
\left|P(\iota^{-1}\theta)-\sum_i c_iP(\iota^{-1}\eta_i)\right|_\ell\le\varepsilon .
$$
Repeated eigenvalue vectors may be combined by adding coefficients. These are the quantifiers of the [limit trace](../zh/%E6%80%8E%E6%A0%B7%E4%BB%8E%E7%A8%A0%E5%AF%86Frobenius%E5%8F%96%E5%80%BC%E6%9E%84%E9%80%A0%E6%9E%81%E9%99%90%E8%BF%B9.md) approximation.

## Proof

Let $v_P=P(\theta)v_0+\sum_i P(\eta_i)v_i$. For integer constants its evaluated norm is bounded by $\varepsilon$ because those constants have norm at most one. The bound is preserved by addition using the ultrametric inequality, and under multiplication of $P$ by $X_j$ because $v_{X_jP}=T_j v_P$ and the operator preserves evaluation bounds. Thus it holds for all integral polynomials. Evaluate at $x_0$ and divide by $e_{x_0}(v_0)$ of unit norm. The choice
$$
c_i=-\frac{\iota^{-1}(e_{x_0}(v_i))}{\iota^{-1}(e_{x_0}(v_0))}
$$
is independent of $P$ and gives the claim.

In the project, the operators are common Hecke operators and evaluations read coefficients in common integral frames. Integrality supplies the bound preservation. Normalize a nonzero evaluation of the original form, use [character approximation](approximating-automorphic-forms-with-nontrivial-characters.md), and decompose the approximants into finitely many automorphic eigensummands. The lemma at every precision gives `PolyApprox` for their eigenvalues.

## Lean correspondence

- [`eigen_small_sub_finite_approx`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/EigenvectorSmallSubFiniteEigenApproxInequality.lean#L9) gives the fixed coefficients. [Formal interface](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/EigenvectorSmallSubFiniteEigenApproxInequalityStatement.lean)
- [`toPolyX_pf`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/GaloisRepresentations/SeparatingAlgebras/ToPolyX.lean#L11) normalizes, decomposes and applies the lemma.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
