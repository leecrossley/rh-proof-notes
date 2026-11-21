# A cyclotomic subfield class number bound

[Chinese proof](../zh/%E4%B8%BA%E4%BB%80%E4%B9%88%E5%88%86%E5%9C%86%E5%AD%90%E5%9F%9F%E7%9A%84%E7%B1%BB%E6%95%B0%E5%8F%AA%E9%9C%80%E5%AF%BC%E5%AD%90%E7%9A%84%E5%AF%B9%E6%95%B0.md)

Let \(K\) embed over \(\mathbb Q\) into \(\mathbb Q(\mu_F)\), \(F\ge2\), with degree \(n\), discriminant \(D_K\) and ideal class number \(h_K\). Then \(n\le F\), \(|D_K|\le F^n\), and \(\log h_K\le3n\log F\). The first two bounds hold for \(F>0\).

**Counting ideals.** For each rational prime \(p\), enumerate the primes \(\mathfrak p_{p,i}\) above it using distinct \(i\in\{1,\ldots,n\}\), possible by \(\sum_i e_{p,i}f_{p,i}=n\). For an integral nonzero ideal with exponents \(a_{p,i}\), put \(d_i=\prod_p p^{f_{p,i}a_{p,i}}\), with missing indices of exponent zero. These determine all \(a_{p,i}\) and have product the norm. For \(X\ge1\), the number of tuples of positive integers with product at most \(X\) is at most \(X(\sum_{j\le X}1/j)^{n-1}\): fix the first \(n-1\) coordinates and bound the last by their reciprocal product times \(X\). By the integral comparison this is at most \(X(1+\log X)^{n-1}\), including \(n=1\) by the empty product. [Ideal injection](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CyclotomicBounds/ClassNumberBounds/IdealCounting/ClassB.lean#L84) · [Tuple count](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CyclotomicBounds/ClassNumberBounds/IdealCounting/ClassA.lean#L27)

Minkowski's theorem gives a representative in every class of norm at most \((4/\pi)^{r_2}n!\sqrt{|D_K|}/n^n\). The coefficient is at most one since \(4/\pi<2\), \(r_2\le n-1\), and \(2^{n-1}n!\le n^n\) by induction using \(2\le(1+1/n)^n\). Apply the count at \(\sqrt{|D_K|}\) and relax \(n-1\) to \(n\) to find
$$
\log h_K\le\tfrac12\log |D_K|+n\log(1+\tfrac12\log|D_K|).
$$
[General class number estimate](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/CyclotomicBounds/ClassNumberBounds/IdealCounting/ClassC.lean#L63)

There are \(n\) characters of \(\operatorname{Gal}(K/\mathbb Q)\), all of conductor dividing \(F\). The [conductor–discriminant identity](cyclotomic-differences-give-the-conductor-discriminant-formula.md) gives \(|D_K|\le F^n\), and \(n\le\varphi(F)\le F\). Thus \(1+\tfrac12\log|D_K|\le1+\tfrac F2\log F\le F^2\) by \(\log F\le F-1\). Substitution gives \(\log h_K\le(1/2+2)n\log F\le3n\log F\), as used in the [cohomology count](adjoining-one-root-of-unity-bounds-prime-torsion-in-cohomology.md). [Discriminant `logDisc`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/LogDisc.lean#L6) · [Final `logH`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/OddResidueBounds/LogH.lean#L7)

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
