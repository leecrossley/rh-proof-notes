# Prescribed points in one reduced projective fiber

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E8%AE%A9%E6%8C%87%E5%AE%9A%E5%9B%BA%E5%AE%9A%E7%82%B9%E8%90%BD%E5%9C%A8%E5%90%8C%E4%B8%80%E4%B8%AA%E7%BA%A6%E5%8C%96%E5%B0%84%E5%BD%B1%E7%BA%A4%E7%BB%B4.md)

## Statement

Let $X\subseteq\mathbb P^N_{\mathbb C}$ be integral, smooth, projective of dimension $d$, and $S\subset X(\mathbb C)$ finite. There are forms $f_0,\ldots,f_d$ of one positive degree with no common zero on $X$, each nonzero generically, such that $\pi:X\to\mathbb P^d$ given by these forms is finite, with $S$ in the reduced fiber over $[1:0:\cdots:0]$. At each point of that fiber the pullback coordinates $t_j=f_j/f_0$ generate the maximal ideal and give a cotangent basis. In the fixed-point proof $S$ consists of images of coincidences in the target, and finite étale pullback preserves this reduced fiber.

## Choosing forms

Use [homogeneous first-jet interpolation](../zh/%E6%80%8E%E6%A0%B7%E7%94%A8%E9%BD%90%E6%AC%A1%E5%BC%8F%E5%90%8C%E6%97%B6%E6%8F%92%E5%80%BC%E6%9C%89%E9%99%90%E7%82%B9%E7%9A%84%E4%B8%80%E9%98%B6%E6%95%B0%E6%8D%AE.md) to find equal positive degree forms $h,g_1,\ldots,g_d$. Each $g_j$ is nonzero generically and vanishes on $S$, with their first jets a basis at each point of $S$. The form $h$ vanishes to order at least two there, and the only common zeros of all these forms lie in $S$. On the affine open $h\ne0$ let $u=(g_j/h)_j$. The [critical-value argument](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E9%81%BF%E5%BC%80%E9%9B%B6%E6%B5%8B%E9%9B%86%E5%B0%B1%E8%83%BD%E5%BE%97%E5%88%B0%E9%9D%9E%E9%80%80%E5%8C%96%E7%9A%84%E5%85%B1%E5%90%8C%E9%9B%B6%E7%82%B9.md) supplies a null set of $\boldsymbol c$ to exclude so that at every $u+\boldsymbol c=0$ the differentials span the cotangent space. For each $j$ at most one $c_j$ makes $g_j+c_jh$ generically zero, since two would make both forms generically zero. Exclude these coordinate hyperplanes too and put $f_j=g_j+c_jh$.

At $S$ the zeros and first jets are unchanged. On $h=0$ their common zeros lie in $S$. On $h\ne0$ every common zero has full cotangent rank, hence is isolated in the finite-type affine zero locus and there are only finitely many. Choose $f_0$ of the same degree nonvanishing there and generically. Each forbidden condition is a proper linear subspace, as a power of a nonzero coordinate can avoid vanishing at the specified point. The forms have no common zero. Dividing by $f_0$ preserves the cotangent basis since at a zero the linear term is multiplied by a unit value.

## Finiteness and reducedness

The pullback of $\mathcal O_{\mathbb P^d}(1)$ is the ample $\mathcal O_X(n)$ for common degree $n>0$. A positive-dimensional fiber would restrict it to a trivial ample line bundle, impossible. Thus $\pi$ is quasi-finite and proper, hence finite. On the zeroth chart with coordinate ring $B$ upstairs, the fiber is $B/(t_1,\ldots,t_d)$, a finite-dimensional algebra. At each point $y$ of the fiber, $\mathfrak m_y=(t_1,\ldots,t_d)+\mathfrak m_y^2$ by the cotangent basis. Nakayama gives $\mathfrak m_y=(t_1,\ldots,t_d)$, so each fiber local ring is $\mathbb C$. The finite algebra is the product of those Artin local rings and reduced. Pullback under a finite étale map is then a product of finite étale $\mathbb C$-algebras, also reduced.

## Lean correspondence

- [`exists_transversal_forms_first_separate`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFormsTransversalAtComplexPoints.lean#L83) uses [first-jet interpolation](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFormsVanishingComplexPointsFullJetsStatement.lean) and translation for transversality.
- [`exists_finCover_fibre_reduced`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AbelianVarietyTheory/Proofs/SatakeParameters/ExistsFiniteCoverProjSpaceReducedFibreOrigin.lean#L40) states the cover in function-field terms. The [integral fixed-point proof](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/Foundations/EtaleClopenDescent/HolomorphicLefschetzFiniteEtaleIntegral.lean#L74) uses the fiber for comparing two charts.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
