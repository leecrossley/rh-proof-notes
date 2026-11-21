# Choosing the cyclotomic layer for small-index counting

[Chinese proof](../zh/%E6%80%8E%E6%A0%B7%E9%80%89%E4%B8%80%E5%B1%82%E5%88%86%E5%9C%86%E6%89%A9%E5%BC%A0%E8%AE%A9%E5%B0%8F%E6%8C%87%E6%A0%87%E7%95%8C%E5%8F%AF%E4%BB%A5%E4%BD%BF%E7%94%A8.md)

## Statement

Let $L$ contain $\mu_\ell$ for a prime $\ell$, or $\mu_4$ when $\ell=2$. Take $e\ge1$, $n=[L:\mathbb Q]$, $D=|\operatorname{disc}L|$, and let $s(L,\ell,e)$ be the length of the localization kernel for $(\mathbb Q_\ell/\mathbb Z_\ell)(-e)$ on the Galois group unramified outside places above $\ell$, with restriction zero at those places. There is a cyclotomic layer $L'$ of $L$, totally imaginary, containing a primitive $\ell^c$th root but none of order $\ell^{c+1}$, with $c\ge2$ if $\ell=2$. For $d=[L':L]$,
$$
\begin{gathered}
2e+1<\ell^c,\qquad 2e+1<r_2(L'),\qquad
[L':\mathbb Q]=dn,\qquad d\le(n+1)(4e+4),\\
\ell^c\le2[L':\mathbb Q],\qquad
|\operatorname{disc}L'|\le D^d(\ell^c)^{[L':\mathbb Q]},\qquad
s(L,\ell,e)\le s(L',\ell,e).
\end{gathered}
$$
Here $r_2$ counts conjugate pairs of complex embeddings. This is `SLayer`, and the first two inequalities are used by `SFew`.

## Degree and discriminant

Let $c_0$ be the largest exponent of $\ell$-power roots in $L$. It is finite by growth of cyclotomic degree, and $c_0\ge1$, or at least two if $\ell=2$. Choose minimal $m$ with $\ell^m\ge4e+4$ and take $L'=L(\mu_{\ell^{c_0+m}})$. The cyclotomic image of $G_L$ is contained in $1+\ell^{c_0}\mathbb Z_\ell$ and has an element outside the next layer. Its logarithm is a closed subgroup containing an element of valuation $c_0$, hence the entire $\ell^{c_0}\mathbb Z_\ell$. The hypothesis at two ensures the logarithm identification. Therefore $d=\ell^m$. By minimality and $\ell-1\le n$, $d\le\ell(4e+4)\le(n+1)(4e+4)$. Moreover $\ell^c\ge d\ge4e+4$ and $r_2(L')=dn/2\ge2e+2$. The degree of the contained cyclotomic field gives $\ell^c\le2\varphi(\ell^c)\le2[L':\mathbb Q]$.

Put $N=\ell^{c_0+m}$ and take a primitive $N$th root $\zeta$ generating $L'/L$, with minimal polynomial $f$. Since $\zeta$ is integral, $X^N-1=f(X)g(X)$ over $O_L$. Differentiation at $\zeta$ gives $N=\zeta f'(\zeta)g(\zeta)$. The relative different contains $f'(\zeta)$ and therefore contains $(N)$. Its absolute norm is at most $N^{[L':\mathbb Q]}$. The discriminant tower formula yields $|\operatorname{disc}L'|\le D^d N^{[L':\mathbb Q]}\le D^d(\ell^c)^{[L':\mathbb Q]}$.

## Monotonicity of length

For the layers $L_m/L$ of degree $\ell^m$, the [cyclotomic module formula](../zh/%E5%88%86%E5%9C%86%E5%A1%94%E4%B8%8A%E7%9A%84%E5%90%8C%E8%B0%83%E6%A0%B8%E4%B8%BA%E4%BB%80%E4%B9%88%E5%8F%98%E6%88%90%E4%BD%99%E6%A0%B8%E9%95%BF%E5%BA%A6.md) gives
$$
s(L_m,\ell,e)=\operatorname{length}_{\mathbb Z_\ell}
\operatorname{coker}(A_e^{\ell^m}-1).
$$
Use a fixed tower module and $A_e$ given by a chosen lift of a tower generator acting with the $e$th cyclotomic twist in the convention of `xTw`. Over the whole tower the cocycles become additive characters. Descent takes invariants of the generator power and duality turns them into the displayed cokernel. The factorization of $A_e^{\ell^m}-1$ by $A_e-1$ puts its image in the latter's image, so the higher-layer cokernel surjects onto the base-layer cokernel. This is the desired monotonicity.

## Lean correspondence

- [`SLayer`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/ModularityArgument/ClassCounting/LemmaKOfSteps.lean#L149) specifies the conditions, and [`layer_statement_holds`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/FinSLayer.lean#L4) supplies them.
- [`SLayerCut.goal_of`, `disc_cyc` and `sha_le`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/EtaleCohomology/CyclotomicDiscriminants/SLayerCut.lean) prove degree, discriminant and length. [`exists_descends` and `step0`](https://github.com/tamnd/riemann-lean/blob/9110120cdc195ee8d2fb08d2adac8b1747912d8f/lean/src/Development/AutomorphicArithmetic/AutomorphicVarieties/NumberFieldTowers/ExistsDescends.lean) supply the fixed-module identity.

Status. Translation draft based on the Chinese proof and its pinned Lean references. The Lean verification record is tracked [separately](../../STATUS.md#lean-verification--lean-核验).
